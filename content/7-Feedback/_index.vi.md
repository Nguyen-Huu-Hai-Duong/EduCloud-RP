---
title: "Chia sẻ, đóng góp ý kiến"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

Đây là những chia sẻ chân thật của mình sau quãng thời gian tham gia chương trình First Cloud AI Journey (FCAJ), song song với việc làm thành viên trong nhóm 5 người xây dựng và đưa EduCloud Lite vào hoạt động thực tế.

### Đánh giá chung

**1. Môi trường làm việc**

Môi trường làm việc chung khá dễ chịu, không gian văn phòng thoáng đãng và rộng rãi. Mình cũng có dịp làm quen với các bạn đến từ nhiều trường đại học khác nhau, khá là thú vị.

**2. Hỗ trợ từ mentor / định hướng chương trình**

Đội ngũ mentor cùng team admin luôn nhiệt tình và dễ gần. Cho dù project có bận đến đâu, mọi người vẫn dành thời gian hướng dẫn, hỗ trợ và giải đáp thắc mắc cho mình xuyên suốt quá trình làm việc.

**3. Mức độ phù hợp với chuyên ngành**

Những đầu việc mình đảm nhận bám khá sát chuyên ngành đang theo học. Bên cạnh đó, nhờ tham gia các buổi event do phía công ty tổ chức, mình còn tiếp thu thêm nhiều kiến thức thực tế về quy trình làm việc và cách một doanh nghiệp vận hành — những điều mà ở giảng đường ít khi có cơ hội trải nghiệm.

**4. Cơ hội học hỏi và phát triển kỹ năng**

Đây là giai đoạn mà các dịch vụ AWS không còn nằm rời rạc mỗi nơi một kiểu, mà ghép lại thành một hệ thống vận hành thống nhất. Mình xây dựng Course & Lesson backend API và kết nối nó với database Supabase PostgreSQL quản lý sẵn, trong khi theo sát khi đồng đội tích hợp Cognito, deploy backend lên Elastic Beanstalk và phân phối file riêng tư qua S3 kết hợp CloudFront. Chứng kiến một lần deploy thật làm lộ ra những lỗi chưa từng thấy khi chạy local — rồi tìm hiểu lý do — có lẽ là bước tiến kỹ năng lớn nhất của mình, kể cả với những phần mình không trực tiếp deploy.

**5. Văn hóa chương trình và tinh thần học tập**

FCAJ chọn cách học bằng việc thật sự tạo ra sản phẩm, thay vì chỉ dừng lại ở lý thuyết suông. Mình không chỉ tìm hiểu các dịch vụ AWS một cách chung chung, mà phải làm ra một thứ chạy được công khai, giải thích rõ được lý do phía sau mỗi lựa chọn kiến trúc và có minh chứng đi kèm. Chính sự khác biệt giữa một bản prototype chỉ chạy local với một ứng dụng triển khai được, truy cập công khai — đó mới là điều giá trị nhất mà chương trình đã đẩy mình hướng tới.

**6. Chính sách / lợi ích của kỳ thực tập**

Dù chỉ là thực tập sinh, mình vẫn cảm nhận được các chính sách hỗ trợ của chương trình khá chu đáo. Thời gian làm việc linh động giúp mình cân đối được giữa việc học ở trường và thực tập. Công ty cũng tạo điều kiện hết mức về tài nguyên — cấp tài khoản cloud, server... — để tụi mình thực hành trực tiếp một cách hiệu quả nhất.

---

### Câu hỏi bổ sung

**Điều gì khiến tôi hài lòng nhất trong kỳ thực tập?**

Điều làm mình hài lòng nhất chính là được trải nghiệm thật trong một môi trường doanh nghiệp hòa đồng, năng động và vui vẻ. Được gặp các anh chị đi trước, có những đồng đội luôn sẵn lòng hỗ trợ nhau. Việc được trực tiếp thực hành với các công nghệ mới giúp mình vỡ ra rất nhiều điều mà trước đây chỉ hiểu trên lý thuyết.

**Theo tôi, chương trình nên cải thiện điều gì cho các bạn thực tập sinh sau?**

Mình nghĩ phần onboarding (tiếp nhận và hướng dẫn ban đầu) nên được xây dựng chi tiết và bài bản hơn một chút, để các bạn mới vào đỡ bỡ ngỡ. Ngoài ra, nếu có lịch review tiến độ rõ ràng hơn thì các bạn thực tập sinh sẽ nắm bắt định hướng nhanh và nâng cao chất lượng công việc tốt hơn.

**Tôi có giới thiệu kỳ thực tập này cho bạn bè không?**

Có chứ, nhất là với những bạn đã có nền tảng phát triển web cơ bản và muốn học cách đưa một ứng dụng từ trạng thái "chỉ chạy trên máy mình" thành một hệ thống có cấu trúc rõ ràng, bảo mật và triển khai công khai được.

---

### Đề xuất & mong muốn

- Cung cấp sẵn một reference architecture ở mức tối giản ngay từ đầu, để sinh viên hình dung được đích đến của việc deploy trước khi bắt tay vào làm.
- Khuyến khích ghi worklog và chụp ảnh minh chứng theo từng tuần, thay vì để đến gần hạn nộp mới cố nhớ lại và dựng lại từ đầu.
- Bổ sung một hướng dẫn ngắn gọn về cách ước tính chi phí AWS và dọn dẹp tài nguyên sau khi hoàn tất nộp bài.
- Tập hợp lại các lỗi hay gặp khi troubleshoot: đăng nhập Cognito, CORS, hành vi origin của CloudFront, quyền truy cập S3 OAC, và log deployment từ Elastic Beanstalk.
- Duy trì việc để sinh viên tự chọn đề tài project — vì làm một thứ bản thân thực sự quan tâm sẽ khiến cả quá trình học chủ động và hào hứng hơn nhiều.
