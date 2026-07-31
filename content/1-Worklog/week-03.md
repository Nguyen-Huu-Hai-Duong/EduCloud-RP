---
title: "Week 3 - Architecture planning and AWS service selection"
menuTitle: "Week 3"
weight: 3
pre: "<b>1.3.</b>"
---

**Period:** June 22, 2026 - June 26, 2026

## Objectives

- Study the planned React -> FastAPI -> PostgreSQL request flow with the team.
- Learn IAM, VPC, EC2, and RDS fundamentals to evaluate which AWS services the project would need.
- Help the team settle on the technology and database choices before development started.

## AWS Learning Phase

| Learning content | Reference | Application in EduCloud |
| --- | --- | --- |
| IAM users, policies, roles, and the principle of least-privilege access. | [Access Control with AWS IAM](https://000002.awsstudygroup.com/) | Shaped how AWS infrastructure permissions would later stay separate from the Student, Instructor, and Admin roles inside the app. |
| VPCs, subnets, routing, security groups, and how an application gets reached from the Internet. | [Amazon VPC Workshop](https://000003.awsstudygroup.com/) | Built a mental model of the network path a hosted backend would need. |
| EC2, Amazon Linux, compute resources, and the basics of hosting an application. | [Introduction to Amazon EC2](https://000004.awsstudygroup.com/) | Got a feel for the infrastructure layer behind a managed compute service like Elastic Beanstalk. |
| Relational databases, PostgreSQL, SSL, backups, and network isolation. | [Amazon RDS Workshop](https://000005.awsstudygroup.com/) | Informed the team's discussion about using a managed PostgreSQL database instead of self-hosting one. |

## Work completed

| Date | Activity | Outcome |
| --- | --- | --- |
| Jun 22 | Reviewed the team's draft React -> FastAPI -> PostgreSQL architecture and discussed how frontend, backend, and database responsibilities would split. | Confirmed the overall technical direction for EduCloud Lite. |
| Jun 23 | Studied IAM users, policies, and least-privilege access as background for later API authorization design. | Built a working model for keeping AWS access separate from application roles. |
| Jun 24 | Went through the Amazon VPC workshop material to understand the networking basics behind a hosted backend. | Understood how a deployed backend would be reached from the Internet. |
| Jun 25 | Studied EC2 and Amazon Linux fundamentals as background for the team's later Elastic Beanstalk deployment. | Got a working sense of what runs underneath a managed compute service. |
| Jun 26 | Went through the RDS workshop material and discussed with the team why a managed PostgreSQL database (Supabase) made sense for this project. | Contributed to the team's decision to use Supabase for the database layer. |

## Achievements

- Understood the planned request flow and where each AWS service would fit into it.
- Built a working understanding of IAM, VPC, EC2, and RDS fundamentals ahead of hands-on development.
- Contributed to the team's decision to use Supabase as the application database.
