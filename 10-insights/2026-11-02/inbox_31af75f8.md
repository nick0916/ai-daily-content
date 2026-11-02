---
id: inbox_31af75f8
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2325-claude-mem-releases-v15-8-3-9e18]]"
title: "v15.8.3"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.8.3
source: claude-mem-releases
published_at: 2026-11-02T06:26:25+00:00
fetched_at: 2026-11-02T23:34:40.792239+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v15.8.3 修正隱私問題：瀏覽器設定不再未經同意就上傳使用者的 prompt。 **Why** 自 v15.2.0 起，npx claude-mem install 的瀏覽器設定會掃描本機 agent 歷史，並上傳過去 30 天的 prompt 全文。 **How** 改為先只讀取本機資料，再顯示同意面板，只上傳使用者勾選的工具；選擇「全部保留在本機」即不上傳任何內容。 **What** analytics 改為獨立、預設關閉的選項；此版本不會移除舊版已上傳的 prompt，cmem.ai 伺服器端處理與隱私政策文字也不在此次變更範圍內。"
key_points:
  - "原行為：未詢問即上傳過去 30 天 prompt 全文，並附 session ID、專案名、資料夾路徑與時間戳（對應 issue #5176）"
  - "新行為：同意面板列出每個偵測到的工具與 prompt 數；新增 POST /api/setup/scan/consent，僅限 loopback 且有 origin 檢查"
  - "未涵蓋：舊版已上傳的 prompt 不會因此更新被刪除；cmem.ai 端與隱私政策文字不在此次變更內"
tags: [privacy, claude-mem, consent, data-upload]
topics: [security, agents.coding_agents]
importance: 3
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.8.3

claude-mem v15.8.3 修正隱私問題：瀏覽器設定不再未經同意就上傳使用者的 prompt。

**Why** 自 v15.2.0 起，npx claude-mem install 的瀏覽器設定會掃描本機 agent 歷史，並上傳過去 30 天的 prompt 全文。

**How** 改為先只讀取本機資料，再顯示同意面板，只上傳使用者勾選的工具；選擇「全部保留在本機」即不上傳任何內容。

**What** analytics 改為獨立、預設關閉的選項；此版本不會移除舊版已上傳的 prompt，cmem.ai 伺服器端處理與隱私政策文字也不在此次變更範圍內。

### 重點
- 原行為：未詢問即上傳過去 30 天 prompt 全文，並附 session ID、專案名、資料夾路徑與時間戳（對應 issue #5176）
- 新行為：同意面板列出每個偵測到的工具與 prompt 數；新增 POST /api/setup/scan/consent，僅限 loopback 且有 origin 檢查
- 未涵蓋：舊版已上傳的 prompt 不會因此更新被刪除；cmem.ai 端與隱私政策文字不在此次變更內

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.8.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Privacy fix 
 Browser setup no longer uploads your prompts to cmem.ai without asking. Fixes #5176 . 
 The browser setup opened by npx claude-mem install (since v15.2.0) scanned local agent histories and uploaded the full text of the last 30 days of prompts, with session IDs, project names, folder paths and timestamps, without asking. 
 What changed ( #5220 ) 
 
 The scan now reads local history only, then stops and asks. Nothing leaves the machine until you answer. 
 A new consent panel states what is sent and lists each detected tool with its prompt count. Only ticked tools are uploaded. 
 "Keep everything local", or unticking every tool, uploads nothing. 
 The analytics box is optional, off by default, and separate from upload consent. 
 A second start request while the question is open, or during an upload, joins the current state instead of starting a second upload. 
 New POST /api/setup/scan/consent route: loopback-only and origin-guarded. 
 
 Not covered by this release 
 
 Prompts already uploaded by earlier versions are not removed by this update. 
 Server-side handling at cmem.ai and privacy-policy wording are outside this change. 
 
 Full Changelog : v15.8.2...v15.8.3

</details>