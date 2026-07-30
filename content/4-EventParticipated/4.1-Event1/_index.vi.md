---
title: "Sự kiện 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Báo cáo tóm tắt: "FCAJ x Agentic AI Build Week 2026 — Trao giải Hackathon và trình diễn dự án Agentic AI"

### Thông tin sự kiện

- **Tên sự kiện:** FCAJ x Agentic AI Build Week 2026 — Trao giải Hackathon và trình diễn dự án
- **Ngày & thời gian:** 25/07/2026
- **Địa điểm:** AWS Office, 26th Floor, Bitexco Tower, 02 Hai Trieu Street, Saigon Ward, Ho Chi Minh City
- **Đơn vị tổ chức:** First Cloud AI Journey (FCAJ), Amazon Web Services (AWS) và cộng đồng Agentic AI Build Week

### Mục tiêu sự kiện

Vinh danh các đội nổi bật tại Agentic AI Build Week (AABW) Hackathon (8-12/07/2026, TP.HCM), cho các đội kể lại thật quá trình build 24 giờ, và giới thiệu bốn hướng ứng dụng Agentic AI khác nhau: an toàn đám đông, đặt hàng đa kênh, hỗ trợ Solution Architect và phân tích tín hiệu doanh nghiệp.

### Các đội trình bày

- **3KA — S.H.E.P.H.E.R.D:** Huỳnh An Khương, Nguyễn Quốc Huy, Ngô Quang Khôi, Hoàng Lê Thành Đức, Đặng Nguyễn Phước Lộc, Đặng Trường Hưng.
- **OneTeam — KFC Bot Agent:** Anh Duy, Trần Đồng, Đoàn Trung, Minh Việt, Anshul Roy.
- **Plan V — Solution Architect Professional Native App:** Phạm Tiến Thuận Phát, Huỳnh Hoàng Long, Lê Minh Nghĩa, Trần Đại Vĩ, Nguyễn An.
- **SignalScout:** Lê Tấn Lực, Đỗ Hoàng Hiếu, Triệu Quốc Hào, Nguyễn Văn Duy Khiêm, Nguyễn Công Minh, Nguyễn Trần Minh Quân.

### Nội dung nổi bật

**3KA — S.H.E.P.H.E.R.D:** Vốn là đề tài Capstone, được prototype trong 24 giờ để giám sát đám đông: YOLO + ByteTrack phát hiện người, Amazon SageMaker suy luận mật độ, Amazon Bedrock AgentCore + Strands Agent chia thành Autonomous Monitor (tự cảnh báo) và Operator Copilot (trả lời câu hỏi vận hành). Đội thẳng thắn kể lại khó khăn thật: chưa ai biết AI, lần đầu dùng AWS, code lỗi giữa đêm, lỡ push file `.env` lên GitHub. Bài học: chuẩn bị sẵn mục tiêu, toolkit, vai trò và kịch bản demo trước khi bắt đầu.

**OneTeam — KFC Bot Agent:** AI Agent đặt món qua Zalo/WhatsApp, theo chu trình Mục tiêu → Kế hoạch → Công cụ → Hành động → Xác minh, tách adapter từng kênh khỏi logic dùng chung. Chi phí ước tính 0,006 USD/đơn, ~88 USD/tháng, độ trễ 3-5 giây.

**Plan V — Solution Architect Professional Native App:** Giải quyết bài toán khách yêu cầu gấp: ứng dụng nhận yêu cầu ngôn ngữ tự nhiên, sinh sơ đồ **draw.io** với icon AWS chính thức và ước tính chi phí cho region **ap-southeast-1**, đồng thời liệt kê rõ giả định còn thiếu để Solution Architect duyệt lại qua chat sidebar thay vì nhận một kết quả khó kiểm chứng.

**SignalScout:** Nền tảng phát hiện sớm tín hiệu tái cấu trúc/thay đổi chiến lược doanh nghiệp, dùng TinyFish/Apify để crawl bằng chứng và Langfuse để log observability. Công khai bảng chi phí thật: khoảng 17-130 USD/tháng riêng AWS, 81-359 USD/tháng nếu tính cả dịch vụ bên thứ ba — kèm sẵn phương án kiến trúc rẻ hơn. Bài học gói trong ba từ: **Clear Direction, Execution, Teamwork**.

### Bài học rút ra

- Một agent "chạy được demo" và một agent "sẵn sàng vận hành" khác nhau: cần vòng lặp rõ ràng, lớp giám sát tách biệt, và log/observability đi kèm mọi câu trả lời.
- Tách adapter kênh khỏi logic dùng chung giúp mở rộng dễ dàng mà không cần thiết kế lại toàn bộ.
- Chi phí và giả định kiến trúc nên minh bạch ngay từ bản nháp đầu, không phải thứ bổ sung sau khi demo đã chạy.

### Liên hệ với EduCloud Lite

Cách 3KA tách phần tự động khỏi phần tương tác, cách Plan V ghi rõ giả định kiến trúc, và bảng chi phí minh bạch của SignalScout đều là chuẩn mực tôi muốn áp dụng cho tài liệu kiến trúc và kiểm soát chi phí của EduCloud Lite — biết rõ dịch vụ nào đang sinh phí và có phương án cắt giảm nếu cần.

### Áp dụng vào công việc

- Ghi rõ giả định trong tài liệu kiến trúc thay vì trình bày kết quả như điều hiển nhiên.
- Theo dõi chi phí AWS theo từng dịch vụ, không chỉ tổng hóa đơn.
- Ưu tiên một luồng nghiệp vụ nhỏ chạy trọn vẹn end-to-end trước khi mở rộng.
- Giữ bước con người kiểm tra ở các thao tác nhạy cảm như cấp quyền Admin.

### Trải nghiệm sự kiện

Điều đọng lại nhiều nhất là các đội dám kể thật phần "hậu trường" — thiếu kinh nghiệm AI, code lỗi giữa đêm, lỡ push nhầm file nhạy cảm — thay vì chỉ khoe kết quả đẹp. Nghe cả đội đạt giải lẫn các đội khác chia sẻ giúp tôi hiểu rõ hơn tiêu chí đánh giá thật sự: mức độ hoàn thiện, khả năng giải thích kiến trúc, và việc kiểm soát được chi phí/rủi ro — không chỉ là ý tưởng hay.

#### Minh chứng sự kiện

<img src="/images/events/event-03.jpg" alt="Minh chứng sự kiện FCAJ x Agentic AI Build Week 2026" style="max-width:420px; width:100%; height:auto;">

> FCAJ x Agentic AI Build Week 2026 cho tôi thấy rõ khoảng cách giữa một demo AI "chạy được trên sân khấu" và một hệ thống có kiến trúc, chi phí và giám sát đủ minh bạch để tin tưởng — điều tôi cố gắng mang vào EduCloud Lite.
