---
title: "Tuần 4 - Xác thực cơ bản và phân quyền"
menuTitle: "Tuần 4"
weight: 4
pre: "<b>1.4.</b>"
---

**Thời gian:** 29/06/2026 - 03/07/2026

## Mục tiêu

- Dựng luồng đăng ký, đăng nhập và phiên JWT cho môi trường phát triển.
- Giới hạn API và giao diện theo đúng vai trò người dùng.
- Giữ lớp xác thực đủ linh hoạt để sau này chuyển sang Cognito.

## Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| --- | --- | --- |
| Cấu trúc IAM Policy, Role, cấp quyền tạm thời và nguyên tắc least privilege. | [Access Control with AWS IAM](https://000002.awsstudygroup.com/) | Áp dụng tư duy tương tự để dựng authorization helper và giới hạn API theo vai trò. |
| User Pool, JWT và điểm khác biệt giữa xác thực người dùng với việc cấp quyền truy cập tài nguyên AWS. | [Amazon Cognito Across Sites](https://000141.awsstudygroup.com/) | Chuẩn bị sẵn kiến trúc để chuyển từ JWT local sang Cognito khi lên production. |

## Công việc thực hiện

| Ngày | Công việc | Kết quả |
| --- | --- | --- |
| 29/06 | Dựng user schema, cơ chế băm mật khẩu và API đăng ký/đăng nhập cho môi trường dev. | Tạo và xác thực được tài khoản local một cách an toàn. |
| 30/06 | Tạo JWT mang theo user id, email, role và thời hạn; xử lý xác thực Bearer token. | Backend nhận diện đúng người dùng ở từng request. |
| 01/07 | Dựng auth middleware và các authorization helper cho Student, Instructor, Admin. | Các API mutation chỉ được thực hiện bởi đúng vai trò. |
| 02/07 | Tạo `AuthContext`, lưu session, tự động đính kèm token và `RequireRole` ở phía frontend. | Điều hướng và các trang riêng được bảo vệ đúng theo role. |
| 03/07 | Thử nghiệm truy cập chéo vai trò; bổ sung phản hồi 401/403, security headers và giới hạn tần suất xác thực cơ bản. | Giảm nguy cơ leo thang quyền và lộ route nhạy cảm. |

## Kết quả đạt được

- Hoàn tất authentication cho môi trường dev với phiên JWT kéo dài 12 giờ.
- Chức năng Instructor/Admin được bảo vệ ở cả frontend lẫn backend.
- Đảm bảo đăng ký công khai không thể tự gán quyền Admin.
- Giữ được lối đi rõ ràng để chuyển sang Cognito mà không phải đập đi làm lại toàn bộ ứng dụng.
