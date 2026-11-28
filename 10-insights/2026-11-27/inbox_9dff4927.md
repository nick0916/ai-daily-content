---
id: inbox_9dff4927
date: 2026-11-27
source_ref: "[[00-inbox/2026-11-27/0141-simon-willison-datasette-charts-0-4a0-c508]]"
title: "datasette-charts 0.4a0"
url: https://simonwillison.net/2026/Nov/27/datasette-charts/
source: simon-willison
published_at: 2026-11-27T23:57:17+00:00
fetched_at: 2026-11-28T01:50:56.198932+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓外掛作者更容易替 Datasette 新增圖表類型的外掛框架更新。 **Why** datasette-charts 提供 plugin hook 讓其他外掛定義新圖表，但作者還沒實際用過，設計上的摩擦點不明。 **How** 作者讓 Claude Opus 5.5 實際寫一個實驗性外掛來試用 hook，由此找出設計上的摩擦點並在此版修正。 **What** datasette-charts 0.4a0 發布，修正 hook 的易用性問題；同時上線 charts.datasette.io，含外掛作者教學，以及展示核心圖表與註解的 gallery，每個範例連到 Datasette Lite 互動 demo。"
key_points:
  - "datasette-charts 0.4a0：依 Claude Opus 5.5 試作外掛暴露的設計摩擦點，改善新圖表類型 plugin hook 的易用性"
  - "新網站 charts.datasette.io：含外掛作者教學與核心圖表／註解 gallery"
  - "gallery 每個範例連到 Datasette Lite 的互動 demo"
tags: [datasette, datasette-charts, plugin-hook, visualization, claude-opus]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-charts 0.4a0

讓外掛作者更容易替 Datasette 新增圖表類型的外掛框架更新。

**Why** datasette-charts 提供 plugin hook 讓其他外掛定義新圖表，但作者還沒實際用過，設計上的摩擦點不明。

**How** 作者讓 Claude Opus 5.5 實際寫一個實驗性外掛來試用 hook，由此找出設計上的摩擦點並在此版修正。

**What** datasette-charts 0.4a0 發布，修正 hook 的易用性問題；同時上線 charts.datasette.io，含外掛作者教學，以及展示核心圖表與註解的 gallery，每個範例連到 Datasette Lite 互動 demo。

### 重點
- datasette-charts 0.4a0：依 Claude Opus 5.5 試作外掛暴露的設計摩擦點，改善新圖表類型 plugin hook 的易用性
- 新網站 charts.datasette.io：含外掛作者教學與核心圖表／註解 gallery
- gallery 每個範例連到 Datasette Lite 的互動 demo

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/27/datasette-charts/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-charts 0.4a0 
 The new datasette-charts plugin has its own plugin hook to allow other plugins to define new chart types, but I hadn't actually used it for anything yet. I had Claude Opus 5.5 build an experimental plugins just to try out the hook and it came up with a bunch of friction points in the design. This release addresses those, which should make building additional chart plugins a whole lot more ergonomic. 
 I've also added a website for the plugin, at charts.datasette.io . The new website includes a tutorial for plugin authors , and a gallery showing all of the core charts and annotations, each one linking to an interactive demo on Datasette Lite . 
 
 
 
 Tags: datasette-charts , datasette , visualization , datasette-lite

</details>