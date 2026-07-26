---
title : "Dọn dẹp tài nguyên"
date : 2026-07-26
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### Tổng kết

Trong workshop này, EduCloud Lite đã được kết nối với ba mảng dịch vụ AWS: **Cognito** cho xác thực, **S3** cho lưu trữ file upload, và **CloudWatch/Cost Explorer** cho giám sát chi phí/tài nguyên trên trang Admin Health, cùng với việc deploy frontend qua **Amplify**.

Để tránh phát sinh chi phí ngoài ý muốn sau khi kết thúc đợt báo cáo/demo, dọn dẹp tài nguyên theo thứ tự sau:

#### Dọn dẹp

1. **Amazon S3**
   - Mở S3 console, chọn bucket đã tạo cho khóa học (ví dụ `educloud-lite-media-bucket`).
   - Empty toàn bộ object trong bucket, sau đó **Delete bucket**.

2. **Amazon Cognito**
   - Nếu không còn nhu cầu demo, xóa **User pool** đã tạo (kèm theo App client).
   - Xóa Lambda function pre sign-up trigger nếu không dùng cho dự án khác.

3. **Database (Supabase / RDS PostgreSQL)**
   - Tắt hoặc xóa project/instance nếu không sử dụng lâu dài.

4. **Backend hosting**
   - Dừng/terminate instance hoặc service đã deploy backend (App Runner/EC2/nền tảng theo Procfile).

5. **AWS Amplify**
   - Xóa Amplify app đã dùng để host frontend nếu không cần giữ bản demo online.

6. **AWS CloudWatch**
   - Xóa các Log Group liên quan đến ứng dụng.

7. **Kiểm tra chi phí**
   - Mở **AWS Billing & Cost Management Dashboard**, xác nhận không còn tài nguyên nào phát sinh chi phí ngoài dự kiến.
