---
title: "Bản đề xuất"
date: 2026-07-26
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

## Đề xuất dự án — EduCloud

### Bối cảnh bài toán

Nhu cầu học trực tuyến ngày càng tăng, kéo theo yêu cầu về hệ thống quản lý khóa học, lưu trữ tài liệu/video, phân quyền người dùng và theo dõi tiến độ học tập. Việc triển khai hệ thống trên cloud giúp ứng dụng có thể truy cập online, dễ mở rộng, dễ giám sát và phù hợp với mô hình phát triển phần mềm hiện đại.

### Vấn đề cần giải quyết

- Quản lý người dùng và phân quyền.
- Quản lý khóa học và bài học.
- Lưu trữ tài liệu/video an toàn.
- Theo dõi tiến độ học tập.
- Triển khai hệ thống có thể truy cập online.
- Theo dõi log và lỗi hệ thống.
- Dọn dẹp tài nguyên AWS để tránh phát sinh chi phí.

### Mục tiêu dự án

**Mục tiêu chức năng**

- Đăng ký, đăng nhập; phân quyền Student, Instructor, Admin.
- Xem danh sách khóa học, chi tiết khóa học và bài học.
- Đăng ký khóa học, đánh dấu hoàn thành bài học và xem tiến độ học tập.
- Upload ảnh, video hoặc tài liệu phục vụ nội dung khóa học.

**Mục tiêu kỹ thuật**

- Backend API hoạt động ổn định, có cấu trúc rõ ràng.
- Database chạy trên AWS RDS; file được lưu trên AWS S3.
- Backend được deploy lên AWS EC2 hoặc Lambda.
- Log được ghi nhận bằng AWS CloudWatch.
- Có tài liệu triển khai step-by-step và hướng dẫn clean-up resource.

**Mục tiêu học tập**

- Hiểu quy trình phát triển ứng dụng web trên AWS.
- Thực hành tích hợp frontend, backend, database và cloud service.
- Rèn luyện teamwork, quản lý tiến độ, kiểm thử và viết tài liệu kỹ thuật.

### Phạm vi dự án

| Trong phạm vi | Ngoài phạm vi |
| :--- | :--- |
| User authentication; Course management; Lesson management; Enrollment; Progress tracking; S3 upload; RDS database; CloudWatch logging; Basic UI. | Thanh toán thật; Livestream; AI recommendation; Mobile app; Hệ thống chứng chỉ nâng cao. |

### Kiến trúc hệ thống

*(Chèn sơ đồ kiến trúc hệ thống của bạn tại đây)*

![Kiến trúc hệ thống EduCloud](/images/2-Proposal/architecture-diagram.png)

**Luồng kiến trúc đề xuất:**

- User → Frontend Web → Backend API → AWS RDS.
- Backend API → AWS S3.
- Backend API → AWS CloudWatch.
- AWS IAM quản lý quyền truy cập giữa các service.

**Thành phần chính**

- **Frontend Web:** Giao diện cho Student, Instructor và Admin.
- **Backend API:** Xử lý nghiệp vụ, xác thực, quản lý dữ liệu.
- **AWS EC2 hoặc Lambda:** Môi trường triển khai backend.
- **AWS RDS PostgreSQL:** Lưu dữ liệu người dùng, khóa học, bài học, enrollment và progress.
- **AWS S3:** Lưu ảnh khóa học, video bài học, tài liệu PDF.
- **AWS CloudWatch:** Theo dõi log, lỗi và hoạt động hệ thống.
- **AWS IAM:** Quản lý quyền truy cập an toàn giữa các dịch vụ.

### Lý do chọn các dịch vụ AWS

