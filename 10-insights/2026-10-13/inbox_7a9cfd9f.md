---
id: inbox_7a9cfd9f
date: 2026-10-13
source_ref: "[[00-inbox/2026-10-13/0256-medium-towards-data-science-coding-agents-can-solve-the-task-but-how-02c9]]"
title: "Coding Agents Can Solve the Task — But How Much Work Did They Waste?"
url: https://towardsdatascience.com/coding-agents-can-solve-the-task-but-how-much-work-did-they-waste/
source: medium-towards-data-science
published_at: 2026-10-13T12:30:00+00:00
fetched_at: 2026-10-18T03:16:45.761406+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "這篇 Towards Data Science 文章探討 coding agent 在「能解題」之外的效率問題：做了多少白工。依摘要，研究在真實 repository 上植入（seeded）agent 決策，共跑了 50,400 次 run。衡量面向包含浪費的 turn 數與 patch churn（修補內容反覆被改動）。摘要也提到比較了哪些 harness 規則有幫助。目前只有摘要，沒有具體的浪費比例、模型名稱或各規則的效果數字，這些無法確認。對開發 coding agent harness 的團隊來說，這提示評估不該只看任務成功率，也要看過程成本。"
key_points:
  - "規模：真實 repository 上植入 agent 決策，共 50,400 次 run"
  - "效率指標：浪費的 turn 數與 patch churn，不只看是否解題"
  - "比較哪些 harness 規則有效（具體規則與數字摘要未提供）"
tags: [coding-agents, agent-efficiency, harness, patch-churn, benchmark]
topics: [agents.coding_agents, engineering.evals]
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Coding Agents Can Solve the Task — But How Much Work Did They Waste?

這篇 Towards Data Science 文章探討 coding agent 在「能解題」之外的效率問題：做了多少白工。依摘要，研究在真實 repository 上植入（seeded）agent 決策，共跑了 50,400 次 run。衡量面向包含浪費的 turn 數與 patch churn（修補內容反覆被改動）。摘要也提到比較了哪些 harness 規則有幫助。目前只有摘要，沒有具體的浪費比例、模型名稱或各規則的效果數字，這些無法確認。對開發 coding agent harness 的團隊來說，這提示評估不該只看任務成功率，也要看過程成本。

### 重點
- 規模：真實 repository 上植入 agent 決策，共 50,400 次 run
- 效率指標：浪費的 turn 數與 patch churn，不只看是否解題
- 比較哪些 harness 規則有效（具體規則與數字摘要未提供）

**原文：** [medium-towards-data-science](https://towardsdatascience.com/coding-agents-can-solve-the-task-but-how-much-work-did-they-waste/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Real repositories, seeded agent decisions: what 50,400 runs show about wasted turns, patch churn, and which harness rules help 
 The post Coding Agents Can Solve the Task — But How Much Work Did They Waste? appeared first on Towards Data Science .

</details>