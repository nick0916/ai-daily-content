---
id: inbox_385a064c
date: 2026-10-06
source_ref: "[[00-inbox/2026-10-06/0256-claude-code-releases-v2-1-291-9913]]"
title: "v2.1.291"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.291
source: claude-code-releases
published_at: 2026-10-06T03:55:19+00:00
fetched_at: 2026-10-18T02:59:37.251771+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.291 為小幅修正版本，處理兩項 regression。其一，修正 2.1.290 中雲端 session 可能遺失對權限提示回覆的問題。其二，修正 2.1.288 中退出時 session 最後幾則訊息可能遺失的問題。使用雲端 session 或在意 session 紀錄完整性的使用者建議升級。"
key_points:
  - "修正 2.1.290 的 regression：雲端 session 可能丟失權限提示的回覆"
  - "修正 2.1.288 的 regression：退出時 session 最後幾則訊息可能遺失"
tags: [claude-code, regression-fix, cloud-sessions, release-notes]
topics: [agents.coding_agents]
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.291

Claude Code v2.1.291 為小幅修正版本，處理兩項 regression。其一，修正 2.1.290 中雲端 session 可能遺失對權限提示回覆的問題。其二，修正 2.1.288 中退出時 session 最後幾則訊息可能遺失的問題。使用雲端 session 或在意 session 紀錄完整性的使用者建議升級。

### 重點
- 修正 2.1.290 的 regression：雲端 session 可能丟失權限提示的回覆
- 修正 2.1.288 的 regression：退出時 session 最後幾則訊息可能遺失

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.291)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Fixed a regression in 2.1.290 where cloud sessions could drop answers to permission prompts 
 Fixed a regression in 2.1.288 where the last messages of a session could be lost when quitting

</details>