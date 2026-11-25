## Hi, I'm Siddharth

I'm a final-year ECE student at IIIT Sri City who ended up spending most of college on the backend. I like the parts of a system that break quietly: retries that create duplicates, two people accepting the same job at once, a worker that runs out of memory in production. That's the stuff I build and debug.

Right now I'm interning at **MiracleAI**. I work on a production customer-support platform built on Rails and FastAPI, and I help keep it running.

[Portfolio](https://portfolio-os-siddharth.vercel.app/) · [LinkedIn](https://www.linkedin.com/in/siddharth-singh-dev/) · [LeetCode](https://leetcode.com/u/Siddharth_Singh2711/) · siddharth.s23@iiits.in

---

### What I'm working on

**MiracleAI**, Software Development Intern (Jun 2026 – present)

I build features for DurianORM, a unified support inbox that pulls an e-commerce client's Instagram, Facebook, WhatsApp, Gmail and web-chat messages into one place. It's a Chatwoot fork (Rails 7.1) with a Python/FastAPI service next to it.

- Connected the two services with a webhook pipeline that uses idempotency keys. Webhooks get delivered more than once, and this stops retries from creating duplicate tickets or replies.
- GPT-4o-mini with JSON-schema outputs sorts incoming messages by spam and intent, and drafts replies that an agent reviews before anything is sent.
- Zoho Desk and CRM integration, including OAuth across the US and India data centres, plus a manual approval step before a ticket gets filed.
- Added a WhatsApp Cloud API channel and a Google Reviews poller.
- I run it on DigitalOcean (systemd, Puma, Sidekiq). So far I've chased down OOM kills, config drift and dropped ActionCable WebSockets.

Before this I was an SDE intern at **Qbtrix Innovations** (Jul – Aug 2024), working on Interacly, an LLM-based support automation tool. I refactored the Node.js services to cut monthly server cost by about 30%, and added Redis caching that took 200+ ms off the common read endpoints.

---

### Things I've built

**[Cowscue](https://github.com/Siddharth-singh2111/cowscue)**: rescue dispatch for injured stray cattle ([live](https://cowscue.vercel.app))
A citizen uploads a photo. Gemini vision checks that it's actually cattle and grades how bad the injury is. Then the case goes to the nearest verified NGO.
- Finding that NGO is one MongoDB `$geoNear` query on a 2dsphere index. If no one accepts, BullMQ delayed jobs widen the radius and try again, on a separate worker tier with idempotent handlers.
- Accepting a case is an atomic compare-and-set, so if two NGOs tap "accept" at the same moment, exactly one of them gets it, even across replicas.
- Runs as 3 stateless replicas behind Nginx (least-connections), with a Redis sliding-window rate limiter. 42 unit tests and an end-to-end lifecycle test run in GitHub Actions.
- Drivers don't need accounts. They get HMAC-signed, expiring links per case, and their ambulance location streams live over Pusher.

`Next.js` `TypeScript` `MongoDB` `Redis` `BullMQ` `Docker` `Nginx`

**[NexusV2X](https://github.com/Siddharth-singh2111/NexusV2X)**: vehicle telemetry and collision alerts
Simulated high-frequency GPS data streams through Kafka into FastAPI. A 2D Kalman filter smooths the noise, Redis geospatial indexes hold vehicle state, and radius queries flag likely collisions and push alerts over WebSockets. The live traffic heatmap is drawn with Deck.gl.

`Python` `FastAPI` `Kafka` `Redis` `Next.js` `Deck.gl` `Docker Compose`

**[MailFlow](https://github.com/Siddharth-singh2111/MailFlow)**: bulk email sender ([live](https://mail-flow-nu.vercel.app))
Sends are queued in BullMQ so a big campaign never blocks the API. Workers deliver over pooled SMTP connections with retries and backoff, and tracking pixels record opens.

`Node.js` `TypeScript` `Redis` `BullMQ`

---

### Tools I actually use

**Languages:** TypeScript, Python, Ruby, C++, SQL, JavaScript
**Backend:** Node.js, Express, FastAPI, Ruby on Rails, Next.js, React
**Data & queues:** PostgreSQL, MongoDB, Redis, Kafka, BullMQ, Sidekiq
**Infra:** Docker, Nginx, Linux/systemd, AWS, GCP, DigitalOcean, GitHub Actions

---

### Outside of code

- LeetCode Knight, peak rating 1868, 450+ problems
- Reliance Foundation UG Scholar (2023), selected from 58,000+ applicants
- I lead the AWS Student Builder Group at IIIT Sri City and work as a Placement Coordinator with the T&P Cell
- Ran Web3SSH '25, a national bootcamp and hackathon, as lead coordinator, and led sponsorships for Abhisarga 2025

If you're working on something in this space, or just want to talk about queues and race conditions, email me.
