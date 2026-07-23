---
title : "Giới thiệu"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Giới thiệu về Amazon Cognito

+ **Amazon Cognito** là dịch vụ quản lý danh tính (identity) của AWS, cung cấp sẵn các luồng đăng ký, đăng nhập, xác thực email/số điện thoại, khôi phục mật khẩu và phát hành token chuẩn OAuth2/OIDC (ID token, Access token, Refresh token) mà không cần tự xây dựng và vận hành hệ thống lưu mật khẩu.
+ Thành phần trung tâm là **User Pool** — một thư mục người dùng có thể cấu hình chính sách mật khẩu, thuộc tính bắt buộc, cách xác thực (email/username), MFA... Mỗi ứng dụng client kết nối vào User Pool thông qua một **App Client**.
+ Cognito ký các token bằng khóa riêng theo chuẩn **JWKS** (JSON Web Key Set), cho phép backend xác minh token mà không cần gọi ngược lại Cognito ở mỗi request.

#### Vai trò của Cognito trong kiến trúc EduCloud Lite

EduCloud Lite tách bạch rõ hai vai trò:

+ **Amazon Cognito** sở hữu mật khẩu, mã xác nhận email và luồng khôi phục mật khẩu. Đây là nguồn xác thực (authentication) duy nhất cho tài khoản mới.
+ **Supabase PostgreSQL** vẫn là cơ sở dữ liệu ứng dụng và là nơi lưu **vai trò (role)** của người dùng (student/instructor/admin), tiến trình học tập, khoá học... Cognito không biết gì về vai trò này.

Luồng xác thực tổng quát:

```text
React + Vite frontend (localhost:5173)
              |
              | Đăng ký / đăng nhập trực tiếp qua Cognito SDK
              v
Amazon Cognito User Pool (xác thực email, khôi phục mật khẩu)
              |
              | Cognito ID token đã xác thực (JWT, RS256)
              v
FastAPI backend (localhost:8001)  --  xác minh token qua JWKS,
              |                        phát hành JWT nội bộ EduCloud
              | SQLAlchemy + psycopg2
              v
Supabase PostgreSQL (bảng users, gắn cognito_sub, chứa role)
```

*(Chèn ảnh sơ đồ kiến trúc bạn tự vẽ tại đây, ví dụ lưu vào `/images/5-Workshop/5.1-Workshop-overview/architecture.png`)*

Trong workshop, bạn sẽ đi qua hai đường xác thực song song mà EduCloud Lite hỗ trợ:

+ **Đường Cognito (chính thức)** — mọi tài khoản đăng ký mới đều đi qua Cognito; backend chỉ chấp nhận ID token đã được Cognito ký và đã xác thực email (`email_verified = true`).
+ **Đường legacy (chỉ dùng khi phát triển)** — một cơ chế đăng nhập bằng bcrypt/JWT nội bộ, được bật bằng cờ `ALLOW_LEGACY_AUTH`, chỉ tồn tại để các tài khoản seed cũ còn dùng được trong lúc chờ migrate sang Cognito. Cờ này bắt buộc phải tắt khi triển khai thật.
