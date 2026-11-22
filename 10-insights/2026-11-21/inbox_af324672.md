---
id: inbox_af324672
date: 2026-11-21
source_ref: "[[00-inbox/2026-11-21/0238-claude-mem-releases-v16-0-3-cb2b]]"
title: "v16.0.3"
url: https://github.com/thedotmack/claude-mem/releases/tag/v16.0.3
source: claude-mem-releases
published_at: 2026-11-21T20:56:15+00:00
fetched_at: 2026-11-22T02:46:09.558350+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 claude-mem 的 OMP hook 直接連 server，不再把事件送到本地 worker。 **Why** 設定 server 模式時，OMP hook 仍把所有事件送到本地 worker，導致 OMP 的 session 被丟棄。 **How** hook 改讀 CLAUDE_MEM_SERVER_URL 等環境變數，直接呼叫 server 的 /v1 API，並套用與 worker 相同的過濾規則。 **What** v16.0.3 同時修正知識查詢 10 分鐘、corpus 請求 15 分鐘的逾時問題，並修復 Docker 映像建置；OMP 使用者需執行 npx claude-mem install --ide omp 才會取得修正。"
key_points:
  - "OMP hook 改為直連 server 的 /v1 API，修正 server 模式下 OMP session 被丟棄的問題"
  - "知識查詢於 10 分鐘、corpus 請求於 15 分鐘後以 504 逾時結束"
  - "OMP 使用者需執行 npx claude-mem install --ide omp，單純更新 plugin 不會替換 hook 檔案"
tags: [claude-mem, memory, release-notes, omp, server-mode]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v16.0.3

讓 claude-mem 的 OMP hook 直接連 server，不再把事件送到本地 worker。

**Why** 設定 server 模式時，OMP hook 仍把所有事件送到本地 worker，導致 OMP 的 session 被丟棄。

**How** hook 改讀 CLAUDE_MEM_SERVER_URL 等環境變數，直接呼叫 server 的 /v1 API，並套用與 worker 相同的過濾規則。

**What** v16.0.3 同時修正知識查詢 10 分鐘、corpus 請求 15 分鐘的逾時問題，並修復 Docker 映像建置；OMP 使用者需執行 npx claude-mem install --ide omp 才會取得修正。

