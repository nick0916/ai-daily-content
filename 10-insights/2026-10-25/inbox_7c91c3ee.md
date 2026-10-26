---
id: inbox_7c91c3ee
date: 2026-10-25
source_ref: "[[00-inbox/2026-10-25/0249-infoq-main-google-ml-drift-accelerates-on-device-ai-8aac]]"
title: "Google ML Drift Accelerates On-Device AI Inference Across Diverse GPUs"
url: https://www.infoq.com/news/2026/10/google-ml-drift/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-25T17:00:00+00:00
fetched_at: 2026-10-26T02:55:24.996895+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一套讓同一份 AI 推論程式能在不同裝置 GPU 上運行的開源引擎。 **Why** 不同 GPU 硬體與底層 API 差異大，on-device AI 推論要跨平台很麻煩。 **How** ML Drift 抽象化各種 GPU 硬體與低階 API 的複雜度，支援 OpenGL ES、OpenCL、Metal 與 WebGPU。 **What** Google 釋出開源（Apache 2.0）的跨平台 GPU 運算引擎 ML Drift，用於裝置端 AI／機器學習推論。"
key_points:
  - "Google 開源 ML Drift，授權為 Apache 2.0"
  - "支援 OpenGL ES、OpenCL、Metal、WebGPU 四種 GPU API"
  - "定位為跨平台 on-device 推論的 GPU 運算引擎"
tags: [ml-drift, on-device-ai, gpu, inference, google]
topics: [engineering.inference]
importance: 3
novelty: 3
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Google ML Drift Accelerates On-Device AI Inference Across Diverse GPUs

一套讓同一份 AI 推論程式能在不同裝置 GPU 上運行的開源引擎。

**Why** 不同 GPU 硬體與底層 API 差異大，on-device AI 推論要跨平台很麻煩。

**How** ML Drift 抽象化各種 GPU 硬體與低階 API 的複雜度，支援 OpenGL ES、OpenCL、Metal 與 WebGPU。

**What** Google 釋出開源（Apache 2.0）的跨平台 GPU 運算引擎 ML Drift，用於裝置端 AI／機器學習推論。

### 重點
- Google 開源 ML Drift，授權為 Apache 2.0
- 支援 OpenGL ES、OpenCL、Metal、WebGPU 四種 GPU API
- 定位為跨平台 on-device 推論的 GPU 運算引擎

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/google-ml-drift/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Google has released ML Drift, an open-source, cross-platform GPU compute engine designed for on-device AI and machine learning inference. Licensed under Apache 2.0, it abstracts the complexities of different GPU hardware and low-level APIs, supporting OpenGL ES, OpenCL, Metal, and WebGPU. By Sergio De Simone

</details>