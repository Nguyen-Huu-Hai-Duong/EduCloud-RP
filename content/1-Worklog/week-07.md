---
title: "Week 7 - Final assessments and certificates"
menuTitle: "Week 7"
weight: 7
pre: "<b>1.7.</b>"
---

**Period:** July 20, 2026 - July 24, 2026

## Objectives

- Give Instructors a way to configure the final assessment for a course.
- Enforce timing, scoring, and attempt limits on the backend.
- Only issue certificates once lessons and the assessment are both complete.

## AWS Learning Phase

| Learning content | Reference | Application in EduCloud |
| --- | --- | --- |
| CloudWatch metrics, logs, alarms, and dashboards. | [AWS CloudWatch Workshop](https://000008.awsstudygroup.com/) | Sketched out how the assessment and certificate flows could be monitored once deployed. |
| Patterns for running applications reliably: health checks, idempotency, and recoverable request handling. | [Explore AWS Services](https://cloudjourney.awsstudygroup.com/) | Shaped idempotent certificate issuance and safer rules for submitting assessments. |

## Work completed

| Date | Activity | Outcome |
| --- | --- | --- |
| Jul 20 | Designed the assessment settings, questions, and attempts tables. | Configuration and attempt history now persist. |
| Jul 21 | Built an editor covering the timer, pass mark, attempt count, publication state, and dynamic answer options. | Made assessment authoring flexible. |
| Jul 22 | Added single-answer, all-correct, and any-correct grading modes plus drag-and-drop for options. | Supported several different grading strategies. |
| Jul 23 | Built the timed Student page with a question navigator, answered-state tracking, and auto-submit. | Made taking and reviewing assessments easier to follow. |
| Jul 24 | Added backend scoring, deadlines, eligibility checks, and idempotent certificate issuance with a print UI. | Enforced completion rules from end to end. |

## Achievements

- Timers and attempt limits are enforced on the backend.
- Supports up to twelve options and multiple correct answers.
- Added a clickable question navigator with previous/next controls.
- Certificates are printable and only issued after a passing, completed attempt.
