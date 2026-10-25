---
id: inbox_bb793f9b
date: 2026-10-24
source_ref: "[[00-inbox/2026-10-24/0101-gitnexus-releases-rc-11a49a15c6befbe4d5de1cebe74b5456aeb44-1388]]"
title: "rc/11a49a15c6befbe4d5de1cebe74b5456aeb44b99: fix(cli): reap embedding sidecar after query (#3693)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F11a49a15c6befbe4d5de1cebe74b5456aeb44b99
source: gitnexus-releases
published_at: 2026-10-24T08:58:58+00:00
fetched_at: 2026-10-25T01:13:41.427962+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "CLI 查詢後回收 embedding sidecar 行程。 **What** 包含三個 commit：查詢後回收 sidecar、清理前先排空 hybrid search、群組查詢後同樣回收 sidecar（PR #3693）。"
key_points:
  - "修正 CLI 查詢後 embedding sidecar 未被回收的問題"
  - "清理前先排空 hybrid search"
  - "群組查詢（group query）後同樣回收 sidecar"
tags: [gitnexus, cli, embeddings, hybrid-search, bugfix]
topics: [engineering.rag]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/11a49a15c6befbe4d5de1cebe74b5456aeb44b99: fix(cli): reap embedding sidecar after query (#3693)

CLI 查詢後回收 embedding sidecar 行程。 **What** 包含三個 commit：查詢後回收 sidecar、清理前先排空 hybrid search、群組查詢後同樣回收 sidecar（PR #3693）。

### 重點
- 修正 CLI 查詢後 embedding sidecar 未被回收的問題
- 清理前先排空 hybrid search
- 群組查詢（group query）後同樣回收 sidecar

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F11a49a15c6befbe4d5de1cebe74b5456aeb44b99)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(cli): reap embedding sidecar after query 
 
 
 fix(cli): drain hybrid search before cleanup 
 
 
 fix(cli): reap sidecar after group query 
 
 
 
 Co-authored-by: Gergő Magyar gergomagyar@icloud.com

</details>