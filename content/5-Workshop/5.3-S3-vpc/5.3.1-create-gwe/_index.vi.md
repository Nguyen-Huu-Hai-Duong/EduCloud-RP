---
title : "Tạo Cognito User Pool"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.3.1 </b> "
---

1. Mở [Amazon Cognito console](https://ap-southeast-1.console.aws.amazon.com/cognito/v2/idp/user-pools?region=ap-southeast-1), chọn **Create user pool**.

*(Chèn ảnh màn hình danh sách User pools tại đây)*

2. **Configure sign-in experience**
+ Cognito user pool sign-in options: chọn **Email** (người dùng đăng nhập bằng địa chỉ email, khớp với cách EduCloud gọi `signInWithCognito(email, password)`).

*(Chèn ảnh bước chọn sign-in option)*

3. **Configure security requirements**
+ Password policy: dùng mặc định của Cognito (tối thiểu 8 ký tự, có chữ hoa/thường/số/ký tự đặc biệt) — đủ mạnh cho một LMS thật.
+ Multi-factor authentication: chọn **No MFA** để đơn giản hoá lab (README của EduCloud có ghi chú MFA là hướng nâng cao dành cho tài khoản Admin sau này).
+ User account recovery: giữ **Enable self-service account recovery**, phương thức khôi phục là **Email only**.

4. **Configure sign-up experience**
+ Bật **Enable self-registration**.
+ Cognito assigns user confirmation: chọn **Send email message, verify email address**.
+ Required attributes: chọn thêm **name**, ngoài **email** đã bắt buộc sẵn — khớp với 2 attribute mà `signUpWithCognito()` trong `cognitoService.ts` gửi lên (`email`, `name`).

*(Chèn ảnh bước cấu hình sign-up experience)*

5. **Configure message delivery**
+ Email provider: chọn **Send email with Cognito** (đủ dùng cho lab; production nên chuyển sang Amazon SES).

6. **Integrate your app**
+ User pool name: đặt ví dụ `educloud-lite-user-pool`.
+ Hosted authentication pages: **không bật** — EduCloud dùng UI đăng nhập tự viết bằng React, gọi thẳng Cognito SDK, không dùng Hosted UI.
+ Initial app client: đặt tên ví dụ `educloud-lite-web-client`, loại **Public client** (không cần client secret vì client chạy trên trình duyệt).

*(Chèn ảnh bước Integrate your app)*

7. **Review and create**, kiểm tra lại các lựa chọn rồi bấm **Create user pool**.

*(Chèn ảnh xác nhận tạo thành công)*

8. Sau khi tạo xong, mở lại User pool vừa tạo và ghi lại **User pool ID** (dạng `ap-southeast-1_xxxxxxxxx`) — bạn sẽ dùng giá trị này ở phần 5.3.2 và 5.4.
