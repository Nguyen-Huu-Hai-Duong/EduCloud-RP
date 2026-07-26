---
title : "Prerequisites"
date : 2026-07-26
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### Accounts and tools

+ A personal AWS account (suggested region: `ap-southeast-1` — Singapore), never shared with another developer.
+ A **Supabase** (PostgreSQL) project already created — use the **Session Pooler** connection string, port `5432`.
+ **Node.js** ≥ 18, **Python** 3.12 (avoid 3.14; some packages don't yet ship prebuilt wheels for it).
+ **AWS CLI** configured (`aws configure`) with the access key/secret key of the account above — used to quickly test S3 and check IAM.
+ The `EduCloud` repo cloned locally, with `backend/.env.example` → `backend/.env` and `frontend/.env.example` → `frontend/.env` already copied.

#### IAM permissions needed for the deploying user/role

Full admin access is not required; only enough permissions for three things: creating/looking up the Cognito User Pool, managing the S3 bucket, and reading (read-only) CloudWatch/Cost Explorer.

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
This is the minimal permission set for the steps in this workshop. Do not grant billing-mutation permissions (`aws-portal:*`, `ce:UpdateCostAllocationTagsStatus`, etc.) to the role used for monitoring — that role should stay read-only.
{{% /notice %}}

Once prerequisites are ready, move on to [Deploying AWS for EduCloud](../5.3-Trien-khai-AWS/) to configure Cognito, S3, and deployment/monitoring in turn.
