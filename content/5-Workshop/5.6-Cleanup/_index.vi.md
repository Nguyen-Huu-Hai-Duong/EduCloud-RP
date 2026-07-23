---
title : "Dọn dẹp tài nguyên"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

#### Dọn dẹp tài nguyên

Xin chúc mừng bạn đã hoàn thành workshop!

Trong workshop này, bạn đã dựng lại toàn bộ lớp xác thực của EduCloud Lite bằng Amazon Cognito: tạo User Pool và App Client, nối chúng vào backend FastAPI (xác minh ID token qua JWKS, phát hành JWT nội bộ, tự động đồng bộ user sang Supabase) và frontend React (gọi Cognito SDK trực tiếp cho đăng ký/đăng nhập/quên mật khẩu), rồi kiểm chứng thêm các lớp bảo mật đi kèm (rate limiting, chống dò email, chống downgrade tài khoản).

#### Dọn dẹp

1. Mở Cognito console → User pool → tab **Users**, xoá các tài khoản thử nghiệm bạn đã tạo trong lúc test (CLI test user, tài khoản đăng ký qua UI...).

*(Chèn ảnh danh sách Users trước khi xoá)*

2. Nếu User Pool này chỉ tạo riêng cho workshop và không dùng tiếp, xoá luôn cả pool: User pool → **Delete user pool**, gõ tên pool để xác nhận.

*(Chèn ảnh xác nhận xoá User pool)*

3. Kiểm tra lại `backend/.env` và `frontend/.env`: đảm bảo hai file này **không** bị commit lên Git (đã có trong `.gitignore`). Không đưa `COGNITO_CLIENT_ID`, `JWT_SECRET_KEY` hay chuỗi kết nối Supabase vào bất kỳ commit hay ảnh chụp màn hình nào bạn đính vào báo cáo.

4. Trước khi triển khai ngoài môi trường local, đặt lại theo checklist bảo mật của EduCloud: `ALLOW_LEGACY_AUTH=false`, `ENABLE_DEV_AUTH=false`, thay `JWT_SECRET_KEY` bằng một chuỗi ngẫu nhiên dài, và giới hạn `CORS_ORIGINS` về đúng domain triển khai thật.

5. Dừng các tiến trình dev đang chạy local (`uvicorn`, `npm run dev`) bằng `Ctrl+C` ở từng terminal.
