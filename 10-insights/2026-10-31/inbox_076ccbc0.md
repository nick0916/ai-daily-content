---
id: inbox_076ccbc0
date: 2026-10-31
source_ref: "[[00-inbox/2026-10-31/0019-substack-bytebytego-ep231-ai-terms-you-need-to-know-e048]]"
title: "EP231: AI Terms You Need to Know"
url: https://blog.bytebytego.com/p/ep231-ai-terms-you-need-to-know
source: substack-bytebytego
published_at: 2026-10-31T15:31:08+00:00
fetched_at: 2026-11-01T00:24:08.902825+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用幾個名詞解釋與 GPT-2 到 GPT-6 的演進，快速補齊 AI 基礎概念。 **What** ByteByteGo EP231 解釋 Agentic AI、Large Reasoning Model、Vector Database、RAG、MCP，並依公開資訊整理 GPT 世代差異：GPT-2（1.5B，只做預訓練）、GPT-3（175B，展現 in-context learning）、GPT-4（加入 RLHF、多模態、32K context）、GPT-5（內建推理、400K context、ChatGPT 路由器）、GPT-6（1.05M context、async tool calling、mid-turn steering）。另含 AI/ML 面試主題清單、GPU 架構（SM、warp scheduler、L1/L2 cache）簡介，以及 AI Cost Optimization 課程的推廣。"
key_points:
  - "GPT 世代演進主軸：GPT-2/3 靠預訓練與規模、GPT-4 加 RLHF 與多模態、GPT-5 加內建推理與 400K context、GPT-6 為 1.05M context、async tool calling 與 mid-turn steering"
  - "GPU 靠大規模平行化隱藏記憶體延遲：多個 SM，各含 warp scheduler、CUDA cores、register file 與 L1 cache，共用 L2 與高頻寬但高延遲的全域記憶體"
  - "含贊助內容與 AI Cost Optimization 課程推廣（newsletter 訂閱者 20% 折扣）"
tags: [bytebytego, gpt-history, ai-glossary, gpu-architecture, system-design]
topics: [foundation_models.gpt, engineering.architecture]
importance: 2
novelty: 1
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## EP231: AI Terms You Need to Know

用幾個名詞解釋與 GPT-2 到 GPT-6 的演進，快速補齊 AI 基礎概念。

**What** ByteByteGo EP231 解釋 Agentic AI、Large Reasoning Model、Vector Database、RAG、MCP，並依公開資訊整理 GPT 世代差異：GPT-2（1.5B，只做預訓練）、GPT-3（175B，展現 in-context learning）、GPT-4（加入 RLHF、多模態、32K context）、GPT-5（內建推理、400K context、ChatGPT 路由器）、GPT-6（1.05M context、async tool calling、mid-turn steering）。另含 AI/ML 面試主題清單、GPU 架構（SM、warp scheduler、L1/L2 cache）簡介，以及 AI Cost Optimization 課程的推廣。

### 重點
- GPT 世代演進主軸：GPT-2/3 靠預訓練與規模、GPT-4 加 RLHF 與多模態、GPT-5 加內建推理與 400K context、GPT-6 為 1.05M context、async tool calling 與 mid-turn steering
- GPU 靠大規模平行化隱藏記憶體延遲：多個 SM，各含 warp scheduler、CUDA cores、register file 與 L1 cache，共用 L2 與高頻寬但高延遲的全域記憶體
- 含贊助內容與 AI Cost Optimization 課程推廣（newsletter 訂閱者 20% 折扣）

