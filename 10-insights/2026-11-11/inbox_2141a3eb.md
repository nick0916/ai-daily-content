---
id: inbox_2141a3eb
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0252-infoq-main-github-makes-agentic-workflows-generally-a0f1]]"
title: "GitHub Makes Agentic Workflows Generally Available with Isolation and Budget Controls"
url: https://www.infoq.com/news/2026/11/github-agentic-workflows-ga/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-11T17:00:00+00:00
fetched_at: 2026-11-12T02:59:23.369443+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 AI 寫程式的代理人在 GitHub Actions 裡跑，預設只能讀、要寫入得另開受限的工作。 **Why** 讓 coding agent 在 CI 中自動執行很方便，但給它寫入權限會有安全風險，需要隔離與預算控管。 **How** 預設唯讀，寫入動作放在權限範圍分開的獨立 job；但直接設定寫入權限或自訂 job 不在這些保護範圍內，安全性取決於每個 workflow 的設定。 **What** GitHub Agentic Workflows 正式 GA，在 GitHub Actions 中執行 coding agent，具備隔離與預算控制。"
key_points:
  - "GitHub Agentic Workflows GA，在 GitHub Actions 中執行 coding agent"
  - "預設唯讀，寫入動作由權限範圍分開的 job 負責"
  - "直接寫入權限與自訂 job 不受上述保護，須自行正確設定 workflow"
tags: [github-actions, agentic-workflows, coding-agents, sandboxing, permissions]
topics: [agents.coding_agents, security]
importance: 3
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## GitHub Makes Agentic Workflows Generally Available with Isolation and Budget Controls

讓 AI 寫程式的代理人在 GitHub Actions 裡跑，預設只能讀、要寫入得另開受限的工作。

**Why** 讓 coding agent 在 CI 中自動執行很方便，但給它寫入權限會有安全風險，需要隔離與預算控管。

**How** 預設唯讀，寫入動作放在權限範圍分開的獨立 job；但直接設定寫入權限或自訂 job 不在這些保護範圍內，安全性取決於每個 workflow 的設定。

**What** GitHub Agentic Workflows 正式 GA，在 GitHub Actions 中執行 coding agent，具備隔離與預算控制。

### 重點
- GitHub Agentic Workflows GA，在 GitHub Actions 中執行 coding agent
- 預設唯讀，寫入動作由權限範圍分開的 job 負責
- 直接寫入權限與自訂 job 不受上述保護，須自行正確設定 workflow

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/github-agentic-workflows-ga/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

GitHub Agentic Workflows is generally available, running coding agents in GitHub Actions with read-only defaults and separately scoped write jobs. Those protections do not cover direct write permissions or custom jobs, so they depend on how each workflow is configured. By Mark Silvester

</details>