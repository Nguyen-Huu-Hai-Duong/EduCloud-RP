---
title: "Week 3 - Backend and database foundation"
menuTitle: "Week 3"
weight: 3
pre: "<b>1.3.</b>"
---

**Period:** June 22, 2026 - June 26, 2026

## Objectives

- Map out the request flow across React, FastAPI, and PostgreSQL.
- Wire FastAPI up to Supabase PostgreSQL via SQLAlchemy.
- Put together the models, schemas, services, and routes.
- Build reusable tooling for environment setup, migrations, and seeding.

## AWS Learning Phase

| Learning content | Reference | Application in EduCloud |
| --- | --- | --- |
| IAM users, policies, roles, and the principle of least-privilege access. | [Access Control with AWS IAM](https://000002.awsstudygroup.com/) | Kept AWS infrastructure permissions distinct from the Student, Instructor, and Admin roles inside the app. |
| VPCs, subnets, routing, security groups, and how an application gets reached from the Internet. | [Amazon VPC Workshop](https://000003.awsstudygroup.com/) | Mapped out the network path for backend and database access. |
| EC2, Amazon Linux, compute resources, and the basics of hosting an application. | [Introduction to Amazon EC2](https://000004.awsstudygroup.com/) | Got a feel for the infrastructure layer sitting underneath Elastic Beanstalk. |
| Relational databases, PostgreSQL, SSL, backups, and network isolation. | [Amazon RDS Workshop](https://000005.awsstudygroup.com/) | Shaped the SQLAlchemy models and a secure connection to Supabase PostgreSQL. |

## Work completed

| Date | Activity | Outcome |
| --- | --- | --- |
| Jun 22 | Laid out the React → FastAPI → PostgreSQL architecture and split up frontend, backend, and database responsibilities. | Produced EduCloud's request flow and technical stack. |
| Jun 23 | Set up environment configuration, `.env.example`, and wired SQLAlchemy to the Supabase SSL pooler URI. | Kept secrets out of source control and got a stable database connection running. |
| Jun 24 | Built out the User, Course, Lesson, Enrollment, and Progress models. | Captured the core business relationships in the schema. |
| Jun 25 | Added Pydantic schemas, services, routers, and response helpers. | Landed on a consistent backend structure. |
| Jun 26 | Added startup table creation, compatibility migrations, database checks, and development seed data. | Made it possible to spin up new environments reliably. |

## Achievements

- Got FastAPI talking to Supabase through `psycopg2`.
- Settled on a clean router → service → model separation.
- Added a diagnostic script that checks the database connection safely.
- Prepped development data for the Student, Instructor, and Admin roles.
