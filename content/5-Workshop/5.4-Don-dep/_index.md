---
title : "Cleaning up resources"
date : 2026-07-26
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### Summary

In this workshop, EduCloud Lite was connected to three AWS service areas: **Cognito** for authentication, **S3** for upload storage, and **CloudWatch/Cost Explorer** for cost/resource monitoring on the Admin Health page, alongside deploying the frontend through **Amplify**.

To avoid unwanted cost after finishing your report/demo period, clean up resources in the following order:

#### Clean-up

1. **Amazon S3**
   - Open the S3 console and select the bucket created for the course (e.g. `educloud-lite-media-bucket`).
   - Empty all objects in the bucket, then **Delete bucket**.

2. **Amazon Cognito**
   - If no longer needed for demos, delete the **User pool** created (along with its App client).
   - Delete the pre sign-up Lambda function if not used by another project.

3. **Database (Supabase / RDS PostgreSQL)**
   - Pause or delete the project/instance if it won't be used long-term.

4. **Backend hosting**
   - Stop/terminate the instance or service running the backend (App Runner/EC2/a Procfile-based platform).

5. **AWS Amplify**
   - Delete the Amplify app used to host the frontend if you don't need to keep the demo online.

6. **AWS CloudWatch**
   - Delete the log groups related to the application.

7. **Check costs**
   - Open the **AWS Billing & Cost Management Dashboard** and confirm no resource is generating unexpected cost.
