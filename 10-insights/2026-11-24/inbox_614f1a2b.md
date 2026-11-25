---
id: inbox_614f1a2b
date: 2026-11-24
source_ref: "[[00-inbox/2026-11-24/0006-infoq-main-presentation-inferencing-for-enterprises-08d2]]"
title: "Presentation: Inferencing for Enterprises"
url: https://www.infoq.com/presentations/enterprise-ai-inference-architecture-costs/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-24T11:00:00+00:00
fetched_at: 2026-11-25T00:12:22.141646+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "企業做 AI 推論不只是生成 token 要快，還需要專門的系統工程。 **Why** 企業要面對 GPU 使用率陷阱、地端與雲端成本取捨，以及多 agent 的延遲確定性問題。 **What** InfoQ 收錄 Dio Rettori 的演講，內容涵蓋 GPU 利用率陷阱、地端與雲端的 TCO 比較、多 agent 延遲確定性分析；他主張團隊應把領域本體（domain ontology）直接嵌入模型，而不是只依賴 RAG。原文只有簡介，沒有具體數據。"
key_points:
  - "企業推論需要專門的系統工程，不只是 token 生成速度"
  - "涵蓋 GPU 利用率陷阱、地端與雲端 TCO 比較、多 agent 延遲確定性"
  - "主張把領域本體直接嵌入模型，而非只依賴 RAG"
tags: [enterprise-inference, gpu-utilization, tco, multi-agent, domain-ontology]
topics: [engineering.inference, engineering.rag]
importance: 2
novelty: 2
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Inferencing for Enterprises

企業做 AI 推論不只是生成 token 要快，還需要專門的系統工程。

**Why** 企業要面對 GPU 使用率陷阱、地端與雲端成本取捨，以及多 agent 的延遲確定性問題。

**What** InfoQ 收錄 Dio Rettori 的演講，內容涵蓋 GPU 利用率陷阱、地端與雲端的 TCO 比較、多 agent 延遲確定性分析；他主張團隊應把領域本體（domain ontology）直接嵌入模型，而不是只依賴 RAG。原文只有簡介，沒有具體數據。

### 重點
- 企業推論需要專門的系統工程，不只是 token 生成速度
- 涵蓋 GPU 利用率陷阱、地端與雲端 TCO 比較、多 agent 延遲確定性
- 主張把領域本體直接嵌入模型，而非只依賴 RAG

**原文：** [infoq-main](https://www.infoq.com/presentations/enterprise-ai-inference-architecture-costs/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Dio Rettori discusses the operational realities of enterprise AI inference. Moving beyond fast token generation, he explores why inference requires dedicated systems engineering, tackles GPU utilization pitfalls, compares on-prem versus cloud TCO, and analyzes multi-agent latency determinism. He shares why teams must embed domain ontology directly into models rather than relying solely on RAG. By Dio Rettori

</details>