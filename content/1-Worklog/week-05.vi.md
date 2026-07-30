---
title: "Tuần 5 - Quản lý khóa học, bài học và tài nguyên"
menuTitle: "Tuần 5"
weight: 5
pre: "<b>1.5.</b>"
---

**Thời gian:** 06/07/2026 - 10/07/2026

## Mục tiêu

- Xây dựng quy trình để Instructor tạo và quản lý các khóa học của riêng mình.
- Sắp xếp curriculum theo thứ tự bài học rõ ràng.
- Hỗ trợ upload thumbnail, video và tài liệu học tập.

## Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| --- | --- | --- |
| Mô hình lưu trữ object của S3, cấu hình quyền riêng tư bucket và cách lưu tài nguyên học tập được tải lên. | [S3 Static Website Hosting](https://000057.awsstudygroup.com/) | Phác thảo bucket upload private để sau này chuyển thumbnail, video và tài liệu từ local sang S3. |
| Cách Amplify kết hợp xác thực với storage dựa trên Cognito và S3. | [Amplify Authentication and Storage](https://000134.awsstudygroup.com/) | Chuẩn bị frontend và backend sẵn sàng cho việc chuyển upload sang AWS S3 sau này. |

## Công việc thực hiện

| Ngày | Công việc | Kết quả |
| --- | --- | --- |
| 06/07 | Dựng model, schema, service và CRUD API cho course, kèm kiểm tra quyền sở hữu. | Instructor chỉ chỉnh sửa được khóa học mình sở hữu. |
| 07/07 | Xây trang danh sách, tạo và chỉnh sửa khóa học với metadata, tag, giá và trạng thái. | Hoàn thiện không gian làm việc của Instructor. |
| 08/07 | Triển khai lesson CRUD, order index, ghi chú, URL video và URL tài liệu. | Cho phép sắp xếp curriculum theo đúng thứ tự. |
| 09/07 | Dựng Curriculum Editor với thêm/sửa/xóa và kiểm tra dữ liệu đầu vào. | Kết nối giao diện biên soạn với dữ liệu lưu trữ. |
| 10/07 | Thêm cơ chế upload local, xem trước thumbnail và công cụ crop ảnh tỉ lệ 4:3 kéo thả được. | Hỗ trợ upload tài nguyên và chuẩn hóa thumbnail 1200x900. |

## Kết quả đạt được

- Hoàn thành CRUD cho Course và Lesson theo quyền sở hữu.
- Thêm các trạng thái Draft, Published và Hidden.
- Giữ nội dung curriculum riêng tư được bảo vệ.
- Thêm thao tác kéo, zoom, thay ảnh và crop cho thumbnail.
