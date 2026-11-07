---
id: inbox_a2b02b8c
date: 2026-11-04
source_ref: "[[00-inbox/2026-11-04/0142-hackernews-show-hn-a-decent-text-to-image-model-tra-5396]]"
title: "Show HN: A decent text-to-image model trained for ~$20K (Apache 2.0 Weights)"
url: https://www.linum.ai/field-notes/pjit-21k
source: hackernews
published_at: 2026-11-04T16:45:11+00:00
fetched_at: 2026-11-07T01:47:09.469902+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "兩人小實驗室用約 2 萬美元訓練出一個開源文字生圖模型，並驗證不用 VAE 的像素空間擴散架構。 **Why** 現有影片模型太慢太貴、可控性不足，無法支撐迭代式的創作；他們想先把推論成本壓低。 **How** 捨棄 VAE，讓擴散模型直接在像素空間學出適合任務的表示，採用 Pyramid-JiT 架構，attention 的 token 縮減力道提高 4 倍且品質無明顯損失。 **What** Linum 以約 2 萬美元在 6.6 億樣本上訓練文字生圖模型，並以 Apache 2.0 釋出權重；原文稱其收斂速度比對應的 latent diffusion 快 11 倍，是邁向 Linum v3 影片模型的墊腳石（影片模型多半從圖像模型起步）。"
key_points:
  - "約 2 萬美元、6.6 億樣本訓練文字生圖模型，Apache 2.0 開放權重"
  - "像素空間擴散（無 VAE）：收斂速度比 latent diffusion 對照組快 11 倍"
  - "Pyramid-JiT 的 attention context token 縮減多 4 倍，品質無明顯損失"
tags: [text-to-image, pixel-space-diffusion, open-weights, pyramid-jit, video-generation]
topics: [foundation_models.open_weights, research.training]
importance: 3
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: A decent text-to-image model trained for ~$20K (Apache 2.0 Weights)

兩人小實驗室用約 2 萬美元訓練出一個開源文字生圖模型，並驗證不用 VAE 的像素空間擴散架構。

**Why** 現有影片模型太慢太貴、可控性不足，無法支撐迭代式的創作；他們想先把推論成本壓低。

**How** 捨棄 VAE，讓擴散模型直接在像素空間學出適合任務的表示，採用 Pyramid-JiT 架構，attention 的 token 縮減力道提高 4 倍且品質無明顯損失。

**What** Linum 以約 2 萬美元在 6.6 億樣本上訓練文字生圖模型，並以 Apache 2.0 釋出權重；原文稱其收斂速度比對應的 latent diffusion 快 11 倍，是邁向 Linum v3 影片模型的墊腳石（影片模型多半從圖像模型起步）。

### 重點
- 約 2 萬美元、6.6 億樣本訓練文字生圖模型，Apache 2.0 開放權重
- 像素空間擴散（無 VAE）：收斂速度比 latent diffusion 對照組快 11 倍
- Pyramid-JiT 的 attention context token 縮減多 4 倍，品質無明顯損失

**原文：** [hackernews](https://www.linum.ai/field-notes/pjit-21k)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

My brother and I run a 2-person lab that trains our own generative video models from scratch. The ultimate goal is a set of creative tools that make it easier for anyone to make animation. Video models today are too slow/expensive and lack sufficient controls. Creativity is an iterative process. You make, you tweak, you get better. In our opinion, they're not usable yet for storytelling. When we set out to build Linum v3 (our next video model) earlier this year, the primary goal was to bring the cost envelope of inference down significantly. If our model is fast and cheap, it's the first step (of many) towards useful creative tools. Typically, you see "latent diffusion models". A VAE (Variational Autoencoder) compresses the input data into a smaller "latent space" and the diffusion model learns how to generate within this subspace. Over the past few months, we've been publishing our work on efficient pixel-space diffusion models. These throw away the VAE, having the diffusion model learn a latent-space optimized for its exact task. This serves 3 purposes:
1) Simplify Architecture (no 2-stage model training)
2) Faster Convergence (11x faster convergence vs. our latent diffusion counterpart)
3) Cheaper Inference (4x more aggressive token reduction in attention context-windows, without significant loss in quality) This past month we were pressure testing our latest architecture (Pyramid-JiT) by training a text-to-image model longer than the typical one-off experiment. Specifically, we trained it for ~$20K on 660M samples. We were surprised by the quality of results, so we thought we'd release it as open weights for the community (Apache 2.0). The research itself is already public, on our website. For us, it's a big stepping stone towards cheaper video models, since pretty much all video models start as image models. We like to say these models have to learn nouns before they learn verbs.

</details>