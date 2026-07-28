---
title: "Worklog Tuần 7"
date: 2026-07-28
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

## Tuần 7 - Final assessment, chứng chỉ và triển khai AWS

**Thời gian:** 20/07/2026 - 24/07/2026

### Mục tiêu

- Xây dựng API cấu hình bài đánh giá cuối khóa, chấm điểm và cấp chứng chỉ ở backend.
- Triển khai backend lên hạ tầng AWS thật (Elastic Beanstalk, S3, CloudFront) và phối hợp deploy frontend qua Amplify trước tuần kiểm tra cuối.

### Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| :--- | :--- | :--- |
| Metrics, logs, alarms và dashboard cho ứng dụng. | [AWS CloudWatch Workshop](https://000008.awsstudygroup.com/) | Xác định dữ liệu cần theo dõi cho lượt làm bài, lỗi submit và latency. |
| Thiết kế ứng dụng có trạng thái nhất quán, xử lý retry và thao tác idempotent. | [Application Modernization on AWS](https://cloudjourney.awsstudygroup.com/) | Bảo đảm submit bài và cấp chứng chỉ không tạo bản ghi trùng. |
| Elastic Beanstalk environment, cấu hình biến môi trường và health monitoring. | AWS Elastic Beanstalk Developer Guide | Triển khai backend FastAPI lên môi trường production. |

### Công việc thực hiện

| Ngày | Công việc | Kết quả |
| :--- | :--- | :--- |
| 20/07 | Thiết kế bảng course_assessments, assessment_questions, assessment_attempts; xây dựng API cấu hình bài thi (thời gian, điểm đạt, số lần thi, publish, nhiều loại đáp án). | Instructor cấu hình được final assessment linh hoạt qua API, database lưu đủ dữ liệu. |
| 21/07 | Xây dựng API làm bài cho Student (nộp bài, chấm điểm tự động theo đáp án); triển khai scoring, deadline, attempt limit ở backend. | Backend kiểm soát chấm điểm/thời hạn/số lần thi, không phụ thuộc client. |
| 22/07 | Xây dựng logic cấp certificate idempotent (chỉ cấp một lần sau khi hoàn thành lesson và thi đạt); tạo Elastic Beanstalk environment cho backend. | Certificate không bị cấp trùng; backend chạy được trên Elastic Beanstalk. |
| 23/07 | Cấu hình biến môi trường production qua AWS Systems Manager Parameter Store; tạo S3 bucket, chuyển UPLOAD_STORAGE sang s3, cấu hình CloudFront với Origin Access Control. | Secret quản lý an toàn; ảnh/video/tài liệu phục vụ qua CloudFront thay vì lưu local. |
| 24/07 | Phối hợp deploy frontend lên AWS Amplify Hosting (CORS, domain backend/Cognito); kiểm thử API end-to-end trên môi trường thật. | Ứng dụng EduCloud Lite chạy đầy đủ trên domain public, API phản hồi đúng từ production. |

### Kết quả đạt được

- API kiểm soát thời gian, số lần thi, chấm điểm và cấp chứng chỉ idempotent.
- Backend chạy trên AWS Elastic Beanstalk, secret quản lý qua Parameter Store.
- Ảnh, video, tài liệu chuyển sang phục vụ qua S3 + CloudFront (Origin Access Control) thay vì lưu local.
- Backend production sẵn sàng phục vụ frontend đã deploy qua AWS Amplify.
