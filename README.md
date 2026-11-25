<img src="https://capsule-render.vercel.app/api?type=waving&color=0:7C3AED,100:2563EB&height=190&section=header&text=Siddharth%20Singh&fontSize=46&fontColor=ffffff&fontAlignY=36&desc=Backend-focused%20full-stack%20engineer&descSize=16&descAlignY=56&animation=fadeIn" width="100%" alt="Siddharth Singh" />

<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=18&duration=2800&pause=1200&color=8B5CF6&center=true&vCenter=true&width=560&lines=SDE+Intern+%40+MiracleAI;Webhooks%2C+queues+and+race+conditions;Final+year+B.Tech+%40+IIIT+Sri+City;LeetCode+Knight+%C2%B7+peak+1868" alt="Typing intro" />

<a href="https://portfolio-os-siddharth.vercel.app/"><img src="https://img.shields.io/badge/Portfolio-7C3AED?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" /></a>&nbsp;<a href="https://www.linkedin.com/in/siddharth-singh-dev/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>&nbsp;<a href="https://leetcode.com/u/Siddharth_Singh2711/"><img src="https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=black" alt="LeetCode" /></a>&nbsp;<a href="mailto:siddharth.s23@iiits.in"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>

</div>

I'm a final-year ECE student at IIIT Sri City who ended up spending most of college on the backend. I like the parts of a system that break quietly: retries that create duplicates, two people accepting the same job at once, a worker that runs out of memory in production. That's the stuff I build and debug.

Right now I'm interning at **MiracleAI**. I work on a production customer-support platform built on Rails and FastAPI, and I help keep it running.

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

**[Cowscue](https://github.com/Siddharth-singh2111/cowscue)**: rescue dispatch for injured stray cattle &nbsp;<a href="https://cowscue.vercel.app"><img src="https://img.shields.io/badge/live-cowscue.vercel.app-22C55E?style=flat-square" alt="Live demo" align="center" /></a>

A citizen uploads a photo. Gemini vision checks that it's actually cattle and grades how bad the injury is. Then the case goes to the nearest verified NGO.
- Finding that NGO is one MongoDB `$geoNear` query on a 2dsphere index. If no one accepts, BullMQ delayed jobs widen the radius and try again, on a separate worker tier with idempotent handlers.
- Accepting a case is an atomic compare-and-set, so if two NGOs tap "accept" at the same moment, exactly one of them gets it, even across replicas.
- Runs as 3 stateless replicas behind Nginx (least-connections), with a Redis sliding-window rate limiter. 42 unit tests and an end-to-end lifecycle test run in GitHub Actions.
- Drivers don't need accounts. They get HMAC-signed, expiring links per case, and their ambulance location streams live over Pusher.

`Next.js` `TypeScript` `MongoDB` `Redis` `BullMQ` `Docker` `Nginx`

**[NexusV2X](https://github.com/Siddharth-singh2111/NexusV2X)**: vehicle telemetry and collision alerts

Simulated high-frequency GPS data streams through Kafka into FastAPI. A 2D Kalman filter smooths the noise, Redis geospatial indexes hold vehicle state, and radius queries flag likely collisions and push alerts over WebSockets. The live traffic heatmap is drawn with Deck.gl.

`Python` `FastAPI` `Kafka` `Redis` `Next.js` `Deck.gl` `Docker Compose`

**[MailFlow](https://github.com/Siddharth-singh2111/MailFlow)**: bulk email sender &nbsp;<a href="https://mail-flow-nu.vercel.app"><img src="https://img.shields.io/badge/live-mail--flow-22C55E?style=flat-square" alt="Live demo" align="center" /></a>

Sends are queued in BullMQ so a big campaign never blocks the API. Workers deliver over pooled SMTP connections with retries and backoff, and tracking pixels record opens.

`Node.js` `TypeScript` `Redis` `BullMQ`

---

### Tools I actually use

<p align="center">
  <img src="https://skillicons.dev/icons?i=ts,py,ruby,cpp,js,nodejs,express,fastapi,rails,nextjs,react&perline=11" alt="Languages and frameworks" />
  <br />
  <img src="https://skillicons.dev/icons?i=postgres,mongodb,redis,kafka,docker,nginx,linux,aws,gcp,githubactions&perline=10" alt="Data and infra" />
</p>

<p align="center"><sub>Plus BullMQ, Sidekiq and DigitalOcean, which don't have icons here.</sub></p>

---

### On GitHub

<p align="center">
  <img height="165" src="https://github-readme-stats.vercel.app/api?username=Siddharth-singh2111&show_icons=true&count_private=true&hide=stars,issues&hide_border=true&bg_color=00000000&title_color=8B5CF6&icon_color=8B5CF6&text_color=8B949E&ring_color=8B5CF6" alt="GitHub stats" />
  <img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Siddharth-singh2111&layout=compact&langs_count=6&hide_border=true&bg_color=00000000&title_color=8B5CF6&text_color=8B949E" alt="Top languages" />
</p>

<p align="center">
  <img src="https://streak-stats.demolab.com?user=Siddharth-singh2111&hide_border=true&background=00000000&ring=8B5CF6&fire=8B5CF6&currStreakLabel=8B5CF6&currStreakNum=8B949E&sideNums=8B949E&sideLabels=8B949E&dates=8B949E&stroke=8B949E40" alt="Contribution streak" />
</p>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=Siddharth-singh2111&bg_color=00000000&color=8B949E&title_color=8B5CF6&line=8B5CF6&point=8B5CF6&area=true&area_color=8B5CF6&hide_border=true" width="100%" alt="Contribution activity graph" />

---

### Outside of code

- LeetCode Knight, peak rating 1868, 450+ problems
- Reliance Foundation UG Scholar (2023), selected from 58,000+ applicants
- I lead the AWS Student Builder Group at IIIT Sri City and work as a Placement Coordinator with the T&P Cell
- Ran Web3SSH '25, a national bootcamp and hackathon, as lead coordinator, and led sponsorships for Abhisarga 2025

If you're working on something in this space, or just want to talk about queues and race conditions, email me.

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:2563EB,100:7C3AED&height=110&section=footer" width="100%" alt="" />
