---
title: "Worklog Tuần 2"
date: 2026-07-28
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

## Tuần 2 - AWS cơ bản, thành lập nhóm và chọn đề tài

**Thời gian:** 15/06/2026 - 19/06/2026

### Mục tiêu

- Hiểu các nhóm dịch vụ AWS cơ bản, tập trung vào Compute/Database/Storage phục vụ backend.
- Tham gia nhóm thảo luận từ ngày 16/06 và thống nhất phương pháp phối hợp.
- Khảo sát đề tài phù hợp, xác định EduCloud Lite là sản phẩm thực tập.

### Giai đoạn học AWS

| Giai đoạn | Nội dung học | Nguồn tài liệu | Áp dụng |
| :--- | :--- | :--- | :--- |
| Tổng quan | Compute, Storage, Database, Networking, Security và Monitoring. | [Explore AWS Services](https://cloudjourney.awsstudygroup.com/1-explore/) | Nhận diện nhóm dịch vụ cần thiết cho phần backend/hạ tầng. |
| Tài khoản và chi phí | AWS Free Tier, credit, dịch vụ dễ phát sinh phí và cách đặt ngân sách cảnh báo. | [AWS Free Tier](https://000001.awsstudygroup.com/), [AWS Budgets](https://000007.awsstudygroup.com/) | Ưu tiên dịch vụ chi phí thấp khi thiết kế hạ tầng backend. |
| Công cụ quản trị | Cài đặt AWS CLI, profile, Region mặc định và các định dạng output. | [Getting Started with AWS CLI](https://000011.awsstudygroup.com/) | Chuẩn bị thao tác/triển khai tài nguyên backend bằng lệnh. |

### Công việc thực hiện

| Ngày | Công việc | Kết quả |
| :--- | :--- | :--- |
| 15/06 | Cài đặt và cấu hình AWS CLI (profile, region), thử các lệnh `describe`/`list` cơ bản trên EC2, S3, RDS. | Thao tác được AWS qua dòng lệnh, hiểu output JSON trả về. |
| 16/06 | Tham gia họp nhóm thảo luận đề tài, ghi biên bản họp và tổng hợp ý tưởng của các thành viên. | Bắt đầu phối hợp nhóm từ ngày 16/06/2026. |
| 17/06 | Khảo sát lựa chọn database quan hệ (Supabase PostgreSQL so với AWS RDS) cho backend LMS. | Có cơ sở chọn Supabase PostgreSQL cho giai đoạn phát triển. |
| 18/06 | Cùng nhóm xác định ba vai trò Student/Instructor/Admin; phác thảo sơ bộ các bảng dữ liệu chính (user, course, lesson). | Có bản nháp mô hình dữ liệu ban đầu. |
| 19/06 | Chia yêu cầu thành backlog phần backend (auth, course, lesson, enrollment...); ước lượng độ ưu tiên theo tuần. | Có backlog backend và kế hoạch triển khai theo giai đoạn. |

### Kết quả đạt được

- Thao tác thành thạo AWS CLI cho các dịch vụ Compute/Storage/Database cơ bản.
- Biết sử dụng AWS Budgets để kiểm soát chi phí ngay từ đầu dự án.
- Tham gia nhóm thảo luận từ ngày 16/06 và thống nhất đề tài EduCloud Lite.
- Có backlog phần backend và bản nháp mô hình dữ liệu đầu tiên.
