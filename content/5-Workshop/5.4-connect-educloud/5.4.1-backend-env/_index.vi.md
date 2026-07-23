---
title : "Cấu hình biến môi trường backend"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.4.1 </b> "
---

Để backend FastAPI xác minh được token do Cognito phát hành, bạn cần khai báo 3 biến môi trường trong `backend/.env`, lấy từ phần 5.3:

```dotenv
COGNITO_REGION=ap-southeast-1
COGNITO_USER_POOL_ID=ap-southeast-1_xxxxxxxxx
COGNITO_CLIENT_ID=xxxxxxxxxxxxxxxxxxxxxxxxxx
```

1. Mở `backend/.env`, thay 2 giá trị `COGNITO_USER_POOL_ID` và `COGNITO_CLIENT_ID` bằng giá trị bạn đã ghi lại ở 5.3.1/5.3.2.

*(Chèn ảnh file .env đã điền — nhớ che các giá trị nhạy cảm khác trước khi chụp)*

2. Khởi động lại backend để nạp cấu hình mới:

```powershell
cd backend
.\.venv\Scripts\python.exe -m scripts.check_database
.\.venv\Scripts\python.exe -m scripts.seed_dev_accounts
uvicorn main:app --reload --port 8001
```

#### Backend xác minh Cognito ID token như thế nào

`app/services/cognito_service.py` xử lý việc xác minh và trao đổi token:

```python
def verify_id_token(id_token: str) -> dict:
    header = jwt.get_unverified_header(id_token)
    signing_key = _signing_keys().get(header.get("kid"))   # tải JWKS từ
    ...                                                     # {issuer}/.well-known/jwks.json
    claims = jwt.decode(
        id_token, signing_key, algorithms=["RS256"],
        audience=settings.COGNITO_CLIENT_ID,
        issuer=settings.COGNITO_ISSUER,
    )
    if claims.get("token_use") != "id":
        raise ValueError("Cognito ID token required")
    if claims.get("email_verified") is not True:
        raise ValueError("Confirm your email before signing in")
    return claims
```

Có 4 điều backend luôn kiểm tra trước khi tin tưởng một token: chữ ký RS256 khớp với JWKS của đúng User Pool, `audience` khớp `COGNITO_CLIENT_ID`, `issuer` khớp User Pool, token phải là **ID token** (`token_use == "id"`, không chấp nhận access token), và email phải đã được xác thực.

Sau khi token hợp lệ, `exchange_token()` sẽ:

+ Tìm user trong Supabase theo `cognito_sub` (subject của Cognito).
+ Nếu chưa có, thử liên kết theo email (trường hợp tài khoản legacy cũ đang migrate) hoặc tạo mới một `User` với `role="student"` mặc định.
+ Phát hành JWT nội bộ của EduCloud (12 giờ, HS256) chứa `role` hiện tại lấy từ Supabase — Cognito hoàn toàn không biết và không quyết định role này.

Endpoint tương ứng là `POST /api/auth/cognito/exchange`, nhận `{ "id_token": "<Cognito ID token>" }` và trả về `{ token, user }` giống hệt định dạng của `/api/auth/login` (legacy), để frontend không cần phân biệt hai nguồn xác thực khi lưu session.
