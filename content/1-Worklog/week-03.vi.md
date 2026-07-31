---
title: "Tuần 3 - Lên kế hoạch kiến trúc và chọn dịch vụ AWS"
menuTitle: "Tuần 3"
weight: 3
pre: "<b>1.3.</b>"
---

**Thời gian:** 22/06/2026 - 26/06/2026

## Mục tiêu

- Cùng team tìm hiểu luồng request dự kiến React -> FastAPI -> PostgreSQL.
- Học IAM, VPC, EC2 và RDS để đánh giá dự án cần dùng những dịch vụ AWS nào.
- Góp ý cùng team chốt công nghệ và lựa chọn database trước khi bắt tay code.

## Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| --- | --- | --- |
| IAM User, Policy, Role và nguyên tắc cấp quyền tối thiểu. | [Access Control with AWS IAM](https://000002.awsstudygroup.com/) | Định hình cách sau này tách quyền hạ tầng AWS khỏi các role Student/Instructor/Admin trong ứng dụng. |
| VPC, subnet, route, Security Group và cách ứng dụng được truy cập từ Internet. | [Amazon VPC Workshop](https://000003.awsstudygroup.com/) | Hình dung được luồng mạng mà một backend được host sẽ cần đến. |
| EC2/Amazon Linux, cách triển khai ứng dụng và quản lý tài nguyên compute. | [Introduction to Amazon EC2](https://000004.awsstudygroup.com/) | Hiểu được lớp hạ tầng nằm bên dưới một dịch vụ compute quản lý sẵn như Elastic Beanstalk. |
| Cơ sở dữ liệu quan hệ, PostgreSQL, SSL, backup và cách cô lập mạng. | [Amazon RDS Workshop](https://000005.awsstudygroup.com/) | Góp phần vào việc team thảo luận chọn database PostgreSQL quản lý sẵn thay vì tự host. |

## Công việc thực hiện

| Ngày | Công việc | Kết quả |
| --- | --- | --- |
| 22/06 | Xem lại bản nháp kiến trúc React → FastAPI → PostgreSQL của team, thảo luận cách chia trách nhiệm frontend/backend/database. | Chốt được hướng kỹ thuật tổng thể cho EduCloud Lite. |
| 23/06 | Tìm hiểu IAM User, Policy và nguyên tắc cấp quyền tối thiểu để chuẩn bị cho việc thiết kế authorization ở API sau này. | Có mô hình rõ ràng để tách quyền AWS khỏi role trong ứng dụng. |
| 24/06 | Học tài liệu VPC Workshop để hiểu nền tảng mạng đằng sau một backend được host. | Hiểu được cách một backend triển khai sẽ được truy cập từ Internet. |
| 25/06 | Tìm hiểu EC2 và Amazon Linux, chuẩn bị kiến thức nền cho việc team sẽ deploy bằng Elastic Beanstalk sau này. | Có cái nhìn tổng quan về lớp hạ tầng bên dưới một dịch vụ compute quản lý sẵn. |
| 26/06 | Học tài liệu RDS Workshop và thảo luận cùng team lý do nên dùng database PostgreSQL quản lý sẵn (Supabase). | Góp phần vào quyết định dùng Supabase làm database cho dự án. |

## Kết quả đạt được

- Hiểu được luồng request dự kiến và vị trí của từng dịch vụ AWS trong đó.
- Nắm được kiến thức nền về IAM, VPC, EC2 và RDS trước khi bắt tay code thật.
- Góp phần vào quyết định của team khi chọn Supabase làm database cho ứng dụng.
