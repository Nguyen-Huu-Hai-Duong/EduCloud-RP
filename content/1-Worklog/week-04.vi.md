---
title: "Tuần 4 - Đào sâu kiến thức AWS và chuẩn bị backend"
menuTitle: "Tuần 4"
weight: 4
pre: "<b>1.4.</b>"
---

**Thời gian:** 29/06/2026 - 03/07/2026

## Mục tiêu

- Tìm hiểu Cognito User Pool và cách xác thực sẽ hoạt động trong EduCloud Lite.
- Xem lại thiết kế IAM Policy và nguyên tắc least privilege kỹ hơn.
- Dựng môi trường phát triển backend cục bộ và lên kế hoạch code API cho tuần sau.

## Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| --- | --- | --- |
| Cấu trúc IAM Policy và nguyên tắc cấp quyền tối thiểu. | [Access Control with AWS IAM](https://000002.awsstudygroup.com/) | Củng cố mô hình phân quyền dự kiến áp dụng cho các route API. |
| User Pool, app client, JWT và sự khác biệt giữa xác thực và cấp quyền. | [Amazon Cognito Workshop](https://000141.awsstudygroup.com/) | Làm rõ cách danh tính (Cognito) và role ứng dụng sẽ được tách riêng trong thiết kế. |

## Công việc thực hiện

| Ngày | Công việc | Kết quả |
| --- | --- | --- |
| 29/06 | Xem lại cấu trúc IAM Policy và nguyên tắc least privilege kỹ hơn. | Củng cố mô hình phân quyền dự kiến cho API. |
| 30/06 | Học tài liệu Cognito Workshop để hiểu User Pool, app client và JWT. | Hiểu được cách xác thực và phân quyền sẽ tách biệt nhau sau này. |
| 01/07 | Dựng môi trường phát triển Python/FastAPI cục bộ, đọc qua khung project ban đầu của team. | Sẵn sàng bắt đầu đóng góp code backend. |
| 02/07 | Xem lại schema database dự kiến (users, courses, lessons) cùng team. | Thống nhất mô hình dữ liệu trước khi viết code API. |
| 03/07 | Lên kế hoạch các endpoint Course và Lesson API sẽ xây dựng tuần sau. | Có danh sách việc rõ ràng để bước vào tuần 5. |

## Kết quả đạt được

- Hiểu rõ sự khác biệt giữa xác thực (Cognito) và phân quyền ở tầng ứng dụng.
- Chuẩn bị xong môi trường phát triển local để bắt đầu đóng góp code backend.
- Lên kế hoạch cho phần Course và Lesson API sẽ làm ở tuần tiếp theo.
