---
id: inbox_73757bfa
date: 2026-11-17
source_ref: "[[00-inbox/2026-11-17/2317-claude-mem-releases-v15-21-0-cf31]]"
title: "v15.21.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.21.0
source: claude-mem-releases
published_at: 2026-11-17T20:54:27+00:00
fetched_at: 2026-11-17T23:28:32.972551+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem 15.21.0 修正與 Claude Code Code Mode 的衝突，並改進自動清除的續接方式。 **Why** 原本 claude-mem 的 auto-clear 模組掛上 tool.call hook，導致 Code Mode 拒絕啟動，即使 auto-clear 關閉也受影響。 **How** 改由 session.append 讀取工具結果；auto-clear 清除前先保存工作狀態，清除後以帶有目標與已完成任務的提示續接。 **What** 新增 Hermes Desktop 的 MCP 連接與 VS Code Copilot 整合，CLAUDE_MEM_API_AGENT_EXTRA_BODY 可附加自訂請求欄位，shell-quote 升級至 1.11.0 以排除 CVE-2026-102422。"
key_points:
  - "Code Mode（Claude Code 2.1.323 以上的實驗功能）現可在 claude-mem 啟用時正常啟動（#6278）"
  - "auto-clear 仍預設關閉，需設定 CLAUDE_MEM_AUTO_CLEAR_ENABLED=true；觸發門檻由 33% 改為 40%，續接提示改為帶入目標與最近完成的任務（#6294）"
  - "CLAUDE_MEM_API_AGENT_EXTRA_BODY 可為 api agent 的每個請求附加 JSON 欄位；例如 Qwen on vLLM 可設 chat_template_kwargs.enable_thinking 為 false 關閉推理"
tags: [claude-mem, claude-code, code-mode, auto-clear, memory-tool]
topics: [agents.coding_agents, agents.mcp, security]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.21.0

claude-mem 15.21.0 修正與 Claude Code Code Mode 的衝突，並改進自動清除的續接方式。

**Why** 原本 claude-mem 的 auto-clear 模組掛上 tool.call hook，導致 Code Mode 拒絕啟動，即使 auto-clear 關閉也受影響。

**How** 改由 session.append 讀取工具結果；auto-clear 清除前先保存工作狀態，清除後以帶有目標與已完成任務的提示續接。

**What** 新增 Hermes Desktop 的 MCP 連接與 VS Code Copilot 整合，CLAUDE_MEM_API_AGENT_EXTRA_BODY 可附加自訂請求欄位，shell-quote 升級至 1.11.0 以排除 CVE-2026-102422。

### 重點
- Code Mode（Claude Code 2.1.323 以上的實驗功能）現可在 claude-mem 啟用時正常啟動（#6278）
- auto-clear 仍預設關閉，需設定 CLAUDE_MEM_AUTO_CLEAR_ENABLED=true；觸發門檻由 33% 改為 40%，續接提示改為帶入目標與最近完成的任務（#6294）
- CLAUDE_MEM_API_AGENT_EXTRA_BODY 可為 api agent 的每個請求附加 JSON 欄位；例如 Qwen on vLLM 可設 chat_template_kwargs.enable_thinking 為 false 關閉推理

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.21.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

