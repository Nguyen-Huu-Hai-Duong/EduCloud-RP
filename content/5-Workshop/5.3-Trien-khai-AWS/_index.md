---
title : "Deploying AWS for EduCloud"
date : 2026-07-26
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Three areas of deployment

This section has three steps, done in sequence since each one depends on the configuration of the previous one (the frontend needs a valid Cognito token before it can call the upload/monitoring APIs):

1. [Setting up Amazon Cognito (Authentication)](5.3.1-Cognito/)
2. [Setting up Amazon S3 (Upload storage)](5.3.2-S3-Upload/)
3. [Deploy & Monitoring (Amplify + CloudWatch/Cost Explorer)](5.3.3-Deploy-Monitoring/)
