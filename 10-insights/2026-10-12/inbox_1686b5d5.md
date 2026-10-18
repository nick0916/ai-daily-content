---
id: inbox_1686b5d5
date: 2026-10-12
source_ref: "[[00-inbox/2026-10-12/0256-ruflo-releases-v3-56-9-policy-envelope-metering-codex-m-04bc]]"
title: "v3.56.9 — policy envelope metering, Codex MCP backend retired, CLI parser fixes, ruflo-mods guards"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.56.9
source: ruflo-releases
published_at: 2026-10-12T21:14:45+00:00
fetched_at: 2026-10-18T03:20:23.504890+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo 發布 v3.56.9 patch 版本，涵蓋 @claude-flow/cli、claude-flow、ruflo 三個套件，並先獨立發布 @claude-flow/security 3.0.5 與 @claude-flow/codex 3.0.5，CLI 以精確版本 pin 住它們以及 shared 3.0.5、cli-core 3.7.2。Policy envelope（security 3.0.5）改為明確的 envelope 上限必須搭配計量（metering），未計量的 worker 上限維持 opt-in。Codex MCP backend 不再啟動 `@openai/codex mcp-server`（現行 Codex CLI 已移除該指令），改為無啟動卡頓地退役（#3522，由 #3509 回報）。另有一批 CLI parser、retry、rate-limit、monitoring 與 config 修正（#4107，涵蓋 #4000–#4017），以及 `analyze diff` 結果顯示修正（#4102）。ruflo-mods 的 root-delete guard 補上先前漏掉的 brace、nesting 與 fork-bomb 形式，screen .env 檢查也已修正，`init` 產生的 hook 會帶入變更（簽署過的 hook-handler.cjs 於 #4096 重新簽署）。Console 外掛方面，worktree 移除不再執行 fsmonitor 或 hooks 且保留 untracked 檔案（#4092），圖片在 Claude Code Desktop 改以 SVG 繪製（#4112）。CI 現在會跑完 v3 root-suite 全部測試檔，且不再把崩潰的執行視為通過（#4099，不屬於套件內容）。主要影響使用 ruflo 搭配 Claude Code / Codex 的使用者，尤其是依賴 Codex MCP backend 或 ruflo-mods 安全 guard 的人。"
key_points:
  - "Codex MCP backend 不再啟動 `@openai/codex mcp-server`（現行 Codex CLI 已移除），於 codex 3.0.5 退役且無啟動卡頓（#3522）"
  - "ruflo-mods root-delete guard 補上 brace、nesting、fork-bomb 形式漏洞；signed helper hook-handler.cjs 於 #4096 重新簽署"
  - "CI 修正：執行全部 v3 root-suite 測試檔，且崩潰的 run 不再被當成通過（#4099）"
tags: [ruflo, codex-mcp, policy-envelope, cli-fixes, security-guard]
topics: [agents.coding_agents, agents.mcp, security]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.56.9 — policy envelope metering, Codex MCP backend retired, CLI parser fixes, ruflo-mods guards

Ruflo 發布 v3.56.9 patch 版本，涵蓋 @claude-flow/cli、claude-flow、ruflo 三個套件，並先獨立發布 @claude-flow/security 3.0.5 與 @claude-flow/codex 3.0.5，CLI 以精確版本 pin 住它們以及 shared 3.0.5、cli-core 3.7.2。Policy envelope（security 3.0.5）改為明確的 envelope 上限必須搭配計量（metering），未計量的 worker 上限維持 opt-in。Codex MCP backend 不再啟動 `@openai/codex mcp-server`（現行 Codex CLI 已移除該指令），改為無啟動卡頓地退役（#3522，由 #3509 回報）。另有一批 CLI parser、retry、rate-limit、monitoring 與 config 修正（#4107，涵蓋 #4000–#4017），以及 `analyze diff` 結果顯示修正（#4102）。ruflo-mods 的 root-delete guard 補上先前漏掉的 brace、nesting 與 fork-bomb 形式，screen .env 檢查也已修正，`init` 產生的 hook 會帶入變更（簽署過的 hook-handler.cjs 於 #4096 重新簽署）。Console 外掛方面，worktree 移除不再執行 fsmonitor 或 hooks 且保留 untracked 檔案（#4092），圖片在 Claude Code Desktop 改以 SVG 繪製（#4112）。CI 現在會跑完 v3 root-suite 全部測試檔，且不再把崩潰的執行視為通過（#4099，不屬於套件內容）。主要影響使用 ruflo 搭配 Claude Code / Codex 的使用者，尤其是依賴 Codex MCP backend 或 ruflo-mods 安全 guard 的人。

### 重點
- Codex MCP backend 不再啟動 `@openai/codex mcp-server`（現行 Codex CLI 已移除），於 codex 3.0.5 退役且無啟動卡頓（#3522）
- ruflo-mods root-delete guard 補上 brace、nesting、fork-bomb 形式漏洞；signed helper hook-handler.cjs 於 #4096 重新簽署
- CI 修正：執行全部 v3 root-suite 測試檔，且崩潰的 run 不再被當成通過（#4099）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.56.9)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release: @claude-flow/cli , claude-flow , ruflo 3.56.9 (latest, alpha, v3alpha). The bundled leaves @claude-flow/security 3.0.5 and @claude-flow/codex 3.0.5 were published standalone first, and the CLI pins them, @claude-flow/shared 3.0.5 and @claude-flow/cli-core 3.7.2 exactly. Signed helpers changed ( hook-handler.cjs , re-signed in #4096 ). 
 Fixed 
 
 Policy envelope ( security 3.0.5): explicit envelope ceilings require metering, and unmetered worker ceilings stay opt-in ( #3503 , @rudycelekli ). 
 Codex MCP backend ( codex 3.0.5 and the ruflo wrapper bridge): the opt-in codex backend no longer launches @openai/codex mcp-server , which current Codex CLI dropped, and is retired without a startup stall ( #3522 , @rudycelekli ; reported in #3509 by @pacphi ). 
 CLI parser, retry, rate-limit, monitoring and config fixes : a reviewed batch ( #4107 , covering #4000 - #4017 , @rudycelekli and others). 
 analyze diff renders the analyze_diff result shape ( #4102 , fixes #4101 , @z4forzubair ). 
 shared 3.0.5 and cli-core 3.7.2: narrow-column truncation, rate-window retry times, structured network error codes ( #4014 , #4015 , #4018 , @rudycelekli ). 
 ruflo-mods guards ( #4096 , @proffesor-for-testing ): the root-delete guard no longer misses brace, nesting and fork-bomb forms, the screen .env check is fixed, and init -generated hooks carry the changes. 
 Console (marketplace plugin; its tui.mjs is bundled into the CLI): worktree removal runs no fsmonitor or hooks and keeps untracked files ( #4092 ), console_state reports an expired confirm card ( #4067 ), pictures draw as SVG on Claude Code Desktop ( #4112 ), all by @proffesor-for-testing ; the Skills page pins its skills CLI ( #4113 , @martinvlad ). 
 ruflo-cost-tracker logs Stop-hook telemetry write failures instead of discarding them ( #3227 , @nicholas-ruest ; marketplace plugin). 
 CI runs every v3 root-suite test file and no longer accepts a crashed run as a pass ( #4099 , @proffesor-for-testing ); not part of the package. 
 
 Thanks 
 @rudycelekli , @proffesor-for-testing , @z4forzubair , @nicholas-ruest , @martinvlad , @ronmikailov (whose reports shaped the 3.56.7 and 3.56.8 trains) and @pacphi .

</details>