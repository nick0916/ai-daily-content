---
id: inbox_a2ee9010
date: 2026-11-04
source_ref: "[[00-inbox/2026-11-04/0001-simon-willison-datasette-apps-0-3a0-1bc5]]"
title: "datasette-apps 0.3a0"
url: https://simonwillison.net/2026/Nov/4/datasette-apps/
source: simon-willison
published_at: 2026-11-04T00:29:36+00:00
fetched_at: 2026-11-06T00:08:18.220978+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 AI 助理能在聊天中直接叫出、管理資料庫小工具，且碰到會改資料的查詢要先問你。 **Why** 用 LLM 產生的 HTML 應用若能任意呼叫寫入型查詢會有風險，需要權限與人工核准把關。 **How** 在 Datasette Agent 聊天輸入 # 自動補全可檢視的 app；新增 app_add_stored_queries() 與 app_remove_stored_queries() 工具管理 app 可呼叫的 stored query，授予寫入型查詢須經使用者核准。 **What** datasette-apps 0.3a0 發布：app_create() 會檢查 stored query 是否存在且使用者可檢視，並對寫入型查詢先要求核准；「View app」按鈕與 # 連結改為在 Datasette Agent 面板全螢幕開啟。"
key_points:
  - "輸入 # 可在 Datasette Agent 聊天中標記並自動補全使用者有權限的 app"
  - "新增 app_add_stored_queries() / app_remove_stored_queries() 工具，授予寫入型查詢須使用者核准"
  - "app_create() 會驗證 stored query 存在且可檢視，寫入型查詢建立前需核准"
tags: [datasette, datasette-apps, datasette-agent, permissions, human-in-the-loop]
topics: [agents.frameworks, security]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-apps 0.3a0

讓 AI 助理能在聊天中直接叫出、管理資料庫小工具，且碰到會改資料的查詢要先問你。

**Why** 用 LLM 產生的 HTML 應用若能任意呼叫寫入型查詢會有風險，需要權限與人工核准把關。

**How** 在 Datasette Agent 聊天輸入 # 自動補全可檢視的 app；新增 app_add_stored_queries() 與 app_remove_stored_queries() 工具管理 app 可呼叫的 stored query，授予寫入型查詢須經使用者核准。

**What** datasette-apps 0.3a0 發布：app_create() 會檢查 stored query 是否存在且使用者可檢視，並對寫入型查詢先要求核准；「View app」按鈕與 # 連結改為在 Datasette Agent 面板全螢幕開啟。

### 重點
- 輸入 # 可在 Datasette Agent 聊天中標記並自動補全使用者有權限的 app
- 新增 app_add_stored_queries() / app_remove_stored_queries() 工具，授予寫入型查詢須使用者核准
- app_create() 會驗證 stored query 存在且可檢視，寫入型查詢建立前需核准

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/4/datasette-apps/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-apps 0.3a0 
 Datasette Apps adds support for hosting and editing custom HTML applications inside of Datasette. 
 These can be created by hand, but it's easier to create them using LLMs via Datasette Agent . This release improves that integration: 
 
 
 Apps can now be tagged in Datasette Agent chat messages by typing # , which autocompletes from the apps the user has permission to view. 
 New app_add_stored_queries() and app_remove_stored_queries() tools let the agent manage which stored queries an app is allowed to call. Granting a write query requires approval from the user first. 
 app_create() now checks that each requested stored query exists and that the user can view it, and asks the user to approve any write queries before the app is created. 
 The "View app" buttons shown by the agent tools, and the links on # app references, now open the app full screen in the Datasette Agent panel. 
 
 
 
 
 Tags: datasette , datasette-agent , datasette-apps

</details>