---
title: "Worklog Tuần 6"
date: 2026-07-28
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

## Tuần 6 - Ghi danh, học tập và theo dõi tiến độ

**Thời gian:** 13/07/2026 - 17/07/2026

### Mục tiêu

- Xây dựng API catalog khóa học công khai, chỉ trả outline (không lộ nội dung riêng tư).
- Xây dựng API ghi danh (enrollment) và API tiến độ học tập (progress).
- Xây dựng API tổng hợp dữ liệu cho dashboard Student/Instructor.

### Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| :--- | :--- | :--- |
| Luồng frontend đăng nhập, truy cập API và sử dụng storage theo access level. | [Amplify Authentication and Storage](https://000134.awsstudygroup.com/) | Thiết kế điều kiện chỉ người đã ghi danh mới truy cập nội dung học qua API. |
| Cache nội dung tĩnh tại edge và bảo vệ origin S3. | [CloudFront with S3 Origin](https://000094.awsstudygroup.com/) | Chuẩn bị hướng phân phối video, thumbnail và tài liệu cho Learning Page. |

### Công việc thực hiện

| Ngày | Công việc | Kết quả |
| :--- | :--- | :--- |
| 13/07 | Xây dựng endpoint public course (danh sách + chi tiết khóa học Published), chỉ trả outline bài học. | Người dùng chưa đăng nhập xem được catalog nhưng không thấy nội dung riêng tư. |
| 14/07 | Triển khai `enrollment_service`/API với unique constraint (course, student) và kiểm tra role Student. | Ghi danh idempotent, không tạo bản ghi trùng khi gọi lại API. |
| 15/07 | Xây dựng API trả nội dung học đầy đủ (video, notes, tài liệu) chỉ cho Student đã ghi danh hoặc chủ khóa học. | Kiểm soát được ai được xem nội dung học ở tầng API, không chỉ ở UI. |
| 16/07 | Tạo `progress_service`/API để complete/undo lesson; tính số bài đã học và phần trăm hoàn thành. | Tiến độ được lưu và tính toán chính xác theo từng Student và lesson. |
| 17/07 | Xây dựng API tổng hợp My Learning (Student) và thống kê enrollment/completion (Instructor); viết test cho enrollment/progress. | Có API dashboard trả dữ liệu thật từ Supabase, có test bảo vệ logic. |

### Kết quả đạt được

- Public API chỉ trả outline, không làm lộ video và tài liệu riêng tư.
- API ghi danh idempotent, API tiến độ lưu đúng theo từng Student và lesson.
- API dashboard Student/Instructor phản ánh dữ liệu thật thay vì số liệu cố định.
- Có test tự động cho enrollment và progress.
