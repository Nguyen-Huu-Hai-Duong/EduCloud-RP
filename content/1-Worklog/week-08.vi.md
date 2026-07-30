---
title: "Tuần 8 - Kiểm tra cuối, hoàn thiện báo cáo và nộp bài"
menuTitle: "Tuần 8"
weight: 8
pre: "<b>1.8.</b>"
---

**Thời gian:** 27/07/2026 - 31/07/2026

**Hạn nộp workshop:** 31/07/2026

## Mục tiêu

- Khóa phạm vi tính năng của EduCloud Lite, tránh thêm thay đổi rủi ro trước khi nộp bài.
- Rà soát lại luồng Student, Instructor, các dịch vụ AWS đang chạy và toàn bộ public link.
- Hoàn tất Hugo workshop song ngữ, ảnh minh chứng, sơ đồ kiến trúc và hồ sơ nộp bài.
- Đảm bảo nộp workshop chậm nhất vào ngày 31/07/2026.

## Kiểm tra cuối project và AWS

| Phạm vi kiểm tra | Hoạt động xác minh | Minh chứng nộp bài |
| --- | --- | --- |
| Danh tính và bảo mật | Kiểm tra login qua Cognito, đổi mật khẩu lần đầu, khôi phục mật khẩu, JWT exchange, IAM role và secret trong Parameter Store. | Ảnh chụp màn hình xác thực, ghi chú cấu hình và link mã nguồn. |
| Hosting ứng dụng | Kiểm tra tình trạng Elastic Beanstalk, việc deploy qua Amplify, routing của CloudFront, CORS và SPA rewrite. | Link EduCloud công khai và trạng thái deploy thành công. |
| Lưu trữ và dữ liệu | Xác nhận việc phân phối S3 ở chế độ private, kết nối Supabase, đường dẫn upload và role lấy từ database. | Sơ đồ kiến trúc và ảnh chụp workshop. |
| Tài liệu | Rà lại proposal, worklog, blogs, events, các bước workshop, self-assessment và feedback ở cả hai ngôn ngữ. | Hugo report công khai và repository GitHub. |

## Kế hoạch công việc và tiến độ hiện tại

| Ngày | Công việc | Kết quả cần đạt |
| --- | --- | --- |
| 27/07 | Chỉnh lại mốc thời gian thực tập và phạm vi worklog; bổ sung nốt nội dung và minh chứng còn thiếu trong báo cáo. | Báo cáo phản ánh đúng kỳ thực tập thực tế 01/06-15/08. |
| 28/07 | Chạy checklist production cho login, xem khóa học, ghi danh, học bài, làm assessment, cấp certificate và tạo nội dung phía Instructor. | Các luồng demo quan trọng chạy thông suốt trên website công khai. |
| 29/07 | Rà lại sơ đồ kiến trúc AWS, ảnh chụp, đoạn code, hướng dẫn repository và tài khoản demo. | Mentor có thể hiểu và làm theo đúng nội dung nộp bài. |
| 30/07 | Đọc lại toàn bộ trang tiếng Anh và tiếng Việt; kiểm tra điều hướng, dấu trang đã xem, hình ảnh, liên kết và giao diện responsive. | Hugo report nhất quán, không còn placeholder hay tài nguyên lỗi. |
| 31/07 | Chuẩn bị gói nộp bài cuối cùng, gửi kèm website, repository mã nguồn, link workshop và các file PDF được chọn. | Nộp workshop đúng hạn. |

## Kết quả hiện tại

- EduCloud Lite đã hoạt động tại một đường dẫn Amplify độc lập.
- Backend FastAPI chạy trên Elastic Beanstalk, đọc secret production từ Parameter Store.
- Cognito, Supabase, S3, CloudFront và Amplify đều đã được kết nối vào ứng dụng đang triển khai.
- Sơ đồ kiến trúc, Hugo report song ngữ, link demo và tài khoản dành cho mentor đều đã được ghi lại đầy đủ.
- Phần việc còn lại chỉ là kiểm tra cuối, rà soát minh chứng, đọc lại nội dung và nộp bài.

## Liên kết nộp bài

- [Website EduCloud Lite](https://main.djk00b5qbck73.amplifyapp.com/courses)
- [Repository mã nguồn EduCloud](https://github.com/Funacius/EduCloud)
- [Báo cáo thực tập công khai](https://nguyen-huu-hai-duong.github.io/EduCloud-RP/vi/)

> Sau ngày 31/07 sẽ không mở rộng thêm tính năng nào cho project. Thời gian còn lại của kỳ thực tập được dành riêng cho việc học AWS và First Cloud AI Journey.
