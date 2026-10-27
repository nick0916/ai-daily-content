---
id: inbox_8c7dedfd
date: 2026-10-26
source_ref: "[[00-inbox/2026-10-26/0124-claude-mem-releases-v15-3-0-ffa2]]"
title: "v15.3.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.3.0
source: claude-mem-releases
published_at: 2026-10-26T23:57:00+00:00
fetched_at: 2026-10-27T01:38:32.585852+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 agent 產出的檔案在暫存目錄消失後仍能保留。 **Why** 複本需要比 worktree、暫存資料夾或 temp 目錄活得更久。 **How** Stop hook 把本回合產出的檔案以內容雜湊命名複製到 ~/.claude-mem/deliverables/，SubagentStop 也擷取子 agent 的產出。 **What** claude-mem v15.3.0 在 My Work 卡片新增 Deliverables 區塊；單次 Stop 上限 50 檔、單檔 512 MiB，設 CLAUDE_MEM_DELIVERABLES_ENABLED=false 可關閉；同版也加入預設關閉的自動 DB 快照與 opt-in 的 Notion 匯出。"
key_points:
  - "Stop hook 以內容雜湊命名複製產出檔，存於 ~/.claude-mem/deliverables/，與來源目錄解耦"
  - "單次 Stop 最多 50 檔、單檔 512 MiB，超過會回報而非靜默略過"
  - "新增 CLAUDE_MEM_BACKUP_ENABLED 等設定的本地 DB 快照（預設關閉）與 Notion 匯出（需 token 與 database id）"
tags: [claude-mem, claude-code, deliverables, memory, backup]
topics: [agents.coding_agents]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.3.0

讓 agent 產出的檔案在暫存目錄消失後仍能保留。

**Why** 複本需要比 worktree、暫存資料夾或 temp 目錄活得更久。

**How** Stop hook 把本回合產出的檔案以內容雜湊命名複製到 ~/.claude-mem/deliverables/，SubagentStop 也擷取子 agent 的產出。

**What** claude-mem v15.3.0 在 My Work 卡片新增 Deliverables 區塊；單次 Stop 上限 50 檔、單檔 512 MiB，設 CLAUDE_MEM_DELIVERABLES_ENABLED=false 可關閉；同版也加入預設關閉的自動 DB 快照與 opt-in 的 Notion 匯出。

### 重點
- Stop hook 以內容雜湊命名複製產出檔，存於 ~/.claude-mem/deliverables/，與來源目錄解耦
- 單次 Stop 最多 50 檔、單檔 512 MiB，超過會回報而非靜默略過
- 新增 CLAUDE_MEM_BACKUP_ENABLED 等設定的本地 DB 快照（預設關閉）與 Notion 匯出（需 token 與 database id）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.3.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What changed 
 Deliverables on the My Work card ( #5109 ) 
 Ask an agent for a deck, a report, an HTML page or any other file, and it is one click away on the front of the request's card in My Work, under Deliverables . 
 
 The Stop hook copies what the turn made for you into ~/.claude-mem/deliverables/ / , content-addressed ( report-3f9a1c2b.md ), so the copy outlives the worktree, scratch folder or temp directory it was made in. Files an agent attaches through work_state_write ( work_product , deliverable , or any field naming a file a person opens) count, as do decks, documents, pages, images, video and spreadsheets written outside the source tree. Source files are never copied by inference. SubagentStop captures what a subagent made from its own transcript. 
 The worker records and serves each copy at GET /api/deliverables/:id/:filename , with the same loopback, same-origin and sandbox rules as recorded files; markdown and text open inline. While a copy is on disk and the file has not been written since, it stands in for the record of where the file was made. 
 Privacy and limits are explicit. A turn whose prompt is entirely leaves no copy and no record. Nothing is copied for a worker on another host, which could not open the copy. 50 files per Stop and 512 MiB per file, reported when hit, never silent. CLAUDE_MEM_DELIVERABLES_ENABLED=false turns the copy off. 
 The SessionStart work-state rule now asks agents to write the thing you asked for as a file and attach it as work_product before they finish. 
 
 Also new 
 
 Automatic local database snapshots with crash-safe restore: npx claude-mem backup [run|status|list] and npx claude-mem restore . Off by default; CLAUDE_MEM_BACKUP_ENABLED=true with CLAUDE_MEM_BACKUP_INTERVAL_HOURS and CLAUDE_MEM_BACKUP_RETAIN_COUNT . ( #3751 ) 
 Notion export. Each new observation is upserted into a Notion database as soon as it is stored. Opt-in through CLAUDE_MEM_NOTION_ENABLED , a token and a database id; never blocks capture. ( #4799 ) 
 Codex subagents start with the memory timeline. A new SubagentStart hook gives a fresh subagent the same context SessionStart gives a session; forks, which inherit their parent's history, are skipped. Codex asks once to trust the new hook. ( #4760 ) 
 Runcrate preset for the openai-compatible provider. ( #5067 ) 
 
 Fixes 
 
 Antigravity CLI: claude-mem no longer registers PreToolUse , which auto-approved every agy tool call and queued each call twice ( #5085 ). agy prompts are now recorded once per turn, so agy work shows up in My Work, and files read in agy get their observation history ( #5092 ). 
 Redaction: temporary AWS credentials are redacted in full: ASIA access key IDs, session tokens, and the SecretAccessKey in aws sts JSON output ( #5066 , #5073 , #5080 ). 
 Transcripts: watcher checkpoints are held until buffered work is stored ( #5072 ); the transcript-watch config path follows CLAUDE_MEM_DATA_DIR ( #5070 ). 
 Observer parser: reads the type the model settled on, never markup around it ( #5077 ). 
 Windows: the launcher compiles through the 8.3 short path when bun.exe is on a non-ASCII path ( #5089 ). 
 SessionStart terminal preview leaves room for its footer ( #5084 ); install help says which providers need a cmem.ai sign-in ( #5086 ). 
 Release tooling: every shipped plugin manifest carries the same version, synced by the build and checked in CI ( #5083 , #5082 , #5075 ). 
 
 Full Changelog : v15.2.1...v15.3.0

</details>