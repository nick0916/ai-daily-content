---
id: inbox_d5a9bcfe
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-medium-towards-data-science-when-eeg-models-see-the-same-people-in-t-0c68]]"
title: "When EEG Models See the Same People in Training and Testing"
url: https://towardsdatascience.com/when-eeg-models-see-the-same-people-in-training-and-testing/
source: medium-towards-data-science
published_at: 2026-10-17T12:00:00+00:00
fetched_at: 2026-10-18T03:15:28.762293+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Towards Data Science 文章探討 EEG（腦電圖）模型在訓練與測試集中出現同一批受試者時的評估問題。依原文摘要，作者比較了「participant-aware」評估方式對三種機器學習模型表現的影響。摘要未提供具體模型名稱或數字，因此無法確定效能變化幅度。一般而言，此類主題關乎資料洩漏（受試者層級的 leakage）會否讓成績被高估，這屬於推論，需以全文驗證。對做生醫訊號或任何有重複個體資料的團隊，這提醒資料切分應以個體為單位。"
key_points:
  - "主題：EEG 模型在訓練/測試包含相同受試者時的評估偏差"
  - "比較 participant-aware 評估對三種機器學習模型表現的影響"
  - "具體模型與數字原文摘要未提供"
tags: [eeg, data-leakage, evaluation-methodology, participant-aware-split, machine-learning]
topics: [engineering.evals]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## When EEG Models See the Same People in Training and Testing

Towards Data Science 文章探討 EEG（腦電圖）模型在訓練與測試集中出現同一批受試者時的評估問題。依原文摘要，作者比較了「participant-aware」評估方式對三種機器學習模型表現的影響。摘要未提供具體模型名稱或數字，因此無法確定效能變化幅度。一般而言，此類主題關乎資料洩漏（受試者層級的 leakage）會否讓成績被高估，這屬於推論，需以全文驗證。對做生醫訊號或任何有重複個體資料的團隊，這提醒資料切分應以個體為單位。

### 重點
- 主題：EEG 模型在訓練/測試包含相同受試者時的評估偏差
- 比較 participant-aware 評估對三種機器學習模型表現的影響
- 具體模型與數字原文摘要未提供

**原文：** [medium-towards-data-science](https://towardsdatascience.com/when-eeg-models-see-the-same-people-in-training-and-testing/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

How participant-aware evaluation changed performance across three machine-learning models 
 The post When EEG Models See the Same People in Training and Testing appeared first on Towards Data Science .

</details>