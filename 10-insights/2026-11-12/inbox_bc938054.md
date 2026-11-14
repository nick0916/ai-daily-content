---
id: inbox_bc938054
date: 2026-11-12
source_ref: "[[00-inbox/2026-11-12/0146-claude-mem-releases-v15-18-3-3149]]"
title: "v15.18.3"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.18.3
source: claude-mem-releases
published_at: 2026-11-12T18:53:05+00:00
fetched_at: 2026-11-14T01:56:16.150712+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem 修正 Codex hook 在每次更新後被關閉、session 停止儲存的問題。 **Why** Codex 以整個外掛資料夾的指紋核准 hook，每次更新都會改寫資料夾，導致七個 hook 全被停用且無提示。 **How** 安裝器改將 hook 註冊到使用者自己的 ~/.codex/hooks.json，hook 執行 PATH 上的 launcher；Codex 依 hooks.json 中的定義與位置信任，批准一次即可跨更新。 **What** 舊用戶需執行 npx claude-mem install 並選 Codex，再於互動式 Codex 執行 /hooks 批准七個 hook；另新增選用的 CLAUDE_MEM_LOCAL_API_TOKEN，預設關閉。"
key_points:
  - "Codex 核准指紋綁定整個外掛資料夾，更新即失效；修正後 hook 寫入 ~/.codex/hooks.json"
  - "舊用戶需執行 npx claude-mem install 選 Codex，並在互動式 Codex 執行 /hooks（codex exec 無法批准）"
  - "新增選用 CLAUDE_MEM_LOCAL_API_TOKEN，worker API 與 MCP HTTP 需帶 token；預設不啟用"
tags: [claude-mem, codex, hooks, api-token, plugin-updates]
topics: [agents.coding_agents, security]
importance: 3
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.18.3

claude-mem 修正 Codex hook 在每次更新後被關閉、session 停止儲存的問題。

**Why** Codex 以整個外掛資料夾的指紋核准 hook，每次更新都會改寫資料夾，導致七個 hook 全被停用且無提示。

**How** 安裝器改將 hook 註冊到使用者自己的 ~/.codex/hooks.json，hook 執行 PATH 上的 launcher；Codex 依 hooks.json 中的定義與位置信任，批准一次即可跨更新。

**What** 舊用戶需執行 npx claude-mem install 並選 Codex，再於互動式 Codex 執行 /hooks 批准七個 hook；另新增選用的 CLAUDE_MEM_LOCAL_API_TOKEN，預設關閉。

### 重點
- Codex 核准指紋綁定整個外掛資料夾，更新即失效；修正後 hook 寫入 ~/.codex/hooks.json
- 舊用戶需執行 npx claude-mem install 選 Codex，並在互動式 Codex 執行 /hooks（codex exec 無法批准）
- 新增選用 CLAUDE_MEM_LOCAL_API_TOKEN，worker API 與 MCP HTTP 需帶 token；預設不啟用

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.18.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Critical fixes 
 
 
 Codex keeps recording after claude-mem updates ( #6058 , thanks @wiesenthal ). Codex approves a hook that ships inside a plugin against a fingerprint of the plugin's whole folder. Every claude-mem update rewrites that folder, so after every update Codex switched all seven claude-mem hooks off ("plugin contents changed; hook approval required") and Codex sessions stopped being saved, with no message. The installer now registers claude-mem's Codex hooks in your own ~/.codex/hooks.json , and each hook runs the on-PATH claude-mem launcher, which finds the newest install by itself. Codex trusts a hook in hooks.json by its own definition and position, so one approval now lasts across updates. Other tools' hooks in that file are kept in place, a second install changes nothing, a hooks.json that can't be parsed is refused and left untouched, and uninstall removes only claude-mem's entries. Turning the claude-mem plugin off in Codex still stops capture. npx claude-mem doctor has a new Codex hooks row that warns when the plugin is on but its hooks are missing from hooks.json . 
 Codex users: do this once after updating. 
 
 Run npx claude-mem install and select Codex. npx claude-mem update and auto-update don't move the hooks, because older installers saved no agent selection. The installer prints Registered 7 claude-mem hooks in /hooks.json . 
 Open interactive Codex, run /hooks , and approve the seven claude-mem hooks. codex exec can't ask for approval, so do this in interactive Codex first. 
 
 After that, updates don't need a new approval. Codex asks again only when a claude-mem hook's definition changes, when claude-mem adds a hook, or when another tool's hook listed before claude-mem's is removed. 
 
 
 Improvements 
 
 Optional local API token for the worker API and MCP HTTP transport ( #6056 , thanks @kartik70 , closes #5141 ). This is for machines with more than one OS user. It is off by default and nothing changes unless you set it. Set CLAUDE_MEM_LOCAL_API_TOKEN in ~/.claude-mem/settings.json , and restart the worker and the MCP HTTP server. After that, the worker API and the MCP HTTP transport refuse any request that doesn't carry the token ( X-Claude-Mem-Token or Authorization: Bearer ), except the health checks. Open the viewer as /?token=... or /viewer?token=... . The token can only be set in the file: the settings API can't set or clear it, and it is masked when read. omp , hermes and openclaw don't send the token yet. See "Local API Token" in the configuration docs. 
 The quota fallback warning names both providers ( #6071 , thanks @bulanovk ). When the quota fallback moves memory work to another provider, the worker log now names the provider you selected and the one actually doing the work, says when the stand-in spends your Anthropic account, and names CLAUDE_MEM_QUOTA_FALLBACK_PROVIDER=off to turn it off. The default fallback is unchanged. 
 n8n workflow for saving and finding memories ( #6066 , thanks @Kirat0201 , closes #5923 ). An importable n8n workflow saves a note, checks the worker confirmed the save, then searches and retrieves it within the chosen project. It is inactive until you run it and adds no automatic capture. Setup is in the new n8n docs page. 
 
 Fixes 
 
 smart-read (thanks @Afloat16 ):
 
 Getters and setters with the same name now unfold separately ( #6060 ). 
 Markdown heading levels are kept as written ( #6064 ). 
 Pascal routine bodies are found even when the declaration's case differs ( #6063 ). 
 Python docstrings keep their statement ranges ( #6057 ). 
 Captured source is parsed in native batches ( #6059 ). 
 
 
 The observation parser accepts XML whitespace before tag delimiters ( #6065 , thanks @Afloat16 ). 
 Globstar exclusions now also apply to paths that contain line terminators ( #6061 , thanks @Afloat16 ). 
 Cost report: repository-wide wins are looked up only when asked for explicitly ( #6081 ), and named steering relays are recognized ( #6082 ) (thanks @Kirat0201 ). 
 The installation guide lists the real Node.js and Bun minimums ( #6076 , thanks @DeryFerd ). 
 
 CI and tests 
 
 The publish and ods-native jobs pin Bun instead of using the newest release ( #6075 ), and CI now runs the hook-io and spawn-env checks ( #6074 ) (thanks @DeryFerd ). 
 Windows test fixes: temp-dir cleanup retries, per-platform memory paths, and paused-pipe hook cases skipped where Node can't run them ( #6072 , #6073 , thanks @DeryFerd ). The sync-hub test stub is typed so the package typechecks ( #6077 , thanks @DeryFerd ). 
 The #4689 env-fallback test no longer depends on a real Claude login on the machine ( #6068 , thanks @bulanovk ).

</details>