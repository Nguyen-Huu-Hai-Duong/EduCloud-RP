---
title: "Workshop"
date: 2026-07-26
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Triển khai AWS cho nền tảng học trực tuyến EduCloud Lite

#### Tổng quan

**EduCloud Lite** là nền tảng học trực tuyến gồm backend **FastAPI (Python)** và frontend **React + TypeScript (Vite)**, dữ liệu lưu ở **PostgreSQL (Supabase)**. Phần Workshop này trình bày lại các bước triển khai ba mảng dịch vụ AWS đã được tích hợp thực tế vào EduCloud Lite:

+ **Amazon Cognito** — xác thực người dùng (đăng ký, đăng nhập, quên mật khẩu) thay cho việc tự xây dựng cơ chế auth.
+ **Amazon S3** — lưu trữ file người dùng tải lên (ảnh thumbnail khóa học, tài liệu bài học, video bài giảng).
+ **Triển khai & giám sát** — build/deploy ứng dụng lên AWS và bật giám sát chi phí/tài nguyên bằng CloudWatch và Cost Explorer cho trang Admin Health.

#### Nội dung

1. [Tổng quan kiến trúc](5.1-Tong-quan/)
2. [Chuẩn bị](5.2-Chuan-bi/)
3. [Triển khai AWS cho EduCloud](5.3-Trien-khai-AWS/)
4. [Dọn dẹp tài nguyên](5.4-Don-dep/)
