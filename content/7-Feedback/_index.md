---
title: "Sharing and Feedback"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

Here are my honest reflections from my time in the First Cloud AI Journey (FCAJ) program, alongside working as part of a 5-person team building and shipping EduCloud Lite into a real, working application.

### Overall Evaluation

**1. Working Environment**

The overall working environment was pretty comfortable, with a spacious, airy office. I also got to meet people from a number of different universities, which turned out to be one of the more interesting parts of the experience.

**2. Support from Mentor / Program Direction**

The mentors and the admin team were consistently friendly and approachable. No matter how busy the project got, everyone stayed open to guiding me, helping out, and answering questions throughout the process.

**3. Relevance of Work to Academic Major**

The work I was assigned lined up closely with my major. On top of that, attending the events the company organized taught me a lot about real-world workflows and how a business actually operates — things you rarely get exposed to in a classroom.

**4. Learning & Skill Development Opportunities**

This internship is where the individual AWS services stopped being separate topics and became one connected system. I built the Course & Lesson backend API and connected it to a managed Supabase PostgreSQL database, while following closely as my teammates wired the app into Cognito, deployed the backend on Elastic Beanstalk, and served private files through S3 and CloudFront. Watching a real deployment surface issues that never showed up locally — and digging into why — was probably my single biggest skill jump, even for the parts I wasn't the one deploying.

**5. Program Culture & Learning Spirit**

FCAJ's approach is to learn by actually shipping something, not by reading about it. Instead of studying AWS services in the abstract, I had to build something that ran publicly, explain the reasoning behind each architectural choice, and back it up with evidence. That gap — between a prototype that only runs locally and an application that's deployable and publicly reachable — was the most valuable thing the program pushed me toward.

**6. Internship Policies / Benefits**

Even as an intern, I felt the program's support policies were genuinely thoughtful. The flexible schedule let me balance the internship with schoolwork. The company also went out of its way on resources — cloud accounts, servers, and so on — so we could get hands-on practice as effectively as possible.

---

### Additional Questions

**What was the most satisfying part of the internship?**

What satisfied me most was getting a real taste of a friendly, energetic, and fun corporate environment — meeting people further along in their careers, and having teammates who were always ready to help each other out. Getting hands-on with new technologies directly cleared up a lot of things I'd only understood in theory before.

**What should be improved for future interns?**

I think the onboarding process could be made a bit more detailed and structured, so new interns feel less lost at the start. On top of that, a clearer progress-review schedule would help interns pick up direction faster and improve the quality of their work sooner.

**Would I recommend this internship to a friend?**

Absolutely — especially to students who already have basic web development skills and want to learn how to take an application from "it works on my machine" to a secure, well-structured, publicly deployed system.

---

### Suggestions & Expectations

- Share a minimal reference architecture early on, so students can picture the deployment target before they start building toward it.
- Encourage weekly worklog entries and screenshots, instead of trying to reconstruct evidence from memory right before the deadline.
- Add a short primer on estimating AWS cost and cleaning up resources after submission.
- Collect common troubleshooting patterns for Cognito login, CORS, CloudFront origin behavior, S3 OAC access, and Elastic Beanstalk deployment logs.
- Keep letting students pick their own project — working on something you genuinely care about makes the whole process a lot more engaging.
