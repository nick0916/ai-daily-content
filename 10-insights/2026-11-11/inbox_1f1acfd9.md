---
id: inbox_1f1acfd9
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0252-simon-willison-anthropic-s-ipo-roadshow-video-0d13]]"
title: "Anthropic's IPO roadshow video"
url: https://simonwillison.net/2026/Nov/11/anthropic-ipo-roadshow/
source: simon-willison
published_at: 2026-11-11T15:11:59+00:00
fetched_at: 2026-11-12T02:58:27.301225+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Anthropic 在 IPO roadshow 影片中說明它如何靠多晶片與「運算倍增器」累積運算優勢。 **Why** 不同晶片各需獨立的軟體與推論堆疊，成本高、難建，當初許多人認為不值得；Anthropic 早期卻押注多晶片策略。 **How** 聯合創辦人 Tom Brown 說，Anthropic 追求「總有效運算」，即實體算力乘上所發現的運算倍增器，且倍增器彼此疊加。 **What** Claude 目前在 AWS Trainium、Google TPU、NVIDIA GPU、AMD GPU 四大晶片家族上訓練與服務；今年首次導入 AMD，Mythos 在約三天內、幾乎無人工介入讓 Claude 跑上 AMD，並移植或撰寫近 100% 的 kernel。舉例：4 倍倍增器可用 25 單位算力訓練原需 100 單位的模型，或用 100 單位訓練原需 400 單位的更強模型。"
key_points:
  - "Claude 已在 Trainium、TPU、NVIDIA GPU、AMD GPU 四大晶片家族上訓練與服務"
  - "過去導入新晶片平台需數十位工程師數月；這次 Mythos 約三天讓 Claude 跑上 AMD，近 100% kernel 由 Claude 移植或撰寫"
  - "總有效運算 = 實體算力 × 運算倍增器；4x 倍增器可讓 100 單位達成原需 400 單位的成果，倍增器彼此疊加"
tags: [anthropic, ipo, multi-chip, compute-multipliers, amd-gpu]
topics: [foundation_models.claude, engineering.inference, product_and_org.leadership]
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Anthropic's IPO roadshow video

Anthropic 在 IPO roadshow 影片中說明它如何靠多晶片與「運算倍增器」累積運算優勢。

**Why** 不同晶片各需獨立的軟體與推論堆疊，成本高、難建，當初許多人認為不值得；Anthropic 早期卻押注多晶片策略。

**How** 聯合創辦人 Tom Brown 說，Anthropic 追求「總有效運算」，即實體算力乘上所發現的運算倍增器，且倍增器彼此疊加。

**What** Claude 目前在 AWS Trainium、Google TPU、NVIDIA GPU、AMD GPU 四大晶片家族上訓練與服務；今年首次導入 AMD，Mythos 在約三天內、幾乎無人工介入讓 Claude 跑上 AMD，並移植或撰寫近 100% 的 kernel。舉例：4 倍倍增器可用 25 單位算力訓練原需 100 單位的模型，或用 100 單位訓練原需 400 單位的更強模型。

### 重點
- Claude 已在 Trainium、TPU、NVIDIA GPU、AMD GPU 四大晶片家族上訓練與服務
- 過去導入新晶片平台需數十位工程師數月；這次 Mythos 約三天讓 Claude 跑上 AMD，近 100% kernel 由 Claude 移植或撰寫
- 總有效運算 = 實體算力 × 運算倍增器；4x 倍增器可讓 100 單位達成原需 400 單位的成果，倍增器彼此疊加

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/11/anthropic-ipo-roadshow/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Anthropic's IPO roadshow video 
Anthropic kicked off their IPO roadshow yesterday, and their roadshow video has some previously unreleased information about how their business works. 
 The section on "Approach to compute" with co-founder Tom Brown is particularly interesting, describing how Anthropic train and serve Claude across AWS Trainium, Google TPUs, NVIDIA GPUs, and AMD GPUs. 
 I'm not sure why there's no official video transcript, but here's one that I extracted using MacWhisper. Highlights below: 
 
 We train and serve Claude now across all four major chip families. That's only possible because early on we made an unconventional bet on a multi-chip strategy. At the time, many people thought that running AI models on different chips wasn't worth the effort. Each chip needs its own tailored software stack and inference stack, which is expensive and difficult to build. We've now been doing it for years, and we've gotten incredibly good at it. [...] 
 As an example, this year, we started working with AMD GPUs for the first time. In the past, bringing on a new chip platform took dozens of engineers months of work This time, we had Mythos try it out. It got Claude running on AMD in just three days, with basically no human intervention . Claude ported or wrote almost 100% of the kernels. [...] 
 The second driver of our compute advantage is our rate of discovery of compute multipliers. We focus on total effective compute, which is the multiplicative product of physical capacity times the compute multipliers that we discover. Each one we discover makes our pool of total effective compute bigger. For example, say you need 100 units of compute to train a model of a certain intelligence. A 4x compute multiplier means you can use 25 units of compute to train the exact same model. Or you can use those hundred physical units to train an even more intelligent model that would have previously required 400 units. 
 Compute multipliers create a competitive advantage for us that's hard to replicate. They build on each other. Each new multiplier we discover has a positive effect on the multipliers before it. They stack. We believe that this can accelerate even further as we approach recursive self-improvement. Claude will be able to discover compute multipliers entirely by itself , allowing the number of compute multipliers to grow faster and faster. 
 
 We got a hint at Anthropic's multi-chip strategy last September in their postmortem of three recent issues , where they described bugs that affected just their TPU deployments.

 Tags: ai , generative-ai , llms , anthropic , gpus , claude-mythos-fable , recursive-self-improvement

</details>