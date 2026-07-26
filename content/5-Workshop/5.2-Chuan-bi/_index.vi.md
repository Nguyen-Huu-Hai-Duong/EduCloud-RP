---
title : "Các bước chuẩn bị"
date : 2026-07-26
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### Tài khoản và công cụ

+ Một tài khoản AWS cá nhân (region gợi ý: `ap-southeast-1` — Singapore), không dùng chung mật khẩu/tài khoản với người khác.
+ Một project **Supabase** (PostgreSQL) đã tạo sẵn — dùng chuỗi kết nối **Session Pooler**, port `5432`.
+ **Node.js** ≥ 18, **Python** 3.12 (tránh 3.14 vì một số gói build từ source chưa có wheel sẵn).
+ **AWS CLI** đã cấu hình `aws configure` với access key/secret key của tài khoản trên (dùng để test nhanh S3 và kiểm tra IAM).
+ Repo `EduCloud` đã clone về máy, đã copy `backend/.env.example` → `backend/.env` và `frontend/.env.example` → `frontend/.env`.

#### IAM permissions cần cấp cho user/role triển khai

Không cần quyền admin toàn bộ tài khoản; chỉ cần đủ quyền cho ba việc: tạo/tra cứu Cognito User Pool, quản lý bucket S3, và đọc (read-only) CloudWatch/Cost Explorer.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "CognitoSetup",
      "Effect": "Allow",
      "Action": [
        "cognito-idp:CreateUserPool",
        "cognito-idp:CreateUserPoolClient",
        "cognito-idp:UpdateUserPool",
        "cognito-idp:DescribeUserPool",
        "cognito-idp:DescribeUserPoolClient",
        "cognito-idp:AdminCreateUser",
        "cognito-idp:AdminSetUserPassword"
      ],
      "Resource": "*"
    },
    {
      "Sid": "LambdaTrigger",
      "Effect": "Allow",
      "Action": [
        "lambda:CreateFunction",
        "lambda:AddPermission",
        "lambda:InvokeFunction",
        "lambda:GetFunction"
      ],
      "Resource": "*"
    },
    {
      "Sid": "S3Storage",
      "Effect": "Allow",
      "Action": [
        "s3:CreateBucket",
        "s3:PutObject",
        "s3:GetObject",
        "s3:DeleteObject",
        "s3:ListBucket",
        "s3:PutBucketPolicy",
        "s3:PutBucketPublicAccessBlock",
        "s3:PutBucketOwnershipControls"
      ],
      "Resource": "*"
    },
    {
      "Sid": "MonitoringReadOnly",
      "Effect": "Allow",
      "Action": [
        "cloudwatch:GetMetricStatistics",
        "ce:GetCostAndUsage"
      ],
      "Resource": "*"
    }
  ]
}
```

{{% notice note %}}
Đây là tập quyền tối thiểu cho các bước trong workshop này. Không cấp thêm quyền sửa/xóa billing (`aws-portal:*`, `ce:UpdateCostAllocationTagsStatus`...) cho role dùng ở bước giám sát — role đó chỉ nên có quyền đọc.
{{% /notice %}}

Sau khi chuẩn bị xong, chuyển sang phần [Triển khai AWS cho EduCloud](../5.3-Trien-khai-AWS/) để cấu hình lần lượt Cognito, S3 và deploy/giám sát.
