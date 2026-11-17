---
id: inbox_4d4e5be8
date: 2026-11-16
source_ref: "[[00-inbox/2026-11-16/2317-infoq-main-ubers-legal-ai-agent-cuts-contract-revie-13dc]]"
title: "Uber’s Legal AI Agent Cuts Contract Review Time by 20% with Rules and RAG"
url: https://www.infoq.com/news/2026/11/uber-legal-redlining-agent/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-16T14:37:00+00:00
fetched_at: 2026-11-17T23:24:44.534899+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Uber 讓 AI 在 Word 裡直接審合約修改，並用固定規則把關 AI 的判斷。 **How** 系統結合 RAG、過去律師的回饋紀錄，以及確定性的政策規則，在 Microsoft Word 內審閱合約變更；以 LangGraph、OpenSearch、Redis 建構。 **What** Uber 的 Legal Redlining Agent 回報平均合約審閱時間降低超過 20%，AI 產生的決策準確率為 91%。團隊正評估 agentic harness、skills、法務 ontology 與知識圖譜。"
key_points:
  - "Uber Legal Redlining Agent 在 Word 中審合約，平均審閱時間降低逾 20%，AI 決策準確率 91%"
  - "技術組合：LangGraph + OpenSearch + Redis，搭配 RAG、歷史律師回饋與確定性政策規則"
  - "下一步探索 agentic harness、skills、法務 ontology、知識圖譜"
tags: [legal-ai, rag, langgraph, opensearch, uber]
topics: [agents.frameworks, engineering.rag, product_and_org.adoption]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Uber’s Legal AI Agent Cuts Contract Review Time by 20% with Rules and RAG

Uber 讓 AI 在 Word 裡直接審合約修改，並用固定規則把關 AI 的判斷。

**How** 系統結合 RAG、過去律師的回饋紀錄，以及確定性的政策規則，在 Microsoft Word 內審閱合約變更；以 LangGraph、OpenSearch、Redis 建構。

**What** Uber 的 Legal Redlining Agent 回報平均合約審閱時間降低超過 20%，AI 產生的決策準確率為 91%。團隊正評估 agentic harness、skills、法務 ontology 與知識圖譜。

### 重點
- Uber Legal Redlining Agent 在 Word 中審合約，平均審閱時間降低逾 20%，AI 決策準確率 91%
- 技術組合：LangGraph + OpenSearch + Redis，搭配 RAG、歷史律師回饋與確定性政策規則
- 下一步探索 agentic harness、skills、法務 ontology、知識圖譜

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/uber-legal-redlining-agent/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Uber’s Legal Redlining Agent reviews contract changes in Microsoft Word using RAG, historical lawyer feedback, and deterministic policy rules. Built with LangGraph, OpenSearch, and Redis, the system reports more than 20% lower average contract review time and 91% accuracy in AI-generated decisions. Uber is exploring agentic harnesses, skills, legal ontologies, and knowledge graphs. By Leela Kumili

</details>