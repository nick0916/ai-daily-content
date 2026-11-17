---
id: inbox_b63beac3
date: 2026-11-15
source_ref: "[[00-inbox/2026-11-15/2317-claude-mem-releases-v15-18-5-bfef]]"
title: "v15.18.5"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.18.5
source: claude-mem-releases
published_at: 2026-11-15T18:10:20+00:00
fetched_at: 2026-11-17T23:29:11.956963+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 claude-mem 在 tree-sitter 安裝失敗時仍能取得可用執行檔，並避免同一個 Chroma 集合被重複刪除。 **Why** 網路受限時安裝腳本常失敗，多個平行回填同時刪除會讓 chroma-mcp 記憶體暴增到 312 GB，拖垮 32 GB 的 Mac。 **How** 腳本失敗後直接下載同一個 release 資產，只有解壓後 SHA-256 符合固定值才執行；同一集合的刪除只跑一次，其他呼叫者等待並共用結果。 **What** claude-mem v15.18.5 修正 tree-sitter CLI 安裝（#6110）與 Chroma 重複刪除（#6115），另讓 `--help` 在 mcp、status、doctor、hook 等指令前先攔截（#6142）。"
key_points:
  - "tree-sitter 安裝腳本失敗時，額外下載一次同版本資產，解壓後 SHA-256 符合才執行"
  - "同一 Chroma 集合的刪除只執行一次，其他呼叫者共用結果；失敗只扣一次重試額度"
  - "`npx claude-mem mcp --help` 等指令改為印出說明；plain `mcp` 仍會啟動 stdio 伺服器"
tags: [claude-mem, tree-sitter, chroma, single-flight, mcp]
topics: [agents.mcp, agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.18.5

讓 claude-mem 在 tree-sitter 安裝失敗時仍能取得可用執行檔，並避免同一個 Chroma 集合被重複刪除。

**Why** 網路受限時安裝腳本常失敗，多個平行回填同時刪除會讓 chroma-mcp 記憶體暴增到 312 GB，拖垮 32 GB 的 Mac。

**How** 腳本失敗後直接下載同一個 release 資產，只有解壓後 SHA-256 符合固定值才執行；同一集合的刪除只跑一次，其他呼叫者等待並共用結果。

**What** claude-mem v15.18.5 修正 tree-sitter CLI 安裝（#6110）與 Chroma 重複刪除（#6115），另讓 `--help` 在 mcp、status、doctor、hook 等指令前先攔截（#6142）。

### 重點
- tree-sitter 安裝腳本失敗時，額外下載一次同版本資產，解壓後 SHA-256 符合才執行
- 同一 Chroma 集合的刪除只執行一次，其他呼叫者共用結果；失敗只扣一次重試額度
- `npx claude-mem mcp --help` 等指令改為印出說明；plain `mcp` 仍會啟動 stdio 伺服器

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.18.5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Critical fixes 
 
 The tree-sitter CLI installs on networks where its download script keeps failing ( #6110 , thanks @rigel905 , closes #6109 ). On some networks tree-sitter-cli's own install.js had its request reset every time, or exited 0 on a truncated file. The pinned SHA-256 check correctly refused the file, but nothing recovered after that, so smart_search , smart_outline , smart_unfold and the File Read Gate stayed off on every worker start, and npx claude-mem repair aborted. Now, when the script fails or leaves anything but the pinned executable, claude-mem fetches the same release asset directly, once, inside the same install time budget, and runs it only after it unpacks to the same pinned SHA-256. The script still runs first, so HTTPS_PROXY keeps working. A script that used up the whole budget gets no second attempt. 
 A corrupt Chroma collection is dropped once, not once per parallel backfill ( #6115 , thanks @mohitdixit02 and @0xABCD01 , closes #6113 ). When the HNSW segment of a large collection was corrupt, every parallel per-project backfill that hit it passed the "drop only once" check before the first delete finished, and queued its own delete against chroma-mcp. In #6113 that ran 19 drops at once and pushed chroma-mcp to a 312 GB memory footprint, stalling a 32 GB Mac. Callers now join the one drop already running for that collection and share its outcome. A failed drop costs one attempt from the retry budget, not one per caller, and different collections still drop independently. The remaining asks from that report (a memory bound on chroma-mcp, stopping writes when a drop can't be confirmed, measuring footprint on macOS) are tracked in #3610 . 
 
 Fixes 
 
 --help prints help instead of running the command ( #6142 , thanks @liuyinchu ). npx claude-mem mcp --help used to start the stdio server, and status , doctor and hook entered their runtime paths; t3code and its aliases rejected the flag. -h and --help are now handled before dispatch for these commands. Plain mcp still starts the server. 
 
 Docs 
 
 OmO Native recall guide ( #6087 , thanks @mschoi0411 ). How to connect OmO Native to the local worker through the existing stdio MCP server: tool discovery, recall by project and observation ID, troubleshooting and disconnect.

</details>