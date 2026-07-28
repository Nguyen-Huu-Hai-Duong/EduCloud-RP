---
title: "Worklog Tuần 3"
date: 2026-07-28
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

## Tuần 3 - Thiết kế hệ thống và xây dựng khung backend đầu tiên

**Thời gian:** 22/06/2026 - 26/06/2026

### Mục tiêu

- Cùng nhóm thiết kế kiến trúc tổng thể hệ thống EduCloud Lite (frontend, backend, database, AWS).
- Khởi tạo project backend, kết nối được tới database.
- Xác định cấu trúc thư mục chuẩn cho backend (routes/services/models/schemas).

### Giai đoạn thiết kế và triển khai

| Giai đoạn | Nội dung | Kết quả |
| :--- | :--- | :--- |
| Thiết kế kiến trúc | Vẽ sơ đồ luồng dữ liệu tổng thể (User → Cognito → Backend → Database/S3), xác định công nghệ từng phần. | Có bản kiến trúc hệ thống được cả nhóm thống nhất. |
| Chuẩn hóa backend | Nghiên cứu FastAPI + SQLAlchemy, cấu trúc thư mục `routes`/`services`/`models`/`schemas`. | Xác định cấu trúc project chuẩn cho toàn bộ backend. |
| Kết nối database | Tạo project Supabase PostgreSQL, lấy connection string Session Pooler. | Backend kết nối được database qua SQLAlchemy. |

### Công việc thực hiện

| Ngày | Công việc | Kết quả |
| :--- | :--- | :--- |
| 22/06 | Họp nhóm thiết kế kiến trúc tổng thể hệ thống (frontend/backend/database/AWS). | Có sơ đồ kiến trúc được cả nhóm thống nhất. |
| 23/06 | Khởi tạo project backend bằng FastAPI, cấu hình cấu trúc thư mục `routes`/`services`/`models`/`schemas`. | Project backend khởi tạo thành công, chạy được `uvicorn` ở local. |
| 24/06 | Tạo project Supabase, cấu hình `config.py`/`.env` và kết nối SQLAlchemy tới PostgreSQL (SSL). | Backend kết nối ổn định tới database qua session pooler. |
| 25/06 | Xây dựng model nền tảng đầu tiên (User) và endpoint health-check `/`. | Backend phản hồi được request đầu tiên, ghi/đọc được bảng users. |
| 26/06 | Tổng hợp kiến trúc và tiến độ backend vào ghi chú nội bộ của nhóm. | Có ghi chú kiến trúc đầy đủ để tham khảo khi viết báo cáo sau này. |

### Kết quả đạt được

- Có bản kiến trúc hệ thống EduCloud Lite được cả nhóm thống nhất.
- Khởi tạo thành công project backend (FastAPI + SQLAlchemy).
- Backend kết nối ổn định tới Supabase PostgreSQL.
- Có model và endpoint đầu tiên hoạt động được, sẵn sàng phát triển các tính năng tiếp theo.
