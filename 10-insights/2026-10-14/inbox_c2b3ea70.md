---
id: inbox_c2b3ea70
date: 2026-10-14
source_ref: "[[00-inbox/2026-10-14/0256-medium-towards-data-science-voting-on-features-federated-feature-sel-8d11]]"
title: "Voting on Features: Federated Feature Selection Without Sharing Data"
url: https://towardsdatascience.com/voting-on-features-federated-feature-selection-without-sharing-data/
source: medium-towards-data-science
published_at: 2026-10-14T12:30:00+00:00
fetched_at: 2026-10-18T03:16:18.768333+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "這篇文章介紹聯邦式特徵選擇（federated feature selection）：參與方不分享資料列，而是分享「投票」來共同決定哪些特徵重要。原文指出適用對象包括醫院、銀行與邊緣裝置。摘要同時提到這個做法可在 NVIDIA FLARE 與 Flower 這兩個聯邦學習框架中執行。投票的具體演算法、聚合規則與實驗結果，原文摘要沒有說明，因此無法確定。實務意義在於：在資料不能離開各自機構的情境下，仍可用分享投票的方式達成特徵選擇共識。"
key_points:
  - "做法：各方分享對特徵的投票而非資料列，以達成特徵選擇共識"
  - "可在 NVIDIA FLARE 與 Flower 中執行"
  - "適用情境：醫院、銀行、邊緣裝置"
tags: [federated-learning, feature-selection, nvidia-flare, flower, privacy]
topics: [research.training, engineering.architecture]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Voting on Features: Federated Feature Selection Without Sharing Data

這篇文章介紹聯邦式特徵選擇（federated feature selection）：參與方不分享資料列，而是分享「投票」來共同決定哪些特徵重要。原文指出適用對象包括醫院、銀行與邊緣裝置。摘要同時提到這個做法可在 NVIDIA FLARE 與 Flower 這兩個聯邦學習框架中執行。投票的具體演算法、聚合規則與實驗結果，原文摘要沒有說明，因此無法確定。實務意義在於：在資料不能離開各自機構的情境下，仍可用分享投票的方式達成特徵選擇共識。

### 重點
- 做法：各方分享對特徵的投票而非資料列，以達成特徵選擇共識
- 可在 NVIDIA FLARE 與 Flower 中執行
- 適用情境：醫院、銀行、邊緣裝置

**原文：** [medium-towards-data-science](https://towardsdatascience.com/voting-on-features-federated-feature-selection-without-sharing-data/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hospitals, banks, and edge devices can agree on which features matter by sharing votes instead of rows, runnable in NVIDIA FLARE and Flower 
 The post Voting on Features: Federated Feature Selection Without Sharing Data appeared first on Towards Data Science .

</details>