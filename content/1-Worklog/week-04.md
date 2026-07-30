---
title: "Week 4 - Basic authentication and authorization"
menuTitle: "Week 4"
weight: 4
pre: "<b>1.4.</b>"
---

**Period:** June 29, 2026 - July 3, 2026

## Objectives

- Build out development-mode registration, login, and JWT sessions.
- Lock down APIs and pages according to user role.
- Keep the authentication layer swappable so Cognito can be dropped in later.

## AWS Learning Phase

| Learning content | Reference | Application in EduCloud |
| --- | --- | --- |
| How IAM policies are structured and the idea of least-privilege authorization. | [Access Control with AWS IAM](https://000002.awsstudygroup.com/) | Carried the same permission mindset into Admin, Instructor, and Student route protection. |
| User Pools, app clients, JWTs, and the distinction between authentication and authorization. | [Amazon Cognito Workshop](https://000141.awsstudygroup.com/) | Set the authentication layer up so it could later move from local JWT to Cognito. |

## Work completed

| Date | Activity | Outcome |
| --- | --- | --- |
| Jun 29 | Added user schemas, password hashing, and development register/login endpoints. | Made local account authentication possible. |
| Jun 30 | Started issuing JWTs carrying identity, role, and expiry, and parsed Bearer tokens on incoming requests. | Requests to protected endpoints could now be tied to a specific user. |
| Jul 01 | Added auth middleware plus authorization helpers for the Student, Instructor, and Admin roles. | Mutating actions were now limited to the right roles. |
| Jul 02 | Added `AuthContext`, session persistence, automatic token attachment, and `RequireRole` on the frontend. | Locked down frontend navigation and role-specific pages. |
| Jul 03 | Tested cross-role access attempts and added 401/403 responses, security headers, and basic auth throttling. | Cut down the risk of privilege escalation. |

## Achievements

- Finished development-mode authentication with 12-hour JWT sessions.
- Locked down Instructor and Admin functionality on both the frontend and backend.
- Made sure public registration can't self-assign the Admin role.
- Kept a clean migration path open for moving to Cognito later.
