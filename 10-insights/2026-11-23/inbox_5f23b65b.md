---
id: inbox_5f23b65b
date: 2026-11-23
source_ref: "[[00-inbox/2026-11-23/0209-infoq-main-podcast-simulation-can-tell-you-what-you-0aee]]"
title: "Podcast: Simulation Can Tell You What Your Agents are Actually Doing: A Conversation with Zhou Yu"
url: https://www.infoq.com/podcasts/simulation-agents-actually-doing/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-23T11:00:00+00:00
fetched_at: 2026-11-24T02:16:26.721372+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用模擬的使用者反覆跟 AI agent 對話，來看它實際在做什麼。 **Why** LLM 輸出不固定，對話型 agent 的每個動作又取決於前面的回應，靜態、有標準答案的 benchmark 不夠用。 **How** 用動態模擬，納入不同 persona、目標與邊角案例來測試 agent。 **What** InfoQ podcast，Michael Stiefel 訪談 Zhou Yu，主題是用動態模擬評估對話型 AI agent；內容摘要只有這些，沒有提供具體數據或工具名稱。"
key_points:
  - "對話型 agent 的行動取決於先前回應，加上 LLM 非確定性，不能只靠靜態、以參考答案為基礎的 benchmark"
  - "評估方法是動態模擬，需涵蓋不同 persona、目標與 corner case"
  - "來源為 InfoQ podcast（Michael Stiefel 訪談 Zhou Yu），摘要未提供具體工具或數字"
tags: [agent-evaluation, simulation, conversational-agents, non-determinism, podcast]
topics: [engineering.evals, agents.frameworks]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Podcast: Simulation Can Tell You What Your Agents are Actually Doing: A Conversation with Zhou Yu

用模擬的使用者反覆跟 AI agent 對話，來看它實際在做什麼。

**Why** LLM 輸出不固定，對話型 agent 的每個動作又取決於前面的回應，靜態、有標準答案的 benchmark 不夠用。

**How** 用動態模擬，納入不同 persona、目標與邊角案例來測試 agent。

**What** InfoQ podcast，Michael Stiefel 訪談 Zhou Yu，主題是用動態模擬評估對話型 AI agent；內容摘要只有這些，沒有提供具體數據或工具名稱。

### 重點
- 對話型 agent 的行動取決於先前回應，加上 LLM 非確定性，不能只靠靜態、以參考答案為基礎的 benchmark
- 評估方法是動態模擬，需涵蓋不同 persona、目標與 corner case
- 來源為 InfoQ podcast（Michael Stiefel 訪談 Zhou Yu），摘要未提供具體工具或數字

**原文：** [infoq-main](https://www.infoq.com/podcasts/simulation-agents-actually-doing/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Michael Stiefel spoke to Zhou Yu about using dynamic simulations to evaluate AI agents. One particular focus was conversational agents where actions depend on prior responses, and the non-deterministic nation of LLMs means you cannot rely on static, reference-based benchmarks. You need to test them using dynamic simulations that incorporate different personas, goals, and corner cases. By Zhou Yu

</details>