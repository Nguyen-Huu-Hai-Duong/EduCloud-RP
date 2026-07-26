---
title : "Architecture overview"
date : 2026-07-26
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Introducing EduCloud Lite

EduCloud Lite serves three roles: **Student** (enroll in courses, study lessons, take the final assessment, receive a certificate), **Instructor** (create courses, add lessons, configure assessments), and **Admin** (approve Instructor applications, monitor the system).

Before AWS was integrated, the app ran entirely on its own: authentication was self-managed with bcrypt, uploaded files were kept on local disk, and there were no cost/resource monitoring tools. This workshop chapter describes how the following three AWS areas were added on top of that existing architecture.

#### Overall architecture

```
                 ┌──────────────────────┐
                 │   Amazon Cognito     │  (1) Sign-up / sign-in / forgot password
                 └──────────┬───────────┘
                             │ ID Token (JWT)
                 ┌───────────▼───────────┐
Browser (React) ─┤  POST /api/auth/      │
  Vite + TS      │  cognito/exchange     │
                 └──────────┬───────────┘
                             │ verify + map user, issue internal JWT
                 ┌───────────▼───────────┐        ┌──────────────────┐
                 │   Backend FastAPI      ├───────▶│  PostgreSQL       │
                 │   (uvicorn)            │        │  (Supabase)       │
                 └───┬───────────────┬────┘        └──────────────────┘
                     │               │
        (2) file upload│               │ (3) read metrics
                     ▼               ▼
             ┌──────────────┐  ┌─────────────────────┐
             │  Amazon S3    │  │ CloudWatch / Cost    │
             │  (thumbnail,  │  │ Explorer (read-only) │
             │  material,    │  └─────────────────────┘
             │  video)       │
             └──────────────┘
```

+ **(1) Cognito**: owns the entire account lifecycle (sign-up, email confirmation, sign-in, password reset). The backend only verifies the ID Token issued by Cognito and maps it to a user in PostgreSQL.
+ **(2) S3**: when `UPLOAD_STORAGE=s3`, the backend pushes files straight to the S3 bucket instead of storing them under `backend/uploads`.
+ **(3) CloudWatch / Cost Explorer**: when `AWS_MONITORING_ENABLED=true`, the backend reads (read-only) S3 storage size and the current month's AWS cost to display on the `/admin/health` page.

The next three sections go deeper into each area, in the actual order they were implemented: Cognito first (every API needs an authenticated user), then S3 (to support the upload features), and finally deployment plus monitoring.
