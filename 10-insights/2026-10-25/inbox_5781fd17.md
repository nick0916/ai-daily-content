---
id: inbox_5781fd17
date: 2026-10-25
source_ref: "[[00-inbox/2026-10-25/0249-infoq-main-php-patches-two-critical-rce-flaws-that-75fa]]"
title: "PHP Patches Two Critical RCE Flaws That Were Already Under Attack"
url: https://www.infoq.com/news/2026/10/php-critical-rce-patches/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-25T18:07:00+00:00
fetched_at: 2026-10-26T02:55:24.996498+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "PHP 緊急修補兩個可讓未經驗證者遠端執行程式碼的嚴重漏洞，且已有人在攻擊。 **Why** 漏洞在修補前就遭利用，營運團隊還得先花一整天釐清自己是否在跑 PHP、去哪取得套件、如何確認已套用。 **What** PHP 釋出 8.5.12、8.4.27、8.3.36、8.2.35 修補兩個 unauthenticated RCE 漏洞；Amazon 在修補釋出前四天就記錄到一次利用嘗試。"
key_points:
  - "修補版本：PHP 8.5.12、8.4.27、8.3.36、8.2.35"
  - "兩個嚴重漏洞皆為 unauthenticated remote code execution"
  - "Amazon 在修補發布前四天已記錄到利用嘗試；營運端難點在於盤點是否使用 PHP、取得套件與確認修補生效"
tags: [php, rce, vulnerability, patch-management]
topics: [security]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## PHP Patches Two Critical RCE Flaws That Were Already Under Attack

PHP 緊急修補兩個可讓未經驗證者遠端執行程式碼的嚴重漏洞，且已有人在攻擊。

**Why** 漏洞在修補前就遭利用，營運團隊還得先花一整天釐清自己是否在跑 PHP、去哪取得套件、如何確認已套用。

**What** PHP 釋出 8.5.12、8.4.27、8.3.36、8.2.35 修補兩個 unauthenticated RCE 漏洞；Amazon 在修補釋出前四天就記錄到一次利用嘗試。

### 重點
- 修補版本：PHP 8.5.12、8.4.27、8.3.36、8.2.35
- 兩個嚴重漏洞皆為 unauthenticated remote code execution
- Amazon 在修補發布前四天已記錄到利用嘗試；營運端難點在於盤點是否使用 PHP、取得套件與確認修補生效

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/php-critical-rce-patches/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

PHP released 8.5.12, 8.4.27, 8.3.36, and 8.2.35 to fix two critical vulnerabilities allowing unauthenticated remote code execution. Amazon recorded an exploitation attempt four days before the patches shipped, and operators spent the day working out whether they ran PHP, where to get the package, and how to tell it had landed. By Steef-Jan Wiggers

</details>