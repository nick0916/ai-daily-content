---
id: inbox_dadb330d
date: 2026-10-29
source_ref: "[[00-inbox/2026-10-29/0035-infoq-main-anthropic-says-nobody-needs-a-mental-mod-e5cc]]"
title: "Anthropic Says Nobody Needs a Mental Model of Claude Code. Practitioners Are Testing That"
url: https://www.infoq.com/news/2026/10/anthropic-code-review/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-29T09:58:00+00:00
fetched_at: 2026-10-30T00:40:04.711241+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "當程式碼九成由 AI 寫，團隊承認沒人再掌握整個程式碼庫的完整心智模型，改靠 AI 審查把關。 **Why** Claude 寫了約 90% 的 Claude Code 程式碼，人已無法逐行理解全部內容。 **How** Anthropic 公開 Claude Code 團隊的審查做法：一個 PR 在一夜之間跑了五十多輪審查，審查者多數心力花在既有程式碼上。 **What** Anthropic 發文說明 Claude Code 團隊如何做 code review，並坦承有一項控制機制目前還沒有；InfoQ 報導實務界正在檢驗「沒人需要完整心智模型」這個主張。"
key_points:
  - "Claude 寫了約 90% 的 Claude Code 程式碼，Anthropic 稱沒人保有完整的程式碼庫心智模型"
  - "一個 PR 一夜之間跑了超過五十輪審查"
  - "審查者大部分心力花在既有（pre-existing）程式碼上，且團隊坦承尚缺一項控制機制"
tags: [claude-code, code-review, mental-model, ai-generated-code, anthropic]
topics: [agents.coding_agents, foundation_models.claude, product_and_org.adoption]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Anthropic Says Nobody Needs a Mental Model of Claude Code. Practitioners Are Testing That

當程式碼九成由 AI 寫，團隊承認沒人再掌握整個程式碼庫的完整心智模型，改靠 AI 審查把關。

**Why** Claude 寫了約 90% 的 Claude Code 程式碼，人已無法逐行理解全部內容。

**How** Anthropic 公開 Claude Code 團隊的審查做法：一個 PR 在一夜之間跑了五十多輪審查，審查者多數心力花在既有程式碼上。

**What** Anthropic 發文說明 Claude Code 團隊如何做 code review，並坦承有一項控制機制目前還沒有；InfoQ 報導實務界正在檢驗「沒人需要完整心智模型」這個主張。

### 重點
- Claude 寫了約 90% 的 Claude Code 程式碼，Anthropic 稱沒人保有完整的程式碼庫心智模型
- 一個 PR 一夜之間跑了超過五十輪審查
- 審查者大部分心力花在既有（pre-existing）程式碼上，且團隊坦承尚缺一項控制機制

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/anthropic-code-review/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Anthropic has published how the Claude Code team reviews code now that Claude writes roughly 90% of it, including a claim that nobody keeps a complete mental model of the codebase. The post documents a pull request that ran more than fifty review rounds overnight, a reviewer spending most of its effort on pre-existing code, and a control the team says it does not yet have. By Steef-Jan Wiggers

</details>