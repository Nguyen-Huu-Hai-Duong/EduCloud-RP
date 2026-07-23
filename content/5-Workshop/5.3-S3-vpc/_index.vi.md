---
title : "Tạo và cấu hình Amazon Cognito User Pool"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Tạo kho danh tính cho EduCloud Lite

Trong phần này, bạn sẽ tạo một **Amazon Cognito User Pool** dành riêng cho EduCloud Lite — nơi lưu trữ tài khoản, mật khẩu (đã băm), trạng thái xác thực email và phát hành token cho ứng dụng. Sau đó, bạn sẽ tạo một **App Client** (không có client secret, phù hợp cho ứng dụng SPA React chạy phía trình duyệt) và kiểm tra nhanh User Pool bằng AWS CLI trước khi nối vào code.

#### Nội dung

- [Tạo Cognito User Pool](5.3.1-create-gwe/)
- [Tạo App Client & kiểm tra bằng CLI](5.3.2-test-gwe/)