claude-mem no longer turns off Claude Code's Code Mode 
 
 Code Mode starts with claude-mem enabled ( #6278 , thanks @naive000 ; reported in #6209 by @nasif-naseef ). Code Mode (experimental, Claude Code 2.1.323 and later) refuses to start when a plugin's hooks module hooks tool.call . claude-mem's auto-clear mod did, so Code Mode was off for everyone with claude-mem enabled, even with auto-clear off. The mod now reads tool results through session.append instead. Auto-clear still works on every Claude Code version that runs mods (2.1.287 and later). 
 
 Auto-clear picks up where it left off 
 Auto-clear is still off unless you set CLAUDE_MEM_AUTO_CLEAR_ENABLED to true . When it is on: 
 
 It resumes with a continuation prompt instead of the bare word "continue" ( #6294 ). Before clearing, Claude saves its work state one last time, naming the list it is working from, the task it just finished and the overall goal. After /clear , auto-clear sends: You are working on " " and recently completed " ". Pick back up on our overarching goal " " from where you left off. If that save left any of the three out, it sends "continue" as before and logs why. 
 It starts at 40% of the context window instead of 33% ( #6294 ). A CLAUDE_MEM_AUTO_CLEAR_PERCENT you set in settings.json or the environment still wins. 
 
 New ways to connect 
 
 Hermes Desktop, search and save over MCP ( #6284 , thanks @krishnadobhal ; part of #5940 ). claude-mem hermes install --mcp-only --project-cwd adds claude-mem as an MCP server for Hermes One and Hermes Desktop without making it the memory provider. You get search and save when you ask for them; nothing is captured or injected on its own. claude-mem hermes uninstall removes only what it wrote and restores config.yaml byte for byte. 
 GitHub Copilot in VS Code ( #6286 , thanks @krishnadobhal ; part of #5895 ). npx claude-mem install --ide copilot-vscode writes the MCP entry that VS Code's Copilot agent reads ( ~/.copilot/mcp-config.json , the same file Copilot CLI uses). The entry now includes "tools": ["*"] . Without it, VS Code connected to claude-mem but never offered its tools to the model. No automatic capture yet. 
 ModelGo preset ( #6277 , thanks @lichloe1116-gif of the ModelGo team). The OpenAI-compatible provider has a modelgo preset for https://api.modelgo.ai/v1 . It sets no default model, so pick one your key can use. 
 
 Also new 
 
 Work-state write checks ( #6217 , thanks @vieGPT ). You can make work_state_write run a local check command before it writes to lists you choose, set in ~/.claude-mem/work-state-write-guard.json . A refused write returns HTTP 409 and nothing is saved. With no file, nothing changes. 
 CLAUDE_MEM_API_AGENT_EXTRA_BODY ( #6225 , thanks @Moep90 ; #6223 ). A JSON object added to every request the api agent sends (the My Work refresh and the corpus agent with api ). For a Qwen model on vLLM, {"chat_template_kwargs":{"enable_thinking":false}} turns reasoning off. Fields such as model , messages and max_tokens are dropped with a warning, and it is never sent to the cmem.ai gateway. 
 
 My Work refresh 
 
 Slow answers from your own model no longer fail at about 5 minutes ( #6224 , thanks @Moep90 ; #6222 ). Bun's fetch gave up on a connection that had been quiet for 5 minutes, before the api agent's 10-minute request limit applied. Now that limit is the only one. 
 Endpoints that want max_completion_tokens work ( #6242 ). When an endpoint refuses max_tokens , the api agent sends the request once more with max_completion_tokens , instead of failing every call with HTTP 400. 
 A refresh no longer stalls on an answer that was refused twice ( #6212 , thanks @Moep90 ). On the one retry for grouping, focus or review, the parts that fail the checks are dropped and the rest is saved. Before, the same batch failed on every run. 
 The build story is written in parts ( #6279 , thanks @0xABCD01 ; reported in #6226 by @Moep90 ). The story step sent every changed review in one question. That question grew past the model's context window, and every refresh after that failed. It now sends parts that fit the same question budget the other steps use. 
 Long conversations are grouped by their latest requests, not their first ten ( #6243 , thanks @Afloat16 ). 
 Commits made with git commit --message or --message= are recognized ( #6236 , thanks @Afloat16 ). 
 A commit gets a GitHub link only when the evidence names one repository ( #6237 , thanks @Afloat16 ). 
 While My Rules waits for an agent, it links the instructions for setting up an API refresh ( #6214 , thanks @liuyinchu ). 
 
 Setup, import and export 
 
 Setup finishes when your prompt history is large ( #6280 , thanks @0xABCD01 ; #6266 ; reported in #6227 by @deserteaglemj ). Setup stopped at 99% on "Finding your recent work" when the recent prompts were over the 2 MiB hosted upload limit, and every retry failed the same way. It now finishes setup on your machine and says so. The consent step also shows "Too much for one upload. Untick a tool or skip the scan." and turns off the upload button until the selection fits. 
 Large exports import ( #6261 , thanks @Afloat16 ). A file over the worker's 5 MiB request limit was refused (HTTP 413) before anything was saved. Large files are now sent in parts, sessions first, with their full content. 
 Imported observations are found by deduplication the same way live ones are, when CLAUDE_MEM_DEDUP_ENABLED is on ( #6263 , thanks @Afloat16 ). 
 claude-mem import --dry-run no longer stops on a bad worker setting, since a preview never calls the worker ( #6215 , thanks @liuyinchu ). 
 Conversations Codex Desktop imported from another agent are no longer counted as prompts typed in Codex ( #6219 , thanks @rigel905 ; #6218 ). 
 Exporting to /dev/stdout , /dev/stderr , a symlink to either, or a FIFO writes clean JSON there, and progress lines and warnings go to the other stream ( #6288 , from #6258 by @Afloat16 ). 
 
 Fixes 
 
 Windows: Claude Code loads RULES-AND-TOOLS.md again ( #6234 , thanks @QuantScorpus ). claude-mem wrote its @ import lines with backslashes. Claude Code skips those without a word, and claude-mem then also left out its other copy of the instructions, so neither reached the model. The lines now use forward slashes. An @ import shown inside a fenced code example no longer counts as the real one ( #6293 , from #6241 by @Afloat16 ). 
 claude-mem start runs the installed worker ( #6235 , thanks @ZedingZhang ; reported in #6228 by @ExactDoug ), not the copy an old shell alias points at, which can be missing its dependencies. 
 Backups keep the new snapshot after the clock is set back ( #6273 , thanks @Afloat16 ). Before, cleanup could delete the snapshot it had just reported as saved. 
 teambrain join turns on the new sync connection even when the optional sharing step fails ( #6275 , thanks @Afloat16 ). 
 Summaries with no progress in them are not stored ( #6202 , thanks @ShitK ). A summary with only a title or future plans used to be saved and announced as a success. 
 Claude Code's automatic messages no longer split a request ( #6251 , thanks @Afloat16 ). The advisor and deliverable scans treated them as new requests and lost earlier advice and file writes from the same turn. 
 Corpus builds over 250,000 observations work ( #6271 , thanks @Afloat16 ). They failed with too many SQL variables . 
 Codex: a plugin turned off with a dotted TOML key stays off ( #6239 , thanks @Afloat16 ), for example plugins."claude-mem@claude-mem-local".enabled = false . 
 The mem-search skill's frontmatter is valid YAML ( #6276 , thanks @Afloat16 ; reported in #6267 by @orbiutyt ). 
 Aider: the installer edits the config file Aider actually uses (working directory first, then git root, then home) ( #6289 , from #6230 by @Afloat16 ), and keeps quoted file paths intact in read: lists ( #6290 , from #6231 by @Afloat16 ). 
 Cursor and Grok context files keep the newer context when two refreshes overlap ( #6291 , from #6232 by @Afloat16 ). 
 Self-hosted server: a job with a revoked key or a scope violation runs once instead of three times ( #6252 ), and claude-mem server jobs retry republishes with the queue's retries and backoff ( #6253 ), thanks @HEOJUNFO . The OpenRouter provider reads at most 64 KiB when it checks an answer for a token-field error ( #6238 , thanks @Afloat16 ). One unreadable agent event no longer breaks every read of that table ( #6199 , thanks @DeryFerd ). 
 
 Security 
 
 shell-quote 1.11.0 ( #6205 , thanks @manippoudel ; reported in #6200 by @lucasbritolubro ). Version 1.9.0 is in the range of CVE-2026-102422 (critical). No code path in claude-mem reached the affected code; this takes it out of what ships. 
 adm-zip 0.6.1 and zod 4.6.7 in the plugin runtime, out of their High advisories ( #6220 , thanks @LeviReisJs ; reported in #6211 by @noumanbhatti ). 
 The Gemini API key goes in a header, not the request URL ( #6196 , thanks @DeryFerd ), so proxies and access logs don't record it. 
 Temp files get a random name and are created exclusively at the remaining atomic-write sites ( #6198 , #6193 , thanks @DeryFerd ), so a planted symlink can't redirect a write of settings or state files. 
 The self-hosted server's unauthenticated /v1/info shows state only ( #6195 , thanks @DeryFerd ): no auth mode, schema version, Redis host or driver error text. 
 CI: the postinstall allowlist check inspects every direct plugin dependency ( #6197 ), and the spawn environment check reads env blocks declared above a spawn and scans the plugin runtime ( #6194 ), thanks @DeryFerd . 
 
 For contributors 
 
 TypeScript 7.0.2 ( #6207 , thanks @krishnadobhal ; #6188 ). The scripts and tests that use the compiler API keep TypeScript 6 through an alias. 
 The import smoke test closes its SQLite readers before the final scan ( #6216 , thanks @liuyinchu ).

</details>