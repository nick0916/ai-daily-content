---
id: inbox_ef073d64
date: 2026-11-13
source_ref: "[[00-inbox/2026-11-13/0146-medium-tag-claude-one-in-twenty-llm-requests-waits-18-to-4-443c]]"
title: "One in twenty LLM requests waits 18 to 49 seconds for its first token."
url: https://medium.com/@bysu721/one-in-twenty-llm-requests-waits-18-to-49-seconds-for-its-first-token-a694342094a3?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-11-13T21:42:12+00:00
fetched_at: 2026-11-14T01:55:29.579033+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一週真實流量顯示，約 20 分之 1 的 LLM 請求要等 18 到 49 秒才出現第一個 token。 **How** 作者檢視某 LLM API gateway 一週的正式流量，範圍限定為串流請求與 28 個文字模型，以首 token 延遲（TTFT）為指標。 **What** 標題給出的數據為：約 5% 的請求 TTFT 落在 18 到 49 秒之間。"
key_points:
  - "資料來源：某 LLM API gateway 一週正式流量，28 個文字模型，僅串流請求"
  - "指標：TTFT；約 1/20 請求等待 18 到 49 秒"
  - "節錄未說明成因或各模型之間的差異"
tags: [ttft, llm-gateway, latency, streaming, production-traffic]
topics: [engineering.inference]
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## One in twenty LLM requests waits 18 to 49 seconds for its first token.

一週真實流量顯示，約 20 分之 1 的 LLM 請求要等 18 到 49 秒才出現第一個 token。

**How** 作者檢視某 LLM API gateway 一週的正式流量，範圍限定為串流請求與 28 個文字模型，以首 token 延遲（TTFT）為指標。

**What** 標題給出的數據為：約 5% 的請求 TTFT 落在 18 到 49 秒之間。

### 重點
- 資料來源：某 LLM API gateway 一週正式流量，28 個文字模型，僅串流請求
- 指標：TTFT；約 1/20 請求等待 18 到 49 秒
- 節錄未說明成因或各模型之間的差異

**原文：** [medium-tag-claude](https://medium.com/@bysu721/one-in-twenty-llm-requests-waits-18-to-49-seconds-for-its-first-token-a694342094a3?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I looked at one week of production traffic through an LLM API gateway: 28 text models, streaming requests only, time to first token (TTFT)... Continue reading on Medium »

</details>