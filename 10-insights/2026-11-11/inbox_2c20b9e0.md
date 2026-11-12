---
id: inbox_2c20b9e0
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0252-infoq-main-jiohotstar-benchmarks-knowledge-bases-fo-1731]]"
title: "JioHotstar Benchmarks Knowledge Bases for AI Coding Agents"
url: https://www.infoq.com/news/2026/11/jiohotstar-codingagent-retrieval/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-11T14:28:00+00:00
fetched_at: 2026-11-12T02:59:23.371824+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "替 AI 寫程式代理人找程式碼資料時，要依任務類型選對檢索工具，沒有單一最佳解。 **Why** coding agent 要先找到相關程式碼才能動手，不同檢索方式在準確度與 token 用量上各有取捨。 **How** JioHotstar 用 SWE、CodeScale Bench 與內部問答 harness 評測 6 種程式碼檢索做法。 **What** 結果顯示結構化搜尋在具體任務表現好，語意檢索則在需求模糊時有幫助；結論是要讓檢索工具與任務類型相匹配。"
key_points:
  - "JioHotstar 評測 6 種 coding agent 程式碼檢索方法"
  - "評測工具：SWE、CodeScale Bench、內部問答 harness"
  - "結構化搜尋適合具體任務，語意檢索適合模糊需求"
tags: [code-retrieval, coding-agents, benchmark, semantic-search, jiohotstar]
topics: [agents.coding_agents, engineering.rag, engineering.evals]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## JioHotstar Benchmarks Knowledge Bases for AI Coding Agents

替 AI 寫程式代理人找程式碼資料時，要依任務類型選對檢索工具，沒有單一最佳解。

**Why** coding agent 要先找到相關程式碼才能動手，不同檢索方式在準確度與 token 用量上各有取捨。

**How** JioHotstar 用 SWE、CodeScale Bench 與內部問答 harness 評測 6 種程式碼檢索做法。

**What** 結果顯示結構化搜尋在具體任務表現好，語意檢索則在需求模糊時有幫助；結論是要讓檢索工具與任務類型相匹配。

### 重點
- JioHotstar 評測 6 種 coding agent 程式碼檢索方法
- 評測工具：SWE、CodeScale Bench、內部問答 harness
- 結構化搜尋適合具體任務，語意檢索適合模糊需求

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/jiohotstar-codingagent-retrieval/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

JioHotstar evaluated 6 approaches to code retrieval for AI coding agents using SWE, CodeScale Bench, and an internal question-answering harness. Structural search performed well on concrete tasks, while semantic retrieval helped with ambiguous requirements. The findings highlight trade-offs in accuracy, token use, and tool design, underscoring the need to match retrieval tools to task types. By Leela Kumili

</details>