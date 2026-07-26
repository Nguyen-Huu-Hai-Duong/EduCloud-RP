---
title: "Proposal"
date: 2026-07-26
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

## Project Proposal — EduCloud

### Background

The demand for online learning is growing, bringing with it the need for course management, document/video storage, user role management, and learning-progress tracking. Deploying the system on the cloud makes the application accessible online, easy to scale, easy to monitor, and aligned with modern software development practices.

### Problems to Solve

- Managing users and their roles.
- Managing courses and lessons.
- Securely storing documents and videos.
- Tracking learning progress.
- Deploying a system that is accessible online.
- Tracking system logs and errors.
- Cleaning up AWS resources to avoid unnecessary cost.

### Project Objectives

**Functional objectives**

- Registration and sign-in; Student, Instructor, and Admin roles.
- Browsing the course list, course details, and lessons.
- Enrolling in courses, marking lessons complete, and viewing learning progress.
- Uploading images, videos, or documents for course content.

**Technical objectives**

- A stable, clearly structured backend API.
- Database running on AWS RDS; files stored on AWS S3.
- Backend deployed to AWS EC2 or Lambda.
- Logs recorded via AWS CloudWatch.
- Step-by-step deployment documentation and a resource clean-up guide.

**Learning objectives**

- Understand the process of building a web application on AWS.
- Practice integrating frontend, backend, database, and cloud services.
- Build teamwork, progress management, testing, and technical-writing skills.

### Project Scope

| In scope | Out of scope |
| :--- | :--- |
| User authentication; Course management; Lesson management; Enrollment; Progress tracking; S3 upload; RDS database; CloudWatch logging; Basic UI. | Real payment processing; Livestreaming; AI recommendations; Mobile app; Advanced certificate system. |

### System Architecture

*(Insert your own system architecture diagram here)*

![EduCloud system architecture](/images/2-Proposal/architecture-diagram.png)

**Proposed architecture flow:**

- User → Frontend Web → Backend API → AWS RDS.
- Backend API → AWS S3.
- Backend API → AWS CloudWatch.
- AWS IAM manages access permissions between services.

**Main components**

- **Frontend Web:** Interface for Student, Instructor, and Admin.
- **Backend API:** Handles business logic, authentication, and data management.
- **AWS EC2 or Lambda:** Backend deployment environment.
- **AWS RDS PostgreSQL:** Stores user, course, lesson, enrollment, and progress data.
- **AWS S3:** Stores course images, lesson videos, and PDF documents.
- **AWS CloudWatch:** Tracks logs, errors, and system activity.
- **AWS IAM:** Securely manages access permissions between services.

### Why These AWS Services

| AWS Service | Purpose | Reason for choosing it |
| :--- | :--- | :--- |
| EC2 or Lambda | Deploy the backend API | Well-suited to deploying web apps/APIs, easy to configure for the project's needs. |
| S3 | Store images, videos, documents | A widely used, durable object-storage service that's easy to integrate for upload/download. |
| RDS PostgreSQL | Store relational data | Stable managed database, reduces manual operational effort. |
| CloudWatch | Logging and monitoring | Tracks logs, errors, and metrics, and supports debugging the system. |
| IAM | Access management | Increases security when the backend accesses S3, CloudWatch, and other services. |

### Project Timeline

| Week | Goal | Main tasks | Expected output | Owner |
| :--- | :--- | :--- | :--- | :--- |
| Week 1 | Cloud web overview | Study web architecture on the cloud, finalize the topic, assign roles | Initial proposal | [Fill in] |
| Week 2 | Requirements analysis | Design the database, design the AWS architecture | SRS, ERD, architecture draft | [Fill in] |
| Week 3 | Project bootstrap | Bootstrap backend, frontend, GitHub repo, project structure | Source base | [Fill in] |
| Week 4 | Authentication | Build authentication, user roles, JWT | Auth API | [Fill in] |
| Week 5 | Course/Lesson API | Build the course API and lesson API | Core API | [Fill in] |
| Week 6 | Basic frontend | Build the frontend for the main pages | UI prototype | [Fill in] |
| Week 7 | S3 upload | Integrate file/video/document upload | Upload module | [Fill in] |
| Week 8 | RDS/Backend deploy | Integrate RDS, deploy backend to AWS | Public backend endpoint | [Fill in] |
| Week 9 | Enrollment/Progress | Build enrollment and progress tracking | Learning flow | [Fill in] |
| Week 10 | Monitoring | Configure CloudWatch, logging, monitoring | Log dashboard/basic metrics | [Fill in] |
| Week 11 | E2E testing | End-to-end testing, bug fixes, UI/API optimization | Test report | [Fill in] |
| Week 12 | Finalization | Finalize documentation, clean-up guide, slides, and demo | Final draft/demo | [Fill in] |

### Risks and Mitigation

| Risk | Impact level | Cause | Mitigation |
| :--- | :--- | :--- | :--- |
| Cannot connect to RDS | High | Wrong security group, endpoint, or credentials | Check the inbound rule, VPC, endpoint, username/password, and backend logs. |
| Permission error when uploading to S3 | High | Incorrect IAM policy or bucket policy | Apply least privilege, test with the AWS CLI, check S3 CORS if needed. |
| Unexpected AWS cost | High | Forgetting to disable/delete resources | Monitor the Billing Dashboard, set a budget alert, follow the clean-up checklist. |
| CORS error between frontend and backend | Medium | Backend origin not configured | Configure CORS for the frontend domain and the local environment. |
| Frontend/backend API mismatch | Medium | Missing API contract | Agree on an API spec, keep Postman/OpenAPI updated, and review periodically. |
| Team member misses a deadline | Medium | Workload not well distributed | Break tasks down further, keep the worklog updated, and support each other as needed. |
| Deployment failure on EC2/Lambda | High | Missing environment variables or wrong runtime | Prepare a deployment checklist, check logs, and roll back to a stable release. |