| Dịch vụ AWS | Mục đích sử dụng | Lý do lựa chọn |
| :--- | :--- | :--- |
| EC2 hoặc Lambda | Deploy backend API | Phù hợp triển khai ứng dụng web/API, dễ cấu hình theo nhu cầu dự án. |
| S3 | Lưu ảnh, video, tài liệu | Dịch vụ lưu trữ object phổ biến, bền vững, dễ tích hợp upload/download. |
| RDS PostgreSQL | Lưu database quan hệ | Quản lý database ổn định, giảm công sức vận hành thủ công. |
| CloudWatch | Logging và monitoring | Theo dõi log, lỗi, metric và hỗ trợ debug hệ thống. |
| IAM | Quản lý quyền truy cập | Tăng an toàn khi backend truy cập S3, CloudWatch và các service khác. |

### Timeline dự án

| Tuần | Mục tiêu | Công việc chính | Output dự kiến | Người phụ trách |
| :--- | :--- | :--- | :--- | :--- |
| Week 1 | Tổng quan cloud web | Tìm hiểu kiến trúc Web trên Cloud, chốt đề tài, chia vai trò | Proposal sơ bộ | [Điền thông tin] |
| Week 2 | Phân tích yêu cầu | Thiết kế database, thiết kế kiến trúc AWS | SRS, ERD, architecture draft | [Điền thông tin] |
| Week 3 | Khởi tạo dự án | Khởi tạo backend, frontend, repo GitHub, cấu trúc project | Source base | [Điền thông tin] |
| Week 4 | Authentication | Xây dựng authentication, user roles, JWT | Auth API | [Điền thông tin] |
| Week 5 | Course/Lesson API | Xây dựng course API và lesson API | API chính | [Điền thông tin] |
| Week 6 | Frontend cơ bản | Xây dựng frontend các trang chính | UI prototype | [Điền thông tin] |
| Week 7 | S3 upload | Tích hợp upload file/video/tài liệu | Upload module | [Điền thông tin] |
| Week 8 | RDS/Deploy backend | Tích hợp RDS, deploy backend lên AWS | Public backend endpoint | [Điền thông tin] |
| Week 9 | Enrollment/Progress | Xây dựng enrollment, progress tracking | Learning flow | [Điền thông tin] |
| Week 10 | Monitoring | Cấu hình CloudWatch, logging, monitoring | Log dashboard/basic metrics | [Điền thông tin] |
| Week 11 | E2E testing | Kiểm thử end-to-end, fix bug, tối ưu UI/API | Test report | [Điền thông tin] |
| Week 12 | Hoàn thiện | Hoàn thiện tài liệu, clean-up guide, slide và demo | Final draft/demo | [Điền thông tin] |

### Rủi ro và phương án xử lý

| Rủi ro | Mức độ ảnh hưởng | Nguyên nhân | Phương án xử lý |
| :--- | :--- | :--- | :--- |
| Không kết nối được RDS | Cao | Security group, endpoint, credential sai | Kiểm tra inbound rule, VPC, endpoint, username/password và log backend. |
| Lỗi permission khi upload S3 | Cao | IAM policy hoặc bucket policy chưa đúng | Áp dụng least privilege, test bằng AWS CLI, kiểm tra CORS S3 nếu cần. |
| Phát sinh chi phí AWS | Cao | Quên tắt/xóa resource | Theo dõi Billing Dashboard, đặt budget alert, thực hiện clean-up checklist. |
| Lỗi CORS giữa frontend và backend | Trung bình | Backend chưa cấu hình origin | Cấu hình CORS theo domain frontend và môi trường local. |
| Không đồng bộ API giữa frontend và backend | Trung bình | Thiếu API contract | Thống nhất API spec, cập nhật Postman/OpenAPI và review định kỳ. |
| Thành viên trễ deadline | Trung bình | Khối lượng chưa phù hợp | Chia nhỏ task, cập nhật worklog, hỗ trợ chéo khi cần. |
| Deploy lỗi trên EC2/Lambda | Cao | Thiếu biến môi trường hoặc sai runtime | Chuẩn bị deployment checklist, kiểm tra log và rollback bản ổn định. |
