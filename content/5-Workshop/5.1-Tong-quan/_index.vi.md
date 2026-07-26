---
title : "Tổng quan kiến trúc"
date : 2026-07-26
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Giới thiệu EduCloud Lite

EduCloud Lite phục vụ ba vai trò: **Student** (đăng ký học, học bài, làm bài đánh giá cuối khóa, nhận chứng chỉ), **Instructor** (tạo khóa học, thêm bài học, cấu hình bài đánh giá) và **Admin** (duyệt đơn Instructor, giám sát hệ thống).

Trước khi tích hợp AWS, ứng dụng chạy hoàn toàn cục bộ: tự xác thực bằng bcrypt, lưu file tải lên trên ổ đĩa local, không có công cụ giám sát chi phí/tài nguyên. Phần workshop này mô tả cách bổ sung ba mảng AWS sau vào kiến trúc sẵn có.

#### Kiến trúc tổng thể

```
                 ┌──────────────────────┐
                 │   Amazon Cognito     │  (1) Đăng ký / đăng nhập / quên mật khẩu
                 └──────────┬───────────┘
                             │ ID Token (JWT)
                 ┌───────────▼───────────┐
Browser (React) ─┤  POST /api/auth/      │
  Vite + TS      │  cognito/exchange     │
                 └──────────┬───────────┘
                             │ verify + map user, cấp JWT nội bộ
                 ┌───────────▼───────────┐        ┌──────────────────┐
                 │   Backend FastAPI      ├───────▶│  PostgreSQL       │
                 │   (uvicorn)            │        │  (Supabase)       │
                 └───┬───────────────┬────┘        └──────────────────┘
                     │               │
       (2) upload file│               │ (3) đọc metric
                     ▼               ▼
             ┌──────────────┐  ┌─────────────────────┐
             │  Amazon S3    │  │ CloudWatch / Cost    │
             │  (thumbnail,  │  │ Explorer (read-only) │
             │  material,    │  └─────────────────────┘
             │  video)       │
             └──────────────┘
```

+ **(1) Cognito**: sở hữu toàn bộ vòng đời tài khoản (signup, xác nhận email, đăng nhập, reset mật khẩu). Backend chỉ verify ID Token do Cognito phát hành rồi ánh xạ sang user trong PostgreSQL.
+ **(2) S3**: khi `UPLOAD_STORAGE=s3`, backend đẩy file trực tiếp lên bucket S3 thay vì lưu ở `backend/uploads`.
+ **(3) CloudWatch / Cost Explorer**: khi bật `AWS_MONITORING_ENABLED=true`, backend đọc (read-only) dung lượng S3 và chi phí AWS tháng hiện tại để hiển thị trên trang `/admin/health`.

Ba phần tiếp theo trong workshop sẽ đi sâu vào từng mảng, theo đúng thứ tự triển khai thực tế: Cognito trước (vì mọi API đều cần user đã xác thực), sau đó S3 (phục vụ nghiệp vụ upload), cuối cùng là deploy và bật giám sát.
