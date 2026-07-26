---
title : "Thiết lập Amazon Cognito"
date : 2026-07-26
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

#### Vì sao dùng Cognito

EduCloud Lite giữ vai trò/dữ liệu nghiệp vụ (role student/instructor/admin) trong PostgreSQL, nhưng **giao toàn bộ vòng đời định danh** (đăng ký, xác nhận email, đăng nhập, quên/đặt lại mật khẩu) cho Amazon Cognito. Backend chỉ tin tưởng ID Token do Cognito ký, không tự lưu mật khẩu người dùng mới.

*(Chèn ảnh chụp màn hình các bước tạo tài nguyên của bạn vào các vị trí `![...]` bên dưới.)*

#### Bước 1 — Tạo Cognito User Pool

1. Vào **Amazon Cognito → User pools → Create user pool**.
2. Chọn phương thức đăng nhập: **Email**.
3. Password policy: dùng mặc định hoặc tùy chỉnh theo yêu cầu báo cáo của bạn.
4. Ở bước **App client**, tạo một **public app client** (**không** tạo client secret) — vì frontend React gọi thẳng Cognito từ trình duyệt bằng `amazon-cognito-identity-js`.
5. Hoàn tất tạo pool, ghi lại 3 giá trị sẽ dùng ở Bước 3: **Region**, **User pool ID**, **App client ID**.

![tạo user pool](/images/5-Workshop/5.3.1-Cognito/create-user-pool.png)

#### Bước 2 — Gắn Lambda pre sign-up trigger

Mặc định Cognito bắt người dùng tự bấm mã xác nhận gửi qua email. EduCloud Lite dùng một Lambda trigger (`EduCloud/aws/cognito-pre-signup/index.mjs`) để **tự động confirm và verify email** ngay khi người dùng tự đăng ký, giúp luồng đăng ký/đăng nhập mượt hơn còn email vẫn được đánh dấu verified cho luồng quên mật khẩu:

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

1. Tạo Lambda function (Node.js runtime), dán nội dung `index.mjs` ở trên.
2. Vào User pool vừa tạo → **User pool properties → Lambda triggers → Pre sign-up** → chọn function này.

{{% notice note %}}
Trigger chỉ tự động confirm cho **luồng tự đăng ký** (`PreSignUp_SignUp`). Các tài khoản tạo bằng `AdminCreateUser` (ví dụ script seed tài khoản demo) không đi qua trigger này — phải tự set `email_verified=true` và dùng `MessageAction=SUPPRESS` khi tạo.
{{% /notice %}}

![gắn lambda trigger](/images/5-Workshop/5.3.1-Cognito/pre-signup-trigger.png)

#### Bước 3 — Cấu hình biến môi trường

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

#### Bước 4 — Luồng xác thực hoạt động thế nào

1. Frontend (`cognitoService.ts`) đăng ký/đăng nhập trực tiếp với Cognito qua `amazon-cognito-identity-js`, nhận về **ID Token**.
2. Frontend gọi `POST /api/auth/cognito/exchange` kèm ID Token.
3. Backend (`cognito_service.verify_id_token`) tải JWKS công khai của Cognito (`https://cognito-idp.<region>.amazonaws.com/<pool-id>/.well-known/jwks.json`), verify chữ ký RS256, kiểm tra `audience`, `issuer` và `email_verified`.
4. Backend ánh xạ định danh Cognito (`sub`) sang user trong PostgreSQL theo cột `cognito_sub`, hoặc theo email nếu là tài khoản cũ đang migrate. Tài khoản Cognito mới luôn nhận role mặc định `student`.
5. Backend cấp một JWT nội bộ (`create_access_token`) — đây mới là token frontend lưu ở `sessionStorage` và gửi kèm mọi request sau đó (`Authorization: Bearer ...`).

#### Bước 5 — Kiểm thử

+ Đăng ký một tài khoản Student mới trên frontend (`http://localhost:5173/register`) → xác nhận đăng nhập được ngay (không cần nhập mã email nhờ trigger).
+ Kiểm tra bảng `users` trong Supabase có dòng mới với `cognito_sub` đã được điền.
+ Thử **Quên mật khẩu**: xác nhận `POST /api/auth/forgot-password` trả về cùng một thông điệp dù email có tồn tại hay không (chống dò email).

![test đăng ký](/images/5-Workshop/5.3.1-Cognito/test-signup.png)
