---
id: inbox_816f60d5
date: 2026-11-26
source_ref: "[[00-inbox/2026-11-26/0052-infoq-main-presentation-finetuning-your-embedding-m-aa10]]"
title: "Presentation: Finetuning Your Embedding Model for Better Search: Learning from Agentic Search at Dell"
url: https://www.infoq.com/presentations/fine-tune-enterprise-rag-embeddings/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-26T11:00:00+00:00
fetched_at: 2026-11-27T00:59:20.240379+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把開源 embedding 模型用公司內部資料微調，讓企業搜尋看得懂內部術語。 **Why** 企業 RAG 在內部專有術語上常檢索失敗，通用 embedding 模型無法理解這些詞。 **How** 微調開源 embedding 模型：準備含 hard negatives 的資料，在 H100 GPU 上以分散式 InfoNCE loss 訓練，搭配自動化超參數調整，並以 LLM-as-a-judge 做上線評估。 **What** Rachel Shalom 在 InfoQ 演講中分享 Dell 的 agentic search 實戰經驗，涵蓋資料準備、訓練、調參到 production 評估的完整流程。"
key_points:
  - "Dell 以微調開源 embedding 模型解決內部術語造成的 RAG 檢索失敗"
  - "訓練細節：hard negatives 資料準備、H100 上的分散式 InfoNCE loss、自動化超參數調整"
  - "以 LLM-as-a-judge 做 production 評估"
tags: [rag, embedding, fine-tuning, enterprise-search, infonce]
topics: [engineering.rag, engineering.evals]
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Finetuning Your Embedding Model for Better Search: Learning from Agentic Search at Dell

把開源 embedding 模型用公司內部資料微調，讓企業搜尋看得懂內部術語。

**Why** 企業 RAG 在內部專有術語上常檢索失敗，通用 embedding 模型無法理解這些詞。

**How** 微調開源 embedding 模型：準備含 hard negatives 的資料，在 H100 GPU 上以分散式 InfoNCE loss 訓練，搭配自動化超參數調整，並以 LLM-as-a-judge 做上線評估。

**What** Rachel Shalom 在 InfoQ 演講中分享 Dell 的 agentic search 實戰經驗，涵蓋資料準備、訓練、調參到 production 評估的完整流程。

### 重點
- Dell 以微調開源 embedding 模型解決內部術語造成的 RAG 檢索失敗
- 訓練細節：hard negatives 資料準備、H100 上的分散式 InfoNCE loss、自動化超參數調整
- 以 LLM-as-a-judge 做 production 評估

**原文：** [infoq-main](https://www.infoq.com/presentations/fine-tune-enterprise-rag-embeddings/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Rachel Shalom explains how Dell solved enterprise RAG retrieval failures on internal terminology by fine-tuning open-source embedding models. She discusses data prep with hard negatives, distributed InfoNCE loss training on H100 GPUs, automated hyperparameter tuning, and production evaluation using LLM-as-a-judge. By Rachel Shalom

</details>