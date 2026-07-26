---
title : "Deploy & Monitoring"
date : 2026-07-26
weight : 3
chapter : false
pre : " <b> 5.3.3. </b> "
---

#### Goal

Ship EduCloud Lite's frontend/backend to a real AWS environment, and enable the cost/resource monitoring dashboard (`/admin/health`) for the Admin role using CloudWatch and Cost Explorer.

*(Insert your own screenshots of the deployment process and the actual Admin Health page at the `![...]` placeholders below.)*

#### Step 1 — Deploy the frontend with AWS Amplify Hosting

The repo already has an `amplify.yml` at the root of `EduCloud/`:

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

1. Go to **AWS Amplify → New app → Host web app** and connect it to the GitHub repo containing EduCloud.
2. Amplify auto-detects `amplify.yml`; confirm **App root = frontend**.
3. Declare the build environment variables (`VITE_API_BASE_URL`, `VITE_COGNITO_REGION`, `VITE_COGNITO_USER_POOL_ID`, `VITE_COGNITO_CLIENT_ID`) pointing at the production backend and the Cognito pool created earlier.
4. Deploy; every push to the chosen branch triggers an automatic rebuild.

![amplify deploy](/images/5-Workshop/5.3.3-Deploy-Monitoring/amplify-deploy.png)

#### Step 2 — Deploy the backend

The repo already has a `Procfile` (`web: uvicorn main:app --host 0.0.0.0 --port 8000`), suited to platforms that run off a Procfile or a container (App Runner, EC2 + a process manager, a Heroku-like PaaS). For a production deploy, change the following compared to the local `.env`:

```dotenv
APP_ENV=production
ALLOW_LEGACY_AUTH=false
ENABLE_DEV_AUTH=false
JWT_SECRET_KEY=<a long random string, different from the dev value>
CORS_ORIGINS=https://<amplify-frontend-domain>
```

#### Step 3 — Enable AWS monitoring for the Admin Health page

1. Grant the IAM role/user running the backend exactly the two read permissions prepared earlier: `cloudwatch:GetMetricStatistics` and `ce:GetCostAndUsage`. Do not add billing-mutation permissions.
2. Set `AWS_MONITORING_ENABLED=true` in the production `.env`.
3. Sign in as Admin and open `/admin/health`. This page calls one aggregated API (`monitoring_service.get_health_dashboard`) that returns four sections:
   - **Database**: latency, size, and row counts for the main tables (users, courses, lessons, enrollments, assessment_attempts, certificates).
   - **Traffic**: request/error counts for the last 5 minutes and the most-hit routes — this data is recorded in real time by a middleware in `main.py` (in-memory), no CloudWatch needed.
   - **Storage**: if `UPLOAD_STORAGE=s3`, reads `BucketSizeBytes`/`NumberOfObjects` from the CloudWatch `AWS/S3` namespace.
   - **AWS cost**: current month's cost (`UnblendedCost`) and applied credits, read from Cost Explorer (`get_cost_and_usage`).

![admin health page](/images/5-Workshop/5.3.3-Deploy-Monitoring/admin-health.png)

#### Step 4 — Testing

+ Compare the bucket storage size shown on `/admin/health` against **S3 → bucket → Metrics** on the real CloudWatch console (note: CloudWatch's S3 metrics are delayed, typically updated daily).
+ Compare the current month's cost shown against **Cost Explorer** on the AWS Billing console.
+ Turn `AWS_MONITORING_ENABLED` off and confirm the page still works normally, just hiding the cost/S3-metrics section (the feature must be optional and must not break the page when disabled).
