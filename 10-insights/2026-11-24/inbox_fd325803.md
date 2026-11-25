---
id: inbox_fd325803
date: 2026-11-24
source_ref: "[[00-inbox/2026-11-24/0006-simon-willison-datasette-charts-0-2a0-2e85]]"
title: "datasette-charts 0.2a0"
url: https://simonwillison.net/2026/Nov/24/datasette-charts/
source: simon-willison
published_at: 2026-11-24T04:24:29+00:00
fetched_at: 2026-11-25T00:11:49.520549+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓使用者在聊天中直接叫 AI 畫圖表，而不必手動操作圖表介面。 **What** Simon Willison 的 datasette-charts 0.2a0 新增與 Datasette Agent 的整合，可在對話中以相同的圖表建議與生成工具建立圖表。示範中輸入 #stats 開啟資料表搜尋，圖表內嵌顯示於聊天，並可在面板開啟圖表建構器；切換圖表後 agent 能察覺面板內容改變並描述新圖表。可在 agent.datasette.io 用 GitHub 登入試用。"
key_points:
  - "datasette-charts 0.2a0 整合 Datasette Agent，聊天中即可要求建立圖表"
  - "輸入 #stats 可開啟資料表搜尋，圖表內嵌在聊天並可用 Open in the chart builder 開啟面板"
  - "使用者在面板改變圖表後，agent 能偵測變化並描述新圖表"
tags: [datasette, datasette-charts, datasette-agent, visualization, plugin]
topics: [agents.frameworks]
importance: 2
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-charts 0.2a0

讓使用者在聊天中直接叫 AI 畫圖表，而不必手動操作圖表介面。

**What** Simon Willison 的 datasette-charts 0.2a0 新增與 Datasette Agent 的整合，可在對話中以相同的圖表建議與生成工具建立圖表。示範中輸入 #stats 開啟資料表搜尋，圖表內嵌顯示於聊天，並可在面板開啟圖表建構器；切換圖表後 agent 能察覺面板內容改變並描述新圖表。可在 agent.datasette.io 用 GitHub 登入試用。

### 重點
- datasette-charts 0.2a0 整合 Datasette Agent，聊天中即可要求建立圖表
- 輸入 #stats 可開啟資料表搜尋，圖表內嵌在聊天並可用 Open in the chart builder 開啟面板
- 使用者在面板改變圖表後，agent 能偵測變化並描述新圖表

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/24/datasette-charts/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-charts 0.2a0 
 I introduced this new charting plugin for Datasette yesterday . Today it's gained integration with Datasette Agent , so now you can ask chat for a chart and it will create one for you using the same underlying chart suggestion and generation tools. 
 Here's a demo video, recorded on agent.datasette.io where you can sign in with GitHub to try the plugin yourself: 
 
 
 
 Download the video (MP4) 
 
 
 I prompt Datasette Agent to "Use #stats to show sqlite-utils downloads over time as a chart" - where typing "#stats" opens a table search box. It shows me a chart inline in the chat, and when I click "Open in the chart builder" it opens the chart in a panel along with the table page. I use the table page to switch to a chart of "datasette", then when I ask the agent "what does the chart show?" it notices that I changed the content in the panel and describes the new Datasette chart to me.
 
 

 Here's a Markdown export of the chat from the video. 
 
 
 Tags: datasette-agent , datasette , visualization

</details>