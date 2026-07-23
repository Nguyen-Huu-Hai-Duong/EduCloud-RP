---
title : "Kiểm thử luồng đăng ký & xác thực email"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.4.3 </b> "
---

#### Đăng ký tài khoản Student mới

1. Mở `http://localhost:5173`, vào trang **Register**, chọn vai trò **Student**, điền họ tên/email/mật khẩu và submit.

*(Chèn ảnh form đăng ký EduCloud)*

Thao tác này gọi `signUpWithCognito()` → Cognito tạo user ở trạng thái **Unconfirmed** và gửi email chứa mã xác nhận 6 số. Vì luồng này gọi thẳng Cognito, **chưa có bản ghi nào** được tạo trong bảng `users` của Supabase ở bước này.

2. Mở Cognito console → User pool → tab **Users**, xác nhận user mới xuất hiện với **Confirmation status = Unconfirmed**.

*(Chèn ảnh danh sách Users, trạng thái Unconfirmed)*

3. Quay lại ứng dụng, nhập mã 6 số vừa nhận được vào màn hình xác nhận (gọi `confirmCognitoSignUp()`). Nếu mã hết hạn/không nhận được, dùng nút gửi lại (gọi `resendCognitoConfirmation()`).

*(Chèn ảnh màn hình nhập mã xác nhận)*

4. Sau khi xác nhận thành công, kiểm tra lại Cognito console: trạng thái user chuyển thành **Confirmed**.

*(Chèn ảnh trạng thái Confirmed)*

#### Kiểm tra Supabase đã tự tạo user tương ứng

5. Đăng nhập bằng tài khoản vừa đăng ký. Lần đăng nhập đầu tiên này gọi `POST /api/auth/cognito/exchange`, kích hoạt `exchange_token()` ở backend tự động tạo một dòng mới trong bảng `users` của Supabase với `cognito_sub` được gắn với subject của Cognito và `role = student`.

6. Mở Supabase table editor, kiểm tra bảng `users`: user mới phải có `email` khớp, `cognito_sub` không rỗng, `password_hash` là `NULL` (vì tài khoản này không đi qua đường legacy).

*(Chèn ảnh bảng users trên Supabase)*

#### Tóm tắt

Bạn đã xác minh được rằng: Cognito sở hữu toàn bộ vòng đời đăng ký/xác thực email, còn Supabase chỉ được cập nhật **sau khi** có một ID token hợp lệ được trao đổi qua backend — đúng như thiết kế tách bạch giữa "ai được xác thực" (Cognito) và "ai được phép làm gì" (Supabase) của EduCloud Lite.
