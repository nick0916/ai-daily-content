---
id: inbox_8ef333fd
date: 2026-11-24
source_ref: "[[00-inbox/2026-11-24/0007-claude-mem-releases-v16-1-3-f144]]"
title: "v16.1.3"
url: https://github.com/thedotmack/claude-mem/releases/tag/v16.1.3
source: claude-mem-releases
published_at: 2026-11-24T18:32:35+00:00
fetched_at: 2026-11-25T00:14:52.883582+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "HTTP 200 不代表成功，claude-mem 改看回應內的錯誤碼，避免丟掉佇列事件。 **Why** OpenRouter 會在 200 回應內回報「high demand」等暫時性錯誤，舊版誤判為不可復原，結束 session 並丟棄排隊的 observation；回報者一天損失 8.5% 至 16% 的事件。 **How** 分類器在 HTTP 2xx 時改讀數值 error.code（429 為限流、5xx 為暫時性錯誤）；server 端 job 遇到 Retry-After 時依提供方等待時間延後，上限 60 秒。 **What** v16.1.3 同時修正 POST /v1/events 對含 NUL 字元的資料改回 400（原為 500），並新增 CLAUDE_MEM_OPENAI_COMPAT_REASONING_EFFORT、CLAUDE_MEM_WORK_VIEW_API_TIMEOUT_MS（預設 600000）與 CLAUDE_MEM_WORK_VIEW_MAX_OUTPUT_TOKENS（預設 16000）設定，並補上巴西葡萄牙語翻譯。"
key_points:
  - "OpenRouter 200 回應內的暫時性錯誤，舊版會丟棄排隊事件，回報者一天損失 8.5% 至 16%"
  - "分類器改讀 error.code：429 為限流、5xx 為暫時性錯誤；Retry-After 延後上限 60 秒"
  - "POST /v1/events 對 NUL 字元回 400 而非 500；新增 CLAUDE_MEM_WORK_VIEW_API_TIMEOUT_MS 等設定"
tags: [claude-mem, openrouter, retry-backoff, error-handling, observability]
topics: [engineering.inference, agents.coding_agents]
importance: 3
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v16.1.3

HTTP 200 不代表成功，claude-mem 改看回應內的錯誤碼，避免丟掉佇列事件。

**Why** OpenRouter 會在 200 回應內回報「high demand」等暫時性錯誤，舊版誤判為不可復原，結束 session 並丟棄排隊的 observation；回報者一天損失 8.5% 至 16% 的事件。

**How** 分類器在 HTTP 2xx 時改讀數值 error.code（429 為限流、5xx 為暫時性錯誤）；server 端 job 遇到 Retry-After 時依提供方等待時間延後，上限 60 秒。

**What** v16.1.3 同時修正 POST /v1/events 對含 NUL 字元的資料改回 400（原為 500），並新增 CLAUDE_MEM_OPENAI_COMPAT_REASONING_EFFORT、CLAUDE_MEM_WORK_VIEW_API_TIMEOUT_MS（預設 600000）與 CLAUDE_MEM_WORK_VIEW_MAX_OUTPUT_TOKENS（預設 16000）設定，並補上巴西葡萄牙語翻譯。

### 重點
- OpenRouter 200 回應內的暫時性錯誤，舊版會丟棄排隊事件，回報者一天損失 8.5% 至 16%
- 分類器改讀 error.code：429 為限流、5xx 為暫時性錯誤；Retry-After 延後上限 60 秒
- POST /v1/events 對 NUL 字元回 400 而非 500；新增 CLAUDE_MEM_WORK_VIEW_API_TIMEOUT_MS 等設定

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v16.1.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Critical fix 
 
 OpenRouter errors sent with HTTP 200 no longer discard queued observations ( #6448 , thanks @ryrenz , closes #6447 reported by @claudemeister ). OpenRouter can accept a request and then report a temporary failure ("high demand", "temporarily rate-limited upstream") in the body of a 200 response, as {"error":{"code": ,...}} . The observer classified these as unrecoverable, so it did not retry, pause or fall back: it finalized the session and discarded its queued observations. The reporter lost 8.5% to 16% of events in one day. The classifier now uses the numeric error.code when the HTTP status is 2xx, so code 429 is a rate limit and 5xx is transient. A litellm output failure ("Unable to get json") stays an output failure and is never resent, because the model already ran and was billed. 
 
 Fixes 
 
 claude-mem server jobs retry no longer reports requeued for a job it did not publish ( #6439 , thanks @HEOJUNFO ). If Redis was unreachable, or the shell had no CLAUDE_MEM_QUEUE_ENGINE=bullmq , the command printed "outcome": "requeued" and exited 0, and the job never ran. It now moves the row back to failed with retry_republish_failed , prints the reason and exits 1, so the same command works once the queue is reachable. 
 Server generation jobs wait out a provider's Retry-After ( #6440 , thanks @HEOJUNFO ). A rate-limited job was redelivered after 5s and 10s whatever wait the provider asked for, so all three attempts could land inside the window and the job failed with no observation. When the provider sends a wait, the job is now delayed for it (capped at 60s, the same cap the worker uses). Rate limits without a wait, timeouts and 5xx keep the 5s/10s backoff. 
 POST /v1/events answers 400 instead of 500 for data Postgres can never store ( #6446 , thanks @alessandropcostabr ). A tool result with a NUL character (for example from reading a binary file) failed every time, and a 500 sent it to the local spool to be retried until the window expired. NUL is now removed from payload and metadata before private-tag stripping and redaction, and other data exceptions (SQLSTATE class 22) answer 400 InvalidData . 
 
 My Work and API agents 
 
 OpenAI-compatible observers and API agents can send an explicit reasoning effort ( #6434 , thanks @ZedingZhang , closes #6433 reported by @maxmad64bis ). Set CLAUDE_MEM_OPENAI_COMPAT_REASONING_EFFORT to none , low , medium , high , xhigh or max in the viewer, settings file or environment. Leaving it empty keeps each caller's current behavior. If an endpoint rejects the field, the client resends once without it and remembers that for the URL. 
 My Work API refresh timeout and answer limit are configurable ( #6437 , thanks @ZedingZhang , part of #6432 reported by @hello-sebastian ). With CLAUDE_MEM_WORK_VIEW_AGENT=api , CLAUDE_MEM_WORK_VIEW_API_TIMEOUT_MS (default 600000, 10 minutes) sets the deadline for one refresh question, and CLAUDE_MEM_WORK_VIEW_MAX_OUTPUT_TOKENS (default 16000) caps one answer. A cut-off answer reports the cap it used. 
 A story preference one character over the cap no longer discards the whole story ( #6435 , thanks @GratefulDave ). On the retry, a preference over 200 characters is now cut at a word boundary, like the review steps already do. The first answer is still checked strictly. 
 
 Translations 
 
 Brazilian Portuguese now covers the viewer, settings and setup ( #6436 , thanks @ZedingZhang , closes #6318 reported by @dev-a4 ). Selecting Português (Brasil) translates the classic viewer, settings and setup alongside My Work. 
 
 Internal 
 
 Owner-only file mode assertions are skipped on Windows, which has no POSIX permission bits ( #6443 , thanks @Lupin133 ). 
 The backup restore test suites pass on Windows ( #6444 , thanks @Lupin133 ). 
 
 Full changelog : v16.1.2...v16.1.3

</details>