---
title: "Week 6 - Extending and testing the backend API"
menuTitle: "Week 6"
weight: 6
pre: "<b>1.6.</b>"
---

**Period:** July 13, 2026 - July 17, 2026

## Objectives

- Support the team as they built authentication, enrollment, and dashboard features on top of the Course/Lesson API.
- Extend and refine the Course/Lesson API based on integration feedback from the frontend.
- Learn CloudFront fundamentals for later use in delivering course media.

## AWS Learning Phase

| Learning content | Reference | Application in EduCloud |
| --- | --- | --- |
| How a CDN behaves, cache settings, and serving content from a private origin. | [CloudFront with S3 Origin](https://000094.awsstudygroup.com/) | Prepared me to understand and later document how the team would deliver course media. |
| Frontend hosting, static website deployment, and routing for single-page apps. | [Deploy Static Website on AWS](https://000057.awsstudygroup.com/) | Gave context for how the React app the team was building would eventually be hosted. |

## Work completed

| Date | Activity | Outcome |
| --- | --- | --- |
| Jul 13 | Reviewed integration feedback from the teammate building the frontend and adjusted the Course/Lesson API response shapes. | Aligned the API contract with what the frontend actually needed. |
| Jul 14 | Helped test the enrollment flow the team was building against my Course API to make sure published-course data stayed consistent. | Found and fixed a data-consistency issue in the Course API. |
| Jul 15 | Studied CloudFront and S3 origin patterns to understand how course media would later be delivered. | Got ready to help review the delivery setup during the deployment week. |
| Jul 16 | Documented the Course & Lesson API endpoints for the rest of the team. | Made the API easier for teammates to use without asking me directly. |
| Jul 17 | Joined the team's review of the Supabase-backed workflows and role-based dashboards being built that week. | Stayed aligned with how my API was being used elsewhere in the app. |

## Achievements

- Extended and stabilized the Course/Lesson API based on real integration needs from the frontend.
- Documented the Course/Lesson API for the rest of the team.
- Built a working understanding of CloudFront ahead of the deployment phase.
