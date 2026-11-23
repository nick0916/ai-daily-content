---
id: inbox_5dc60ffa
date: 2026-11-22
source_ref: "[[00-inbox/2026-11-22/0051-infoq-main-aws-lambda-now-runs-gpu-inference-with-4-e754]]"
title: "AWS Lambda Now Runs GPU Inference with 48 Concurrent Invocations Sharing One Model per GPU"
url: https://www.infoq.com/news/2026/11/aws-lambda-gpu-managed-instances/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-22T06:27:00+00:00
fetched_at: 2026-11-23T00:56:33.058674+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS Lambda 現在能在 GPU 上跑推論，多個請求共用同一個模型。 **Why** 原文未說明動機，僅描述功能。 **How** 透過 Lambda Managed Instances 在 EC2 G 系列 GPU 實例上執行 Event Functions，最多 48 個並行呼叫共用每張 GPU 上的一份模型；提供 vLLM 與 SGLang 基底映像，不需寫 handler 程式碼。 **What** 非同步逾時最長 90 分鐘；計費為實例價格加 9.75% 費用。初步實測回報發佈需約八分鐘，且不支援 response streaming。"
key_points:
  - "每張 GPU 最多 48 個並行呼叫共用一份模型，Lambda Managed Instances 於 EC2 G 系列實例執行"
  - "提供 vLLM、SGLang 基底映像，無需 handler 程式碼；非同步逾時 90 分鐘"
  - "計費為實例價格 + 9.75% 費用；實測發佈約八分鐘、不支援 response streaming"
tags: [aws-lambda, gpu-inference, vllm, sglang, serverless]
topics: [engineering.inference]
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## AWS Lambda Now Runs GPU Inference with 48 Concurrent Invocations Sharing One Model per GPU

AWS Lambda 現在能在 GPU 上跑推論，多個請求共用同一個模型。

**How** 透過 Lambda Managed Instances 在 EC2 G 系列 GPU 實例上執行 Event Functions，最多 48 個並行呼叫共用每張 GPU 上的一份模型；提供 vLLM 與 SGLang 基底映像，不需寫 handler 程式碼。

**What** 非同步逾時最長 90 分鐘；計費為實例價格加 9.75% 費用。初步實測回報發佈需約八分鐘，且不支援 response streaming。

### 重點
- 每張 GPU 最多 48 個並行呼叫共用一份模型，Lambda Managed Instances 於 EC2 G 系列實例執行
- 提供 vLLM、SGLang 基底映像，無需 handler 程式碼；非同步逾時 90 分鐘
- 計費為實例價格 + 9.75% 費用；實測發佈約八分鐘、不支援 response streaming

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/aws-lambda-gpu-managed-instances/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AWS Lambda now runs Event Functions on EC2 G-series GPU instances through Lambda Managed Instances, with up to 48 concurrent invocations sharing one model per GPU, vLLM and SGLang base images that need no handler code, and 90-minute asynchronous timeouts. Billing is the instance price plus a 9.75 percent fee; first hands-on tests report an eight-minute publish and no response streaming. By Steef-Jan Wiggers

</details>