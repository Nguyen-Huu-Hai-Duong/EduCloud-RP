---
title: "Week 8 - Final validation, report, and submission"
menuTitle: "Week 8"
weight: 8
pre: "<b>1.8.</b>"
---

**Period:** July 27, 2026 - July 31, 2026

**Submission deadline:** July 31, 2026

## Objectives

- Join the team in locking the EduCloud Lite feature set and avoiding risky changes ahead of submission.
- Help verify the live Student and Instructor journeys, AWS services, and public links all work.
- Write and finalize my own bilingual Hugo workshop report, evidence, and submission package.
- Get my workshop report submitted no later than July 31, 2026.

## Final AWS and Project Review

| Review area | Validation activity | Submission evidence |
| --- | --- | --- |
| Identity and security | Check Cognito login, first-login password change, recovery, JWT exchange, IAM roles, and Parameter Store secrets. | Authentication screenshots, configuration notes, and source links. |
| Application hosting | Check Elastic Beanstalk health, the Amplify deployment, CloudFront routing, CORS, and SPA rewrites. | Public EduCloud link and a successful deployment status. |
| Storage and data | Confirm private S3 delivery, Supabase connectivity, upload paths, and database-backed roles. | Architecture diagram and workshop screenshots. |
| Documentation | Review the proposal, worklog, blogs, events, workshop steps, self-assessment, and feedback pages in both languages. | Public Hugo report and GitHub repository. |

## Work plan and current progress

| Date | Activity | Target outcome |
| --- | --- | --- |
| Jul 27 | Fix the internship dates and worklog scope; fill in remaining report content and evidence. | Report matches the actual June 1-August 15 internship period. |
| Jul 28 | Joined the team to run through the production checklist: login, browsing courses, enrollment, learning, assessment, certificate, and Instructor authoring. | Critical demo journeys work end to end on the public website. |
| Jul 29 | Wrote up the AWS architecture, screenshots, code snippets, repository instructions, and demo-account guidance for my report. | Submission is understandable and reproducible by the reviewer. |
| Jul 30 | Proofread the English and Vietnamese sites; check navigation, visited-page markers, images, links, and responsive layout. | Hugo report reads consistently, with no placeholders or broken assets. |
| Jul 31 | Put together the final submission package and send the live website, source repository, workshop link, and selected PDF files. | Workshop submitted before the deadline. |

## Current results

- EduCloud Lite is live at an independent Amplify URL.
- The FastAPI backend runs on Elastic Beanstalk and pulls production secrets from Parameter Store.
- Cognito, Supabase, S3, CloudFront, and Amplify are all wired into the deployed application.
- The architecture diagram, bilingual Hugo report, demo links, and mentor accounts are all documented.
- What's left is final validation, evidence review, proofreading, and submission.

## Submission links

- [EduCloud Lite live application](https://main.djk00b5qbck73.amplifyapp.com/courses)
- [EduCloud source repository](https://github.com/Funacius/EduCloud)

> No new project features are planned after July 31. The rest of the internship is set aside for AWS and First Cloud AI Journey learning.
