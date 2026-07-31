---
title: "Week 5 - Building the Course & Lesson backend API"
menuTitle: "Week 5"
weight: 5
pre: "<b>1.5.</b>"
---

**Period:** July 6, 2026 - July 10, 2026

## Objectives

- Build the Course API: models, schemas, CRUD routes, and ownership checks.
- Build the Lesson API: ordered curriculum, notes, and video/material URL fields.
- Learn S3 fundamentals in support of the team's later upload and storage work.

## AWS Learning Phase

| Learning content | Reference | Application in EduCloud |
| --- | --- | --- |
| S3 object storage, bucket privacy settings, and storing uploaded learning resources. | [Amazon S3 Security Best Practices](https://000069.awsstudygroup.com/) | Prepared for the team's later work on private course-asset storage. |
| Amplify's authentication and storage patterns built on Cognito and S3. | [Amplify Authentication and Storage](https://000134.awsstudygroup.com/) | Gave context for how uploads would eventually connect to the Course/Lesson data I was building the API for. |

## Work completed

| Date | Activity | Outcome |
| --- | --- | --- |
| Jul 06 | Built the Course model, schema, and CRUD endpoints, including ownership checks so Instructors can only modify courses they own. | Instructors can create, update, and manage courses through the API. |
| Jul 07 | Added validation for course metadata: title, description, price, tags, and status transitions. | Prevented invalid course data from being saved. |
| Jul 08 | Built the Lesson model and CRUD endpoints with order indexes, notes, and video/material URL fields. | Enabled ordered lesson curricula through the API. |
| Jul 09 | Wrote tests for the Course and Lesson endpoints and fixed the issues they turned up. | Confirmed the API behaved correctly for common and edge cases. |
| Jul 10 | Finalized and merged the Course & Lesson backend API with the team. | Completed my core backend contribution to the project. |

## Achievements

- Shipped the Course and Lesson CRUD API, including ownership checks.
- Learned S3 fundamentals ahead of the team's later upload and storage work.
- Delivered a tested, working piece of the backend the rest of the team could build on.
