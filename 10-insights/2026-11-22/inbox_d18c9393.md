---
id: inbox_d18c9393
date: 2026-11-22
source_ref: "[[00-inbox/2026-11-22/0052-claude-mem-releases-v16-0-4-ef58]]"
title: "v16.0.4"
url: https://github.com/thedotmack/claude-mem/releases/tag/v16.0.4
source: claude-mem-releases
published_at: 2026-11-22T19:13:24+00:00
fetched_at: 2026-11-23T00:58:30.828793+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v16.0.4 為修補版，修正 Chroma 搜尋退回 FTS5、OpenCode Go 回 400 等問題。 **Why** 修復前 Chroma 無法新增文件，搜尋會退回 FTS5；OpenCode Go 每個步驟都回 400。 **What** NO_PROXY 的 IPv6 方括號格式使 httpx 0.28 報 Invalid port，已修正（#6399）；OpenCode Go 需 x-opencode-session 標頭並設 reasoning_effort: none（#6395）；INTERNAL_PROJECTOR_URL 啟動時驗證格式，避免內部 secret 以明文送出（#6397，需部署 services/sync-api 才生效）。"
key_points:
  - "NO_PROXY 含 [::1] 這類方括號 IPv6 條目時，httpx 0.28 報 Invalid port；去掉方括號即可（#6399）"
  - "OpenCode Go 需每次 run 一個 x-opencode-session id，並設 reasoning_effort: none，否則回 400 MissingSessionID（#6395）"
  - "INTERNAL_PROJECTOR_URL 啟動時檢查 https 與格式，防止內部 bearer secret 以 http 明文送出（#6397）"
tags: [claude-mem, chroma, httpx, release-notes, security]
topics: [agents.coding_agents, security]
importance: 2
novelty: 1
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v16.0.4

claude-mem v16.0.4 為修補版，修正 Chroma 搜尋退回 FTS5、OpenCode Go 回 400 等問題。

**Why** 修復前 Chroma 無法新增文件，搜尋會退回 FTS5；OpenCode Go 每個步驟都回 400。

**What** NO_PROXY 的 IPv6 方括號格式使 httpx 0.28 報 Invalid port，已修正（#6399）；OpenCode Go 需 x-opencode-session 標頭並設 reasoning_effort: none（#6395）；INTERNAL_PROJECTOR_URL 啟動時驗證格式，避免內部 secret 以明文送出（#6397，需部署 services/sync-api 才生效）。

### 重點
- NO_PROXY 含 [::1] 這類方括號 IPv6 條目時，httpx 0.28 報 Invalid port；去掉方括號即可（#6399）
- OpenCode Go 需每次 run 一個 x-opencode-session id，並設 reasoning_effort: none，否則回 400 MissingSessionID（#6395）
- INTERNAL_PROJECTOR_URL 啟動時檢查 https 與格式，防止內部 bearer secret 以 http 明文送出（#6397）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v16.0.4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Fixes 
 
 Chroma search works again while the embedding model downloads ( #6399 , closes the "Invalid port" part of #6365 reported by @FengJie2004 , root cause found by @kevincommits ). httpx 0.28 misread a bracketed IPv6 entry such as [::1] in NO_PROXY and failed with Invalid port: ':1]' , so chroma-mcp could not add documents and search fell back to FTS5. The chroma-mcp child now gets the same host without brackets ( ::1 ). Entries with a port, and every other entry, are unchanged. 
 Context injection keeps observations whose concepts are an old plain string ( #6393 , thanks @jiangjiang248 , closes #6389 reported by @soarkit ). Keyword search matched a legacy concept such as 缓存 , but context injection dropped the same observation. Both now read concepts through one shared SQL expression, so they cannot drift apart again. 
 OpenCode Go answers My Work refresh and corpus steps ( #6395 , thanks @HemanRamlal ). The API agent now sends the x-opencode-session header OpenCode Go requires (one id per run), and turns reasoning off with reasoning_effort: none , which Go honors. Before, every step failed with 400 MissingSessionID , or ran out of its answer budget while thinking. 
 Expired live observer inputs are counted and reported ( #6394 , thanks @Zhong-fan , closes #6391 reported by @abhiroopb ). The live buffer still drops an input nobody claims within five minutes, and still never replays it. The WARN line now carries a running total, and /api/processing-status returns it as expiredObserverInputs , so the loss is visible without reading logs. 
 /api/tool-uses refuses a bad date instead of ignoring it ( #6387 , thanks @kevincommits ). A dateStart or dateEnd that was not a number (an ISO date, a typo, or the parameter given twice) was dropped, and the listing returned rows from every date. It now answers 400 INVALID_DATE . Epoch-millisecond values work as before. 
 /api/dedup/candidates refuses a fractional limit instead of answering 500 ( #6388 , thanks @REI-330 ). limit=2.5 failed with datatype mismatch . A limit that is not a whole number now answers 400 limit must be a whole number , and the store clamps what it binds so a negative limit cannot read every row. 
 /api/advisor-calls caps its offset like every other listing ( #6396 , thanks @DeryFerd ). A huge offset made SQLite scan and discard rows on the worker's shared connection. It now uses the shared listing cap, and a viewer that keeps paging stops with offsetCapReached . 
 
 Hosted sync service 
 
 The sync API checks the projector URL before sending its secret ( #6397 , thanks @DeryFerd ). INTERNAL_PROJECTOR_URL now follows the same rules as FORWARD_ORIGIN (absolute https, plain http only for loopback, no credentials, query or fragment) and fails at startup. Before, a typo or an http:// address sent the internal bearer secret in cleartext. This changes services/sync-api , which is not part of the npm package: it reaches users only once that service is deployed. 
 
 Internal 
 
 One helper now decides whether a listing offset is past the cap ( #6398 , thanks @DeryFerd ). Behavior is unchanged. 
 The 16.0.3 changelog now tells OMP users to run npx claude-mem install --ide omp once to get the server-runtime fix. 
 
 Full changelog : v16.0.3...v16.0.4

</details>