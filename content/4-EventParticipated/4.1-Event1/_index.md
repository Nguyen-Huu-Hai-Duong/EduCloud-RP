---
title: "Event 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Summary Report: "FCAJ x Agentic AI Build Week 2026 — Hackathon Awards and Project Showcase"

### Event Information

- **Event name:** FCAJ x Agentic AI Build Week 2026 — Hackathon Awards and Project Showcase
- **Date & time:** July 25, 2026
- **Location:** AWS Office, 26th Floor, Bitexco Tower, 02 Hai Trieu Street, Saigon Ward, Ho Chi Minh City
- **Organizers:** First Cloud AI Journey (FCAJ), Amazon Web Services (AWS), and the Agentic AI Build Week community

### Event Objectives

- Recognize the standout teams and solutions from the Agentic AI Build Week (AABW) Hackathon.
- Share each team's hackathon journey — from shaping the idea and splitting up the work, through failed experiments and narrowing scope, to the final demo.
- Showcase real Agentic AI products across ordering, cloud architecture design, strategic analysis, and crowd safety.
- Help the community understand how to use AWS services to take an AI Agent from prototype to a system capable of real operation.

### Presenting Teams

- **3KA — S.H.E.P.H.E.R.D:** Huynh An Khuong, Nguyen Quoc Huy, Ngo Quang Khoi, Hoang Le Thanh Duc, Dang Nguyen Phuoc Loc, and Dang Truong Hung.
- **OneTeam — KFC Bot Agent:** Anh Duy, Tran Dong, Doan Trung, Minh Viet, and Anshul Roy.
- **Plan V — Solution Architect Professional Native App:** Pham Tien Thuan Phat, Huynh Hoang Long, Le Minh Nghia, Tran Dai Vi, and Nguyen An.
- **SignalScout:** Le Tan Luc, Do Hoang Hieu, Trieu Quoc Hao, Nguyen Van Duy Khiem, Nguyen Cong Minh, and Nguyen Tran Minh Quan.

### Key Highlights

#### 3KA and S.H.E.P.H.E.R.D's hackathon journey

- Team 3KA walked through their entire process — picking a track, splitting roles, building, hitting bugs, cutting scope, and preparing the demo under a tight deadline.
- The S.H.E.P.H.E.R.D project assesses crowd flow, predicts congestion, detects hazards, and supports response and coordination decisions.
- The prototype combines YOLO and ByteTrack for crowd detection and tracking, Amazon SageMaker for model workloads, Amazon Bedrock AgentCore and Strands Agents for agent behavior, and a React operations dashboard.
- The team's key takeaway: a small, complete, explainable product with a stable demo is worth more than an overly ambitious idea that never gets finished.

#### OneTeam and the award-winning KFC Bot Agent

- OneTeam presented a multi-channel ordering AI Agent that lets customers order through familiar messaging apps such as Zalo and WhatsApp.
- The solution follows a Goal → Plan → Tool → Act → Verify cycle, keeping each channel's adapter separate from the shared ordering tools and business logic.
- Their slides showed a cost of about $0.006 USD per order, roughly $88 USD per month, and a response latency of about three to five seconds.
- The project shows Amazon Bedrock AgentCore can cut down infrastructure code while keeping the agent architecture modular and easy to extend to new channels.

#### Plan V and the Solution Architect Professional Native App

- Plan V tackles the time-consuming parts of a Solution Architect's job: extracting requirements, drafting architecture, generating diagrams, and estimating cost.
- The app turns natural-language requirements into a standards-based architecture, generates an editable draw.io diagram with official AWS icons, and produces a directional cost estimate for the ap-southeast-1 Region.
- The system also surfaces assumptions and missing requirements for the Solution Architect to review, discuss, and adjust, instead of just handing back an answer that's hard to explain.

#### SignalScout and evidence-based strategic decisions

