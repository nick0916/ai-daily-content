---
id: inbox_1bd3043d
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0252-medium-tag-llm-four-prefix-and-context-hygiene-bugs-bre-17f4]]"
title: "Four Prefix and Context Hygiene Bugs Breaking Production AI Agents"
url: https://medium.com/@frankmiller_48575/four-prefix-and-context-hygiene-bugs-breaking-production-ai-agents-2e43c6a891dc?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-11T20:07:48+00:00
fetched_at: 2026-11-12T03:01:24.831605+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "長時間運作的 AI agent 常因 context 管理問題而出錯，文章整理了四類相關 bug。 **Why** 長 agent session 的 context 會持續增長，管理不當會悄悄拖累 production 中的 agent。 **What** 原文前導文字列出的問題包括：朴素的回合淘汰（naive turn eviction）、動態工具過濾器（dynamic tool filters）、過度膨脹的規則書（bloated rulebooks），以及未加 salt 的快取（unsalted caches）。"
key_points:
  - "朴素的回合淘汰（naive turn eviction）會在長 session 中損害 agent 狀態"
  - "動態工具過濾器（dynamic tool filters）與未加 salt 的快取（unsalted caches）是文中列出的問題點"
  - "過度膨脹的規則書（bloated rulebooks）會讓 context 負擔加重"
tags: [context-management, prompt-caching, agent-sessions, production-agents]
topics: [engineering.inference, agents.frameworks]
importance: 3
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Four Prefix and Context Hygiene Bugs Breaking Production AI Agents

長時間運作的 AI agent 常因 context 管理問題而出錯，文章整理了四類相關 bug。

**Why** 長 agent session 的 context 會持續增長，管理不當會悄悄拖累 production 中的 agent。

**What** 原文前導文字列出的問題包括：朴素的回合淘汰（naive turn eviction）、動態工具過濾器（dynamic tool filters）、過度膨脹的規則書（bloated rulebooks），以及未加 salt 的快取（unsalted caches）。

### 重點
- 朴素的回合淘汰（naive turn eviction）會在長 session 中損害 agent 狀態
- 動態工具過濾器（dynamic tool filters）與未加 salt 的快取（unsalted caches）是文中列出的問題點
- 過度膨脹的規則書（bloated rulebooks）會讓 context 負擔加重

**原文：** [medium-tag-llm](https://medium.com/@frankmiller_48575/four-prefix-and-context-hygiene-bugs-breaking-production-ai-agents-2e43c6a891dc?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Naive turn eviction, dynamic tool filters, bloated rulebooks, and unsalted caches quietly hurt long agent sessions. Here is what goes... Continue reading on Medium »

</details>