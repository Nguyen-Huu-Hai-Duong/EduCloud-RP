---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# Triển khai xác thực người dùng an toàn cho EduCloud Lite bằng Amazon Cognito

#### Tổng quan

**EduCloud Lite** là một hệ thống quản lý học tập (LMS) được xây dựng bằng React + FastAPI, dùng Supabase PostgreSQL làm cơ sở dữ liệu ứng dụng và **Amazon Cognito** làm nhà cung cấp danh tính (identity provider) chịu trách nhiệm đăng ký, xác thực email, đăng nhập và khôi phục mật khẩu.

Trong workshop này, bạn sẽ tự tay dựng lại phần xác thực của EduCloud Lite: tạo một Amazon Cognito User Pool, cấu hình App Client, rồi kết nối User Pool đó vào backend FastAPI và frontend React sẵn có trong repo. Sau khi hoàn thành, bạn sẽ hiểu được:

+ **Cognito User Pool** quản lý danh tính người dùng (email, mật khẩu, trạng thái xác thực) như thế nào, độc lập với cơ sở dữ liệu ứng dụng.
+ **FastAPI backend** xác minh Cognito ID token (JWKS, RS256) và phát hành JWT nội bộ của EduCloud ra sao, kèm cơ chế tự động tạo/liên kết user trong Supabase.
+ **React frontend** gọi trực tiếp Cognito (qua `amazon-cognito-identity-js`) cho luồng đăng ký/đăng nhập/quên mật khẩu, rồi mới trao đổi token với backend như thế nào.

#### Nội dung

1. [Giới thiệu workshop](5.1-Workshop-overview/)
2. [Chuẩn bị](5.2-Prerequiste/)
3. [Tạo và cấu hình Amazon Cognito User Pool](5.3-cognito-user-pool/)
4. [Kết nối EduCloud với Amazon Cognito](5.4-connect-educloud/)
5. [Bảo mật nâng cao (làm thêm)](5.5-advanced-security/)
6. [Dọn dẹp tài nguyên](5.6-Cleanup/)