### 重點
- OMP hook 改為直連 server 的 /v1 API，修正 server 模式下 OMP session 被丟棄的問題
- 知識查詢於 10 分鐘、corpus 請求於 15 分鐘後以 504 逾時結束
- OMP 使用者需執行 npx claude-mem install --ide omp，單純更新 plugin 不會替換 hook 檔案

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v16.0.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Critical fix 
 
 The OMP hook works with the server runtime ( #6367 , thanks @flipcyde101 , closes #6366 reported by @walynde ). When CLAUDE_MEM_RUNTIME was server or server-beta , the OMP hook still sent everything to the local worker, so OMP sessions were dropped. The hook now reads CLAUDE_MEM_SERVER_URL , CLAUDE_MEM_SERVER_API_KEY and CLAUDE_MEM_SERVER_PROJECT_ID (or the CLAUDE_MEM_SERVER_BETA_* names; environment variables win over settings.json ) and talks to the server's /v1 API directly: session start, tool and reply events, context, and session end. It applies the same rules the worker applies before it saves anything: blocks are stripped, excluded projects and CLAUDE_MEM_SKIP_TOOLS are honored, every prompt is recorded, and the project name comes from git. If the server settings are incomplete, it falls back to the worker as before. 
 OMP users: run npx claude-mem install --ide omp once to get this fix. The OMP hook is a copied file, so a plugin update alone does not replace it. 
 
 Fixes 
 
 Knowledge queries and corpus requests can no longer hang forever ( #6368 , thanks @flipcyde101 , closes #6364 reported by @soarkit ). A stalled Agent SDK stream used to keep the request and its Claude CLI child alive with no end. A knowledge query or prime now stops after 10 minutes and a corpus request after 15, with a 504 error. The corpus stays locked until the timed-out work has really stopped, so it cannot write after a delete or rebuild. 
 The "paused saving memories" notice goes away once Codex is saving ( #6374 , thanks @ryrenz , closes #6372 reported by @raw34 ). After you switched CLAUDE_MEM_PROVIDER to codex following a Claude quota pause, every new session still said capture was paused until the old Claude cooldown ran out. The notice is now recomputed when Codex stores a memory. 
 server api-key create --scope with no value is refused ( #6375 , thanks @ryrenz , closes #6373 reported by @soarkit ). It used to create a key scoped to the literal string true , which every request then rejected. A bare --scope , --name , --team or --project now prints -- requires a value and exits 1 without writing anything, on both create and migrate-scopes . 
 The Agent Cost Report no longer crashes on observations with no model ( #6376 , thanks @ZedingZhang , closes #6371 reported by @Realauster ). acr.py rollup raised a TypeError when one window had both a missing model and a named, unpriced one. 
 The Docker server image builds again ( #6386 , closes #6379 reported by @InfoALR ). It now uses node:20-trixie , because tree-sitter 0.26 needs a newer glibc than node:20 ships. 
 My Work refresh runs on OpenCode 2.x ( #6361 , refs #6339 reported by @Realauster ). OpenCode 2.x rejects the --pure and --dir flags, so every refresh step exited 1. The step now checks opencode --version and uses each version's own isolation. 2.0.0 to 2.2.2 and 3.x are refused with a reason, because they cannot keep plugins out. On every version the refresh agent now has all tools denied. 
 OMP and Hermes read a worker port saved as a number ( #6363 , thanks @chuenchen309 ). {"CLAUDE_MEM_WORKER_PORT": 45678} in settings.json used to be ignored, so their requests went to the default port. 
 The OpenClaw installer no longer deletes a folder it did not install ( #6381 , thanks @DeryFerd ). It ran rm -rf on whatever install path ~/.openclaw/openclaw.json named. It now replaces a folder only when it is missing, empty, or holds claude-mem's own OpenClaw manifest. Anything else is left alone with a warning and the default extensions folder is used; if that is also taken by something else, the installer stops. 
 The worker can stop every Claude child it starts ( #6385 , thanks @DeryFerd ). Field compression and the Telegram wrap-up started their Claude process outside the worker's process list, so a worker that exited hard left them running. They are now on that list, and they do not take a concurrency slot. 
 A CLI stuck printing can't grow the worker's memory without limit ( #6384 , thanks @DeryFerd ). Output collected from claude , codex , gemini and opencode is capped at 128 Mi characters, about 2.5 times the largest real turn measured. Past the cap, the start and end are kept, a warning is logged, and the reply is refused instead of read as a partial answer. Smaller outputs are unchanged. 
 A transcript record with no end can't grow the worker's memory without limit ( #6383 , thanks @DeryFerd ). A JSONL record over 64 MiB (the largest real record measured was 44 MiB) is skipped, with a warning that names the file, the record's offset and its size. The lines after it are read as normal. 
 The unauthenticated /v1/info no longer shows Redis error text ( #6380 , thanks @DeryFerd ). A queue lane that could not be read used to publish the driver's error, such as a host and port. The reason now stays in the server log. 
 
 New 
 
 Opt-in CPU cap for chroma-mcp ( #6369 , thanks @flipcyde101 , partly addresses #6365 reported by @FengJie2004 ). Set CLAUDE_MEM_CHROMA_MAX_THREADS to 2 if chroma-mcp keeps several cores busy. It caps the embedder's threads and, on Linux with taskset , the CPUs chroma-mcp can use. It is off by default ( 0 ), because an always-on cap slowed the first backfill. #6365 stays open. 
 AIGROW preset for the OpenAI-compatible provider ( #6370 , thanks @guglielmo-io ). 
 
 Hosted sync service 
 
 The sync services compare their internal projector credential in constant time ( #6382 , thanks @DeryFerd ). A plain string compare could leak the shared secret through response timing. This changes services/sync-api and services/sync-hub , which are not part of the npm package: it reaches users only once those services are deployed, not through this release. 
 
 Tests 
 
 A flaky transcript test now counts the append poll's pokes instead of racing its file check ( #6360 ). 
 
 Full changelog : v16.0.2...v16.0.3

</details>