---
title : "Setting up Amazon Cognito"
date : 2026-07-26
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

#### Why Cognito

EduCloud Lite keeps business roles/data (student/instructor/admin role) in PostgreSQL, but **hands off the entire identity lifecycle** (sign-up, email confirmation, sign-in, forgot/reset password) to Amazon Cognito. The backend only trusts the ID Token signed by Cognito and never stores a new user's password itself.

*(Insert your own screenshots of each resource-creation step at the `![...]` placeholders below.)*

#### Step 1 — Create a Cognito User Pool

1. Go to **Amazon Cognito → User pools → Create user pool**.
2. Choose **Email** as the sign-in option.
3. Password policy: keep the default or customize it as your report requires.
4. At the **App client** step, create a **public app client** (**no** client secret) — because the React frontend calls Cognito directly from the browser using `amazon-cognito-identity-js`.
5. Finish creating the pool and note down the three values needed in Step 3: **Region**, **User pool ID**, **App client ID**.

![create user pool](/images/5-Workshop/5.3.1-Cognito/create-user-pool.png)

#### Step 2 — Attach the pre sign-up Lambda trigger

By default, Cognito makes users enter a confirmation code emailed to them. EduCloud Lite uses a Lambda trigger (`EduCloud/aws/cognito-pre-signup/index.mjs`) to **auto-confirm and auto-verify email** as soon as a user self-registers, making the sign-up/sign-in flow smoother while the email is still marked verified for the forgot-password flow:

```js
export const handler = async (event) => {
  if (event.triggerSource === 'PreSignUp_SignUp') {
    event.response.autoConfirmUser = true;
    if (event.request.userAttributes.email) {
      event.response.autoVerifyEmail = true;
    }
  }
  return event;
};
```

1. Create a Lambda function (Node.js runtime) and paste the `index.mjs` content above.
2. On the User pool just created, go to **User pool properties → Lambda triggers → Pre sign-up** and select this function.

{{% notice note %}}
The trigger only auto-confirms the **self-registration flow** (`PreSignUp_SignUp`). Accounts created with `AdminCreateUser` (for example, the demo-account seed script) do not go through this trigger — they must have `email_verified=true` set explicitly and use `MessageAction=SUPPRESS` when created.
{{% /notice %}}

![attach lambda trigger](/images/5-Workshop/5.3.1-Cognito/pre-signup-trigger.png)

#### Step 3 — Configure environment variables

`backend/.env`:

```dotenv
COGNITO_REGION=ap-southeast-1
COGNITO_USER_POOL_ID=ap-southeast-1_xxxxxxxxx
COGNITO_CLIENT_ID=xxxxxxxxxxxxxxxxxxxxxxxxxx
```

`frontend/.env`:

```dotenv
VITE_COGNITO_REGION=ap-southeast-1
VITE_COGNITO_USER_POOL_ID=ap-southeast-1_xxxxxxxxx
VITE_COGNITO_CLIENT_ID=xxxxxxxxxxxxxxxxxxxxxxxxxx
```

#### Step 4 — How the authentication flow works

1. The frontend (`cognitoService.ts`) signs up/signs in directly with Cognito via `amazon-cognito-identity-js` and receives an **ID Token**.
2. The frontend calls `POST /api/auth/cognito/exchange` with that ID Token.
3. The backend (`cognito_service.verify_id_token`) fetches Cognito's public JWKS (`https://cognito-idp.<region>.amazonaws.com/<pool-id>/.well-known/jwks.json`), verifies the RS256 signature, and checks `audience`, `issuer`, and `email_verified`.
4. The backend maps the Cognito identity (`sub`) to a user in PostgreSQL via the `cognito_sub` column, or by email for an existing account being migrated. New Cognito identities always get the default `student` role.
5. The backend issues an internal JWT (`create_access_token`) — this is the token the frontend stores in `sessionStorage` and sends with every subsequent request (`Authorization: Bearer ...`).

#### Step 5 — Testing

+ Register a new Student account on the frontend (`http://localhost:5173/register`) → confirm you can sign in immediately (no email code needed, thanks to the trigger).
+ Check the `users` table in Supabase for the new row with `cognito_sub` populated.
+ Try **Forgot password**: confirm `POST /api/auth/forgot-password` returns the same message whether or not the email exists (anti account-enumeration).

![test sign-up](/images/5-Workshop/5.3.1-Cognito/test-signup.png)
