---
id: inbox_04fdbf0b
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-ruflo-releases-v3-59-7-policy-lock-hardening-session-li-4a69]]"
title: "v3.59.7 — policy lock hardening + session_list total fix"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.59.7
source: ruflo-releases
published_at: 2026-10-21T07:04:22+00:00
fetched_at: 2026-10-21T23:46:35.272045+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 policy lock 遇到路徑錯誤時快速失敗，並修正 session list 的 total 計數錯誤。 **Why** acquireLock() 把所有 openSync() 錯誤都當成鎖競爭，權限錯誤或路徑被佔用時仍會等滿 5 秒，且每次 MCP 工具呼叫都會發生。 **How** lock 檔以 O_NOFOLLOW 建立以防止透過符號連結建立，非競爭錯誤立即拋出，非一般檔案則被拒絕而非當成可回收的鎖。 **What** ruflo session list 原本在套用 limit 後才計算 total，例如存了 30 筆仍顯示 10 of 10；與 #4324 的 task_list 修正同類（#4343、#4344）。"
key_points:
  - "acquireLock() 把所有 openSync() 錯誤視為鎖競爭，導致路徑錯誤也等滿 5 秒才報 policy-state-lock-timeout"
  - "改用 O_NOFOLLOW 建立 lock 檔，非競爭錯誤立即拋出，非一般檔案不再被當成可回收的鎖"
  - "session list 的 total 改為計算所有已存 session，而非套用 limit 後的筆數"
tags: [ruflo, file-locking, o-nofollow, mcp, session-management]
topics: [engineering.architecture, security]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.59.7 — policy lock hardening + session_list total fix

讓 policy lock 遇到路徑錯誤時快速失敗，並修正 session list 的 total 計數錯誤。

**Why** acquireLock() 把所有 openSync() 錯誤都當成鎖競爭，權限錯誤或路徑被佔用時仍會等滿 5 秒，且每次 MCP 工具呼叫都會發生。

**How** lock 檔以 O_NOFOLLOW 建立以防止透過符號連結建立，非競爭錯誤立即拋出，非一般檔案則被拒絕而非當成可回收的鎖。

**What** ruflo session list 原本在套用 limit 後才計算 total，例如存了 30 筆仍顯示 10 of 10；與 #4324 的 task_list 修正同類（#4343、#4344）。

### 重點
- acquireLock() 把所有 openSync() 錯誤視為鎖競爭，導致路徑錯誤也等滿 5 秒才報 policy-state-lock-timeout
- 改用 O_NOFOLLOW 建立 lock 檔，非競爭錯誤立即拋出，非一般檔案不再被當成可回收的鎖
- session list 的 total 改為計算所有已存 session，而非套用 limit 後的筆數

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.59.7)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Fixes 
 
 Policy lock fails fast on path errors instead of timing out ( #4343 ). acquireLock() treated 
every openSync() error as lock contention, so a permission error, missing parent directory, or 
a directory/symlink/FIFO planted at the lock path waited the full 5s lock budget on every MCP 
tool call before surfacing a misleading policy-state-lock-timeout . The lock is now created 
with O_NOFOLLOW (where supported) to close the create-through-a-symlink path; non-contention 
errors now surface immediately, and a non-regular file planted at the lock path is rejected 
rather than treated as a reclaimable lock. 
 session_list now reports every saved session in total , not just the returned page ( #4344 ). 
 ruflo session list previously printed e.g. "Showing 10 of 10 sessions" even when 30 sessions 
were saved, since total was computed after the limit was applied. Same pattern already 
fixed for task_list in #4324 . 
 
 Published 
 
 @claude-flow/cli@3.59.7 , claude-flow@3.59.7 , ruflo@3.59.7 — latest / alpha / v3alpha 
dist-tags all verified matching on the live registry.

</details>