<div align="center">

# 🧠 WeKraft — Powered by Kaya

### _The AI-native project management platform that thinks like a PM, moves like a dev tool._

[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=flat-square&logo=next.js)](https://nextjs.org/)
[![LangGraph](https://img.shields.io/badge/LangGraph-Multi--Agent-blueviolet?style=flat-square)](https://langchain-ai.github.io/langgraph/)
[![Python](https://img.shields.io/badge/Python-3.11-blue?style=flat-square&logo=python)](https://python.org/)
[![Convex](https://img.shields.io/badge/Convex-Realtime-orange?style=flat-square)](https://convex.dev/)
[![AWS S3](https://img.shields.io/badge/AWS-S3-yellow?style=flat-square&logo=amazonaws)](https://aws.amazon.com/s3/)

</div>

---

## What is WeKraft?

WeKraft is a **collaborative project management platform** built for modern engineering teams — with an AI brain called **Kaya** at its core. Forget clicking through dashboards to understand your project. Just ask Kaya.

> _"What's blocking sprint 3?"_ → Kaya tells you, with data.
> _"Create a client meeting for tomorrow."_ → Done in 2 seconds.
> _"Set up weekly reports for the team."_ → Scheduled, automated, no ops work.

---

## ✨ Features

### 🤖 Kaya — Your AI Product Manager
Kaya is a **multi-agent LangGraph system** that coordinates specialized subagents to answer questions, take actions, and manage your project end-to-end.

- **Natural language project queries** — ask about tasks, issues, blockers, team workload
- **Human-in-the-loop (HITL) approvals** — Kaya proposes, you approve before any write action
- **Persistent memory** — Kaya remembers past sessions via Mem0, context never resets
- **Fast & Deep modes** — switch between quick answers and deep analytical responses
- **Streaming responses** — real-time token-by-token output, no waiting for full response

### 🧩 Multi-Agent Architecture
WeKraft runs a **fleet of specialized agents** under Kaya's orchestration:

| Agent | Role |
|---|---|
| **Kaya** | Orchestrator — routes queries, manages HITL, talks to the user |
| **Project Analyst** | Read-only subagent — fetches tasks, issues, sprints, workloads |
| **Sprint Manager** | Handles sprint creation and task assignment via interrupt UI |
| **Scheduler Agent** | Configures and manages automated report schedulers |
| **Calendar Agent** | Creates calendar events and milestones with HITL approval |

### 🔥 3D Heatmap Visualization
WeKraft features an immersive **3D activity heatmap** that visualizes project health across time:

- Real-time commit, task completion, and issue resolution density
- Interactive 3D surface — rotate, zoom, drill into any time period
- Color-coded intensity by team member, sprint, or issue type
- Instant visual recognition of **crunch periods**, **idle streaks**, and **velocity drops**

### ⏳ Deadline Tracking
Never miss a deadline again:

- **Project-level countdown** — days remaining always visible
- **Sprint deadline heatmap** — see which sprints are at risk
- **Milestone calendar** — all key dates in one place
- **AI deadline alerts** — Kaya proactively flags projects going off-track

### 👥 Collaborative Platform
Built for teams, not individuals:

- **Real-time updates** via Convex — changes sync instantly across all members
- **Member workload view** — see who's overloaded, who has capacity
- **Sprint planning UI** — interactive task selection during sprint creation
- **Automated reports** — scheduled project health emails, configurable per project

### 📅 Calendar & Scheduling
- Full project calendar with events and milestones
- AI-powered event creation via natural language
- Scheduler for automated periodic reporting (configurable frequency + recipient)

### 📁 File & Asset Management
- Project thumbnail uploads via **AWS S3**
- Organized folder structure (`thumbnails/`, `files/`, `images/`)
- Public CDN URLs for instant image delivery

---

## 🆚 Why WeKraft over Jira, Linear, or Notion?

| Feature | WeKraft | Jira | Linear | Notion |
|---|:---:|:---:|:---:|:---:|
| AI that understands your project | ✅ | ❌ | ❌ | ❌ |
| Natural language task queries | ✅ | ❌ | ❌ | Partial |
| Multi-agent orchestration | ✅ | ❌ | ❌ | ❌ |
| 3D heatmap visualization | ✅ | ❌ | ❌ | ❌ |
| HITL approval before writes | ✅ | ❌ | ❌ | ❌ |
| Persistent AI memory per user | ✅ | ❌ | ❌ | ❌ |
| Real-time collaborative sync | ✅ | Partial | ✅ | ✅ |
| Automated AI-generated reports | ✅ | ❌ | ❌ | ❌ |
| Sprint creation via chat | ✅ | ❌ | ❌ | ❌ |
| Open & extensible backend | ✅ | ❌ | ❌ | ❌ |

> WeKraft isn't just a PM tool with an AI chatbot bolted on. **Kaya is the product** — the UI is just how you see what Kaya already knows.

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────┐
│                   Next.js Frontend                   │
│         (Chat UI · Heatmaps · Sprint Board)          │
└────────────────────┬────────────────────────────────┘
                     │ HTTP / Streaming
┌────────────────────▼────────────────────────────────┐
│              Kaya Agent (LangGraph)                  │
│                                                      │
│   ┌──────────┐  ┌───────────────┐  ┌─────────────┐  │
│   │  Project  │  │    Sprint     │  │  Scheduler  │  │
│   │ Analyst  │  │   Manager     │  │    Agent    │  │
│   └──────────┘  └───────────────┘  └─────────────┘  │
│                                                      │
│         Checkpointer (PostgreSQL / Redis)            │
│              Mem0 — Persistent Memory                │
└────────────────────┬────────────────────────────────┘
                     │
        ┌────────────┼────────────┐
        │            │            │
┌───────▼──┐  ┌──────▼───┐  ┌────▼────┐
│  Convex  │  │  AWS S3  │  │ OpenAI  │
│ (DB/RT)  │  │  (Files) │  │  (LLM)  │
└──────────┘  └──────────┘  └─────────┘
```

---

## 🛠️ Tech Stack

### Frontend
- **Next.js 15** — App Router, Server Components, streaming
- **TypeScript** — end-to-end type safety
- **Tailwind CSS** — utility-first styling
- **Three.js / WebGL** — 3D heatmap rendering
- **Convex Client** — real-time reactive queries

### AI & Agents
- **LangGraph** — multi-agent graph orchestration with HITL interrupt support
- **LangChain + OpenAI** — LLM backbone (GPT-4.1-mini / GPT-4.1)
- **Mem0** — persistent cross-session user memory
- **PostgreSQL / Redis** — persistent graph checkpointing for production

### Backend & Infrastructure
- **Convex** — serverless real-time database + HTTP actions
- **Python FastAPI** — Kaya agent server
- **Google Cloud Run** — containerized agent deployment
- **AWS S3** — file and image storage (`ap-south-1`)

---

## ⚙️ Environment Variables

```env
# AI
OPENAI_API_KEY=
MEM0_API_KEY=
KAYA_FAST_MODEL=gpt-4.1-mini
KAYA_DEEP_MODEL=gpt-4.1

# Convex
CONVEX_SITE_URL=
NEXT_PUBLIC_CONVEX_URL=

# AWS S3
AWS_ACCES_KEY=
AWS_SECRET_KEY=
AWS_REGION=ap-south-1
AWS_BUCKET_NAME=wekraft-saas-upload-s3

# Checkpointer (pick one)
DATABASE_URL=postgresql://...
REDIS_URL=redis://...
```

---

## 📁 Project Structure

```
wekraft/
├── app/                  # Next.js App Router
│   ├── (dashboard)/      # Protected routes
│   ├── api/              # API routes (S3 upload, agent proxy)
│   └── globals.css
├── components/           # UI components
│   ├── kaya/             # Chat UI, message renderer, HITL cards
│   ├── heatmap/          # 3D visualization components
│   └── sprint/           # Sprint board & task selector
├── agent/                # Python LangGraph agent
│   ├── graph.py          # Kaya multi-agent graph
│   ├── Dockerfile
│   └── requirements.txt
└── convex/               # Convex schema, queries, mutations, HTTP actions
```

---

## 🚀 Getting Started

```bash
# 1. Clone
git clone https://github.com/wekraft/kaya.git && cd kaya

# 2. Install frontend deps
npm install

# 3. Install agent deps
cd agent && pip install -r requirements.txt

# 4. Set up environment variables (see above)
cp .env.example .env.local

# 5. Run Convex
npx convex dev

# 6. Run agent
cd agent && python graph.py

# 7. Run frontend
npm run dev
```

---

<div align="center">

Built with 🧠 by the WeKraft team · [wekraft.com](https://wekraft.com)

</div>
