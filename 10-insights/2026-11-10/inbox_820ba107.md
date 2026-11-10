---
id: inbox_820ba107
date: 2026-11-10
source_ref: "[[00-inbox/2026-11-10/2323-infoq-main-presentation-batch-intelligence-at-scale-e4ac]]"
title: "Presentation: Batch Intelligence at Scale: Cost-Efficient Multi-Agent LLM Workflows with Built-In Resilience"
url: https://www.infoq.com/presentations/scaling-multi-agent-llm-batch/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-10T11:00:00+00:00
fetched_at: 2026-11-10T23:30:20.297166+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓多個 AI 代理在夜間批次跑庫存預測，並把雲端推論成本壓到十分之一。 **Why** 沃爾瑪要為 4,700 間門市做每晚的庫存預測，正式環境會遇到輸出不符 schema、跨部門資料對不上、網路中斷等問題，成本也是壓力。 **How** 用 MCP grounding 讓代理依實際資料作答，用 loop agent 處理失敗與重試；計費從 PTU（預留吞吐量）改為隨用隨付。 **What** Walmart Global Tech 的 Aditya Mulik 在 InfoQ 演講分享此多代理 LLM 批次工作流；雲端推論月費從 10 萬美元以上降到約 1 萬美元。"
key_points:
  - "規模：4,700 間門市的每晚批次庫存預測，採多代理 LLM 工作流"
  - "可靠性：以 MCP grounding 與 loop agent 處理 schema 違規、跨部門資料不一致、網路中斷"
  - "成本：由 PTU 改為 pay-as-you-go，月費從 $100k+ 降到約 $10k"
tags: [multi-agent, batch-inference, walmart, mcp, cost-optimization]
topics: [agents.frameworks, engineering.inference, product_and_org.adoption]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Batch Intelligence at Scale: Cost-Efficient Multi-Agent LLM Workflows with Built-In Resilience

讓多個 AI 代理在夜間批次跑庫存預測，並把雲端推論成本壓到十分之一。

**Why** 沃爾瑪要為 4,700 間門市做每晚的庫存預測，正式環境會遇到輸出不符 schema、跨部門資料對不上、網路中斷等問題，成本也是壓力。

**How** 用 MCP grounding 讓代理依實際資料作答，用 loop agent 處理失敗與重試；計費從 PTU（預留吞吐量）改為隨用隨付。

**What** Walmart Global Tech 的 Aditya Mulik 在 InfoQ 演講分享此多代理 LLM 批次工作流；雲端推論月費從 10 萬美元以上降到約 1 萬美元。

### 重點
- 規模：4,700 間門市的每晚批次庫存預測，採多代理 LLM 工作流
- 可靠性：以 MCP grounding 與 loop agent 處理 schema 違規、跨部門資料不一致、網路中斷
- 成本：由 PTU 改為 pay-as-you-go，月費從 $100k+ 降到約 $10k

**原文：** [infoq-main](https://www.infoq.com/presentations/scaling-multi-agent-llm-batch/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Aditya Mulik explains how Walmart Global Tech deployed multi-agent LLM workflows across 4,700 stores for nightly batch inventory forecasting. He discusses tackling production hurdles - schema violations, cross-department data mismatches, and network drops - via MCP grounding and loop agents, while slashing cloud inference costs from $100k+ to $10k per month shifting from PTUs to pay-as-you-go. By Aditya Mulik

</details>