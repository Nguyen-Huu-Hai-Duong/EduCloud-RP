---
title: "Tuần 7 - Hỗ trợ tích hợp và học quy trình triển khai AWS"
menuTitle: "Tuần 7"
weight: 7
pre: "<b>1.7.</b>"
---

**Thời gian:** 20/07/2026 - 24/07/2026

## Mục tiêu

- Hỗ trợ team trong giai đoạn nước rút hoàn thiện role workflow, assessment và triển khai.
- Tìm hiểu cách team deploy bằng Elastic Beanstalk, S3 và CloudFront để có thể ghi lại chính xác cho báo cáo.
- Giữ cho Course/Lesson API hoạt động đúng khi các tính năng mới được thêm vào phía trên nó.

## Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| --- | --- | --- |
| Metrics, log, alarm và dashboard của CloudWatch. | [AWS CloudWatch Workshop](https://000008.awsstudygroup.com/) | Chuẩn bị để hiểu và sau này ghi lại cách ứng dụng đã deploy có thể được giám sát. |
| Các pattern giúp ứng dụng chạy ổn định: health check, idempotency và xử lý request có thể phục hồi. | [Explore AWS Services](https://cloudjourney.awsstudygroup.com/) | Cho mình kiến thức nền để rà soát logic assessment/certificate mà đồng đội đang thêm vào, xem có vấn đề idempotency không. |

## Công việc thực hiện

| Ngày | Công việc | Kết quả |
| --- | --- | --- |
| 20/07 | Test lại Course/Lesson API với các tính năng assessment và certificate mới thêm để kiểm tra xung đột. | Xác nhận API của mình vẫn hoạt động đúng cùng các tính năng mới. |
| 21/07 | Theo dõi team cấu hình Elastic Beanstalk để deploy backend. | Học được các bước triển khai để sau này ghi lại trong workshop report. |
| 22/07 | Theo dõi team thiết lập S3 và CloudFront để phân phối media khóa học riêng tư. | Hiểu đủ về cấu hình OAC và bucket policy để viết lại thành hướng dẫn sau này. |
| 23/07 | Xem lại kiến thức nền CloudWatch để giám sát backend sau khi deploy. | Sẵn sàng ghi lại phần cấu hình giám sát trong báo cáo. |
| 24/07 | Hỗ trợ team kiểm tra bản build cuối trước khi deploy, sửa một lỗi nhỏ trong Course API phát hiện được lúc kiểm tra. | Góp phần vào một bản build cuối sạch sẽ. |

## Kết quả đạt được

- Giữ cho Course/Lesson API hoạt động đúng xuyên suốt giai đoạn tích hợp nước rút của team.
- Học đủ sâu quy trình triển khai AWS của team để có thể ghi lại chi tiết trong workshop report.
- Phát hiện và sửa một lỗi trong bước kiểm tra cuối trước khi deploy.
