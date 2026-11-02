---
id: inbox_7dee293b
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2325-claude-mem-releases-v15-8-2-46ac]]"
title: "v15.8.2"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.8.2
source: claude-mem-releases
published_at: 2026-11-02T06:00:18+00:00
fetched_at: 2026-11-02T23:34:40.792739+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v15.8.2 縮減遙測量，並修正 Work view 的幾個問題。 **Why** 原文標題為縮減遙測量，目的是降低高頻事件的上報量。 **How** 將 observer 回合、work-state 使用、context 注入、搜尋與 skills 等高頻事件，改為每台安裝每天一筆帶 count 的彙總；worker 啟停事件附 restart_count，失敗事件則每種類型每天一筆。 **What** 同時修正 runaway 的 opened 事件；cmem.ai 額度用盡後，gateway 改為每天探測一次；閒置任務卡不再顯示 spinner。"
key_points:
  - "高頻事件（observer 回合、work-state、context 注入、搜尋、skills）改為每台安裝每天一筆彙總，附 count"
  - "worker 啟停事件附 restart_count；失敗事件每種類型每天一筆，附 count"
  - "修正：runaway 'opened' 事件；cmem.ai 額度用盡後 gateway 每天只探測一次（#5266、#5269）"
tags: [telemetry, claude-mem, observability, rate-limit]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.8.2

claude-mem v15.8.2 縮減遙測量，並修正 Work view 的幾個問題。

**Why** 原文標題為縮減遙測量，目的是降低高頻事件的上報量。

**How** 將 observer 回合、work-state 使用、context 注入、搜尋與 skills 等高頻事件，改為每台安裝每天一筆帶 count 的彙總；worker 啟停事件附 restart_count，失敗事件則每種類型每天一筆。

**What** 同時修正 runaway 的 opened 事件；cmem.ai 額度用盡後，gateway 改為每天探測一次；閒置任務卡不再顯示 spinner。

### 重點
- 高頻事件（observer 回合、work-state、context 注入、搜尋、skills）改為每台安裝每天一筆彙總，附 count
- worker 啟停事件附 restart_count；失敗事件每種類型每天一筆，附 count
- 修正：runaway 'opened' 事件；cmem.ai 額度用盡後 gateway 每天只探測一次（#5266、#5269）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.8.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Fixes 
 
 Work view: telemetry volume cuts. High-volume events (observer turns, work-state use, context injections, searches, skills) are now one daily rollup per install with a count ; worker start/stop carry restart_count ; failures are one event per type per day with count . 
 Observer: after a spent cmem.ai allowance, the gateway is probed once a day instead of on every resume. 
 Work view: fixed a runaway "opened" event; hosted viewer reports analytics with viewer_host='hosted' . 
 Work view: idle task cards no longer show a spinner ( #5266 ). 
 
 Includes #5266 , #5269 .

</details>