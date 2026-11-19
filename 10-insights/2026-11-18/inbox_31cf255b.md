---
id: inbox_31cf255b
date: 2026-11-18
source_ref: "[[00-inbox/2026-11-18/0812-simon-willison-datasette-arrows-0-1a0-d526]]"
title: "datasette-arrows 0.1a0"
url: https://simonwillison.net/2026/Nov/18/datasette-arrows/
source: simon-willison
published_at: 2026-11-18T17:09:59+00:00
fetched_at: 2026-11-19T08:17:39.691089+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 Datasette 能以串流方式匯出 Apache Arrow 格式，不必把整張表載入記憶體。 **Why** Datasette 核心的 CSV 與 TSV 能串流匯出上百萬列，但其他格式缺乏同樣機制。 **How** Datasette 1.0a43 讓外掛可透過 register_output_renderer() 實作串流匯出格式；作者習慣新增外掛功能時同步釋出一個使用它的外掛。 **What** datasette-arrows 0.1a0 由 Claude Fable 5.2 建議採用 Apache Arrow 串流格式，並幾乎一次完成外掛實作。以 datasette install datasette-arrows 安裝後，匯出對話框會多出 Arrow 選項；截圖來自 main 分支，Arrow 與 CSV/TSV 同組顯示的分組要等下個 alpha 版。"
key_points:
  - "Datasette 1.0a43 讓外掛可用 register_output_renderer() 實作串流匯出格式"
  - "datasette-arrows 0.1a0 加入 Apache Arrow 串流匯出，安裝指令為 datasette install datasette-arrows"
  - "作者指出 Claude Fable 5.2 建議 Arrow 格式並幾乎一次產出外掛；新增外掛功能時同步釋出示範外掛是其慣例"
tags: [datasette, apache-arrow, plugin, streaming-export, claude-fable-5-2]
topics: [agents.coding_agents, engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-arrows 0.1a0

讓 Datasette 能以串流方式匯出 Apache Arrow 格式，不必把整張表載入記憶體。

**Why** Datasette 核心的 CSV 與 TSV 能串流匯出上百萬列，但其他格式缺乏同樣機制。

**How** Datasette 1.0a43 讓外掛可透過 register_output_renderer() 實作串流匯出格式；作者習慣新增外掛功能時同步釋出一個使用它的外掛。

**What** datasette-arrows 0.1a0 由 Claude Fable 5.2 建議採用 Apache Arrow 串流格式，並幾乎一次完成外掛實作。以 datasette install datasette-arrows 安裝後，匯出對話框會多出 Arrow 選項；截圖來自 main 分支，Arrow 與 CSV/TSV 同組顯示的分組要等下個 alpha 版。

### 重點
- Datasette 1.0a43 讓外掛可用 register_output_renderer() 實作串流匯出格式
- datasette-arrows 0.1a0 加入 Apache Arrow 串流匯出，安裝指令為 datasette install datasette-arrows
- 作者指出 Claude Fable 5.2 建議 Arrow 格式並幾乎一次產出外掛；新增外掛功能時同步釋出示範外掛是其慣例

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/18/datasette-arrows/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-arrows 0.1a0 
 Datasette 1.0a43 added the ability for plugins to implement streaming export formats. Datasette core supports streaming CSV and TSV - you can export millions of lines of data from a table without needing to load it all into memory, because those two file formats support streaming data in chunks. The register_output_renderer() plugin hook can now be used to implement the same pattern for other formats. 
 I've learned never to release a new plugin feature without accompanying it with a plugin that uses it. 
 Claude Fable 5.2 suggested the Apache Arrow streaming format as a good option, and built this plugin in almost a single shot. 
 Add the plugin to Datasette ( datasette install datasette-arrows ) and the export dialog gains this new Arrow option: 
 
 This screenshot is from Datasette's main branch - the most recent release doesn't yet group streaming formats such as Arrow with the TSV and CSV in the "All rows in this table" section, but that's coming in the next alpha release. 
 
 
 Tags: datasette , projects

</details>