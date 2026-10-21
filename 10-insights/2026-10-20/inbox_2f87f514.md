---
id: inbox_2f87f514
date: 2026-10-20
source_ref: "[[00-inbox/2026-10-20/0006-medium-towards-data-science-synthetic-to-real-transfer-with-frozen-d-cf99]]"
title: "Synthetic-to-Real Transfer with Frozen DINOv3 Features"
url: https://towardsdatascience.com/synthetic-to-real-transfer-with-frozen-dinov3-features/
source: medium-towards-data-science
published_at: 2026-10-20T15:30:00+00:00
fetched_at: 2026-10-21T00:09:49.940014+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用程式生成的合成資料訓練模型，再遷移到真實世界影像。 **How** 依標題，採用凍結的 DINOv3 特徵進行遷移。 **What** 原文節錄的任務為卡片偵測與分割（card detection and segmentation），訓練資料為 procedurally generated 合成資料集；節錄未提供量化結果。"
key_points:
  - "訓練資料為程序生成（procedurally generated）的合成資料集"
  - "任務：卡片偵測（detection）與分割（segmentation）"
  - "標題指出方法為凍結（frozen）的 DINOv3 特徵，節錄未提供結果數字"
tags: [synthetic-data, sim-to-real, dino-v3, segmentation, transfer-learning]
topics: [research.training]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Synthetic-to-Real Transfer with Frozen DINOv3 Features

用程式生成的合成資料訓練模型，再遷移到真實世界影像。 **How** 依標題，採用凍結的 DINOv3 特徵進行遷移。 **What** 原文節錄的任務為卡片偵測與分割（card detection and segmentation），訓練資料為 procedurally generated 合成資料集；節錄未提供量化結果。

### 重點
- 訓練資料為程序生成（procedurally generated）的合成資料集
- 任務：卡片偵測（detection）與分割（segmentation）
- 標題指出方法為凍結（frozen）的 DINOv3 特徵，節錄未提供結果數字

**原文：** [medium-towards-data-science](https://towardsdatascience.com/synthetic-to-real-transfer-with-frozen-dinov3-features/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Training models on procedurally generated datasets for card detection and segmentation 
 The post Synthetic-to-Real Transfer with Frozen DINOv3 Features appeared first on Towards Data Science .

</details>