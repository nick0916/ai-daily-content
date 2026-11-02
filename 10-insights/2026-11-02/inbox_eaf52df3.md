---
id: inbox_eaf52df3
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2325-infoq-main-article-systemic-approach-to-memory-know-31e5]]"
title: "Article: Systemic Approach to Memory, Knowledge, and Context in Agentic AI Architectures"
url: https://www.infoq.com/articles/agentic-ai-context-memory-knowledge/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-02T11:00:00+00:00
fetched_at: 2026-11-02T23:30:59.142341+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "在資訊送進模型之前，先由一個「上下文引擎」決定放什麼、壓縮什麼、何時過期。 **Why** 可靠的 agentic AI 架構取決於進模型前的資訊管理，常見失誤是上下文塞太滿與過期資料造成的循環。 **How** 將 context、memory、knowledge 三者分開，採用分層記憶、經策展的知識與 token 預算控管，由引擎負責選取、注入、壓縮與過期。 **What** InfoQ 文章（作者 Adi Polak）提出 agentic AI 的 memory／knowledge／context 系統化架構，並列出 context stuffing、stale data loop 等反模式與對應的緩解方式。"
key_points:
  - "區分 context、memory、knowledge 三個概念，由 context engine 負責選取、注入、壓縮、過期"
  - "建議做法：分層記憶、經策展的知識、token 預算控管"
  - "反模式：context stuffing 與 stale data loop，文中附有緩解方式"
tags: [context-engineering, agent-memory, agentic-ai, token-budget, architecture]
topics: [engineering.architecture, agents.frameworks]
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Article: Systemic Approach to Memory, Knowledge, and Context in Agentic AI Architectures

在資訊送進模型之前，先由一個「上下文引擎」決定放什麼、壓縮什麼、何時過期。

**Why** 可靠的 agentic AI 架構取決於進模型前的資訊管理，常見失誤是上下文塞太滿與過期資料造成的循環。

**How** 將 context、memory、knowledge 三者分開，採用分層記憶、經策展的知識與 token 預算控管，由引擎負責選取、注入、壓縮與過期。

**What** InfoQ 文章（作者 Adi Polak）提出 agentic AI 的 memory／knowledge／context 系統化架構，並列出 context stuffing、stale data loop 等反模式與對應的緩解方式。

### 重點
- 區分 context、memory、knowledge 三個概念，由 context engine 負責選取、注入、壓縮、過期
- 建議做法：分層記憶、經策展的知識、token 預算控管
- 反模式：context stuffing 與 stale data loop，文中附有緩解方式

**原文：** [infoq-main](https://www.infoq.com/articles/agentic-ai-context-memory-knowledge/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The article argues that reliable agentic AI architecture depends on a context engine that selects, injects, compresses, and expires information before it reaches the model. It separates context, memory, and knowledge, and recommends tiered memory, curated knowledge, and token budgeting. It also covers common anti-patterns, such as context stuffing and stale data loops, with mitigations. By Adi Polak

</details>