---
id: inbox_b1e513c8
date: 2026-10-12
source_ref: "[[00-inbox/.../inbox_b1e513c8]]"
title: "v13.36.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.36.1
source: claude-mem-releases
published_at: 2026-10-12T21:01:07+00:00
fetched_at: 2026-10-18T03:35:42.225561+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.36.1 是針對 13.36.0 審查發現的三項問題所做的修補，另包含八項社群修正。最重要的隱私修正：在 server runtime 中，檔案編輯、工具輸入輸出與 session-start prompt 會在 <private> 區塊仍存在的情況下送到 server，且 server 會把這些內容保留在原始事件紀錄中，過去只在建構模型 prompt 時才移除。現在 <private> 內容在離開 hook 前就會移除，server 在儲存事件或 session metadata 前再移除一次。預設的 worker runtime 不受影響。另外兩項修正：資料庫升級時，新舊 worker 可能同時通過版本檢查的競爭問題，現在檢查與寫入 schema writer 位於同一個 SQLite 寫入鎖內完成；Chroma 連線取消時可能釋放新連線鎖的問題，現在每個連線持有自己的 writer-lock token，只釋放自己的鎖。社群修正（均由 @rudycelekli 提交）涵蓋 Postgres 數字設定、Gemini 重試提示、UTF-8 BOM 與 API key 陣列等。"
key_points:
  - "server runtime 的 <private> 內容先前會送到 server 並保留在原始事件紀錄中；現在 hook 端先移除，server 儲存前再移除一次"
  - "schema writer 的檢查與寫入移入同一個 SQLite 寫入鎖，避免兩個 worker 同時通過版本檢查"
  - "每個 Chroma 連線持有自己的 writer-lock token，取消時只釋放自己的鎖，避免第二個 writer 寫入同一儲存"
tags: [privacy, server-runtime, sqlite, chroma, race-condition]
topics: [security, engineering.architecture]
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.36.1

claude-mem v13.36.1 是針對 13.36.0 審查發現的三項問題所做的修補，另包含八項社群修正。最重要的隱私修正：在 server runtime 中，檔案編輯、工具輸入輸出與 session-start prompt 會在 <private> 區塊仍存在的情況下送到 server，且 server 會把這些內容保留在原始事件紀錄中，過去只在建構模型 prompt 時才移除。現在 <private> 內容在離開 hook 前就會移除，server 在儲存事件或 session metadata 前再移除一次。預設的 worker runtime 不受影響。另外兩項修正：資料庫升級時，新舊 worker 可能同時通過版本檢查的競爭問題，現在檢查與寫入 schema writer 位於同一個 SQLite 寫入鎖內完成；Chroma 連線取消時可能釋放新連線鎖的問題，現在每個連線持有自己的 writer-lock token，只釋放自己的鎖。社群修正（均由 @rudycelekli 提交）涵蓋 Postgres 數字設定、Gemini 重試提示、UTF-8 BOM 與 API key 陣列等。

### 重點
- server runtime 的 <private> 內容先前會送到 server 並保留在原始事件紀錄中；現在 hook 端先移除，server 儲存前再移除一次
- schema writer 的檢查與寫入移入同一個 SQLite 寫入鎖，避免兩個 worker 同時通過版本檢查
- 每個 Chroma 連線持有自己的 writer-lock token，取消時只釋放自己的鎖，避免第二個 writer 寫入同一儲存

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.36.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.36.1

A patch release that closes three issues found in review of 13.36.0, plus eight community fixes. Upgrading is recommended. 
 Privacy and data safety 
 
 &lt;private&gt; content no longer leaves the hook in server runtime ( #4721 ). In server runtime, file edits, tool inputs and outputs, and session-start prompts were sent to the server with &lt;private&gt; sections still inside, and the server kept them in the raw event record (they were removed only later, when the model prompt was built). Private sections are now removed before anything leaves the hook, and the server removes them again before it stores events or session metadata. Worker runtime (the default) was not affected. 
 Older and newer workers can no longer race on a database upgrade ( #4724 ). The check that stops an older claude-mem from opening a database a newer version upgraded now reads and records the schema writer inside one SQLite write lock, before any migration runs. Before, two workers opening the database at the same moment could both pass the check. 
 A cancelled Chroma connection can no longer release a newer connection's lock ( #4722 ). Each Chroma connection now owns its writer-lock token and releases only that lock, so a reconnect during shutdown can't leave the new sidecar unlocked and allow a second writer on the same store. Process-table parsing for the orphan sweep now has fixture tests. 
 
 Community fixes — thank you @rudycelekli 
 
 Integration ids such as constructor no longer resolve through the alias table ( #4712 ) 
 Postgres numeric settings accept only whole positive numbers; values like 5ms fall back to the default ( #4713 ) 
 Gemini retry hints too large to represent are ignored, so a key isn't parked indefinitely ( #4714 ) 
 The billing-type file is read correctly when it starts with a UTF-8 BOM ( #4715 ) 
 API-key settings arrays keep only string entries ( #4716 ) 
 A malformed part in a Gemini response no longer discards the whole answer ( #4717 ) 
 Refused connections are recognized inside wrapped errors, so recovery kicks in ( #4718 ) 
 Hook launchers honor the environment opt-out flags before starting Node or Bun ( #4719 ) 
 
 Full diff: v13.36.0...v13.36.1

</details>