---
id: inbox_16a1f7c7
date: 2026-11-11
source_ref: "[[00-inbox/2026-11-11/0253-claude-mem-releases-v15-17-0-9cfd]]"
title: "v15.17.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.17.0
source: claude-mem-releases
published_at: 2026-11-11T06:13:38+00:00
fetched_at: 2026-11-12T03:03:11.507955+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "推出 claude-mem/eve，讓 eve agent 能調用使用者在 Claude Code、Codex 等工具中的 claude-mem 記憶。 **How** 每個 turn 前自動搜尋一次記憶，結果以跳脫後的資料送給模型而非指令；寫入只在模型呼叫 remember 時發生，避免 eve 重播擷取步驟時同一回合被存兩次。 **What** 需要 eve 0.84.0 以上與 Node.js 24 以上；附 Vercel 一鍵部署的個人 agent template，需設定 EVE_CHAT_PASSWORD 與 CLAUDE_MEM_API_KEY，iMessage 則需透過 eve 外掛接入。"
key_points:
  - "每 turn 前搜尋一次記憶，不產生推論費用；搜尋結果以跳脫資料形式進入模型"
  - "不做自動擷取：只有模型呼叫 remember 才寫入，避免 replay 造成重複儲存"
  - "需 eve 0.84.0+ 與 Node.js 24+；預設每個 eve scope 使用獨立 claude-mem project（searchAllProjects 僅供單一擁有者 agent）"
tags: [eve, claude-mem, agent-memory, vercel, agent-framework]
topics: [agents.frameworks, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.17.0

推出 claude-mem/eve，讓 eve agent 能調用使用者在 Claude Code、Codex 等工具中的 claude-mem 記憶。

**How** 每個 turn 前自動搜尋一次記憶，結果以跳脫後的資料送給模型而非指令；寫入只在模型呼叫 remember 時發生，避免 eve 重播擷取步驟時同一回合被存兩次。

**What** 需要 eve 0.84.0 以上與 Node.js 24 以上；附 Vercel 一鍵部署的個人 agent template，需設定 EVE_CHAT_PASSWORD 與 CLAUDE_MEM_API_KEY，iMessage 則需透過 eve 外掛接入。

### 重點
- 每 turn 前搜尋一次記憶，不產生推論費用；搜尋結果以跳脫資料形式進入模型
- 不做自動擷取：只有模型呼叫 remember 才寫入，避免 replay 造成重複儲存
- 需 eve 0.84.0+ 與 Node.js 24+；預設每個 eve scope 使用獨立 claude-mem project（searchAllProjects 僅供單一擁有者 agent）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.17.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

New: claude-mem memory for eve agents 
 
 claude-mem/eve is a new export of the claude-mem npm package. It is a memory provider for eve , Vercel's framework for durable backend agents. An eve agent can now recall what you did in Claude Code, Codex and your other claude-mem clients, using your cmem.ai memory (key from cmem.ai/pro/key) ( #5863 ).
 
 Recall: one search before every turn. No inference spend. Matches reach the model as escaped data, never as instructions. 
 Tools: __search to look further back and __remember to save a note. Both are bound to the slot's scope. 
 Separate memory per caller: each eve scope gets its own claude-mem project by default. searchAllProjects reads the whole account and is for single-owner agents only. 
 No automatic capture: eve can replay a capture step, and that would save the same turn twice, so saves only happen when the model calls remember . 
 Failures stay visible: if cmem.ai can't be reached, the turn still runs, the failure is logged, and the model is told memory is unavailable. 
 Requires eve 0.84.0 or later and Node.js 24 or later. eve and zod are optional peer dependencies, so nothing changes for existing installs. 
 
 
 One-click eve personal agent template at integrations/eve/template : password-protected web chat with your claude-mem memory. Deploy with Vercel and enter two values, EVE_CHAT_PASSWORD and CLAUDE_MEM_API_KEY . iMessage is an eve add-on ( npx eve add channel/linq or channel/photon ); only texts from CLAUDE_MEM_OWNER_PHONE get your memory. 
 
 Quick start for an existing eve agent: 
 npm install claude-mem 
 // agent/memory/claude-mem.ts 
 import { claudeMem } from "claude-mem/eve" ; 
 import { defineMemory } from "eve/memory" ; 
 import { byPrincipal } from "eve/memory/scope" ; 

 export default defineMemory ( { 
 description : "Recall and save durable context for the current user." , 
 provider : claudeMem ( { apiKey : process . env . CLAUDE_MEM_API_KEY } ) , 
 scope : byPrincipal , 
 } ) ; 
 Docs: https://docs.claude-mem.ai/eve-integration 
 No changes to the Claude Code plugin's capture, worker or hooks in this release. 
 Full changelog: v15.16.1...v15.17.0

</details>