- SignalScout is an AI-assisted decision platform that detects organizational and market signals, analyzes business scenarios, and then recommends whether to hold, adapt, or accelerate a strategy.
- The architecture uses services such as Amazon Bedrock, AgentCore, Amazon Cognito, AWS Lambda, Amazon API Gateway, Amazon DynamoDB, Amazon S3, AWS WAF, AWS CloudTrail, Amazon CloudWatch, and AWS Secrets Manager.
- The team walked through several realistic cost scenarios and explained the trade-offs between data collection, model usage, observability, security, and operating scale.

### Key Takeaways

#### Technical knowledge

- An AI Agent needs a clear goal, a concrete plan, reliable tools, a verification step, and observable outcomes — a model's answer alone is not a production system.
- Separating adapters from tool interfaces lets the same agent be reused across multiple channels and lets external integrations change without redesigning the whole application.
- Architecture diagrams, cost estimates, monitoring, security, and human-review checkpoints should be considered from the start, not bolted on after the demo works.
- Computer-vision systems depend heavily on data quality, camera angle, tracking stability, inference latency, and fallback mechanisms.

#### Practical value

- An effective hackathon team needs to scope down early, assign clear roles, prepare a demo flow, and prioritize one working end-to-end scenario.
- Product value needs to be backed by numbers: latency, cost per transaction, time saved, reliability, and decision quality.
- Awards and rankings matter, but the most durable takeaway is the engineering process itself — testing assumptions, handling failure, and being able to explain why each service was chosen.

### Connection to EduCloud Lite

- The presentations reinforced the value of separating frontend, backend, authentication, storage, and database in EduCloud Lite.
- The way Plan V generates an editable AWS diagram with documented assumptions is directly useful for describing EduCloud's deployment architecture and helping reviewers understand its request flow.
- OneTeam's modular architecture mirrors how EduCloud separates authentication, course APIs, file delivery, and the user interface.
- SignalScout's cost scenarios are a reminder to keep EduCloud right-sized, track which services are actually in use, and avoid adding infrastructure that isn't needed.

### Applying This to My Work

- Identify one small but fully demonstrable business flow before adding optional features.
- Document architecture, responsibilities, data flow, security boundaries, and operating cost alongside the source code.
- Treat external services as replaceable integrations, and always keep secrets outside the repository.
- Test the full user journey and prepare a stable demo instead of only checking individual components in isolation.
- Keep a human-review step for important decisions and make sure automated outcomes stay explainable.

### Event Experience

The event showed me how several teams turned Agentic AI ideas into products that could be demonstrated, measured, and explained in terms of business value. The awards and project-sharing segment was especially useful, since teams talked not only about their successes but also about their trial-and-error, limitations, and design decisions.

#### Learning from the competing teams

- I learned how to present a complex architecture by starting from the user's problem and then mapping each AWS service to a specific responsibility.
- Comparing the four projects showed how the same Agentic AI principles apply across very different domains: retail ordering, cloud solution design, strategic analysis, and crowd safety.

#### Community experience and discussion

- The presentations offered real examples of scope management, teamwork, technical storytelling, and preparing a demo under a tight timeline.
- Watching both the winning solution and the other standout teams gave me a clearer sense of the judging criteria: useful outcomes, executability, an explainable architecture, and production-ready thinking.

#### Lessons learned

- A focused, working end-to-end implementation beats a broad design that never finishes its most important flow.
- Cost, latency, observability, safety, and user trust are product requirements, not just infrastructure concerns.
- Agentic AI should support people with grounded evidence and controllable actions, not remove human accountability.

#### Event evidence

*Add your event photos here*

> Overall, FCAJ x Agentic AI Build Week 2026 gave me a practical view of how teams build, evaluate, present, and iterate on Agentic AI solutions on AWS. The event also produced several lessons I can apply directly to EduCloud Lite's architecture documentation, deployment planning, cost control, and end-to-end testing.
