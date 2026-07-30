---
title: "Tuần 7 - Final assessment và chứng chỉ"
menuTitle: "Tuần 7"
weight: 7
pre: "<b>1.7.</b>"
---

**Thời gian:** 20/07/2026 - 24/07/2026

## Mục tiêu

- Cho phép Instructor tự cấu hình bài đánh giá cuối khóa.
- Kiểm soát thời gian làm bài, chấm điểm và số lần thi ngay ở backend.
- Chỉ cấp chứng chỉ khi Student đã hoàn thành bài học và thi đạt.

## Giai đoạn học AWS

| Nội dung học | Nguồn tài liệu | Áp dụng vào EduCloud |
| --- | --- | --- |
| Metrics, log, alarm và dashboard phục vụ giám sát ứng dụng. | [AWS CloudWatch Workshop](https://000008.awsstudygroup.com/) | Xác định những chỉ số cần theo dõi cho lượt làm bài, lỗi submit và độ trễ. |
| Cách thiết kế ứng dụng giữ trạng thái nhất quán, xử lý retry và đảm bảo thao tác idempotent. | [Application Modernization on AWS](https://cloudjourney.awsstudygroup.com/) | Đảm bảo việc submit bài thi và cấp chứng chỉ không sinh ra bản ghi trùng lặp. |

## Công việc thực hiện

| Ngày | Công việc | Kết quả |
| --- | --- | --- |
| 20/07 | Thiết kế các bảng course_assessments, assessment_questions và assessment_attempts. | Database lưu được cấu hình bài thi, câu hỏi và lịch sử làm bài. |
| 21/07 | Xây dựng Assessment Editor gồm thời gian làm bài, điểm đạt, số lần thi, trạng thái publish và tùy chỉnh số đáp án. | Instructor tạo được bài đánh giá cuối khóa linh hoạt. |
| 22/07 | Bổ sung chế độ chấm một đáp án, chọn hết đáp án đúng hoặc chọn một trong các đáp án đúng; hỗ trợ kéo thả để sắp xếp đáp án. | Câu hỏi đáp ứng được nhiều kiểu chấm điểm khác nhau. |
| 23/07 | Xây dựng trang làm bài cho Student có đếm giờ, thanh điều hướng câu hỏi, đánh dấu câu đã trả lời và tự động nộp bài. | Trải nghiệm làm bài và xem lại rõ ràng, mạch lạc hơn. |
| 24/07 | Triển khai chấm điểm, deadline, điều kiện đủ điều kiện thi và cấp chứng chỉ idempotent ở backend, kèm giao diện in. | Áp dụng đầy đủ quy tắc hoàn thành xuyên suốt hệ thống. |

## Kết quả đạt được

- Thời gian làm bài và số lần thi được kiểm soát ở backend, không phụ thuộc đồng hồ trình duyệt.
- Hỗ trợ tối đa 12 đáp án và nhiều đáp án đúng cùng lúc.
- Có thanh điều hướng câu hỏi có thể bấm chọn, cho phép xem lại từng câu.
- Chứng chỉ có thể in, chỉ được cấp sau khi hoàn thành và thi đạt.
