---
title : "Deploy & Giám sát"
date : 2026-07-26
weight : 3
chapter : false
pre : " <b> 5.3.3. </b> "
---

#### Mục tiêu

Đưa frontend/backend EduCloud Lite lên môi trường thật trên AWS, và bật bảng giám sát chi phí/tài nguyên (`/admin/health`) cho vai trò Admin bằng CloudWatch và Cost Explorer.

*(Chèn ảnh chụp màn hình quá trình deploy và trang Admin Health thực tế của bạn vào các vị trí `![...]` bên dưới.)*

#### Bước 1 — Deploy frontend bằng AWS Amplify Hosting

Repo đã có sẵn `amplify.yml` ở thư mục gốc `EduCloud/`:

```yaml
version: 1
applications:
  - appRoot: frontend
    frontend:
      phases:
        preBuild:
          commands:
            - npm ci
        build:
          commands:
            - npm run build
      artifacts:
        baseDirectory: dist
        files:
          - '**/*'
      cache:
        paths:
          - node_modules/**/*
```

1. Vào **AWS Amplify → New app → Host web app**, kết nối với repo GitHub chứa EduCloud.
2. Amplify tự nhận diện `amplify.yml`; xác nhận **App root = frontend**.
3. Khai báo biến môi trường build (`VITE_API_BASE_URL`, `VITE_COGNITO_REGION`, `VITE_COGNITO_USER_POOL_ID`, `VITE_COGNITO_CLIENT_ID`) trỏ đến backend production và Cognito pool đã tạo ở phần trước.
4. Deploy; mỗi lần push lên nhánh đã chọn sẽ tự build lại.

![amplify deploy](/images/5-Workshop/5.3.3-Deploy-Monitoring/amplify-deploy.png)

#### Bước 2 — Deploy backend

Repo có sẵn `Procfile` (`web: uvicorn main:app --host 0.0.0.0 --port 8000`), phù hợp với các nền tảng chạy theo Procfile hoặc container (App Runner, EC2 + process manager, Heroku-like PaaS). Khi deploy production cần đổi so với `.env` local:

```dotenv
APP_ENV=production
ALLOW_LEGACY_AUTH=false
ENABLE_DEV_AUTH=false
JWT_SECRET_KEY=<chuỗi random dài, khác giá trị dev>
CORS_ORIGINS=https://<domain-frontend-amplify>
```

#### Bước 3 — Bật giám sát AWS cho trang Admin Health

1. Gắn cho role/IAM user chạy backend đúng hai quyền đọc đã chuẩn bị ở phần trước: `cloudwatch:GetMetricStatistics` và `ce:GetCostAndUsage`. Không cấp thêm quyền sửa billing.
2. Đặt `AWS_MONITORING_ENABLED=true` trong `.env` production.
3. Đăng nhập vai trò Admin, mở `/admin/health`. Trang này gọi API tổng hợp 4 nhóm dữ liệu (`monitoring_service.get_health_dashboard`):
   - **Database**: độ trễ, dung lượng, số dòng ở các bảng chính (users, courses, lessons, enrollments, assessment_attempts, certificates).
   - **Traffic**: số request/lỗi 5 phút gần nhất, route được gọi nhiều nhất — dữ liệu này được middleware trong `main.py` ghi lại theo thời gian thực (in-memory), không cần CloudWatch.
   - **Storage**: nếu `UPLOAD_STORAGE=s3`, đọc `BucketSizeBytes`/`NumberOfObjects` từ CloudWatch namespace `AWS/S3`.
   - **AWS cost**: chi phí tháng hiện tại (`UnblendedCost`) và credit đã áp dụng, đọc từ Cost Explorer (`get_cost_and_usage`).

![trang admin health](/images/5-Workshop/5.3.3-Deploy-Monitoring/admin-health.png)

#### Bước 4 — Kiểm thử

+ So sánh số liệu dung lượng bucket hiển thị trên `/admin/health` với **S3 → bucket → Metrics** trên console CloudWatch thật (lưu ý: CloudWatch cập nhật số liệu S3 có độ trễ, thường theo ngày).
+ So sánh chi phí tháng hiện tại hiển thị với **Cost Explorer** trên console AWS Billing.
+ Tắt `AWS_MONITORING_ENABLED` và xác nhận trang vẫn hoạt động bình thường, chỉ ẩn phần chi phí/S3 metrics (tính năng phải là optional, không được làm hỏng trang khi tắt).
