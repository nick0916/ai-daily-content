---
id: inbox_f54eb5b1
date: 2026-10-31
source_ref: "[[00-inbox/2026-10-31/0019-medium-tag-claude-your-ai-agent-trusts-every-mcp-server-yo-6651]]"
title: "Your AI agent trusts every MCP server you install. So I built a scanner that doesn’t."
url: https://medium.com/@mahamadaliyevbotirjon184/your-ai-agent-trusts-every-mcp-server-you-install-so-i-built-a-scanner-that-doesnt-bdd511c223ab?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-10-31T16:56:29+00:00
fetched_at: 2026-11-01T00:27:17.557213+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AI 代理預設信任所有安裝的 MCP server，作者做了不預設信任的掃描器。 **Why** 代理會直接執行 MCP 工具描述與設定檔中的內容，風險容易被忽略。 **How** 文中列出作者發現的攻擊面，但原文只有摘要，未說明掃描器的實作方式。 **What** 作者列出的問題包括：工具描述被投毒、規則檔含不可見文字、.mcp.json 含 token，以及 hook 會把 curl 導入 bash。"
key_points:
  - "工具描述（tool description）可被投毒，代理會將其視為可信內容"
  - "規則檔中可藏有不可見文字，人工審查難以發現"
  - ".mcp.json 與 hooks 中出現 token，且 hook 會把 curl 輸出導入 bash"
tags: [mcp, security, prompt-injection, agent-security, scanner]
topics: [agents.mcp, security]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Your AI agent trusts every MCP server you install. So I built a scanner that doesn’t.

AI 代理預設信任所有安裝的 MCP server，作者做了不預設信任的掃描器。

**Why** 代理會直接執行 MCP 工具描述與設定檔中的內容，風險容易被忽略。

**How** 文中列出作者發現的攻擊面，但原文只有摘要，未說明掃描器的實作方式。

**What** 作者列出的問題包括：工具描述被投毒、規則檔含不可見文字、.mcp.json 含 token，以及 hook 會把 curl 導入 bash。

### 重點
- 工具描述（tool description）可被投毒，代理會將其視為可信內容
- 規則檔中可藏有不可見文字，人工審查難以發現
- .mcp.json 與 hooks 中出現 token，且 hook 會把 curl 輸出導入 bash

**原文：** [medium-tag-claude](https://medium.com/@mahamadaliyevbotirjon184/your-ai-agent-trusts-every-mcp-server-you-install-so-i-built-a-scanner-that-doesnt-bdd511c223ab?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Poisoned tool descriptions, invisible text in rules files, tokens in .mcp.json and hooks that pipe curl into bash. What I found, and an... Continue reading on Medium »

</details>