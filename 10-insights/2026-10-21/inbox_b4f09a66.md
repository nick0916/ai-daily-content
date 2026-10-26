---
id: inbox_b4f09a66
date: 2026-10-21
source_ref: "[[00-inbox/2026-10-21/2337-ruflo-releases-v3-59-6-memory-export-path-support-c7fa]]"
title: "v3.59.6 — memory export --path support"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.59.6
source: ruflo-releases
published_at: 2026-10-21T04:58:47+00:00
fetched_at: 2026-10-21T23:47:04.680063+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 memory export 可以指定單一儲存庫來匯出，不再只能匯出預設庫。 **Why** memory export 是 memory 子命令中唯一沒有 --path 的，無法從 CLI 匯出特定快照（如 .swarm/agentdb-memory.db 或備份檔）。 **How** 指定 --path 或 dbPath 時改為單純讀取該庫，不初始化也不合併預設庫；未指定時行為不變。 **What** Ruflo v3.59.6（@claude-flow/cli 3.59.6，修正 #3196，PR #4341），latest、alpha、v3alpha 三個 dist-tags 已在 registry 上驗證。"
key_points:
  - "補上 memory export --path，修正 #3196，原為唯一缺 --path 的主要 memory 子命令"
  - "指定 --path 或 dbPath 時為單一儲存庫讀取，不初始化也不合併預設庫；未指定時行為不變"
  - "發布 @claude-flow/cli、claude-flow、ruflo 皆為 3.59.6"
tags: [ruflo, memory-export, cli, agentdb, release-notes]
topics: [agents.frameworks, engineering.architecture]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.59.6 — memory export --path support

讓 memory export 可以指定單一儲存庫來匯出，不再只能匯出預設庫。

**Why** memory export 是 memory 子命令中唯一沒有 --path 的，無法從 CLI 匯出特定快照（如 .swarm/agentdb-memory.db 或備份檔）。

**How** 指定 --path 或 dbPath 時改為單純讀取該庫，不初始化也不合併預設庫；未指定時行為不變。

**What** Ruflo v3.59.6（@claude-flow/cli 3.59.6，修正 #3196，PR #4341），latest、alpha、v3alpha 三個 dist-tags 已在 registry 上驗證。

### 重點
- 補上 memory export --path，修正 #3196，原為唯一缺 --path 的主要 memory 子命令
- 指定 --path 或 dbPath 時為單一儲存庫讀取，不初始化也不合併預設庫；未指定時行為不變
- 發布 @claude-flow/cli、claude-flow、ruflo 皆為 3.59.6

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.59.6)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Fixes 
 
 memory export can now target an explicit store ( #4341 , fixes #3196 ). It was the only primary 
memory subcommand without --path , so a specific snapshot ( .swarm/agentdb-memory.db , an 
archive, a restored backup) could not be exported from the CLI. An explicit --path / dbPath 
is now a true single-store read — it does not initialize or merge the sibling default store. 
Default (no --path ) behavior is unchanged. 
 
 Published 
 
 @claude-flow/cli@3.59.6 , claude-flow@3.59.6 , ruflo@3.59.6 — latest / alpha / v3alpha 
dist-tags all verified matching on the live registry.

</details>