---
title: "Sự kiện 3"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

### Thông tin sự kiện

- **Tên sự kiện:** AWS Security, Cloud Fundamentals and Monitoring
- **Thời gian:** 09:00–12:00, ngày 11/07/2026
- **Địa điểm:** Tầng 26, tòa nhà Bitexco Financial Tower, TP. Hồ Chí Minh
- **Đơn vị tổ chức:** AWS First Cloud AI Journey

### Mục tiêu sự kiện

Buổi này gộp chung ba mảng ít khi được dạy trong cùng một buổi: AI hỗ trợ bảo mật ứng dụng ra sao, kỳ thi AWS Certified Cloud Practitioner thật sự kiểm tra những gì, và vì sao một hạ tầng "trông khỏe" trên dashboard vẫn có thể đang làm người dùng thật sự gặp lỗi. Mục tiêu không dừng ở việc ôn thi hay một checklist bảo mật đơn thuần, mà là những thứ có thể mang thẳng vào một dự án AWS thật.

### Diễn giả

- **Nguyễn Tuấn Thịnh** — DevOps / DevSecOps / Cloud Engineer, Styl Solutions — *Securing Your Web Apps With AWS Security Agent*
- **Ngô Lê Tấn Huy** — *Inside the Exam: AWS Cloud Practitioner*
- **Nguyễn Huỳnh Sơn** — Infrastructure Support Engineer tại Endava, từng là Infrastructure Reliability Engineer tại SPS — *SLA and Monitoring: From SLA to Monitoring What Really Matters*

### Nội dung nổi bật

**Chung kết Cloud Architecture Competition:** Hai đội KLKAT và Ngũ Đại Hiệp khép lại buổi sáng bằng một vòng thi đối kháng kiểm tra kiến thức AWS, giúp phần nội dung kỹ thuật không chỉ dừng ở lý thuyết mà có thêm yếu tố cạnh tranh trực tiếp.

**Để AI agent theo dõi bảo mật cả ứng dụng, không chỉ code:** Phần chia sẻ về bảo mật trình bày AI agent như một lớp giám sát xuyên suốt cả vòng đời phần mềm, chứ không phải một bước quét đơn lẻ. Một design review có thể đọc tài liệu kiến trúc và định nghĩa infrastructure-as-code trước khi bất cứ thứ gì được deploy. Một lượt review code có thể phát hiện lỗ hổng và secret bị lộ ngay trong pull request. Xa hơn các bước kiểm tra tĩnh, một agent pentest tự động có thể nối chuỗi nhiều bước tấn công lại và trả về kết quả mà con người có thể tự kiểm chứng, chứ không chỉ một điểm số mức độ nghiêm trọng. Diễn giả cũng nói rõ giới hạn: các luồng có MFA, lỗi business-logic cần hiểu nghiệp vụ mới phát hiện được, và chi phí thật khi chạy agent theo giờ ở quy mô lớn.

**Kỳ thi Cloud Practitioner thực chất kiểm tra điều gì:** Đề thi chia làm bốn domain — Cloud Concepts, Security and Compliance, Cloud Technology and Services, và Billing, Pricing and Support — và phần chia sẻ chỉ rõ trọng tâm thật sự nằm ở đâu: Shared Responsibility Model, nguyên tắc least privilege trong IAM, AWS Well-Architected Framework, AWS Cloud Adoption Framework, và các công cụ quản lý chi phí. Lời khuyên ôn thi không nặng về học thuộc tên dịch vụ, mà là học từng dịch vụ qua use case nó giải quyết, xem lại toàn bộ câu sai trong đề thi thử thay vì chỉ nhìn điểm số, và dành thời gian thao tác thật trên console trước khi thi.

**Khoảng cách giữa "hạ tầng khỏe" và "người dùng đăng nhập được":** Đây là điểm sắc nhất trong ngày — CPU của EC2 thấp ổn định và health check của ALB đều xanh không nói lên được gì về một luồng đăng nhập đang âm thầm hỏng vì database phía sau gặp sự cố. Giải pháp không phải là thêm metric hạ tầng, mà là theo dõi đồng thời bốn lớp: metric của provider/hạ tầng, độ trễ và tỷ lệ lỗi ở tầng ứng dụng, các chỉ số nghiệp vụ như tỷ lệ đăng nhập thành công, và trải nghiệm thực tế của người dùng. Phần chia sẻ khép lại bằng một chuỗi cảnh báo cụ thể: CloudWatch metrics đưa vào CloudWatch Alarm, từ đó kích hoạt thông báo qua SNS — đơn giản, nhưng chỉ thật sự hữu ích nếu metric được đặt alarm là metric người dùng thật sự quan tâm.

### Bài học rút ra

- Bảo mật cần được cân nhắc xuyên suốt vòng đời ứng dụng, không phải việc bổ sung sau khi đã deploy.
- Các kiến thức nền tảng AWS — IAM, shared responsibility, nguyên tắc Well-Architected, quản lý chi phí — vẫn quan trọng ngay cả với một dự án nhỏ do một nhóm nhỏ làm, không chỉ ở quy mô doanh nghiệp.
- Monitoring nên được xây dựng quanh việc người dùng thật sự đang cố làm gì, không chỉ dừng ở việc server có đang chạy hay không.
- Log, metric, alarm và các tín hiệu hướng tới người dùng cần được đọc cùng nhau, thay vì là những dashboard tách rời không ai đối chiếu qua lại.

### Áp dụng vào EduCloud Lite

- Giữ IAM role ở mức least privilege khi thao tác với S3, Parameter Store, hay CloudWatch, thay vì cấp quyền rộng "cho chắc".
- Xem việc bảo vệ resource private, quản lý secret, và bảo mật ở tầng ứng dụng là quyết định thiết kế, không phải thứ thêm vào ngay trước khi deploy.
- Gắn CloudWatch log, metric và alarm vào đúng những luồng mà học viên hay giảng viên thật sự dùng, không chỉ dừng ở health mặc định của EC2/Elastic Beanstalk.
- Định kỳ soát lại kiến trúc theo nguyên tắc Well-Architected, và theo dõi chi phí qua AWS Budgets, Cost Explorer thay vì chỉ xem hóa đơn cuối tháng.
- Thật sự chạy thử luồng đăng nhập, ghi danh, truy cập khóa học từ đầu đến cuối, thay vì mặc định "AWS resource báo khỏe" nghĩa là sản phẩm đang chạy tốt.

### Trải nghiệm sự kiện

Điều khiến buổi này đọng lại nhất là ví dụ về luồng đăng nhập trong phần chia sẻ về monitoring — một hệ thống có thể vượt qua mọi health check hạ tầng trong khi âm thầm không làm được đúng việc người dùng cần. Đây là một cách nhìn "hoàn thành" rõ ràng hơn so với trước: không phải "resource đang chạy", mà là "việc người dùng cần xảy ra đã thật sự xảy ra". Cùng với phần demo AI agent bảo mật và phần ôn thi chứng chỉ, cả buổi giống như một mạch lập luận thống nhất hơn là ba chủ đề tách rời — rằng nền tảng kỹ thuật, bảo mật và khả năng quan sát hệ thống đều thất bại theo cùng một cách khi không ai thật sự kiểm tra kết quả cuối cùng có đúng như mong đợi hay không.
