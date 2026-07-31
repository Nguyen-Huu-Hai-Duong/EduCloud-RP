---
title: "Week 7 - Supporting integration and learning the AWS deployment process"
menuTitle: "Week 7"
weight: 7
pre: "<b>1.7.</b>"
---

**Period:** July 20, 2026 - July 24, 2026

## Objectives

- Support the team's final push on role workflows, assessments, and deployment.
- Learn how the team's Elastic Beanstalk, S3, and CloudFront deployment worked so I could document it accurately for the report.
- Keep the Course/Lesson API working correctly as new features landed on top of it.

## AWS Learning Phase

| Learning content | Reference | Application in EduCloud |
| --- | --- | --- |
| CloudWatch metrics, logs, alarms, and dashboard concepts. | [AWS CloudWatch Workshop](https://000008.awsstudygroup.com/) | Prepared me to understand and later document how the deployed app could be monitored. |
| Patterns for running applications reliably: health checks, idempotency, and recoverable request handling. | [Explore AWS Services](https://cloudjourney.awsstudygroup.com/) | Gave me the background to review the assessment/certificate logic teammates were adding for idempotency issues. |

## Work completed

| Date | Activity | Outcome |
| --- | --- | --- |
| Jul 20 | Retested my Course/Lesson API against the newly added assessment and certificate features to check for conflicts. | Confirmed my API still behaved correctly alongside the new features. |
| Jul 21 | Followed along as the team configured Elastic Beanstalk for the backend deployment. | Learned the deployment steps I would later document in the workshop report. |
| Jul 22 | Followed along as the team set up S3 and CloudFront for private course-media delivery. | Understood the OAC and bucket-policy setup well enough to write it up later. |
| Jul 23 | Reviewed CloudWatch basics for monitoring the deployed backend. | Got ready to document the monitoring setup in the report. |
| Jul 24 | Helped verify the team's final build before deployment and fixed a small bug in the Course API found during that check. | Contributed to a clean final build. |

## Achievements

- Kept the Course/Lesson API working correctly through the team's final integration push.
- Learned the team's AWS deployment process well enough to document it in detail for the workshop report.
- Found and fixed a bug during final verification before deployment.
