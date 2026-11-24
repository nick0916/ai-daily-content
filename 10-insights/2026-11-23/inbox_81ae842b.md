---
id: inbox_81ae842b
date: 2026-11-23
source_ref: "[[00-inbox/2026-11-23/0209-simon-willison-datasette-charts-0-1a0-44fa]]"
title: "datasette-charts 0.1a0"
url: https://simonwillison.net/2026/Nov/23/datasette-charts/
source: simon-willison
published_at: 2026-11-23T00:37:20+00:00
fetched_at: 2026-11-24T02:14:55.269104+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 新外掛，能針對整張表或任意 SQL 查詢自動建議並畫出圖表。 **Why** 先前的圖表外掛（如 datasette-vega）只能畫目前這一頁的結果，通常最多 100 列。 **How** 外掛把每張圖編譯成 SQL 查詢，用 GROUP BY、時間分桶與 window function 對整個結果集聚合，每次回傳上限 5,000 列；大型表格用抽樣來建議圖表。 **What** datasette-charts 0.1a0 發布，Simon Willison 週日用 Claude Fable 5.2 做出初版原型，效果好到直接做成完整外掛。圖表狀態存在 URL 的 #fragment，可收藏分享，並提供 Datasette Lite 試用。"
key_points:
  - "圖表對全部資料列計算（可達數百萬列），查詢結果上限 5,000 列，而非只看當前頁的約 100 列"
  - "內建多種圖表類型（使用 vendored 的 D3、Observable Plot、topojson-client），各自有啟發式規則判斷是否適合當前資料列"
  - "原型由 Claude Fable 5.2 產出，Simon 想這個問題超過一年，原型成功後轉為正式外掛；目前仍是 alpha"
tags: [datasette, datasette-charts, visualization, coding-agents, claude-fable]
topics: [agents.coding_agents, foundation_models.claude]
importance: 2
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-charts 0.1a0

Datasette 新外掛，能針對整張表或任意 SQL 查詢自動建議並畫出圖表。

**Why** 先前的圖表外掛（如 datasette-vega）只能畫目前這一頁的結果，通常最多 100 列。

**How** 外掛把每張圖編譯成 SQL 查詢，用 GROUP BY、時間分桶與 window function 對整個結果集聚合，每次回傳上限 5,000 列；大型表格用抽樣來建議圖表。

**What** datasette-charts 0.1a0 發布，Simon Willison 週日用 Claude Fable 5.2 做出初版原型，效果好到直接做成完整外掛。圖表狀態存在 URL 的 #fragment，可收藏分享，並提供 Datasette Lite 試用。

### 重點
- 圖表對全部資料列計算（可達數百萬列），查詢結果上限 5,000 列，而非只看當前頁的約 100 列
- 內建多種圖表類型（使用 vendored 的 D3、Observable Plot、topojson-client），各自有啟發式規則判斷是否適合當前資料列
- 原型由 Claude Fable 5.2 產出，Simon 想這個問題超過一年，原型成功後轉為正式外掛；目前仍是 alpha

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/23/datasette-charts/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-charts 0.1a0 
 I've been thinking about this problem for over a year now, but on Sunday I finally fired up Claude Fable 5.2 to build an initial prototype. The prototype went so well that this is now a full plugin. 
 You can try it out in Datasette Lite here . It looks like this: 
 
 The new charts plugin works against any table or arbitrary SQL query in Datasette. It defines several different chart types (using vendored D3 , Observable Plot , and topojson-client ), each with a set of heuristics for identifying when they might be a good match for a specific set of rows. 
 Those suggestion thumbnails at the top are actual visualizations driven by the data, and selecting one pulls up the full chart along with tools for modifying it. You can also manually construct a chart from scratch. 
 As with other Datasette visualization plugins, the current state of your chart is persisted in a #fragment in the URL - so you can bookmark charts or share them with others. 
 The most important feature is that the charts take all rows into account . Previous charting plugins like datasette-vega would only show charts for the current page of results, generally up to 100 rows. 
 The new plugin compiles each chart to a SQL query that aggregates across the entire result set (potentially millions of rows) using GROUP BY, time bucketing, and window functions. Each query returns a result capped at 5,000 rows, suitable for display on the chart. The plugin uses sampling to help suggest charts for larger tables without evaluating the full result set. 
 I'm really happy with this initial release of the plugin. It's still very much an alpha, but it's the closest I've got to the dream of Datasette helping visualize data with as little required direction from the user as possible. 
 
 
 Tags: coding-agents , generative-ai , projects , ai , llms , datasette , visualization , claude-mythos-fable

</details>