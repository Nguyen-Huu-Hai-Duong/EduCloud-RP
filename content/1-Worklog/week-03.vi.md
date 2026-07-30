---
title: "Tuần 3 - Xây dựng nền tảng backend và database"
menuTitle: "Tuần 3"
weight: 3
pre: "<b>1.3.</b>"
---

**Thời gian:** 22/06/2026 - 26/06/2026

## Mục tiêu

- Kết nối FastAPI với Supabase PostgreSQL thông qua SQLAlchemy.
- Dựng khung models, schemas, services và routes cho backend.
- Thiết lập cấu hình môi trường, ghi log và kiểm tra kết nối database.

## Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| --- | --- | --- |
| IAM User, Policy, Role và nguyên tắc cấp quyền tối thiểu. | [Access Control with AWS IAM](https://000002.awsstudygroup.com/) | Tách bạch quyền quản trị hạ tầng AWS với các role Student/Instructor/Admin trong ứng dụng. |
| VPC, subnet, route, Security Group và cách ứng dụng được truy cập từ Internet. | [Amazon VPC Workshop](https://000003.awsstudygroup.com/) | Vạch ra luồng mạng phục vụ backend và database. |
| EC2/Amazon Linux, cách triển khai ứng dụng và quản lý tài nguyên compute. | [Introduction to Amazon EC2](https://000004.awsstudygroup.com/) | Hiểu được lớp hạ tầng nằm bên dưới Elastic Beanstalk. |
| Cơ sở dữ liệu quan hệ, PostgreSQL, SSL, backup và cách cô lập mạng. | [Amazon RDS Workshop](https://000005.awsstudygroup.com/) | Thiết kế schema SQLAlchemy và đường kết nối an toàn tới Supabase PostgreSQL. |

## Công việc thực hiện

| Ngày | Công việc | Kết quả |
| --- | --- | --- |
| 22/06 | Vạch ra kiến trúc React → FastAPI → PostgreSQL, phân rõ trách nhiệm giữa frontend/backend/database. | Có được sơ đồ request flow và bộ công nghệ chính thức cho EduCloud. |
| 23/06 | Dựng `config.py`, `.env.example`, cấu hình SQLAlchemy trỏ tới chuỗi kết nối SSL của Supabase. | Backend kết nối ổn định tới PostgreSQL qua session pooler. |
| 24/06 | Dựng các model nền tảng: user, course, lesson, enrollment và progress. | Database thể hiện đúng các mối quan hệ nghiệp vụ cốt lõi. |
| 25/06 | Bổ sung Pydantic schemas, service layer, router và các response helper. | API có cấu trúc nhất quán, dễ kiểm thử và mở rộng thêm sau này. |
| 26/06 | Thêm cơ chế tạo bảng lúc khởi động, migration tương thích ngược, script kiểm tra database và dữ liệu seed cho môi trường dev. | Có thể dựng lại môi trường mới nhanh chóng bằng các lệnh có sẵn. |

## Kết quả đạt được

- FastAPI kết nối ổn định với Supabase PostgreSQL qua `psycopg2`.
- Định hình xong cấu trúc backend theo hướng router → service → model.
- Có sẵn script kiểm tra kết nối database mà không làm lộ thông tin mật khẩu.
- Chuẩn bị xong dữ liệu mẫu cho các role Student, Instructor và Admin.
