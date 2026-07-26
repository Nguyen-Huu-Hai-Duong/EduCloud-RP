---
title: "Workshop"
date: 2026-07-26
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# AWS Integration for the EduCloud Lite Online Learning Platform

#### Overview

**EduCloud Lite** is an online learning platform with a **FastAPI (Python)** backend and a **React + TypeScript (Vite)** frontend, backed by **PostgreSQL (Supabase)**. This Workshop chapter walks back through the three AWS service areas actually integrated into EduCloud Lite:

+ **Amazon Cognito** — user authentication (sign-up, sign-in, forgot password) instead of a hand-rolled auth system.
+ **Amazon S3** — storage for user-uploaded files (course thumbnails, lesson materials, lecture videos).
+ **Deployment & monitoring** — deploying the app on AWS and enabling CloudWatch/Cost Explorer read-only metrics for the Admin Health page.

#### Content

1. [Architecture overview](5.1-Tong-quan/)
2. [Prerequisites](5.2-Chuan-bi/)
3. [Deploying AWS for EduCloud](5.3-Trien-khai-AWS/)
4. [Cleaning up resources](5.4-Don-dep/)
