---
title: "Worklog Tuần 8"
date: 2026-07-28
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

## Tuần 8 - Kiểm tra cuối, hoàn thiện báo cáo và nộp bài

**Thời gian:** 27/07/2026 - 31/07/2026

**Hạn nộp workshop:** 31/07/2026

### Mục tiêu

- Đóng phạm vi backend/hạ tầng và không bổ sung thay đổi rủi ro trước khi nộp.
- Chạy lại toàn bộ test backend, siết cấu hình bảo mật production và xác minh các dịch vụ AWS.
- Phối hợp với thành viên frontend hoàn thiện Hugo workshop và hồ sơ nộp bài.

### Kiểm tra cuối project và AWS

| Phạm vi kiểm tra | Hoạt động xác minh | Minh chứng nộp bài |
| :--- | :--- | :--- |
| Danh tính và bảo mật | Kiểm tra login/JWT, đặt `ALLOW_LEGACY_AUTH`/`ENABLE_DEV_AUTH` đúng cho production, IAM role và secret trong Parameter Store. | Screenshot xác thực, ghi chú cấu hình và link mã nguồn. |
| Hosting ứng dụng | Kiểm tra Elastic Beanstalk health check, log CloudWatch, CORS và biến môi trường production. | Link EduCloud public và trạng thái triển khai thành công. |
| Lưu trữ và dữ liệu | Xác minh phân phối S3 private qua CloudFront, kết nối Supabase, đường dẫn upload và role lấy từ database. | Sơ đồ kiến trúc và ảnh trong workshop. |
| Tài liệu | Rà soát proposal, worklog, blogs, events, workshop, self-assessment và feedback ở cả hai ngôn ngữ. | Hugo report public và GitHub repository. |

### Kế hoạch công việc và tiến độ hiện tại

| Ngày | Công việc | Kết quả cần đạt |
| :--- | :--- | :--- |
| 27/07 | Chạy lại toàn bộ bộ test backend bằng pytest; sửa lỗi phát sinh nếu có. | Toàn bộ test pass, backend ổn định trước khi nộp. |
| 28/07 | Rà soát cấu hình production (`APP_ENV`, `ALLOW_LEGACY_AUTH=false`, `ENABLE_DEV_AUTH=false`, `JWT_SECRET_KEY` dài ngẫu nhiên, `CORS_ORIGINS`). | Backend production không còn cấu hình chỉ dành cho dev. |
| 29/07 | Kiểm tra CloudWatch log/metrics và Cost Explorer trên trang Admin Health; rà soát sơ đồ AWS, screenshot cho phần Workshop. | Số liệu giám sát hiển thị đúng; mentor có thể hiểu nội dung nộp bài. |
| 30/07 | Phối hợp thành viên frontend chạy checklist demo (login, xem khóa học, ghi danh, học bài, assessment, certificate); đọc lại báo cáo bản Anh/Việt. | Các luồng demo hoạt động qua website public, Hugo report không còn placeholder. |
| 31/07 | Chuẩn bị hồ sơ cuối và gửi website, repository mã nguồn, workshop cùng các file PDF được chọn. | Nộp workshop đúng hạn. |

### Kết quả hiện tại

- Backend FastAPI chạy ổn định trên Elastic Beanstalk, đọc secret production từ Parameter Store.
- Toàn bộ test backend pass, cấu hình production đã được siết chặt (tắt legacy/dev auth).
- CloudWatch và Cost Explorer hiển thị đúng số liệu trên trang Admin Health.
- S3, CloudFront, Supabase đã kết nối ổn định với backend production.
- Công việc còn lại chỉ gồm phối hợp kiểm tra cuối với frontend, rà soát minh chứng và nộp bài.
