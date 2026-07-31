---
title: "Tuần 5 - Xây dựng Course & Lesson API phía backend"
menuTitle: "Tuần 5"
weight: 5
pre: "<b>1.5.</b>"
---

**Thời gian:** 06/07/2026 - 10/07/2026

## Mục tiêu

- Xây dựng Course API: model, schema, CRUD route và kiểm tra quyền sở hữu.
- Xây dựng Lesson API: curriculum có thứ tự, notes và các field URL video/tài liệu.
- Học kiến thức nền S3 để chuẩn bị cho phần upload/storage team sẽ làm sau.

## Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| --- | --- | --- |
| Mô hình lưu trữ object của S3, cấu hình quyền riêng tư bucket và cách lưu tài nguyên học tập được tải lên. | [Amazon S3 Security Best Practices](https://000069.awsstudygroup.com/) | Chuẩn bị nền tảng cho phần lưu trữ tài nguyên khóa học riêng tư mà team sẽ làm sau. |
| Cách Amplify kết hợp xác thực với storage dựa trên Cognito và S3. | [Amplify Authentication and Storage](https://000134.awsstudygroup.com/) | Cho thêm bối cảnh về cách upload sau này sẽ kết nối với dữ liệu Course/Lesson mà mình đang xây API. |

## Công việc thực hiện

| Ngày | Công việc | Kết quả |
| --- | --- | --- |
| 06/07 | Dựng model, schema và CRUD endpoint cho Course, kèm kiểm tra quyền sở hữu để Instructor chỉ sửa được khóa học của mình. | Instructor tạo, cập nhật và quản lý khóa học được qua API. |
| 07/07 | Thêm validation cho metadata khóa học: tiêu đề, mô tả, giá, tag và chuyển trạng thái. | Ngăn được dữ liệu khóa học không hợp lệ bị lưu vào hệ thống. |
| 08/07 | Dựng model Lesson và CRUD endpoint với order index, notes và field URL video/tài liệu. | Cho phép sắp xếp curriculum theo thứ tự qua API. |
| 09/07 | Viết test cho các endpoint Course và Lesson, sửa các lỗi phát hiện được. | Xác nhận API hoạt động đúng cho cả trường hợp thông thường lẫn edge case. |
| 10/07 | Hoàn thiện và merge Course & Lesson backend API cùng team. | Hoàn thành phần đóng góp backend cốt lõi của mình cho dự án. |

## Kết quả đạt được

- Hoàn thành CRUD API cho Course và Lesson, kèm kiểm tra quyền sở hữu.
- Nắm được kiến thức nền S3 trước khi team làm phần upload/storage sau này.
- Bàn giao một phần backend đã được kiểm thử, hoạt động ổn định để team tiếp tục xây dựng thêm.
