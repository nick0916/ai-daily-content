---
id: inbox_6db27f50
date: 2026-11-24
source_ref: "[[00-inbox/2026-11-24/0006-simon-willison-datasette-agent-0-7a1-c1c1]]"
title: "datasette-agent 0.7a1"
url: https://simonwillison.net/2026/Nov/24/datasette-agent/
source: simon-willison
published_at: 2026-11-24T03:45:57+00:00
fetched_at: 2026-11-25T00:12:22.134321+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 Datasette 的 AI 聊天側邊面板，能跟著網址 # 片段切換頁面狀態。 **Why** 其他 Datasette 外掛會在使用者操作時更新 URL 的 fragment hash，側邊面板需要跟著同步，才能深度整合。 **How** 這個版本改進 iframe 側邊面板對 fragment hash 的導覽處理。 **What** datasette-agent 0.7a1（alpha）是小幅改進，作者 Simon Willison 表示是為了修正更重要的 datasette-charts 0.2a0 版本中的一些 bug 而做。"
key_points:
  - "datasette-agent 0.7a1：iframe 側邊面板支援以 fragment hash 導覽"
  - "目的是與會更新 fragment hash 的其他 Datasette 外掛深度整合"
  - "起因是修正 datasette-charts 0.2a0 的 bug"
tags: [datasette, datasette-agent, simon-willison, plugin, alpha-release]
topics: [agents.frameworks]
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-agent 0.7a1

讓 Datasette 的 AI 聊天側邊面板，能跟著網址 # 片段切換頁面狀態。

**Why** 其他 Datasette 外掛會在使用者操作時更新 URL 的 fragment hash，側邊面板需要跟著同步，才能深度整合。

**How** 這個版本改進 iframe 側邊面板對 fragment hash 的導覽處理。

**What** datasette-agent 0.7a1（alpha）是小幅改進，作者 Simon Willison 表示是為了修正更重要的 datasette-charts 0.2a0 版本中的一些 bug 而做。

### 重點
- datasette-agent 0.7a1：iframe 側邊面板支援以 fragment hash 導覽
- 目的是與會更新 fragment hash 的其他 Datasette 外掛深度整合
- 起因是修正 datasette-charts 0.2a0 的 bug

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/24/datasette-agent/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-agent 0.7a1 
 A small improvement to Datasette Agent : chat sessions could already open an iframe side panel that could then navigate to different pages. This version improves navigation by fragment hashes, for deeper integration with other Datasette plugins that update fragment hashes when the user interacts with the plugin in a way that changes state. 
 I built this in order to fix some bugs with the much more exciting datasette-charts 0.2a0 release . 
 
 
 Tags: datasette-agent , datasette

</details>