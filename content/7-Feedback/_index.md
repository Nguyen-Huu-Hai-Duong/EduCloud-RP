---
title: "Sharing and Feedback"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

# Sharing and Feedback

Here are my honest impressions after going through the First Cloud AI Journey (FCAJ) program while building and shipping EduCloud Lite.

### Overall Evaluation

**1. Working Environment**

The program is built around self-directed, hands-on learning rather than close daily supervision. That suited a project like this well: I could research an AWS service, try a deployment option, see it fail, and adjust course without waiting on anyone. What kept me on track was the program's own structure — the report outline and learning materials gave me a clear target even when I was working through a problem on my own.

**2. Support from Mentor / Program Direction**

The clearest value came from the report and workshop template itself: splitting the submission into worklog, proposal, blogs, events, workshop, self-assessment, and feedback made it obvious what "done" looked like at each stage, and kept the final result from turning into a wall of unstructured notes.

**3. Relevance of Work to Academic Major**

EduCloud Lite lines up closely with my Computer Science background — backend API design, frontend development, database modeling, authentication, deployment, and debugging all showed up in some form. What it added on top of coursework was the operational side: CORS policies, IAM permissions, environment configuration, cloud storage rules, and health checks that only really show up once something is live in production.

**4. Learning & Skill Development Opportunities**

This internship is where the individual AWS services stopped being separate topics and started being one system. I deployed FastAPI on Elastic Beanstalk, hosted the React frontend on Amplify, handed identity to Cognito, kept secrets in Parameter Store, served private files through S3 and CloudFront, and connected the backend to a managed Supabase PostgreSQL database. Debugging issues that only appeared after deployment — not in local development — was probably the single biggest skill jump.

**5. Program Culture & Learning Spirit**

FCAJ's approach is learn-by-shipping rather than learn-by-reading. Instead of studying AWS services in the abstract, I had to produce something that actually ran in public, explain the reasoning behind each architectural choice, and back it up with evidence. That distinction — a local prototype versus a deployable, publicly reachable application — was the most useful thing the program pushed me toward.

**6. Internship Policies / Benefits**

The biggest benefit wasn't a perk in the traditional sense — it was the freedom to shape my own project and spend extra time on the parts that were genuinely hard, like Cognito's authentication flows, CloudFront/S3 access control, and Elastic Beanstalk configuration, instead of following a fixed script.

---

### Additional Questions

**What was the most satisfying part of the internship?**

Seeing EduCloud Lite go live behind a public Amplify URL, with login, course browsing, instructor tools, profiles, uploads, assessments, and certificates all working together as one system rather than isolated demos.

**What should be improved for future interns?**

An earlier, short deployment checklist would help — specifically around IAM roles, Parameter Store, CORS, CloudFront behaviors, S3 bucket policies, and Cognito configuration. These are exactly the areas where someone new to AWS can burn a lot of time on trial and error.

**Would I recommend this internship to a friend?**

Yes, particularly to students who already have basic web development skills and want to learn how to take an application from "it works on my machine" to a secure, structured, publicly deployed system.

---

### Suggestions & Expectations

- Share a minimal reference architecture early on, so students know the deployment target before they start building toward it.
- Encourage weekly screenshots and worklog entries instead of reconstructing evidence from memory near the deadline.
- Add a short primer on estimating AWS cost and cleaning up resources after submission.
- Collect common troubleshooting patterns for Cognito login, CORS, CloudFront origin behavior, S3 OAC access, and Elastic Beanstalk deployment logs.
- Keep letting students pick their own project — building something you actually care about makes the whole process far more engaging.
