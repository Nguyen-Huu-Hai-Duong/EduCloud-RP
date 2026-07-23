---
title : "Kiểm thử đăng nhập & khôi phục mật khẩu"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.4.4 </b> "
---

#### Kiểm thử đăng nhập

1. Đăng xuất, quay lại trang **Login**, đăng nhập bằng tài khoản đã xác thực ở phần 5.4.3.

Luồng thực thi: `signInWithCognito()` xác thực trực tiếp với Cognito và trả về ID token → `exchangeCognitoToken()` gửi token đó tới `POST /api/auth/cognito/exchange` → backend gọi `verify_id_token()` rồi `create_access_token()` → frontend lưu `{ user, token }` vào `sessionStorage` → điều hướng theo vai trò qua `getRoleHome()` (student → `/my-learning`).

*(Chèn ảnh sau khi đăng nhập thành công, vào đúng trang theo vai trò)*

2. Mở DevTools → Application → Session Storage, xác nhận key `educloud-auth-session` chứa JWT nội bộ (không phải Cognito ID token) — đây là token mà mọi API call tiếp theo của EduCloud sẽ đính kèm dưới dạng `Authorization: Bearer <token>`.

*(Chèn ảnh sessionStorage chứa token)*

#### Kiểm thử khôi phục mật khẩu (anti-enumeration)

3. Từ trang Login, chọn **Forgot password**, nhập email tài khoản đã tồn tại và submit. Thao tác này gọi `POST /api/auth/forgot-password`.

Ở backend, `request_password_reset()` **chỉ** gọi Cognito `forgot_password` khi tìm thấy một user trong Supabase có đúng email **và** đã có `cognito_sub` (tức đã từng đăng nhập qua Cognito ít nhất một lần). Dù gửi thành công hay không, endpoint luôn trả về cùng một thông điệp chung chung — để không lộ thông tin liệu một email có tồn tại trong hệ thống hay không (chống dò email — account enumeration).

4. Thử lại với một email **không tồn tại** trong hệ thống và so sánh response — xác nhận cả hai trường hợp trả về **y hệt** một thông điệp.

*(Chèn ảnh 2 response — email tồn tại và không tồn tại — cho thấy nội dung giống nhau)*

5. Kiểm tra hộp thư của tài khoản hợp lệ, lấy mã khôi phục Cognito gửi về, nhập mã cùng mật khẩu mới vào form đặt lại mật khẩu. Thao tác này gọi `confirmCognitoPasswordReset()` — gửi thẳng đến Cognito, **không** đi qua backend.

*(Chèn ảnh form đặt mật khẩu mới)*

6. Đăng nhập lại bằng mật khẩu mới để xác nhận luồng khôi phục hoạt động đúng.

#### Tóm tắt

Bạn đã kiểm thử đầy đủ 2 luồng còn lại mà Cognito đảm nhiệm cho EduCloud Lite: đăng nhập (kết hợp xác thực từ Cognito với JWT nội bộ để backend biết vai trò người dùng) và khôi phục mật khẩu (thiết kế chống dò email bằng cách phản hồi giống nhau bất kể tài khoản có tồn tại hay không).
