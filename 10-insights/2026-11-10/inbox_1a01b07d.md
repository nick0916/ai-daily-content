---
id: inbox_1a01b07d
date: 2026-11-10
source_ref: "[[00-inbox/.../inbox_1a01b07d]]"
title: "v15.15.2"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.15.2
source: claude-mem-releases
published_at: 2026-11-10T19:30:00+00:00
fetched_at: 2026-11-10T23:36:56.558285+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem 修正升級後 Antigravity 拒絕所有工具呼叫的問題，並在外送前遮罩敏感資訊。 **Why** 舊版殘留的 PreToolUse hook 讓 agy 每次工具呼叫都被拒絕；未遮罩的憑證可能經 HTTP 外送。 **How** 安裝程式自動找出並遷移過期的 hooks.json；server capture 先套用 redactor 再送出。 **What** v15.15.2（2026-11-10）修正 #5670，並修補 #5774 的遮罩缺口；doctor 新增 macOS launcher 簽章檢查；另新增土耳其文 My Work 頁面。"
key_points:
  - "升級後殘留的 hook 讓 agy 拒絕所有工具呼叫；安裝程式現在自動遷移 ~/.gemini/config/hooks.json"
  - "CLAUDE_MEM_REDACT_ENABLED=true 時，server capture 在資料離開本機前套用遮罩（#5774）"
  - "doctor 新增 macOS launcher 簽章檢查；Bun 低於 1.4.1 時提示先執行 bun upgrade"
tags: [claude-mem, antigravity, redaction, hooks, macos]
topics: [agents.frameworks, security]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.15.2

claude-mem 修正升級後 Antigravity 拒絕所有工具呼叫的問題，並在外送前遮罩敏感資訊。

**Why** 舊版殘留的 PreToolUse hook 讓 agy 每次工具呼叫都被拒絕；未遮罩的憑證可能經 HTTP 外送。

**How** 安裝程式自動找出並遷移過期的 hooks.json；server capture 先套用 redactor 再送出。

**What** v15.15.2（2026-11-10）修正 #5670，並修補 #5774 的遮罩缺口；doctor 新增 macOS launcher 簽章檢查；另新增土耳其文 My Work 頁面。

### 重點
- 升級後殘留的 hook 讓 agy 拒絕所有工具呼叫；安裝程式現在自動遷移 ~/.gemini/config/hooks.json
- CLAUDE_MEM_REDACT_ENABLED=true 時，server capture 在資料離開本機前套用遮罩（#5774）
- doctor 新增 macOS launcher 簽章檢查；Bun 低於 1.4.1 時提示先執行 bun upgrade

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.15.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v15.15.2

Critical fix 
 
 Antigravity no longer denies every tool call after an upgrade from 14.x ( #5670 ): an in-place upgrade from an older install left a PreToolUse hook (and a PreInvocation context hook) in ~/.gemini/config/hooks.json . agy kept firing it before every tool call, the current adapter answered with no decision, and agy denied every call until you re-ran install. Now the Antigravity installer finds those stale entries and migrates the file in place with the same merge install performs. It writes only when something is stale, never throws, and leaves a corrupt file untouched. The worker runs this heal on startup and on Antigravity hook calls, so updating is enough. Thanks to @jiezhiyong for the report ( #5665 ) and to @0xABCD01 for the fix. 
 
 Fixes 
 
 Antigravity: a model call that only called tools no longer becomes an "AntigravityProvider returned Completed" memory. Only a step with a real reply is recorded, so the observer stops writing false memories like "stuck in a retry loop" ( #5667 , thanks @ryrenz ; reported in #5665 by @jiezhiyong ). 
 Redaction: with CLAUDE_MEM_REDACT_ENABLED=true , server capture now applies the configured redactor before the capture leaves your machine, and to session and event metadata before it is stored. Before, an untagged credential in an opening prompt or tool payload could be sent over HTTP unredacted ( #5774 , thanks @Afloat16 ). 
 Doctor: claude-mem doctor now checks the macOS launcher's code signature. A launcher macOS would kill gets a clear hint ( bun upgrade first when Bun is below 1.4.1, otherwise npx claude-mem install rebuilds it); a launcher that still runs only warns ( #5657 , thanks @Kirat0201 ). 
 cmem-pro 0.2.1: the Cowork plugin version is bumped so installed copies pick up the redaction and failed-capture fixes made after 0.2.0. 
 
 New 
 
 Turkish My Work: the My Work page is now available in Turkish ( #5656 , thanks @Kirat0201 ). 
 
 Full changelog: v15.15.1...v15.15.2

</details>