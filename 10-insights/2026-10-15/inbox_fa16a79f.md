---
id: inbox_fa16a79f
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0256-infoq-ai-ml-presentation-what-25-trillion-tokens-rev-d8e8]]"
title: "Presentation: What 25 Trillion Tokens Reveal About How Developers Actually Adopt AI Agents"
url: https://www.infoq.com/presentations/agentic-ai-developer-trust-adoption/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering
source: infoq-ai-ml
published_at: 2026-10-15T11:00:00+00:00
fetched_at: 2026-10-18T03:14:41.285772+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Brendan O'Leary 在這場演講中主張，真實世界的 AI 採用取決於建立信任，而不是追逐模型 benchmark。他引用大規模的 token 使用資料來支持論點；標題寫 25 兆 token，內文摘要則寫 40 兆 token，兩者數字不一致，原文未說明原因。演講提出「AI 採用階梯」的四個階段（rungs），但摘要未列出各階段名稱。他並分析三個關鍵失敗點：context 建構、多模型路由（multi-model routing）與回饋迴圈。目標讀者是需要擴大 agentic workflow 規模的工程主管。實務意義在於：導入 agent 時應優先檢視 context、路由與回饋機制，而非只比較模型分數。"
key_points:
  - "核心論點：AI 採用取決於信任的建立，而非 benchmark 表現"
  - "提出四階的 AI 採用階梯（摘要未列出各階段名稱）"
  - "三個失敗點：context 建構、multi-model routing、feedback loops"
tags: [ai-adoption, agentic-workflows, developer-trust, multi-model-routing, context-construction]
topics: [product_and_org.adoption, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: What 25 Trillion Tokens Reveal About How Developers Actually Adopt AI Agents

Brendan O'Leary 在這場演講中主張，真實世界的 AI 採用取決於建立信任，而不是追逐模型 benchmark。他引用大規模的 token 使用資料來支持論點；標題寫 25 兆 token，內文摘要則寫 40 兆 token，兩者數字不一致，原文未說明原因。演講提出「AI 採用階梯」的四個階段（rungs），但摘要未列出各階段名稱。他並分析三個關鍵失敗點：context 建構、多模型路由（multi-model routing）與回饋迴圈。目標讀者是需要擴大 agentic workflow 規模的工程主管。實務意義在於：導入 agent 時應優先檢視 context、路由與回饋機制，而非只比較模型分數。

### 重點
- 核心論點：AI 採用取決於信任的建立，而非 benchmark 表現
- 提出四階的 AI 採用階梯（摘要未列出各階段名稱）
- 三個失敗點：context 建構、multi-model routing、feedback loops

**原文：** [infoq-ai-ml](https://www.infoq.com/presentations/agentic-ai-developer-trust-adoption/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=AI%2C+ML+%26+Data+Engineering)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Brendan O'Leary discusses how real-world AI adoption depends on building trust rather than chasing model benchmarks. Drawing from 40 trillion tokens of usage data, he explains the four rungs of the AI adoption ladder and analyzes key failure points in context construction, multi-model routing, and feedback loops to help engineering leaders successfully scale agentic workflows. By Brendan O’Leary

</details>