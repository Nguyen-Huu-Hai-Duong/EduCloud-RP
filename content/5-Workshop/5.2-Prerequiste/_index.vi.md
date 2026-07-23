---
title : "Các bước chuẩn bị"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### IAM permissions

Gắn IAM permission policy sau vào tài khoản/role AWS bạn dùng để làm workshop này. Đây là quyền tối thiểu để tạo, cấu hình và dọn dẹp một Cognito User Pool:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "CognitoWorkshop",
            "Effect": "Allow",
            "Action": [
                "cognito-idp:CreateUserPool",
                "cognito-idp:DeleteUserPool",
                "cognito-idp:DescribeUserPool",
                "cognito-idp:UpdateUserPool",
                "cognito-idp:CreateUserPoolClient",
                "cognito-idp:DeleteUserPoolClient",
                "cognito-idp:DescribeUserPoolClient",
                "cognito-idp:UpdateUserPoolClient",
                "cognito-idp:ListUserPools",
                "cognito-idp:ListUserPoolClients",
                "cognito-idp:ListUsers",
                "cognito-idp:AdminGetUser",
                "cognito-idp:AdminCreateUser",
                "cognito-idp:AdminDeleteUser",
                "cognito-idp:AdminConfirmSignUp",
                "cognito-idp:AdminInitiateAuth",
                "cognito-idp:SignUp",
                "cognito-idp:ConfirmSignUp",
                "cognito-idp:ForgotPassword",
                "cognito-idp:ConfirmForgotPassword"
            ],
            "Resource": "*"
        }
    ]
}
```

{{% notice note %}}
Không cần các quyền EC2/VPC/Route53/CloudFormation như bản workshop gốc — Cognito là dịch vụ managed, không cần triển khai hạ tầng mạng.
{{% /notice %}}

#### Chuẩn bị dự án EduCloud Lite ở local

Trong lab này, chúng ta dùng **region ap-southeast-1 (Singapore)** để khớp với cấu hình mặc định trong repo.

1. Yêu cầu cài đặt sẵn: **Python 3.11+**, **Node.js 18+**, và một project **Supabase** (đóng vai trò database ứng dụng, không phải nơi xác thực).

2. Clone và chuẩn bị backend:

```powershell
cd backend
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements-dev.txt
Copy-Item .env.example .env
```

3. Chuẩn bị frontend (terminal thứ hai):

```powershell
cd frontend
Copy-Item .env.example .env
npm install
```

4. Mở `backend/.env`, điền `DATABASE_URL` trỏ tới Supabase Session Pooler của bạn. Các biến `COGNITO_REGION`, `COGNITO_USER_POOL_ID`, `COGNITO_CLIENT_ID` cứ để giá trị mặc định — bạn sẽ thay chúng bằng giá trị thật sau khi tạo User Pool ở phần tiếp theo.

*(Chèn ảnh terminal cài đặt thành công tại đây)*

Sau bước này, môi trường local đã sẵn sàng. Ở phần **5.3**, chúng ta sẽ tạo Amazon Cognito User Pool; ở phần **5.4**, chúng ta quay lại các file `.env` này để nối EduCloud với User Pool vừa tạo.
