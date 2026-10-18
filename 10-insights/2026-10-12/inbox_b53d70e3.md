---
id: inbox_b53d70e3
date: 2026-10-12
source_ref: "[[00-inbox/2026-10-12/0256-simon-willison-profiling-web-edit-with-python-3-15-flam-2abf]]"
title: "Profiling web-edit with Python 3.15: flame graphs and source heatmaps"
url: https://simonwillison.net/2026/Oct/12/python-3-15-web-edit-profiling/
source: simon-willison
published_at: 2026-10-12T16:58:00+00:00
fetched_at: 2026-10-18T03:04:53.007488+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 用新的 Python 3.15 profiler 做實測：他在 Codex 中使用 GPT-6 Astra Extra High，要求它先研究，再針對 PyPI 上的 web-edit app 產生 Python 3.15 flame graph 與 heatmap 範例。Prompt 為「I need a Python 3.15 flame graph and heatmap demo of the 'web-edit' app from PyPI - research first then make me those demos」。結果產出了可檢視的 flame graph 與 source heatmap 範例頁面。這是把 coding agent 用來學習並示範新語言工具（Tachyon sampling profiler）的案例，可作為上手新 profiler 的參考，也是後續 web-edit 0.1a1 效能最佳化所用 profiling 報告的來源脈絡。"
key_points:
  - "使用 Codex + GPT-6 Astra Extra High，對 PyPI 上的 web-edit 跑 Python 3.15 profiler"
  - "Prompt 採「research first then make me those demos」兩階段指令，產出 flame graph 與 source heatmap 範例"
  - "示範 Python 3.15 新 sampling profiler 的實際輸出形式"
tags: [python-3-15, profiling, codex, flame-graph, gpt-6-astra]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Profiling web-edit with Python 3.15: flame graphs and source heatmaps

Simon Willison 用新的 Python 3.15 profiler 做實測：他在 Codex 中使用 GPT-6 Astra Extra High，要求它先研究，再針對 PyPI 上的 web-edit app 產生 Python 3.15 flame graph 與 heatmap 範例。Prompt 為「I need a Python 3.15 flame graph and heatmap demo of the 'web-edit' app from PyPI - research first then make me those demos」。結果產出了可檢視的 flame graph 與 source heatmap 範例頁面。這是把 coding agent 用來學習並示範新語言工具（Tachyon sampling profiler）的案例，可作為上手新 profiler 的參考，也是後續 web-edit 0.1a1 效能最佳化所用 profiling 報告的來源脈絡。

### 重點
- 使用 Codex + GPT-6 Astra Extra High，對 PyPI 上的 web-edit 跑 Python 3.15 profiler
- Prompt 採「research first then make me those demos」兩階段指令，產出 flame graph 與 source heatmap 範例
- 示範 Python 3.15 新 sampling profiler 的實際輸出形式

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/12/python-3-15-web-edit-profiling/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Research: Profiling web-edit with Python 3.15: flame graphs and source heatmaps 
 I put the new Python 3.15 profiler through its paces by having GPT-6 Astra Extra High in Codex run it against my new web-edit app : 
 
 I need a Python 3.15 flame graph and heatmap demo of the "web-edit" app from PyPI - research first then make me those demos 
 
 Here's the resulting example flame graph and heatmap . 
 
 
 Tags: profiling , python , codex

</details>