---
title: "Event 2"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

### Event Information

- **Event name:** AWS: Enterprise Cloud Architectures and Industry Applications – Featuring Cloud Kinetics & Renova Cloud
- **Date & time:** July 4, 2026, 09:00–12:00
- **Location:** Level 26, Bitexco Financial Tower, Ho Chi Minh City
- **Organizer:** AWS First Cloud AI Journey

### Event Objectives

This session was pitched less as a services walkthrough and more as a reality check for students still forming a picture of what cloud work actually looks like day to day. The four threads running through it were: what cloud adoption is doing to enterprise IT right now, what a realistic cloud career path looks like from a student's starting point, how architecture and data engineering decisions get made outside of a classroom setting, and where communication and AI fit into an engineer's day-to-day work.

### Speakers

- **Nguyen Gia Hung** — Head of Solutions Architecture, Vietnam & Cambodia, Amazon Web Services
- **Khang Nguyen** — Solutions Architect, Cloud Kinetics
- **Nhu Tran** — Account Manager, Amazon Web Services
- **Vinh Banh** — Senior Data Engineer, Renova Cloud

### Key Highlights

**Where the cloud job market is heading:** Enterprise cloud adoption keeps expanding, but the speakers were clear that technical skill alone doesn't move a career forward — it needs to be paired with consistency and some form of visibility, whether that's a blog, a GitHub history, or talks like this one. A side project only counts as a signal if it shows a real problem being solved, not a checklist of AWS services someone tried out. Showing up in the community, not just building alone, was framed as an actual career input, not a nice-to-have.

**Why classroom projects and production systems are different animals:** A recurring point was that real business requirements rarely arrive clean — they shift mid-build, and part of the job is absorbing that instead of waiting for a stable spec. Once something is going to run in production, the checklist grows: security, reliability, scalability, cost, and what happens when a dependency fails, not just whether the feature works. Specific tools will keep rotating in and out; the speakers argued that architectural reasoning and fundamentals are what actually carry over, and that talking to both business and technical stakeholders is part of the engineering work itself, not a separate skill.

**Where communication actually breaks and where opportunity comes from:** Most communication friction, per the panel, comes down to two teams or two people looking at the same problem from different starting assumptions — not from anyone being wrong. Their advice to students was blunt: get comfortable asking questions and talking to people who are further along, because a meaningful share of opportunities never get posted anywhere — they come out of a relationship someone already has.

**What AI changes about the job, and what it doesn't:** AI tooling clearly speeds people up, but every speaker pushed back on the idea that it replaces fundamentals. Being able to explain why a generated solution works — not just that it runs — was treated as the actual bar. The advice for students was to go past the minimum a course requires, build things outside of assignments, and treat continuous learning as non-negotiable given how fast the tooling itself keeps changing.

### Key Takeaways

- Start architecture decisions from the problem and its constraints, not from a shortlist of AWS services.
- "It works" is not the same as "it's production-ready" — security, reliability, monitoring, scalability, and cost all have to be accounted for separately.
- A system that runs locally is the starting point of the work, not the finish line.
- Technical skill, communication, and relationships all compound together — none of them substitutes for the others.

### Connection to EduCloud Lite

The line about requirements shifting mid-build landed close to home — the Course & Lesson API I own for EduCloud Lite went through a few rounds of "actually, we also need X" from teammates once the frontend flows got clearer. The panel's point about production readiness also matched what our team ran into once we moved past a local demo: access control on lesson content, what happens if an upload to S3 fails partway, and keeping the API responsive as course data grew — none of that shows up until you stop treating "it runs on my machine" as done.

### Applying This to My Work

- Treat a working local endpoint as a first draft, not a finished feature — check it against failure cases before calling it done.
- Ask teammates clarifying questions earlier in a task instead of assuming the first version of a requirement is final.
- Keep a written note of why an API or architecture decision was made, so it's not just in my head when a teammate asks later.
- Spend some time outside of assigned tasks reading how production systems (not just tutorials) handle the same problems I'm solving.

### Event Experience

What stood out most wasn't the AWS service list — it was how directly the speakers talked about the parts that don't show up in a portfolio: requirements changing after work has already started, disagreements that turn out to be a framing problem rather than someone being wrong, and opportunities that came from a conversation rather than a job posting. It reframed the internship less as "learn these AWS services" and more as "learn to work through the mess a real project brings," which is a distinction I hadn't taken seriously before.
