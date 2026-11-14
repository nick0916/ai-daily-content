---
id: inbox_9b180f16
date: 2026-11-12
source_ref: "[[00-inbox/2026-11-12/0146-claude-mem-releases-v15-18-1-c45b]]"
title: "v15.18.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.18.1
source: claude-mem-releases
published_at: 2026-11-12T07:52:21+00:00
fetched_at: 2026-11-14T01:56:16.152623+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem 限制 My Work 無效回應的重試次數，並降低 observer 的對話預算。 **Why** 無效的模型回應每分鐘原樣重送且沒有上限，一份報告測得 104,869 次呼叫，拖垮本地 Ollama。 **How** 每個請求版本最多重試 3 次、等待時間遞增，之後等輸入或設定改變才再試，並顯示實際失敗原因。 **What** observer 對話預算由 40 萬字元降至 10 萬字元（issue 測量每回合約由 10 萬 token 降至 2.6 萬）；npx claude-mem update 與每日自動更新現在會保留既有 runtime、provider 與 model，不再重新詢問設定。"
key_points:
  - "My Work 無效回應從無上限重送改為每版本最多 3 次、遞增等待"
  - "observer 對話預算 400,000 → 100,000 字元；自行設定的值保留"
  - "update 與自動更新保留 server/server-beta runtime 與 provider，修正前會把 capture 切回本地 worker"
tags: [claude-mem, my-work, retry-policy, observer-cost, ollama]
topics: [agents.coding_agents, engineering.inference]
importance: 3
novelty: 2
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.18.1

claude-mem 限制 My Work 無效回應的重試次數，並降低 observer 的對話預算。

**Why** 無效的模型回應每分鐘原樣重送且沒有上限，一份報告測得 104,869 次呼叫，拖垮本地 Ollama。

**How** 每個請求版本最多重試 3 次、等待時間遞增，之後等輸入或設定改變才再試，並顯示實際失敗原因。

**What** observer 對話預算由 40 萬字元降至 10 萬字元（issue 測量每回合約由 10 萬 token 降至 2.6 萬）；npx claude-mem update 與每日自動更新現在會保留既有 runtime、provider 與 model，不再重新詢問設定。

### 重點
- My Work 無效回應從無上限重送改為每版本最多 3 次、遞增等待
- observer 對話預算 400,000 → 100,000 字元；自行設定的值保留
- update 與自動更新保留 server/server-beta runtime 與 provider，修正前會把 capture 切回本地 worker

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.18.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Critical fixes 
 
 The worker no longer fails to start when the database is busy at startup ( #6041 ). If the My Work refresh record was left as "running" by a restart and the database was locked at that moment, the repair write threw and took down the worker's whole startup, so memory stayed off until the next restart. The repair failure is now logged, and the next scheduled check tries again (whether or not scheduled refresh is on). 
 npx claude-mem update and the daily auto-update keep your setup ( #6045 ). Before this, an unattended update reset a server or server-beta runtime back to the local worker, so capture moved off your server. A legacy install with no saved provider could also have its cloud sync turned off and its Anthropic env keys cleared. Updates now reuse your saved runtime, provider, model and agents. They don't reopen the browser setup or ask the setup questions again, and only ask for a Gemini or OpenRouter key if one is missing. npx claude-mem install is unchanged. 
 My Work summaries stop retrying unusable model answers forever ( #6039 , thanks @mohitdixit02 , reported by @adminwat in #6037 ). When the model's answer failed validation, wasn't JSON or came back empty, the same unchanged request was resent every minute with no end. One report measured 104,869 calls, and the constant load starved a local Ollama runner. Each request version now gets at most 3 tries with a growing wait, then waits until its input or settings change. The card shows the actual reason. Thanks @balabommablock-cpu for testing and finding the empty-answer case. 
 
 Fixes 
 
 Lower observer cost by default ( #6031 , thanks @kartik70 , closes #5023 ). The observer's conversation budget drops from 400,000 to 100,000 characters (about 100K to about 26K tokens per turn in the issue's measurement). Installs that still hold the old shipped default move once; a value you set yourself is kept. 
 Redaction: Heroku API keys and Atlassian API tokens are now removed before storage ( #6046 , thanks @kevin9327 ). 
 TeamBrain: relayed text can no longer pass as claude-mem's own headings, fences or rules ( ~~~ , *** , ___ , setext === ) ( #6048 , thanks @kevin9327 ). 
 Work state: GET /api/work-state/export returns the complete history of a list when it is too long for an MCP reply, and shortened MCP reads now say so and point to it ( #6049 , thanks @Jeremy891102 , closes #6043 ). 
 My Work (thanks @Afloat16 ):
 
 A checked request is unchecked again when a new deliverable revision or published PR changes its result ( #5891 ). 
 The first goals map of a long prompt history runs in checkpointed batches instead of one oversized question that fails and repeats ( #6001 ). 
 Resolving original requests no longer rescans the whole prompt window per conversation ( #6022 ). 
 
 
 Smart file read: function signatures end at the real body boundary in every supported language, so destructured parameters and default objects stay in the outline and are searchable ( #6029 , thanks @Afloat16 ). 
 Gemini CLI: npx claude-mem gemini install finds a worker installed only in the plugin cache instead of reporting it missing ( #6032 , thanks @Kirat0201 ). 
 Memory: replaying an older native memory note uses an index instead of scanning project history inside the write transaction ( #6016 , thanks @Afloat16 ). 
 
 New examples and docs 
 
 Obsidian: an opt-in, one-way export of selected memories into an existing vault, never overwriting your notes ( #6051 , thanks @Jeremy891102 , closes #5943 ). 
 Pipecat: an explicit project-memory pipeline example ( #6050 , thanks @Jeremy891102 , closes #5946 ). 
 elizaOS: a verified explicit-memory example ( #6035 , thanks @Kirat0201 , closes #5914 ). 
 ContextForge: a private recall workflow ( #6033 , thanks @Kirat0201 , closes #5935 ).

</details>