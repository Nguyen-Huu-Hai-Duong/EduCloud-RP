---
title : "Kết nối EduCloud với Amazon Cognito"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### Tổng quan

Ở phần 5.3, bạn đã có một Cognito User Pool hoạt động độc lập, kiểm tra được bằng CLI. Trong phần này, bạn sẽ nối User Pool đó vào code thật của EduCloud Lite:

+ Cấu hình backend FastAPI để **xác minh** Cognito ID token và phát hành JWT nội bộ (`app/services/cognito_service.py`).
+ Cấu hình frontend React để **gọi trực tiếp** Cognito qua SDK cho các luồng đăng ký/đăng nhập/quên mật khẩu (`src/services/cognitoService.ts`, `src/auth/AuthContext.tsx`).
+ Kiểm thử toàn bộ luồng người dùng thật trên trình duyệt: đăng ký, xác thực email, đăng nhập, quên mật khẩu.

![auth flow](/images/5-Workshop/5.4-S3-onprem/auth-flow.png)

*(Ảnh trên là placeholder — bạn tự vẽ sơ đồ luồng request giữa React → Cognito → FastAPI → Supabase rồi lưu vào đường dẫn trên)*
