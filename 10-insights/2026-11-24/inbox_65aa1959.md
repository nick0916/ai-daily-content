---
id: inbox_65aa1959
date: 2026-11-24
source_ref: "[[00-inbox/2026-11-24/0006-infoq-main-openai-scales-git-for-coding-agents-with-d089]]"
title: "OpenAI Scales Git for Coding Agents with Pando"
url: https://www.infoq.com/news/2026/11/openai-git-pando/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-24T11:55:00+00:00
fetched_at: 2026-11-25T00:12:22.141439+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI 重做 Git 的後端，讓大量 coding agent 同時推送程式碼也不塞車。 **Why** coding agent 會產生並行的 Git 工作負載，需要在不改變既有 Git 工作流程的前提下擴展。 **How** 讓各分支的更新彼此獨立協調，並在多次 fetch 之間重複使用已儲存的 packfile。 **What** OpenAI 公開 Pando 後端，據報導 push 延遲中位數降低近 80%。"
key_points:
  - "Pando：為並行 coding agent 負載設計的 Git 後端，不取代既有 Git 工作流程"
  - "各分支更新獨立協調，fetch 時重用已儲存的 packfile"
  - "push 延遲中位數降低近 80%"
tags: [openai, pando, git, coding-agents, infrastructure]
topics: [agents.coding_agents, engineering.architecture]
importance: 3
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## OpenAI Scales Git for Coding Agents with Pando

OpenAI 重做 Git 的後端，讓大量 coding agent 同時推送程式碼也不塞車。

**Why** coding agent 會產生並行的 Git 工作負載，需要在不改變既有 Git 工作流程的前提下擴展。

**How** 讓各分支的更新彼此獨立協調，並在多次 fetch 之間重複使用已儲存的 packfile。

**What** OpenAI 公開 Pando 後端，據報導 push 延遲中位數降低近 80%。

### 重點
- Pando：為並行 coding agent 負載設計的 Git 後端，不取代既有 Git 工作流程
- 各分支更新獨立協調，fetch 時重用已儲存的 packfile
- push 延遲中位數降低近 80%

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/openai-git-pando/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

OpenAI has detailed Pando, a new backend that scales Git for concurrent coding-agent workloads without replacing familiar Git workflows. The company reports nearly 80% lower median push latency by coordinating branch updates independently and reusing stored packfiles across fetches. By Eran Stiller

</details>