---
title: "Week 5 - Courses, lessons, and resources"
menuTitle: "Week 5"
weight: 5
pre: "<b>1.5.</b>"
---

**Period:** July 6, 2026 - July 10, 2026

## Objectives

- Let Instructors create and manage the courses they own.
- Organize lesson curricula in a defined order.
- Support thumbnails, videos, and learning materials.

## AWS Learning Phase

| Learning content | Reference | Application in EduCloud |
| --- | --- | --- |
| S3 object storage, bucket privacy settings, and storing uploaded learning resources. | [Amazon S3 Security Best Practices](https://000069.awsstudygroup.com/) | Sketched out a private upload bucket for course images and lesson resources. |
| Amplify's authentication and storage patterns built on Cognito and S3. | [Amplify Authentication and Storage](https://000134.awsstudygroup.com/) | Got the frontend and backend ready for a later move of uploads from local storage to AWS S3. |

## Work completed

| Date | Activity | Outcome |
| --- | --- | --- |
| Jul 06 | Built Course models, schemas, services, CRUD routes, and ownership checks. | Instructors can now only modify the courses they own. |
| Jul 07 | Built the Instructor list/create/edit pages for course metadata, tags, price, and status. | Rounded out the Instructor course workspace. |
| Jul 08 | Implemented Lesson CRUD, order indexes, notes, video URLs, and material URLs. | Made ordered curricula possible. |
| Jul 09 | Built the Curriculum Editor with create/update/delete and validation. | Linked the authoring UI to persistent data. |
| Jul 10 | Added a local upload abstraction, thumbnail preview, and a draggable 4:3 crop editor. | Enabled resource uploads and 1200x900 thumbnails. |

## Achievements

- Completed CRUD for owned Courses and Lessons.
- Added Draft, Published, and Hidden states.
- Kept private curriculum content protected.
- Added drag, zoom, replace, and crop behavior for thumbnails.
