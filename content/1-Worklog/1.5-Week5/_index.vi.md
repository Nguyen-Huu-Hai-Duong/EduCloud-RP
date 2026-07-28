---
title: "Worklog Tuần 5"
date: 2026-07-28
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

## Tuần 5 - Quản lý khóa học, bài học và tài nguyên

**Thời gian:** 06/07/2026 - 10/07/2026

### Mục tiêu

- Xây dựng model, service và API cho Instructor tạo/quản lý khóa học.
- Xây dựng API quản lý bài học (lesson) có thứ tự trong curriculum.
- Xây dựng lớp abstraction upload file, chạy ở chế độ local trước khi chuyển sang S3.

### Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| :--- | :--- | :--- |
| Mô hình lưu object, upload file và phân tách dữ liệu có cấu trúc với tài nguyên nhị phân. | [S3 Static Website Hosting](https://000057.awsstudygroup.com/) | Thiết kế abstraction để thumbnail, video và tài liệu có thể chuyển từ local sang S3. |
| Access level cho file và kết hợp authentication với storage. | [Amplify Authentication and Storage](https://000134.awsstudygroup.com/) | Xác định quyền upload của Instructor và quyền đọc của Student ở tầng API. |

### Công việc thực hiện

| Ngày | Công việc | Kết quả |
| :--- | :--- | :--- |
| 06/07 | Xây dựng model, schema, service và CRUD API cho course; bổ sung kiểm tra ownership (Instructor chỉ sửa khóa học của mình). | API course hoạt động đầy đủ, có kiểm soát quyền sở hữu. |
| 07/07 | Bổ sung các trường title, description, level, category, tags, price và status (Draft/Published/Hidden) cho course. | Course có đủ thông tin nghiệp vụ và trạng thái xuất bản. |
| 08/07 | Xây dựng model, schema và CRUD API cho lesson: order_index, notes, video_url, material_url. | Instructor quản lý được curriculum theo đúng thứ tự qua API. |
| 09/07 | Viết validation cho dữ liệu course/lesson (Pydantic schema) và test CRUD bằng pytest. | Dữ liệu đầu vào được kiểm tra chặt chẽ trước khi lưu database. |
| 10/07 | Xây dựng `s3_service.save_upload()` ở chế độ local: kiểm tra định dạng/dung lượng, lưu file vào `backend/uploads`. | Backend nhận và lưu được thumbnail/tài liệu/video theo category. |

### Kết quả đạt được

- Hoàn thiện CRUD khóa học và bài học có kiểm tra ownership.
- Tách trạng thái Draft, Published và Hidden ở tầng API.
- Hỗ trợ curriculum có thứ tự, dữ liệu được validate trước khi lưu.
- Có lớp abstraction upload (local mode) sẵn sàng chuyển sang S3 ở tuần triển khai AWS.
