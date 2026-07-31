---
title: "Tuần 6 - Mở rộng và kiểm thử API backend"
menuTitle: "Tuần 6"
weight: 6
pre: "<b>1.6.</b>"
---

**Thời gian:** 13/07/2026 - 17/07/2026

## Mục tiêu

- Hỗ trợ team khi họ xây dựng auth, enrollment và dashboard dựa trên Course/Lesson API mình đã làm.
- Mở rộng và tinh chỉnh Course/Lesson API theo phản hồi tích hợp từ frontend.
- Học kiến thức nền CloudFront để phục vụ việc phân phối media khóa học sau này.

## Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| --- | --- | --- |
| Cách CDN hoạt động, cấu hình cache và phục vụ nội dung từ origin riêng tư. | [CloudFront with S3 Origin](https://000094.awsstudygroup.com/) | Chuẩn bị để hiểu và sau này ghi lại cách team phân phối media khóa học. |
| Hosting frontend, deploy static website và routing cho single-page app. | [Deploy Static Website on AWS](https://000057.awsstudygroup.com/) | Cho thêm bối cảnh về cách ứng dụng React mà team đang xây sẽ được host sau này. |

## Công việc thực hiện

| Ngày | Công việc | Kết quả |
| --- | --- | --- |
| 13/07 | Xem lại phản hồi tích hợp từ đồng đội làm frontend, điều chỉnh cấu trúc response của Course/Lesson API. | Khớp đúng API contract với những gì frontend thực sự cần. |
| 14/07 | Hỗ trợ test luồng enrollment mà team đang xây dựng dựa trên Course API để đảm bảo dữ liệu khóa học Published nhất quán. | Phát hiện và sửa một lỗi thiếu nhất quán dữ liệu trong Course API. |
| 15/07 | Tìm hiểu CloudFront và mô hình S3 origin để hiểu cách media khóa học sẽ được phân phối sau này. | Sẵn sàng hỗ trợ rà soát cấu hình phân phối ở tuần triển khai. |
| 16/07 | Viết tài liệu cho các endpoint của Course & Lesson API cho các thành viên khác trong team. | Giúp team dùng API dễ dàng hơn mà không cần hỏi trực tiếp mình. |
| 17/07 | Tham gia buổi review các luồng nghiệp vụ dùng Supabase và dashboard theo role mà team xây trong tuần đó. | Nắm được cách API của mình đang được sử dụng ở các phần khác của ứng dụng. |

## Kết quả đạt được

- Mở rộng và ổn định Course/Lesson API dựa trên nhu cầu tích hợp thực tế từ frontend.
- Viết tài liệu Course/Lesson API cho các thành viên còn lại trong team.
- Nắm được kiến thức nền CloudFront trước giai đoạn triển khai.
