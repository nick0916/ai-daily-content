---
id: inbox_7acb7dc7
date: 2026-11-25
source_ref: "[[00-inbox/2026-11-25/0052-simon-willison-datasette-charts-0-3a0-ae37]]"
title: "datasette-charts 0.3a0"
url: https://simonwillison.net/2026/Nov/25/datasette-charts/
source: simon-willison
published_at: 2026-11-25T18:16:50+00:00
fetched_at: 2026-11-27T00:58:23.182751+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 datasette 圖表能直接加上線條、色塊與文字標註。 **Why** 圖表只呈現資料，常需要額外標示重點事件或區間才能讓讀者看懂。 **How** 在已渲染的圖表上疊加線條、陰影區域、標籤或三者組合；可在 Datasette Lite 的 chart builder UI 調整，或安裝 Datasette Agent 讓 agent 代為建立。 **What** datasette-charts 0.3a0（alpha）新增 chart annotations。Simon Willison 在 agent.datasette.io demo 用提示詞「比較我的 LLM 與 Datasette 標籤內容並加上標註」產生範例圖。"
key_points:
  - "datasette-charts 0.3a0 新增圖表標註：線條、陰影區域、標籤，可組合使用"
  - "Datasette Lite 的 chart builder UI 可手動調整標註"
  - "搭配 Datasette Agent 可用自然語言提示讓 agent 產生帶標註的圖表"
tags: [datasette, datasette-charts, visualization, simon-willison]
topics: [product_and_org.product]
importance: 2
novelty: 2
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-charts 0.3a0

讓 datasette 圖表能直接加上線條、色塊與文字標註。

**Why** 圖表只呈現資料，常需要額外標示重點事件或區間才能讓讀者看懂。

**How** 在已渲染的圖表上疊加線條、陰影區域、標籤或三者組合；可在 Datasette Lite 的 chart builder UI 調整，或安裝 Datasette Agent 讓 agent 代為建立。

**What** datasette-charts 0.3a0（alpha）新增 chart annotations。Simon Willison 在 agent.datasette.io demo 用提示詞「比較我的 LLM 與 Datasette 標籤內容並加上標註」產生範例圖。

### 重點
- datasette-charts 0.3a0 新增圖表標註：線條、陰影區域、標籤，可組合使用
- Datasette Lite 的 chart builder UI 可手動調整標註
- 搭配 Datasette Agent 可用自然語言提示讓 agent 產生帶標註的圖表

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/25/datasette-charts/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-charts 0.3a0 
 I added chart annotations to datasette-charts ! 
 You can now render a chart and then annotate it with lines, shaded areas, labels, or a combination of the three. 
 A chart with annotations looks like this: 
 
 Here's that same chart in Datasette Lite , where you can tweak the annotations using the chart builder UI: 
 
 If you also install Datasette Agent the agent can build annotated charts for you. Here's what I got on the agent.datasette.io demo for this prompt: 
 
 Show a chart comparing Simon's tagged content about LLMs with his tagged content about Datasette, with annotations 
 
 
 
 
 Tags: datasette , visualization , datasette-charts

</details>