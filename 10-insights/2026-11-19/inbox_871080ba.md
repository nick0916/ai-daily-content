---
id: inbox_871080ba
date: 2026-11-19
source_ref: "[[00-inbox/2026-11-19/0105-simon-willison-postgresql-19-released-36f6]]"
title: "PostgreSQL 19 Released"
url: https://simonwillison.net/2026/Nov/19/postgresql-19/
source: simon-willison
published_at: 2026-11-19T20:43:57+00:00
fetched_at: 2026-11-20T01:11:01.495870+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "PostgreSQL 19 讓你在從備援節點讀資料時，也能讀到剛寫進主節點的內容。 **Why** 把讀取導向 standby 的應用程式，常讀不到剛在 primary 寫入的資料，因為備援有複寫延遲。 **How** 寫入後用 `pg_current_wal_insert_lsn()` 取得 LSN 並存起來（例如放進簽章 cookie），下次請求時在備援先執行 `WAIT FOR LSN '...'`，等 WAL 重放到該位置再查詢；可選擇加 TIMEOUT，逾時未追上會報錯。 **What** PostgreSQL 19 新增 `WAIT FOR LSN` 指令提供 read-your-writes 一致性。本次發布比往年九月晚了約兩個月，作者歸因於團隊需處理大量 AI 回報的漏洞。作者指出此模式最早見於 Wikipedia 的 MediaWiki，其以 MySQL 的 `WAIT_FOR_EXECUTED_GTID_SET()` 自行實作。"
key_points:
  - "寫入後用 `SELECT pg_current_wal_insert_lsn();` 取得 LSN，之後在備援執行 `WAIT FOR LSN '0/0306EE20' WITH (TIMEOUT '0.1s');` 再讀取"
  - "TIMEOUT 為選用；備援在時限內沒追上就回傳錯誤"
  - "PostgreSQL 19 比往年九月的發布時程晚約兩個月，原因是處理 AI 回報的漏洞"
tags: [postgresql, replication, read-your-writes, wal, scaling]
topics: [engineering.architecture, security]
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## PostgreSQL 19 Released

PostgreSQL 19 讓你在從備援節點讀資料時，也能讀到剛寫進主節點的內容。

**Why** 把讀取導向 standby 的應用程式，常讀不到剛在 primary 寫入的資料，因為備援有複寫延遲。

**How** 寫入後用 `pg_current_wal_insert_lsn()` 取得 LSN 並存起來（例如放進簽章 cookie），下次請求時在備援先執行 `WAIT FOR LSN '...'`，等 WAL 重放到該位置再查詢；可選擇加 TIMEOUT，逾時未追上會報錯。

**What** PostgreSQL 19 新增 `WAIT FOR LSN` 指令提供 read-your-writes 一致性。本次發布比往年九月晚了約兩個月，作者歸因於團隊需處理大量 AI 回報的漏洞。作者指出此模式最早見於 Wikipedia 的 MediaWiki，其以 MySQL 的 `WAIT_FOR_EXECUTED_GTID_SET()` 自行實作。

### 重點
- 寫入後用 `SELECT pg_current_wal_insert_lsn();` 取得 LSN，之後在備援執行 `WAIT FOR LSN '0/0306EE20' WITH (TIMEOUT '0.1s');` 再讀取
- TIMEOUT 為選用；備援在時限內沒追上就回傳錯誤
- PostgreSQL 19 比往年九月的發布時程晚約兩個月，原因是處理 AI 回報的漏洞

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/19/postgresql-19/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

PostgreSQL 19 Released 
Most years PostgreSQL ships a new release in September, but this year's release came two months later thanks mainly to the flurry of issues that the PostgreSQL team needed to address as part of the ongoing AI-reported vulnerability apocalypse. 
 This release was definitely worth the wait. My favorite new feature is this one: 
 
 For applications that send reads to standbys, PostgreSQL 19 adds "read-your-writes" consistency with the new WAIT FOR LSN command. A session on a standby can use WAIT FOR LSN to wait until the standby has replayed the write-ahead log (WAL) up to a specific log sequence number (LSN) before running a query, so the application can read data it just wrote on the primary. 
 
 In practice, that looks like this: 
 UPDATE movie SET genre = 'Dramatic' WHERE genre = 'Drama';
SELECT pg_current_wal_insert_lsn();
 
 That returns a value like 0/0306EE20 . Store that somewhere (a signed cookie would work) such that on a subsequent request your application can do: 
 WAIT FOR LSN '0/0306EE20' WITH (TIMEOUT '0.1s');
SELECT * FROM movie WHERE genre = 'Drama';
 
 The timeout is optional - if you provide one you'll get an error if the replica you are talking to doesn't catch up within the specified time. 
 I first encountered this pattern in Wikipedia , which has a hand-rolled version of this built against MySQL replication: 
 
 In addition to this, MediaWiki attempts to ensure that the user sees events occurring on the wiki in chronological order. A few seconds of lag can be tolerated, as long as the user sees a consistent picture from subsequent requests. This is done by saving the primary binlog position in the session, and then at the start of each request, waiting for the replica to catch up to that position before doing any reads from it. 
 
 Here's the relevant MediaWiki code , which these days uses MySQL's WAIT_FOR_EXECUTED_GTID_SET() function and falls back to SOURCE_POS_WAIT() .

 Via Lobste.rs 

 Tags: mysql , postgresql , replication , scaling , wikipedia , ai-security-research

</details>