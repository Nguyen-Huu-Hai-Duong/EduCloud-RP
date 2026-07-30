---
title: "Week 6 - Enrollment and learning progress"
menuTitle: "Week 6"
weight: 6
pre: "<b>1.6.</b>"
---

**Period:** July 13, 2026 - July 17, 2026

## Objectives

- Provide a public catalog of published courses and an enrollment flow.
- Build the Student Learning Page.
- Persist per-lesson progress and completion percentages.

## AWS Learning Phase

| Learning content | Reference | Application in EduCloud |
| --- | --- | --- |
| Frontend hosting, static website deployment, and routing for single-page apps. | [Deploy Static Website on AWS](https://000057.awsstudygroup.com/) | Got the React app ready for production hosting down the line. |
| How a CDN behaves, cache settings, and serving content from a private origin. | [CloudFront with S3 Origin](https://000094.awsstudygroup.com/) | Sketched out how student learning resources could be delivered through CloudFront. |

## Work completed

| Date | Activity | Outcome |
| --- | --- | --- |
| Jul 13 | Built the catalog, search, course cards, and detail page. | Pulled published courses from Supabase for display. |
| Jul 14 | Built a Student-only, idempotent enrollment flow with uniqueness constraints. | Stopped duplicate enrollments from being created. |
| Jul 15 | Built the Learning Page with a lesson playlist, video, notes, and materials. | Restricted full lesson content to enrolled Students only. |
| Jul 16 | Built complete/undo progress endpoints and completion-percentage calculation. | Persisted each Student's lesson progress. |
| Jul 17 | Added My Learning, resuming at the first incomplete lesson, and Instructor enrollment counts. | Gave students continuity and instructors live reporting. |

## Achievements

- Public APIs return outlines only, not private lesson assets.
- Student enrollments and progress now persist in Supabase.
- The Learning Page supports lesson navigation and marking completion.
- Dashboards pull real database data instead of fixed demo values.
