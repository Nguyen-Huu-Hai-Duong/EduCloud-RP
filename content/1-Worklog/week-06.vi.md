---
title: "Tuần 6 - Ghi danh, học tập và theo dõi tiến độ"
menuTitle: "Tuần 6"
weight: 6
pre: "<b>1.6.</b>"
---

**Thời gian:** 13/07/2026 - 17/07/2026

## Mục tiêu

- Xây dựng catalog công khai cho các khóa học đã publish và luồng ghi danh.
- Dựng Learning Page cho Student.
- Lưu tiến độ theo từng bài học và tính phần trăm hoàn thành.

## Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| --- | --- | --- |
| Luồng frontend đăng nhập, gọi API và dùng storage theo từng access level. | [Amplify Authentication and Storage](https://000134.awsstudygroup.com/) | Thiết kế điều kiện chỉ Student đã ghi danh mới truy cập được nội dung học. |
| Cách CDN cache nội dung tại edge và bảo vệ origin S3. | [CloudFront with S3 Origin](https://000094.awsstudygroup.com/) | Vạch hướng phân phối video, thumbnail và tài liệu cho Learning Page. |

## Công việc thực hiện

| Ngày | Công việc | Kết quả |
| --- | --- | --- |
| 13/07 | Xây dựng catalog khóa học, tìm kiếm, course card và trang chi tiết. | Người dùng xem được các khóa học Published lấy từ Supabase. |
| 14/07 | Triển khai luồng ghi danh idempotent chỉ dành cho Student, có ràng buộc unique. | Ngăn được việc tạo bản ghi ghi danh trùng lặp. |
| 15/07 | Dựng Learning Page gồm playlist bài học, video, ghi chú và tài liệu. | Chỉ Student đã ghi danh mới xem được nội dung đầy đủ. |
| 16/07 | Xây API complete/undo cho tiến độ và tính phần trăm hoàn thành. | Tiến độ học được lưu riêng theo từng Student và bài học. |
| 17/07 | Thêm My Learning, tự động tiếp tục ở bài chưa hoàn thành đầu tiên và số liệu ghi danh cho Instructor. | Student học liên tục đúng vị trí, Instructor xem được báo cáo theo thời gian thực. |

## Kết quả đạt được

- API công khai chỉ trả về outline, không làm lộ tài nguyên bài học riêng tư.
- Dữ liệu ghi danh và tiến độ của Student được lưu trên Supabase.
- Learning Page hỗ trợ chuyển bài và đánh dấu hoàn thành.
- Dashboard hiển thị dữ liệu thật từ database thay vì số liệu cố định.
