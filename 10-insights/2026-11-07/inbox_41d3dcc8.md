---
id: inbox_41d3dcc8
date: 2026-11-07
source_ref: "[[00-inbox/2026-11-07/0149-claude-mem-releases-v15-11-1-e13f]]"
title: "v15.11.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.11.1
source: claude-mem-releases
published_at: 2026-11-07T09:51:54+00:00
fetched_at: 2026-11-08T01:56:28.510055+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v15.11.1 修復 cmem.ai Pro 登入 500 錯誤，並調整 Stop hook 與 SessionStart context 的處理。 **Why** 全新安裝的外掛缺少 better-auth，auth 資料表也從未建立，導致每次登入都回 500。 **How** 外掛改為內建 better-auth 與 @better-auth/api-key，並在首次需要時建立 auth 資料表。 **What** 同版本中，Stop hook 改為直接讀取 last_assistant_message 而不再解析 transcript；SessionStart context 先預留 OAuth 提示與 gateway 通知的字元空間，確保總長低於 Claude Code 的 10,000 字元上限。"
key_points:
  - "修復 Pro 登入 500：外掛內建 better-auth 與 @better-auth/api-key，首次需要時建立 auth 資料表"
  - "先預留固定提示的字元空間，再把可變內容 fit 進剩餘空間，使 SessionStart context 低於 10,000 字元"
  - "Stop hook 改讀 last_assistant_message，跳過 transcript 讀取"
tags: [claude-mem, bugfix, session-context, hooks, release-notes]
topics: [agents.coding_agents]
importance: 2
novelty: 1
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.11.1

claude-mem v15.11.1 修復 cmem.ai Pro 登入 500 錯誤，並調整 Stop hook 與 SessionStart context 的處理。

**Why** 全新安裝的外掛缺少 better-auth，auth 資料表也從未建立，導致每次登入都回 500。

**How** 外掛改為內建 better-auth 與 @better-auth/api-key，並在首次需要時建立 auth 資料表。

**What** 同版本中，Stop hook 改為直接讀取 last_assistant_message 而不再解析 transcript；SessionStart context 先預留 OAuth 提示與 gateway 通知的字元空間，確保總長低於 Claude Code 的 10,000 字元上限。

### 重點
- 修復 Pro 登入 500：外掛內建 better-auth 與 @better-auth/api-key，首次需要時建立 auth 資料表
- 先預留固定提示的字元空間，再把可變內容 fit 進剩餘空間，使 SessionStart context 低於 10,000 字元
- Stop hook 改讀 last_assistant_message，跳過 transcript 讀取

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.11.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Pro sign-in works again 
 Signing in to cmem.ai Pro from the plugin returned a 500 error on every fresh plugin install. The plugin's install did not include better-auth , and its tables were never created. The plugin now ships better-auth and @better-auth/api-key as dependencies and creates the auth tables the first time they are needed ( #5455 , thanks @0xABCD01 ). 
 Fixes 
 
 Worker: when a run pauses after a transport, rate-limit or similar abort, it now releases its claims, so the paused session no longer holds pending work that can never expire ( #5457 , thanks @akashpandey ). 
 Worker: an over-budget condense reply is clamped to the budget instead of being thrown away ( #5452 , thanks @xunguangzlj-cloud ). 
 Worker: retry-without-reasoning now recognizes OpenCode Go's "cannot be represented" error wording ( #5439 , thanks @akashpandey ). 
 Hooks: the Stop hook reads Claude Code's last_assistant_message directly and skips reading the transcript ( #5449 , thanks @xunguangzlj-cloud ). 
 Context: the OAuth hint and gateway fallback notice are reserved before the context is fitted, so SessionStart context stays under Claude Code's 10,000-character limit ( #5441 , thanks @liuyinchu ). 
 Codex: stale app-server child processes are recycled on the auth recovery probe ( #5438 , thanks @akashpandey ). 
 Installer: the Goose YAML config is written atomically, so an interrupted install or uninstall can no longer leave a truncated config.yaml ( #5442 , thanks @DeryFerd ). 
 Tests: the sync matrix waits for the page body before reading it, fixing a browser readiness race ( #5448 ). 
 
 Also in this release 
 
 My Work: the scheduled refresh check interval is now a setting ( #5437 , thanks @weirui828 ). 
 Docs: one story across the README and docs: your coding agent forgets between sessions, Claude-Mem remembers ( #5447 ). 
 Docs: README translations keep fenced code examples and single-quoted links intact ( #5458 , thanks @Afloat16 ). 
 
 Full changelog: v15.11.0...v15.11.1

</details>