---
id: inbox_ee863721
date: 2026-11-17
source_ref: "[[00-inbox/2026-11-17/2317-infoq-main-presentation-scaling-llm-based-ranking-s-50f0]]"
title: "Presentation: Scaling LLM-Based Ranking Systems for Latency-Critical Search & Recommendation Workloads"
url: https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-17T11:00:00+00:00
fetched_at: 2026-11-17T23:24:21.623788+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "LinkedIn 分享如何把大型語言模型排序系統做到夠快，能符合嚴格的線上延遲要求。 **Why** 搜尋與推薦排序有嚴格的 P99 延遲 SLA，LLM 排序要上線必須壓低延遲。 **How** 把 7B 模型蒸餾成 400M，將職缺上下文壓縮成單一 token 的 embedding，並逐一消除隱藏的系統瓶頸，包括自訂 flash attention mask、Python GIL 的繞過方式、gc.freeze 與非阻塞 CUDA 記憶體複製。 **What** Sundara Raman Ramachandran 的演講指出，上下文壓縮讓吞吐量提升 10 倍。"
key_points:
  - "將 7B 模型蒸餾至 400M 參數，以滿足 P99 延遲 SLA"
  - "把職缺上下文壓縮為單一 token embedding，吞吐量提升 10 倍"
  - "系統層優化：自訂 flash attention mask、Python GIL 繞過、gc.freeze、非阻塞 CUDA 記憶體複製"
tags: [linkedin, llm-ranking, model-distillation, latency-optimization, inference-serving]
topics: [engineering.inference, engineering.architecture]
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Scaling LLM-Based Ranking Systems for Latency-Critical Search & Recommendation Workloads

LinkedIn 分享如何把大型語言模型排序系統做到夠快，能符合嚴格的線上延遲要求。

**Why** 搜尋與推薦排序有嚴格的 P99 延遲 SLA，LLM 排序要上線必須壓低延遲。

**How** 把 7B 模型蒸餾成 400M，將職缺上下文壓縮成單一 token 的 embedding，並逐一消除隱藏的系統瓶頸，包括自訂 flash attention mask、Python GIL 的繞過方式、gc.freeze 與非阻塞 CUDA 記憶體複製。

**What** Sundara Raman Ramachandran 的演講指出，上下文壓縮讓吞吐量提升 10 倍。

### 重點
- 將 7B 模型蒸餾至 400M 參數，以滿足 P99 延遲 SLA
- 把職缺上下文壓縮為單一 token embedding，吞吐量提升 10 倍
- 系統層優化：自訂 flash attention mask、Python GIL 繞過、gc.freeze、非阻塞 CUDA 記憶體複製

**原文：** [infoq-main](https://www.infoq.com/presentations/scale-llm-ranking-systems-linkedin/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Sundara Raman Ramachandran shares how LinkedIn productionizes LLM ranking under strict P99 latency SLAs. He discusses distilling a 7B model down to 400M parameters, compressing job contexts into single-token embeddings for a 10x throughput leap, and eliminating hidden system bottlenecks - from custom flash attention masks to Python GIL workarounds, gc.freeze, and non-blocking CUDA memory copies. By Sundara Raman Ramachandran

</details>