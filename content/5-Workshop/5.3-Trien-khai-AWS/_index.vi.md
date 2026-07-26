---
title : "Triển khai AWS cho EduCloud"
date : 2026-07-26
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Ba mảng triển khai

Phần này gồm ba bước triển khai, thực hiện tuần tự vì bước sau phụ thuộc cấu hình của bước trước (frontend cần token Cognito hợp lệ trước khi gọi các API upload/giám sát):

1. [Thiết lập Amazon Cognito (Xác thực)](5.3.1-Cognito/)
2. [Thiết lập Amazon S3 (Lưu trữ file upload)](5.3.2-S3-Upload/)
3. [Deploy & Giám sát (Amplify + CloudWatch/Cost Explorer)](5.3.3-Deploy-Monitoring/)
