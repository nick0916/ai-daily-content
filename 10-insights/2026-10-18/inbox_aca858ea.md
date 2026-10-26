---
id: inbox_aca858ea
date: 2026-10-18
source_ref: "[[00-inbox/2026-10-18/0205-simon-willison-llm-echo-0-5-3f91]]"
title: "llm-echo 0.5"
url: https://simonwillison.net/2026/Oct/18/llm-echo/
source: simon-willison
published_at: 2026-10-18T23:16:16+00:00
fetched_at: 2026-10-20T02:09:08.612795+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "llm-echo 0.5 是個不接 LLM、只回放提示的除錯用「假模型」，新版把模擬 token 計數做得更貼近真實。 **Why** Simon 正在準備新的 LLM 版本，測試 PR 時重新檢視這個除錯外掛。 **How** 模擬的 token 用量現在會把 tool call、system prompt 與 reasoning token 一併計入。 **What** llm-echo 0.5；可用 `uvx --with llm-echo llm -m echo 'hi there' -o thinking 1 --usage` 試跑，範例輸出為 2 input、24 output tokens。"
key_points:
  - "llm-echo 提供不涉及 LLM、只回放收到提示的 echo 模型，供除錯使用"
  - "0.5 版的模擬 token 計數納入 tool call、system prompt、reasoning token"
  - "範例指令 `uvx --with llm-echo llm -m echo 'hi there' -o thinking 1 --usage` 輸出 2 input、24 output"
tags: [llm, llm-echo, plugin, debugging, simon-willison]
topics: [agents.frameworks]
importance: 1
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-echo 0.5

llm-echo 0.5 是個不接 LLM、只回放提示的除錯用「假模型」，新版把模擬 token 計數做得更貼近真實。

**Why** Simon 正在準備新的 LLM 版本，測試 PR 時重新檢視這個除錯外掛。

**How** 模擬的 token 用量現在會把 tool call、system prompt 與 reasoning token 一併計入。

**What** llm-echo 0.5；可用 `uvx --with llm-echo llm -m echo 'hi there' -o thinking 1 --usage` 試跑，範例輸出為 2 input、24 output tokens。

### 重點
- llm-echo 提供不涉及 LLM、只回放收到提示的 echo 模型，供除錯使用
- 0.5 版的模擬 token 計數納入 tool call、system prompt、reasoning token
- 範例指令 `uvx --with llm-echo llm -m echo 'hi there' -o thinking 1 --usage` 輸出 2 input、24 output

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/18/llm-echo/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm-echo 0.5 
 I'm working towards a new LLM release, and testing PRs caused me to revisit the llm-echo debug plugin. This plugin provides a "model" which doesn't involve an LLM at all - it just repeats back the prompts that have been fed to it. The new release now updates the simulated token usage counts to take tool calls, system prompts, and reasoning tokens into account. 
 Example usage: 
 uvx --with llm-echo llm -m echo 'hi there' -o thinking 1 --usage
 
 Outputs: 
 First I consider the prompt, then I decide what to say.
{
 "prompt": "hi there",
 "system": "",
 "attachments": [],
 "stream": true,
 "previous": []
}
Token usage: 2 input, 24 output
 
 
 
 Tags: llm

</details>