**原文：** [substack-bytebytego](https://blog.bytebytego.com/p/ep231-ai-terms-you-need-to-know)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The all-in-one intelligent cloud (Sponsored) Y our app, live in seconds, for free. Railway’s push-button compute, storage, and networking is available immediately upon sign-up. Humans and agents alike operate on one vertically integrated system including hardware, software, and a prompt-to-production experience. Sign up with the link below for free cloud credits and let your agents cook. Start free This week’s system design refresher: AI Terms You Need to Know GPT-2 to GPT-6: What Actually Changed Al Topics to Learn before Taking Al/ML Interviews How GPUs Work at a High Level AI Cost Optimization Course Starts Today (Exclusive 20% discount for newsletter subscribers) AI Terms You Need to Know Agentic AI: It's an AI system that describes the behavior of the whole system. The agent understands and interprets the goal. It creates a plan and calls tools and APIs to get the results. The agent evaluates the results and corrects the mistakes. It keeps on improving the results until it achieves the desired goal. Large Reasoning Model: It’s a type of model that is trained to solve problems which require lots of logical steps. It breaks a problem into smaller problems and performs reasoning on them to come up with the right answer. Vector Database: It's a type of database that stores vectors, as the name implies. These vectors are actually lists of numbers which represent the meaning and characteristics of text, audio, video or other data. Retrieval Augmented Generation (RAG): It's a technique to provide relevant information to the model when needed. The relevant information is mostly stored in a vector database, but retrieval can also be through APIs, SQL, or hybrid search. Model Context Protocol (MCP): It provides a standard interface to AI applications to connect and access external tools and APIs. The communication happens through the MCP client within the AI applications communicating through MCP servers. GPT-2 to GPT-6: What Actually Changed It's been seven years from GPT-2 to GPT-6, and a lot has changed. The diagram below shows each generation and its key highlights, based on the public information we know. GPT-2 (2019): More like a prototype to validate the potential of the decoder-only transformer. This was a 1.5B-parameter model that only went through pre-training with next-token prediction. The trained model was only capable of continuing text, not answering questions. GPT-3 (2020): The same recipe as GPT-2, just much bigger and trained on more data to test how far scale alone could go. GPT-3 had 175B parameters, more than 100 times the size of GPT-2, and still only went through pre-training. The scale allowed it to show in-context learning capabilities. When shown some examples, the model could follow them. GPT-4 (2023): On top of pre-training, OpenAI fine-tuned it with RLHF (reinforcement learning from human feedback), so it was not just a completion model but could actually answer questions. It was also multimodal, meaning that it could process input images as well as text, and it handled up to 32K tokens of context. GPT-5 (2025): The first GPT generation with built-in reasoning. Given a prompt, tools, and an effort level, the trained model could generate reasoning tokens before the answer. Its context window grew to 400K tokens, with a router in ChatGPT to decide when a prompt needed thinking mode. GPT-6 (2026): This new model has a bigger context window (1.05M), supports async tool calling, and is generally safer. An interesting feature, called mid-turn steering, is that it can take a new instruction while it's thinking. Al Topics to Learn before Taking Al/ML Interviews AI interviews often test fundamentals, not tools. This visual splits them into two buckets that show up repeatedly: Traditional AI and Modern AI. Traditional AI focuses on fundamental ML topics, mostly from before neural networks became dominant. Modern AI focuses on neural network foundations and newer concepts like transformers, RAG, and post-training. Interviewers generally expect you to know both. They expect you to explain how they work, when they break, and the trade-offs. Use this as a checklist, and make sure you can explain each topic clearly before your next AI interview. Over to you: which topic here do you find hardest to explain under interview pressure? What else is missing? How GPUs Work at a High Level When people say GPUs are powerful, what they really mean is this: GPUs are built for massive parallelism from the ground up. Let’s break down what’s happening under the hood. At the top level, a GPU chip is made up of many Streaming Multiprocessors (SMs). Think of SMs as mini parallel engines replicated across the chip. Instead of one big brain, you get dozens of smaller ones working simultaneously. Inside each SM: A Warp Scheduler decides which group of threads (a warp) runs next. Dozens of CUDA Cores execute instructions in parallel. A Register File stores thread-local data at ultra-low latency. Load/Store units move data between registers and memory. Texture units handle specialized memory operations. L1 Cache provides fast, on-SM data access. Each SM works independently, but they’re connected through an on-chip interconnect. Below that sits the L2 Cache, shared across all SMs. This is the coordination layer. If one SM misses in L1, it checks L2 before going to global memory. Then come the Memory Controllers, which interface with Global Memory. This is where things get interesting: Extremely high bandwidth Much higher latency than on-chip memory That’s why GPUs rely on massive parallelism. While some threads wait on memory, thousands of others keep executing. AI Cost Optimization Course Starts Today Learn how to reduce AI infrastructure and inference costs without sacrificing performance or quality. As a newsletter subscriber, you get an exclusive 20% discount, automatically applied when you click the link. Check it out now What you’ll learn: Understand your AI bill: Break down token usage and calculate the true cost of every request. Track AI spending: Monitor costs across teams, features, and users to identify what’s driving your bill. Optimize prompts and caching: Reduce redundant model calls and avoid unnecessary token consumption. Manage agent context: Keep context windows lean and prevent expensive agent loops. Use smaller models: Replace costly large-model calls with smaller models where appropriate. Build intelligent model routers: Route requests to the most cost-effective models while maintaining quality. Control multi-agent costs: Estimate spending, catch runaway retries, and optimize agent workflows. Check it out now

</details>