---
title: "Event 3"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

### Event Information

- **Event name:** AWS Security, Cloud Fundamentals and Monitoring
- **Date & time:** July 11, 2026, 09:00–12:00
- **Location:** Level 26, Bitexco Financial Tower, Ho Chi Minh City
- **Organizer:** AWS First Cloud AI Journey

### Event Objectives

This session tied together three things that don't usually get taught in the same room: how AI-assisted tooling fits into application security, what actually gets tested on the AWS Certified Cloud Practitioner exam, and why infrastructure that looks healthy on a dashboard can still be failing users. The goal wasn't certification prep or a security checklist on their own — it was giving students something they could carry straight into a real AWS project.

### Speakers

- **Nguyen Tuan Thinh** — DevOps / DevSecOps / Cloud Engineer, Styl Solutions — *Securing Your Web Apps With AWS Security Agent*
- **Ngo Le Tan Huy** — *Inside the Exam: AWS Cloud Practitioner*
- **Nguyen Huynh Son** — Infrastructure Support Engineer at Endava, formerly Infrastructure Reliability Engineer at SPS — *SLA and Monitoring: From SLA to Monitoring What Really Matters*

### Key Highlights

**Cloud Architecture Competition Final:** Two teams, KLKAT and Ngũ Đại Hiệp, closed out the session with a head-to-head round testing AWS knowledge, which kept the technical content grounded in something more competitive than a straight lecture format.

**Letting an AI agent watch your app's security, not just your code:** The security talk framed AI agents as something that can sit across the whole lifecycle rather than a single scan step. A design review can read architecture docs and infrastructure-as-code definitions before anything is deployed. A code review pass can flag vulnerabilities and leaked secrets directly in a pull request. Beyond static checks, an automated pentest agent can chain together multi-step attacks and hand back findings a human can actually verify — not just a severity score. The speaker was equally clear about where this breaks down: MFA-protected flows, business-logic bugs that need domain context to spot, and the real dollar cost of running agent task-hours at scale.

**What the Cloud Practitioner exam is actually testing:** The exam splits across four domains — Cloud Concepts, Security and Compliance, Cloud Technology and Services, and Billing, Pricing and Support — and the talk walked through where the weight really sits: the Shared Responsibility Model, IAM least privilege, the AWS Well-Architected Framework, the AWS Cloud Adoption Framework, and the cost-management tooling. The prep advice was less about memorizing service names and more about learning each service through the use case it solves, going back over every wrong mock-exam answer instead of just the score, and getting real hands-on time in the console before the exam.

**The gap between "infrastructure is healthy" and "users can actually log in":** This was the sharpest point of the day — EC2 CPU sitting comfortably low and ALB health checks all green tell you nothing about a login flow that's silently broken because of a database dependency failing underneath. The fix isn't more infrastructure metrics; it's watching four different layers together: provider/infra metrics, application-level latency and error rates, business metrics like login success rate, and the actual customer experience. The talk closed with a concrete alerting chain: CloudWatch metrics feeding a CloudWatch Alarm, which triggers an SNS notification — simple, but only useful if the metric you're alarming on is the one that matters to a user.

### Key Takeaways

- Security has to be threaded through the whole application lifecycle, not bolted on after deployment.
- AWS fundamentals — IAM, shared responsibility, Well-Architected principles, cost management — matter even on a small, single-team project, not just at enterprise scale.
- Monitoring should be built around what users are actually trying to do, not just whether the server is up.
- Logs, metrics, alarms, and user-facing signals need to be read together, not as separate dashboards nobody cross-checks.

### Applying the Lessons to EduCloud Lite

- Keep IAM roles scoped to least privilege when touching S3, Parameter Store, or CloudWatch, instead of granting broad access "to be safe."
- Treat private resources, secret storage, and application-level security as design decisions, not afterthoughts added right before deployment.
- Wire up CloudWatch logs, metrics, and alarms around the flows that actually matter to a student or instructor, not just default EC2/Elastic Beanstalk health.
- Run the architecture back against Well-Architected principles periodically, and keep an eye on cost through AWS Budgets and Cost Explorer rather than checking the bill once a month.
- Actually exercise login, enrollment, and course-access flows end to end instead of assuming "AWS resources report healthy" means the product works.

### Event Experience

What made this session land was the login-flow example during the monitoring talk — a system that would pass every infrastructure health check while quietly failing the one thing users came to do. It's a cleaner way to think about "done" than I had before: not "the resources are up," but "the thing a user needed to happen, happened." Between that, the security-agent walkthrough, and the exam-prep talk, the day worked less like three separate topics and more like one argument — that fundamentals, security, and observability all fail the same way when nobody's actually checking the outcome that matters.
