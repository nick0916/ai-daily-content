---
id: inbox_cf3d1b60
date: 2026-10-22
source_ref: "[[00-inbox/2026-10-22/0051-infoq-main-harbor-adds-docker-sandboxes-to-run-repr-2556]]"
title: "Harbor Adds Docker Sandboxes to Run Reproducible AI Agent Evals in Isolated MicroVMs"
url: https://www.infoq.com/news/2026/10/ai-agents-harbor-docker/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-22T09:00:00+00:00
fetched_at: 2026-10-23T00:55:43.008528+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓每個 AI agent 評測任務各自跑在獨立的小型虛擬機裡，彼此不互相干擾。 **Why** 多個評測任務共用同一個容器時會互相影響，結果較難重現。 **How** 讓 Harbor 整合 Docker Sandboxes，每個評測任務在自己的 microVM 中執行，而非共用容器。 **What** Docker 宣布開源 agent 評測框架 Harbor 現已支援 Docker Sandboxes，以 microVM 隔離每個任務，提升隔離性與可重現性。"
key_points:
  - "Harbor（開源 agent 評測框架）整合 Docker Sandboxes"
  - "每個評測任務跑在獨立 microVM，而非共用容器"
  - "目標是更可重現、隔離的 AI agent 評測"
tags: [harbor, docker-sandboxes, microvm, agent-evals, isolation]
topics: [engineering.evals, agents.frameworks]
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Harbor Adds Docker Sandboxes to Run Reproducible AI Agent Evals in Isolated MicroVMs

讓每個 AI agent 評測任務各自跑在獨立的小型虛擬機裡，彼此不互相干擾。

**Why** 多個評測任務共用同一個容器時會互相影響，結果較難重現。

**How** 讓 Harbor 整合 Docker Sandboxes，每個評測任務在自己的 microVM 中執行，而非共用容器。

**What** Docker 宣布開源 agent 評測框架 Harbor 現已支援 Docker Sandboxes，以 microVM 隔離每個任務，提升隔離性與可重現性。

### 重點
- Harbor（開源 agent 評測框架）整合 Docker Sandboxes
- 每個評測任務跑在獨立 microVM，而非共用容器
- 目標是更可重現、隔離的 AI agent 評測

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/ai-agents-harbor-docker/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Docker announced that Harbor, the open-source agent evaluation framework, now works with Docker Sandboxes. This change allows each evaluation task to run in its own microVM. So, instead of sharing a container, tasks are isolated for better performance By Claudio Masolo

</details>