---
id: inbox_f95b0146
date: 2026-11-15
source_ref: "[[00-inbox/2026-11-15/2316-simon-willison-datasette-0-65-6-9a34]]"
title: "datasette 0.65.6"
url: https://simonwillison.net/2026/Nov/15/datasette-2/
source: simon-willison
published_at: 2026-11-15T23:18:17+00:00
fetched_at: 2026-11-17T23:22:14.569182+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把 Datasette 1.0a43 的一個安全修補回移植到舊版 0.65 系列。 **Why** 以自訂 route 註冊的資料庫，route 與名稱不同時，被拒絕存取的使用者仍可能繞過權限。 **How** 修正 `add_database(db, name=..., route=...)` 在 route 與 name 不同時的權限檢查，從 1.0a43 backport 過來。 **What** Datasette 0.65.6：修補此類資料庫可被無權限者從 `/<db>.db` 下載的問題。"
key_points:
  - "Datasette 0.65.6 為安全性 backport 版本，修補來自 1.0a43"
  - "漏洞條件：以 `add_database(db, name=..., route=...)` 註冊且 route 與 name 不同的資料庫"
  - "影響：被拒絕存取的 actor 仍可從 `/<db>.db` 下載該資料庫"
tags: [datasette, security-fix, backport, access-control]
topics: [security]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette 0.65.6

把 Datasette 1.0a43 的一個安全修補回移植到舊版 0.65 系列。

**Why** 以自訂 route 註冊的資料庫，route 與名稱不同時，被拒絕存取的使用者仍可能繞過權限。

**How** 修正 `add_database(db, name=..., route=...)` 在 route 與 name 不同時的權限檢查，從 1.0a43 backport 過來。

**What** Datasette 0.65.6：修補此類資料庫可被無權限者從 `/<db>.db` 下載的問題。

### 重點
- Datasette 0.65.6 為安全性 backport 版本，修補來自 1.0a43
- 漏洞條件：以 `add_database(db, name=..., route=...)` 註冊且 route 與 name 不同的資料庫
- 影響：被拒絕存取的 actor 仍可從 `/<db>.db` 下載該資料庫

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/15/datasette-2/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette 0.65.6 
 I backported a minor security fix from 1.0a43: 
 
 Fixed a security issue where a database registered using add_database(db, name=..., route=...) with a route that differs from its name could be downloaded from / .db by actors who were denied access to it. [...] 
 
 
 
 Tags: security , datasette

</details>