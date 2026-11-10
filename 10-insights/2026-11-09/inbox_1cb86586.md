---
id: inbox_1cb86586
date: 2026-11-09
source_ref: "[[00-inbox/2026-11-09/2341-infoq-main-podcast-distributed-llm-inference-on-kub-3ef9]]"
title: "Podcast: Distributed LLM Inference on Kubernetes with llm-d, Wasm, & TornadoVM"
url: https://www.infoq.com/podcasts/distributed-llm-inference-kubernetes/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-09T11:00:00+00:00
fetched_at: 2026-11-10T00:04:08.387695+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓大模型推論在 Kubernetes 上更聰明地分配請求，把昂貴的 GPU 用滿。 **Why** GPU 成本高，推論服務需要最大化利用率。 **How** llm-d 搭配 vLLM，管理 KV cache 與 prefix cache 的位置（cache locality）、請求路由，以及跨 Kubernetes 叢集的批次推論。 **What** InfoQ Podcast 中 Edoardo Vacchi 談 llm-d 與 vLLM 的分散式 AI 推論，另涵蓋後端 WebAssembly 的發展，以及用 TornadoVM 在 GPU 上執行 Java 工作負載。"
key_points:
  - "llm-d 管理 KV cache 與 prefix cache 的 cache locality、請求路由與跨叢集批次推論"
  - "目標是在 Kubernetes 上最大化昂貴 GPU 的利用率，搭配 vLLM"
  - "同集還討論後端 WebAssembly 與 TornadoVM（Java 跑在 GPU 上）"
tags: [llm-d, vllm, kubernetes, kv-cache, distributed-inference]
topics: [engineering.inference]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Podcast: Distributed LLM Inference on Kubernetes with llm-d, Wasm, & TornadoVM

讓大模型推論在 Kubernetes 上更聰明地分配請求，把昂貴的 GPU 用滿。

**Why** GPU 成本高，推論服務需要最大化利用率。

**How** llm-d 搭配 vLLM，管理 KV cache 與 prefix cache 的位置（cache locality）、請求路由，以及跨 Kubernetes 叢集的批次推論。

**What** InfoQ Podcast 中 Edoardo Vacchi 談 llm-d 與 vLLM 的分散式 AI 推論，另涵蓋後端 WebAssembly 的發展，以及用 TornadoVM 在 GPU 上執行 Java 工作負載。

### 重點
- llm-d 管理 KV cache 與 prefix cache 的 cache locality、請求路由與跨叢集批次推論
- 目標是在 Kubernetes 上最大化昂貴 GPU 的利用率，搭配 vLLM
- 同集還討論後端 WebAssembly 與 TornadoVM（Java 跑在 GPU 上）

**原文：** [infoq-main](https://www.infoq.com/podcasts/distributed-llm-inference-kubernetes/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

In this episode, Edoardo Vacchi discusses the evolving landscape of WebAssembly on the backend, running Java workloads on GPUs using TornadoVM, and optimizing distributed AI inference using llm-d and vLLM on Kubernetes. Edoardo explains how llm-d manages cache locality (KV and prefix caches), request routing, and batch inference across Kubernetes clusters to maximize expensive GPU utilization. By Edoardo Vacchi

</details>