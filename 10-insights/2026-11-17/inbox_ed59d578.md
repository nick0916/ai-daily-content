---
id: inbox_ed59d578
date: 2026-11-17
source_ref: "[[00-inbox/2026-11-17/2316-simon-willison-external-sandboxes-for-coding-agents-e7b5]]"
title: "External sandboxes for coding agents"
url: https://simonwillison.net/2026/Nov/17/external-sandboxes-for-coding-agents/
source: simon-willison
published_at: 2026-11-17T22:52:29+00:00
fetched_at: 2026-11-17T23:21:49.082242+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 AI agent 待在沙箱外面，只把它要執行的程式碼丟進沙箱跑。 **Why** 想試用本地模型時，不希望模型出錯或遭 prompt injection 而對本機造成破壞。 **How** 採用「外部沙箱」模式：agent 本身在沙箱外，執行的程式碼則送到專用沙箱；三種實作都提供相同的 localhost API，並可選用 HTTP/HTTPS 白名單 proxy 與憑證替換機制，讓 agent 能呼叫需認證的 API 卻拿不到 secret。 **What** Simon Willison 與 Prime Radiant 發布三個沙箱伺服器：external-sandbox-v86（Node.js + v86 在 WebAssembly 跑 Alpine Linux）、external-sandbox-container（Python + Apple Containers）、external-sandbox-quicksand（Python + 微軟 Quicksand，內含 QEMU 與 Alpine）。Pi、Claude Code、Codex 都可設定把執行程式碼的呼叫導向這些沙箱。"
key_points:
  - "外部沙箱模式：agent 在沙箱外，只有其執行的程式碼跑在沙箱內"
  - "三個實作：external-sandbox-v86、external-sandbox-container（Apple Containers）、external-sandbox-quicksand，共用相同 localhost API"
  - "內建可選的 HTTP/HTTPS 白名單 proxy，及憑證替換機制，讓 agent 不接觸 secret 即可呼叫認證 API"
tags: [sandboxing, coding-agents, prompt-injection, security, webassembly]
topics: [security, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## External sandboxes for coding agents

讓 AI agent 待在沙箱外面，只把它要執行的程式碼丟進沙箱跑。

**Why** 想試用本地模型時，不希望模型出錯或遭 prompt injection 而對本機造成破壞。

**How** 採用「外部沙箱」模式：agent 本身在沙箱外，執行的程式碼則送到專用沙箱；三種實作都提供相同的 localhost API，並可選用 HTTP/HTTPS 白名單 proxy 與憑證替換機制，讓 agent 能呼叫需認證的 API 卻拿不到 secret。

**What** Simon Willison 與 Prime Radiant 發布三個沙箱伺服器：external-sandbox-v86（Node.js + v86 在 WebAssembly 跑 Alpine Linux）、external-sandbox-container（Python + Apple Containers）、external-sandbox-quicksand（Python + 微軟 Quicksand，內含 QEMU 與 Alpine）。Pi、Claude Code、Codex 都可設定把執行程式碼的呼叫導向這些沙箱。

### 重點
- 外部沙箱模式：agent 在沙箱外，只有其執行的程式碼跑在沙箱內
- 三個實作：external-sandbox-v86、external-sandbox-container（Apple Containers）、external-sandbox-quicksand，共用相同 localhost API
- 內建可選的 HTTP/HTTPS 白名單 proxy，及憑證替換機制，讓 agent 不接觸 secret 即可呼叫認證 API

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/17/external-sandboxes-for-coding-agents/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

External sandboxes for coding agents 
I've been exploring new ways to sandbox code that is executed by agents, with a focus on making it safer to try out local models without worrying that a mistake or prompt injection attack might cause them to take damaging actions on a machine. 
 I worked on this project with Prime Radiant , the AI research lab behind Superpowers and other projects . 
 My post on the Prime Radiant blog introduces the external sandbox pattern, where code executed by the agent runs inside a dedicated sandbox while the agent itself lives outside of that sandbox. 
 To demonstrate this pattern we've released three sandbox server implementations: 
 
 external-sandbox-v86 runs a Node.js server which then uses v86 to run Alpine Linux inside WebAssembly. 
 external-sandbox-container is a Python web server which runs the sandbox in Alpine Linux inside an Apple Containers instance. 
 external-sandbox-quicksand is another Python web server, this time using Microsoft's Quicksand sandboxing library, which bundles QEMU and Alpine Linux in a Python package! 
 
 Each of these implementations offers the same localhost API. You can then configure Pi, Claude Code, or Codex to send API calls to that sandbox any time they want to execute code. 
 The sandboxes also include an optional HTTP/HTTPS allow-list proxy, so you can control exactly which hosts your agent's code is allowed to communicate with - plus a credential replacement mechanism to make authenticated API calls without sharing a secret with the agent. Here's the UI you can use to reconfigure that proxy while the sandbox is still running: 
 
 I continue to be fascinated by the challenge of safely running untrusted code. This external sandbox pattern provides a neat way to experiment with different approaches.

 Tags: sandboxing , security , ai , webassembly , generative-ai , llms , coding-agents , claude-code , codex , pi

</details>