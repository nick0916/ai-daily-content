---
id: inbox_236c8dba
date: 2026-10-13
source_ref: "[[00-inbox/.../inbox_236c8dba]]"
title: "v13.39.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.39.0
source: claude-mem-releases
published_at: 2026-10-13T21:31:41+00:00
fetched_at: 2026-10-18T03:35:42.220792+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.39.0 修正 Codex 壓縮（compaction）後子代理（subagent thread）遺失記憶時間軸的問題。Codex 壓縮根 thread 時，會透過 SessionStart（source 為 compact）補回記憶時間軸，但 Codex 不會對子 thread 送出 SessionStart，因此被壓縮的子 agent 會失去記憶並繼續運作。本版新增 PostCompact hook，以 session_id 加 agent_id 為鍵標記被壓縮的 thread。該 thread 的下一次 PostToolUse 會照常記錄觀察、消耗標記，並把時間軸以 additionalContext 回傳一次。SessionStart 會清除標記，避免根 thread 重複收到時間軸。共用的 session-marker 檔案處理現在同時支援 Codex 壓縮閘門與 Kimi context 閘門。PR 編號為 #4733。"
key_points:
  - "新增 PostCompact hook，以 session_id + agent_id 標記被壓縮的子 thread，下一次 PostToolUse 回傳時間軸一次後消耗標記"
  - "SessionStart（source=compact）會清除標記，避免根 thread 重複注入時間軸"
  - "根因：Codex 不對子 thread 發送 SessionStart，導致壓縮後的子 agent 靜默失去記憶（PR #4733）"
tags: [codex, memory-timeline, compaction, subagents, hooks]
topics: [agents.coding_agents, engineering.architecture]
importance: 3
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.39.0

claude-mem v13.39.0 修正 Codex 壓縮（compaction）後子代理（subagent thread）遺失記憶時間軸的問題。Codex 壓縮根 thread 時，會透過 SessionStart（source 為 compact）補回記憶時間軸，但 Codex 不會對子 thread 送出 SessionStart，因此被壓縮的子 agent 會失去記憶並繼續運作。本版新增 PostCompact hook，以 session_id 加 agent_id 為鍵標記被壓縮的 thread。該 thread 的下一次 PostToolUse 會照常記錄觀察、消耗標記，並把時間軸以 additionalContext 回傳一次。SessionStart 會清除標記，避免根 thread 重複收到時間軸。共用的 session-marker 檔案處理現在同時支援 Codex 壓縮閘門與 Kimi context 閘門。PR 編號為 #4733。

### 重點
- 新增 PostCompact hook，以 session_id + agent_id 標記被壓縮的子 thread，下一次 PostToolUse 回傳時間軸一次後消耗標記
- SessionStart（source=compact）會清除標記，避免根 thread 重複注入時間軸
- 根因：Codex 不對子 thread 發送 SessionStart，導致壓縮後的子 agent 靜默失去記憶（PR #4733）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.39.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.39.0

Codex: memory timeline returns to subagent threads after compaction 
 When Codex compacts a thread, the memory timeline drops out of its history. The root thread already got it back through SessionStart (source compact ). Codex never sends SessionStart to subagent threads, though, so a subagent that compacted kept working without its memory. 
 
 A new PostCompact hook marks the compacted thread, keyed by session_id plus agent_id . 
 That thread's next PostToolUse records the observation as usual, consumes the marker, and returns the timeline once as additionalContext . 
 SessionStart clears the marker, so the root thread never gets the timeline twice. 
 Shared session-marker file handling now backs both the Codex compaction gate and the Kimi context gate. 
 
 PR: #4733

</details>