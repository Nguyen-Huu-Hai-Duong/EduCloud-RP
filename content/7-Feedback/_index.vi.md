---
title: "Chia sẻ, đóng góp ý kiến"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

# Chia sẻ, đóng góp ý kiến

Dưới đây là những cảm nhận thật của tôi sau khi trải qua chương trình First Cloud AI Journey (FCAJ) trong lúc xây dựng và đưa EduCloud Lite lên hoạt động thật.

### Đánh giá chung

**1. Môi trường làm việc**

Chương trình xoay quanh việc tự học và tự làm là chính, chứ không giám sát sát sao hằng ngày. Điều này khá phù hợp với một project như EduCloud Lite: tôi có thể tự tìm hiểu một dịch vụ AWS, thử một phương án deploy, thấy nó fail rồi tự điều chỉnh mà không cần chờ ai. Thứ giúp tôi không bị lạc hướng chính là cấu trúc của chương trình — dàn bài báo cáo và tài liệu học tập cho tôi một đích đến rõ ràng, ngay cả khi tôi đang tự loay hoay xử lý một vấn đề.

**2. Hỗ trợ từ mentor / định hướng chương trình**

Giá trị rõ ràng nhất đến từ chính cấu trúc report và workshop template: việc chia bài nộp thành worklog, proposal, blogs, events, workshop, self-assessment và feedback giúp tôi biết chính xác "hoàn thành" ở từng phần nghĩa là gì, và tránh cho kết quả cuối cùng biến thành một mớ ghi chú rời rạc.

**3. Mức độ phù hợp với chuyên ngành**

EduCloud Lite bám khá sát nền tảng Khoa học máy tính của tôi — thiết kế backend API, phát triển frontend, mô hình hóa database, xác thực và debug đều xuất hiện dưới hình thức này hay hình thức khác. Phần chương trình bổ sung thêm so với kiến thức trên trường là khía cạnh vận hành: chính sách CORS, quyền IAM, cấu hình biến môi trường, quy tắc lưu trữ cloud và các health check — những thứ chỉ thực sự bộc lộ khi có gì đó chạy thật trên production.

**4. Cơ hội học hỏi và phát triển kỹ năng**

Kỳ thực tập này là lúc các dịch vụ AWS riêng lẻ không còn là những chủ đề tách biệt mà trở thành một hệ thống thống nhất. Tôi đã deploy FastAPI trên Elastic Beanstalk, host frontend React bằng Amplify, giao việc xác thực cho Cognito, lưu secret trong Parameter Store, phân phối file riêng tư qua S3 và CloudFront, và kết nối backend với database Supabase PostgreSQL được quản lý sẵn. Việc debug những lỗi chỉ xuất hiện sau khi deploy — chứ không phải lúc chạy local — có lẽ là bước tiến kỹ năng lớn nhất của tôi.

**5. Văn hóa chương trình và tinh thần học tập**

Cách tiếp cận của FCAJ là học qua việc đưa sản phẩm ra thật, chứ không phải học qua đọc lý thuyết. Thay vì chỉ tìm hiểu các dịch vụ AWS một cách trừu tượng, tôi phải làm ra thứ thật sự chạy được công khai, giải thích được lý do đằng sau từng lựa chọn kiến trúc và có minh chứng đi kèm. Sự khác biệt đó — giữa một bản prototype chạy local và một ứng dụng có thể triển khai, truy cập công khai — là điều hữu ích nhất mà chương trình đã thúc đẩy tôi hướng tới.

**6. Chính sách / lợi ích của kỳ thực tập**

Lợi ích lớn nhất không phải là một đãi ngộ theo nghĩa thông thường, mà là quyền tự định hình project của riêng mình và dành thêm thời gian cho những phần thực sự khó, như luồng xác thực của Cognito, kiểm soát truy cập CloudFront/S3 hay cấu hình Elastic Beanstalk, thay vì phải đi theo một kịch bản cố định.

---

### Câu hỏi bổ sung

**Điều gì khiến tôi hài lòng nhất trong kỳ thực tập?**

Khoảnh khắc thấy EduCloud Lite chạy công khai qua một URL Amplify, với các luồng đăng nhập, xem khóa học, công cụ cho Instructor, hồ sơ cá nhân, upload, làm bài đánh giá và cấp chứng chỉ đều hoạt động cùng nhau như một hệ thống thống nhất, chứ không phải những bản demo rời rạc.

**Theo tôi, chương trình nên cải thiện điều gì cho các bạn thực tập sinh sau?**

Sẽ hữu ích nếu có một checklist deployment ngắn gọn ngay từ đầu — đặc biệt cho IAM role, Parameter Store, CORS, hành vi của CloudFront, bucket policy của S3 và cấu hình Cognito. Đây chính xác là những phần mà người mới tiếp cận AWS rất dễ mất nhiều thời gian để thử sai.

**Tôi có giới thiệu kỳ thực tập này cho bạn bè không?**

Có, đặc biệt cho các bạn đã có kỹ năng phát triển web cơ bản và muốn học cách đưa một ứng dụng từ "chạy được trên máy mình" thành một hệ thống có cấu trúc, bảo mật và triển khai công khai.

---

### Đề xuất & mong muốn

- Chia sẻ một reference architecture tối giản ngay từ đầu, để sinh viên biết đích đến của việc deploy trước khi bắt tay vào xây dựng.
- Khuyến khích chụp ảnh và ghi worklog theo từng tuần, thay vì phải nhớ lại và dựng minh chứng gần sát hạn nộp.
- Thêm một hướng dẫn ngắn về cách ước lượng chi phí AWS và dọn dẹp tài nguyên sau khi nộp bài.
- Tổng hợp các lỗi thường gặp khi troubleshoot cho đăng nhập Cognito, CORS, hành vi origin của CloudFront, quyền truy cập S3 OAC và log deployment của Elastic Beanstalk.
- Tiếp tục để sinh viên tự chọn đề tài project — làm một thứ mình thực sự quan tâm khiến cả quá trình học chủ động và hứng thú hơn nhiều.
