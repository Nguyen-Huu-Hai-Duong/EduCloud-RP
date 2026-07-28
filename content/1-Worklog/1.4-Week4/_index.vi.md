---
title: "Worklog Tuần 4"
date: 2026-07-28
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

## Tuần 4 - Xác thực cơ bản và phân quyền

**Thời gian:** 29/06/2026 - 03/07/2026

### Mục tiêu

- Xây dựng API đăng ký, đăng nhập và cấp JWT cho môi trường phát triển.
- Bảo vệ API theo vai trò người dùng bằng middleware/dependency.
- Chuẩn bị lớp abstraction để chuyển sang Cognito ở giai đoạn production.

### Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| :--- | :--- | :--- |
| IAM Policy, Role, temporary access và nguyên tắc least privilege. | [Access Control with AWS IAM](https://000002.awsstudygroup.com/) | Thiết kế authorization helper và giới hạn API theo vai trò. |
| User Pool, JWT và sự khác nhau giữa xác thực người dùng với cấp quyền truy cập tài nguyên AWS. | [Amazon Cognito Across Sites](https://000141.awsstudygroup.com/) | Chuẩn bị kiến trúc chuyển từ local JWT sang Cognito ở production. |

### Công việc thực hiện

| Ngày | Công việc | Kết quả |
| :--- | :--- | :--- |
| 29/06 | Xây dựng `security.py`: hash mật khẩu bằng bcrypt, hàm tạo/giải mã JWT (`create_access_token`, `decode_access_token`). | Backend có cơ chế mã hoá mật khẩu và cấp token an toàn. |
| 30/06 | Xây dựng route `POST /api/auth/register` và `POST /api/auth/login`, trả về JWT khi đăng ký/đăng nhập thành công. | Đăng ký/đăng nhập hoạt động end-to-end qua API. |
| 01/07 | Xây dựng `auth_middleware.py`: dependency `get_current_user` đọc `Authorization: Bearer` và giải mã token. | Mọi route cần đăng nhập đều xác thực được người gọi. |
| 02/07 | Xây dựng helper phân quyền theo vai trò (`require_instructor`, kiểm tra `role` trong token) áp cho các route nhạy cảm. | API chỉ cho đúng vai trò Student/Instructor/Admin truy cập. |
| 03/07 | Viết test cho luồng đăng ký/đăng nhập/token hết hạn bằng pytest. | Có bộ test xác nhận auth hoạt động đúng trước khi phát triển tiếp. |

### Kết quả đạt được

- Hoàn thiện API đăng ký/đăng nhập, cấp JWT cho môi trường phát triển.
- Có middleware xác thực và helper phân quyền dùng chung cho toàn bộ API.
- Có test tự động cho luồng auth, chạy được bằng pytest.
- Thiết kế theo hướng dễ thay thế bằng Cognito ở giai đoạn production (tuần 7).
