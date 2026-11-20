---
id: inbox_53cec926
date: 2026-11-19
source_ref: "[[00-inbox/2026-11-19/0105-medium-tag-llm-reinforcement-learning-vs-supervised-fin-4bdb]]"
title: "Reinforcement learning vs supervised fine-tuning for HYROX race commentary on a 3B model"
url: https://medium.com/@vladmatei432/reinforcement-learning-vs-supervised-fine-tuning-for-hyrox-race-commentary-on-a-3b-model-a068a19199de?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-11-19T20:15:53+00:00
fetched_at: 2026-11-20T01:12:45.578661+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "比較兩種讓 3B 模型學會 HYROX 比賽解說的方法。 **How** 一種是以 GRPO 強化學習訓練，並以 Jev 作為 reward model 的評審；另一種是用較大模型校正過的範例做監督式微調。 **What** 原文摘要只描述兩種做法，未提供評估結果或數字。"
key_points:
  - "強化學習組：GRPO，以 Jev 作為 reward model 中的評審"
  - "對照組：在較大模型校正過的範例上做 fine-tuning"
  - "摘要未提供兩者的評估指標或結果，無法判斷優劣"
tags: [grpo, reinforcement-learning, supervised-fine-tuning, reward-model, small-language-model]
topics: [research.training]
importance: 2
novelty: 2
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Reinforcement learning vs supervised fine-tuning for HYROX race commentary on a 3B model

比較兩種讓 3B 模型學會 HYROX 比賽解說的方法。

**How** 一種是以 GRPO 強化學習訓練，並以 Jev 作為 reward model 的評審；另一種是用較大模型校正過的範例做監督式微調。

**What** 原文摘要只描述兩種做法，未提供評估結果或數字。

### 重點
- 強化學習組：GRPO，以 Jev 作為 reward model 中的評審
- 對照組：在較大模型校正過的範例上做 fine-tuning
- 摘要未提供兩者的評估指標或結果，無法判斷優劣

**原文：** [medium-tag-llm](https://medium.com/@vladmatei432/reinforcement-learning-vs-supervised-fine-tuning-for-hyrox-race-commentary-on-a-3b-model-a068a19199de?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

GRPO with Jev as the judge in the reward model against fine-tuning on a bigger model’s checked examples Continue reading on Medium »

</details>