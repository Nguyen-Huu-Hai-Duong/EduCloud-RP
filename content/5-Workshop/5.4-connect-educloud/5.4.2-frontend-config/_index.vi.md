---
title : "Cấu hình frontend kết nối Cognito"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

Trong phần này, bạn cấu hình frontend React để gọi thẳng Cognito bằng SDK `amazon-cognito-identity-js`, thay vì chỉ gọi qua backend.

1. Mở `frontend/.env`, điền cùng Region/User Pool ID/Client ID đã dùng ở phần backend:

```dotenv
VITE_API_BASE_URL=http://127.0.0.1:8001/api
VITE_COGNITO_REGION=ap-southeast-1
VITE_COGNITO_USER_POOL_ID=ap-southeast-1_xxxxxxxxx
VITE_COGNITO_CLIENT_ID=xxxxxxxxxxxxxxxxxxxxxxxxxx
VITE_ALLOW_LEGACY_AUTH=true
```

2. Khởi động lại dev server để Vite nạp biến môi trường mới:

```powershell
cd frontend
npm run dev
```

*(Chèn ảnh terminal frontend chạy thành công tại localhost:5173)*

#### Frontend gọi Cognito trực tiếp như thế nào

`src/services/cognitoService.ts` bọc SDK Cognito thành các hàm dùng lại được:

+ `signUpWithCognito(fullName, email, password)` — gửi 2 attribute `email` và `name`, khớp với 2 required attribute đã cấu hình ở User Pool.
+ `confirmCognitoSignUp(email, code)` — xác nhận mã 6 số gửi qua email.
+ `resendCognitoConfirmation(email)` — gửi lại mã nếu hết hạn.
+ `signInWithCognito(email, password)` — trả về **ID token** (không phải access token) để gửi cho backend.
+ `confirmCognitoPasswordReset(email, code, password)` — xác nhận mã khôi phục và đặt mật khẩu mới, gọi thẳng Cognito, không qua backend.

`src/auth/AuthContext.tsx` là nơi phối hợp toàn bộ luồng:

```ts
async signIn(email, password) {
  if (isCognitoConfigured) {
    try {
      const idToken = await signInWithCognito(email, password);
      const response = await exchangeCognitoToken(idToken); // POST /api/auth/cognito/exchange
      persist({ user, token: response.data.token });
      return { user };
    } catch (error) {
      // chỉ rơi xuống legacy login khi đang dev, bật VITE_ALLOW_LEGACY_AUTH,
      // và lỗi là UserNotFoundException/NotAuthorizedException
    }
  }
  // legacy login: POST /api/auth/login
}
```

Vì `VITE_COGNITO_USER_POOL_ID`/`VITE_COGNITO_CLIENT_ID` giờ đã có giá trị, biến `isCognitoConfigured` sẽ là `true`, và mọi thao tác đăng ký/đăng nhập trên UI sẽ ưu tiên đi qua Cognito thật thay vì gọi thẳng `/api/auth/register` hay `/api/auth/login` kiểu cũ.
