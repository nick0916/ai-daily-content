---
id: inbox_caf768ff
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0253-claude-mem-releases-v15-17-1-4e90]]"
title: "v15.17.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.17.1
source: claude-mem-releases
published_at: 2026-11-11T18:22:35+00:00
fetched_at: 2026-11-12T03:03:11.507362+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "修正 claude-mem 更新後，已開啟的 Claude Code session 靜默停止記錄的問題。 **Why** 15.16.0 起 worker 會清理舊 plugin 版本資料夾，開啟中的 session 因資料夾被刪而無法執行任何 hook，導致 prompt、工具呼叫與摘要都不再儲存。 **How** 清理程式現在會讀取 Claude Code 為每個 plugin 版本保存的 .in_use 紀錄，只要仍有 session 使用該版本就保留它，未被使用的版本照常清理。 **What** 同時修正數個問題（如 content_filter 不完整報告、Sync 的 database is locked 等），並新增 Vercel AI SDK、LangGraph、Pydantic AI、CrewAI、OpenAI Agents SDK、Google ADK 等 14 個 agent 框架的記憶整合。"
key_points:
  - "清理舊 plugin 版本前檢查 .in_use 紀錄，有執行中 session 引用的版本保留（#5971）"
  - "新增 14 個 agent 框架整合（Vercel AI SDK、LangGraph、Pydantic AI、CrewAI 等），各自限定單一 project"
  - "修正 content_filter 截斷的回答仍被儲存（#5878），以及大量首次同步時 database is locked 造成長時間退避（#5996）"
tags: [claude-mem, plugin-cache, session-management, agent-frameworks, bugfix]
topics: [agents.coding_agents, agents.frameworks]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.17.1

修正 claude-mem 更新後，已開啟的 Claude Code session 靜默停止記錄的問題。

**Why** 15.16.0 起 worker 會清理舊 plugin 版本資料夾，開啟中的 session 因資料夾被刪而無法執行任何 hook，導致 prompt、工具呼叫與摘要都不再儲存。

**How** 清理程式現在會讀取 Claude Code 為每個 plugin 版本保存的 .in_use 紀錄，只要仍有 session 使用該版本就保留它，未被使用的版本照常清理。

**What** 同時修正數個問題（如 content_filter 不完整報告、Sync 的 database is locked 等），並新增 Vercel AI SDK、LangGraph、Pydantic AI、CrewAI、OpenAI Agents SDK、Google ADK 等 14 個 agent 框架的記憶整合。

### 重點
- 清理舊 plugin 版本前檢查 .in_use 紀錄，有執行中 session 引用的版本保留（#5971）
- 新增 14 個 agent 框架整合（Vercel AI SDK、LangGraph、Pydantic AI、CrewAI 等），各自限定單一 project
- 修正 content_filter 截斷的回答仍被儲存（#5878），以及大量首次同步時 database is locked 造成長時間退避（#5996）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.17.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Open sessions keep capturing after an update 
 Since 15.16.0 the worker clears old plugin versions out of Claude Code's plugin cache five minutes after it starts and then hourly. A Claude Code session that was already open when an update arrived keeps running from the older version folder. Once the sweep deleted that folder, Claude Code refused to run every claude-mem hook for that session ("Plugin directory does not exist"), so the session silently stopped saving prompts, tool calls, observations and summaries. 
 The sweep now reads the .in_use records Claude Code keeps for each plugin version, and keeps a version while any session loaded from it is still running. Folders no running session uses are still removed on the next sweep, so the disk clean-up from 15.16.0 stays. The worker's sweep, npx claude-mem prune (and its --dry-run ) and the installer all follow the same rule ( #5971 , thanks @rigel905 , fixes #5970 ). 
 Fixes 
 
 Context: an explicitly empty project selection shows nothing instead of observations from every project ( #5866 , thanks @Afloat16 ). 
 Context: read-cost and savings estimates count stored facts once, instead of counting extra escape characters and an invented [] for rows without facts ( #5980 , thanks @Afloat16 ). 
 Observer: a streamed answer that arrives as a refusal counts as generated output, so an interrupted stream is not sent again and charged twice ( #5843 , thanks @Afloat16 ). 
 My Work: the API agent rejects an answer the provider cut with content_filter , instead of saving an incomplete report ( #5878 , thanks @Afloat16 ). 
 Sync: a pulled page of synced records waits for another writer instead of failing at once with "database is locked", so a large first pull no longer backs off for minutes ( #5996 ). 
 My Work: the worker reads My Work's shared history once per change instead of re-reading all of it on every sync pass ( #5986 ). 
 Cloud viewer: a slow-starting cloud viewer reloads its "starting" page until the worker answers, and a hidden cloud My Work tab closes its live feed until it is shown again ( #5988 , #5953 ). 
 
 Integrations 
 New verified memory workflows for agent frameworks, each scoped to one project: Vercel AI SDK ( #5951 ), LangGraph ( #5954 ), Pydantic AI ( #5955 ), Microsoft Agent Framework ( #6017 ), Haystack ( #6018 ), LlamaIndex ( #6019 ), Google ADK ( #6020 ), CrewAI ( #6021 ), Strands Agents ( #6023 ), OpenAI Agents SDK ( #6024 ), Agno ( #6025 ), SmolAgents ( #6026 ), AG2 ( #6027 ) and AutoGen ( #6028 ). Thanks @Afloat16 for all of them. 
 Also in this release 
 
 Cloud viewer: groundwork for routing each signed-in account to its own app; production behaviour is unchanged ( #5952 ). 
 eve template: the template's lockfile includes claude-mem 15.17.0, so its deploy button installs ( #5968 ). 
 
 Full changelog: v15.17.0...v15.17.1

</details>