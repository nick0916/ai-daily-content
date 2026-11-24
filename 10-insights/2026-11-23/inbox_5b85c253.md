---
id: inbox_5b85c253
date: 2026-11-23
source_ref: "[[00-inbox/2026-11-23/0209-infoq-main-claude-code-adds-experimental-code-mode-55c3]]"
title: "Claude Code Adds Experimental Code Mode to Orchestrate Tool Calls with JavaScript"
url: https://www.infoq.com/news/2026/11/claude-code-mode/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-23T12:17:00+00:00
fetched_at: 2026-11-24T02:15:52.715092+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 Claude Code 寫一段 JavaScript 來一次串接多個工具呼叫，而不是一個一個來。 **How** Code Mode 讓 Claude Code 撰寫 JavaScript，對 Bash、Read、Edit 呼叫進行串接、平行化與過濾，並調整 auto mode 與 hooks 審查這些呼叫的方式。 **What** Anthropic 為 Claude Code 新增實驗性的 Code Mode，以 JavaScript 協調 tool calls，同時改變 auto mode 與 hooks 對這些呼叫的審查行為。"
key_points:
  - "Claude Code 實驗性 Code Mode：以 JavaScript 串接、平行化、過濾工具呼叫"
  - "涵蓋 Bash、Read、Edit 三種工具呼叫"
  - "auto mode 與 hooks 審查這些呼叫的方式隨之改變"
tags: [claude-code, code-mode, tool-calls, anthropic, javascript]
topics: [agents.coding_agents, foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude Code Adds Experimental Code Mode to Orchestrate Tool Calls with JavaScript

讓 Claude Code 寫一段 JavaScript 來一次串接多個工具呼叫，而不是一個一個來。

**How** Code Mode 讓 Claude Code 撰寫 JavaScript，對 Bash、Read、Edit 呼叫進行串接、平行化與過濾，並調整 auto mode 與 hooks 審查這些呼叫的方式。

**What** Anthropic 為 Claude Code 新增實驗性的 Code Mode，以 JavaScript 協調 tool calls，同時改變 auto mode 與 hooks 對這些呼叫的審查行為。

### 重點
- Claude Code 實驗性 Code Mode：以 JavaScript 串接、平行化、過濾工具呼叫
- 涵蓋 Bash、Read、Edit 三種工具呼叫
- auto mode 與 hooks 審查這些呼叫的方式隨之改變

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/claude-code-mode/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Anthropic's experimental Code Mode lets Claude Code write JavaScript that chains, parallelizes, and filters Bash, Read, and Edit calls, with changes to how auto mode and hooks review those calls. By Daniel Dominguez

</details>