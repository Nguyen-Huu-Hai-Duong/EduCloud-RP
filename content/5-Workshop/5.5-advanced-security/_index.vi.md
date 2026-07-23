---
title : "Bảo mật nâng cao (làm thêm)"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.5 </b> "
---

Phần bắt buộc của workshop đã kết thúc ở 5.4. Phần này (làm thêm) khảo sát các lớp bảo mật mà EduCloud Lite đã tích hợp sẵn xung quanh luồng xác thực Cognito, và cho bạn tự tay kiểm chứng từng lớp.

#### Giới hạn tần suất request (rate limiting)

`app/middleware/security_middleware.py` cài một bộ đếm sliding-window trong bộ nhớ, áp dụng cho các endpoint xác thực nhạy cảm (`/api/auth/login`, `/api/auth/register`, `/api/auth/forgot-password`, `/api/auth/cognito/exchange`):

```python
def is_rate_limited(client_ip, path, *, limit: int = 10, window_seconds: int = 60) -> bool:
    ...
```

**Thử làm:** gửi liên tiếp hơn 10 request trong 60 giây tới `/api/auth/login` (ví dụ vòng lặp `curl` hoặc Postman Runner) và quan sát các request vượt ngưỡng bị chặn. Cơ chế này giúp làm chậm tấn công dò mật khẩu (credential stuffing) nhắm vào endpoint xác thực.

{{% notice note %}}
Bộ đếm này lưu trong bộ nhớ tiến trình (in-memory), sẽ mất khi backend restart và không đồng bộ nếu chạy nhiều instance — README của dự án ghi rõ đây là giải pháp phù hợp cho demo, production nên chuyển sang WAF/API Gateway/Redis.
{{% /notice %}}

#### HTTP security headers

Mọi response JSON đều được gắn thêm các header sau (cùng file `security_middleware.py`):

| Header | Giá trị | Mục đích |
|---|---|---|
| `X-Content-Type-Options` | `nosniff` | Chặn trình duyệt tự đoán loại nội dung |
| `X-Frame-Options` | `DENY` | Chặn nhúng trang vào iframe (chống clickjacking) |
| `Referrer-Policy` | `strict-origin-when-cross-origin` | Hạn chế rò rỉ URL qua header Referer |
| `Permissions-Policy` | tắt camera/microphone/geolocation | Vô hiệu hoá các quyền trình duyệt không dùng đến |
| `Cache-Control` | `no-store` | Không cache response JSON chứa dữ liệu người dùng |

**Thử làm:** mở DevTools → Network, gọi bất kỳ API nào của EduCloud và kiểm tra các header trên trong response.

#### Chống downgrade tài khoản đã migrate sang Cognito

Trong `auth_service.login_user()`, nếu một tài khoản đã có `cognito_sub` (tức đã từng xác thực qua Cognito), backend **từ chối** cho đăng nhập lại bằng đường legacy (`/api/auth/login`), kể cả khi `ALLOW_LEGACY_AUTH=true`. Điều này ngăn kẻ tấn công lợi dụng đường xác thực cũ, yếu hơn để bỏ qua Cognito một khi tài khoản đã migrate.

#### Cửa sau chỉ dành cho development

`middleware/auth_middleware.get_current_user_from_token()` chấp nhận một token đặc biệt `dev-instructor-token` để dev nhanh không cần đăng nhập thật — nhưng chỉ khi **đồng thời** `APP_ENV=development` **và** `ENABLE_DEV_AUTH=true`. Đây là lý do checklist bảo mật trong README yêu cầu bắt buộc set `ENABLE_DEV_AUTH=false` khi triển khai ngoài local.

**Thử làm:** với `backend/.env` đang chạy ở `ENABLE_DEV_AUTH=false` (giá trị mặc định trong `.env.example`), gọi một API cần xác thực với header `Authorization: Bearer dev-instructor-token` và xác nhận bị từ chối (401).

#### Vòng đời JWT nội bộ

JWT do `create_access_token()` phát hành dùng thuật toán HS256, hết hạn sau 12 giờ, và hiện được lưu ở `sessionStorage` phía frontend thay vì cookie `HttpOnly`. README liệt kê đây là điểm cần nâng cấp cho production: chuyển sang access token sống ngắn kết hợp cookie `Secure, HttpOnly, SameSite` và cơ chế refresh-token rotation.
