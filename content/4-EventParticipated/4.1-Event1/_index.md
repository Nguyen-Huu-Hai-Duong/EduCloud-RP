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

Recognize the standout teams from the Agentic AI Build Week (AABW) Hackathon (July 8-12, 2026, Ho Chi Minh City), let teams share the real story of their 24-hour build, and showcase four different directions for Agentic AI: crowd safety, multi-channel ordering, Solution Architect support, and corporate signal analysis.

### Presenting Teams

- **3KA — S.H.E.P.H.E.R.D:** Huynh An Khuong, Nguyen Quoc Huy, Ngo Quang Khoi, Hoang Le Thanh Duc, Dang Nguyen Phuoc Loc, Dang Truong Hung.
- **OneTeam — KFC Bot Agent:** Anh Duy, Tran Dong, Doan Trung, Minh Viet, Anshul Roy.
- **Plan V — Solution Architect Professional Native App:** Pham Tien Thuan Phat, Huynh Hoang Long, Le Minh Nghia, Tran Dai Vi, Nguyen An.
- **SignalScout:** Le Tan Luc, Do Hoang Hieu, Trieu Quoc Hao, Nguyen Van Duy Khiem, Nguyen Cong Minh, Nguyen Tran Minh Quan.

### Key Highlights

**3KA — S.H.E.P.H.E.R.D:** Originally a Capstone idea, prototyped in 24 hours for crowd monitoring: YOLO + ByteTrack for detection, Amazon SageMaker for density inference, and Amazon Bedrock AgentCore + Strands Agent split into an Autonomous Monitor (auto-alerts) and an Operator Copilot (answers operational questions). The team was candid about the hard parts — no AI background going in, first real AWS project, code breaking overnight, an accidental `.env` push to GitHub. Their lesson: prepare a clear goal, toolkit, roles, and demo plan before day one.

**OneTeam — KFC Bot Agent:** An ordering agent through Zalo/WhatsApp, running a Goal → Plan → Tool → Act → Verify loop with each channel's adapter kept separate from shared logic. Roughly $0.006 USD per order, ~$88 USD/month, 3-5 second latency.

**Plan V — Solution Architect Professional Native App:** Built for the classic "I need it now" client request: the app takes natural-language input, generates an editable **draw.io** diagram with official AWS icons and a directional cost estimate for **ap-southeast-1**, and surfaces missing assumptions through a chat sidebar for the architect to confirm instead of returning an answer no one can verify.

**SignalScout:** Detects early signs of corporate restructuring or strategy shifts, using TinyFish/Apify to crawl evidence and Langfuse for observability. Published real cost numbers: roughly $17-$130 USD/month for AWS alone, $81-$359 USD/month with third-party services included — plus a cheaper backup architecture. Their takeaway in three words: **Clear Direction, Execution, Teamwork**.

### Key Takeaways

- A demo-ready agent and an operations-ready agent are different things: they need a clear action loop, a monitoring layer kept separate from inference, and logging attached to every answer.
- Separating channel adapters from shared business logic makes it easy to extend without redesigning the whole system.
- Cost and architectural assumptions should be transparent from the first draft, not added after the demo already works.

### Connection to EduCloud Lite

3KA's split between automated monitoring and interactive support, Plan V's habit of documenting assumptions, and SignalScout's transparent cost table are all standards I want to apply to EduCloud Lite's architecture docs and cost tracking — knowing exactly which service drives cost and having a plan to cut it.

### Applying This to My Work

- Document assumptions in the architecture write-up instead of presenting results as self-evident.
- Track AWS cost per service, not just the total bill.
- Prioritize one small, fully working end-to-end flow before adding extras.
- Keep a human-review step on sensitive actions like granting Admin access.

### Event Experience

What stuck with me most was how openly teams shared the messy parts — no AI background, code breaking at 3 AM, an accidental push of a sensitive file — instead of only showing polished results. Hearing from winning and non-winning teams alike made the real judging criteria clearer: not just a good idea, but how finished it is, how explainable the architecture is, and whether cost and risk are under control.

#### Event evidence

<img src="/images/events/event-03.jpg" alt="Evidence from FCAJ x Agentic AI Build Week 2026" style="max-width:420px; width:100%; height:auto;">

> FCAJ x Agentic AI Build Week 2026 made the gap clear between an AI demo that works on stage and a system with enough architecture, cost, and monitoring transparency to be trusted — exactly what I've tried to bring into EduCloud Lite.
