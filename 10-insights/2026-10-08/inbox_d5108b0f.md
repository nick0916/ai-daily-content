---
id: inbox_d5108b0f
date: 2026-10-08
source_ref: "[[00-inbox/2026-10-08/0256-claude-code-releases-v2-1-294-2979]]"
title: "v2.1.294"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.294
source: claude-code-releases
published_at: 2026-10-08T05:03:54+00:00
fetched_at: 2026-10-18T02:59:37.236669+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code v2.1.294 發布，內容為兩項 hook 相關修正。第一，修正以「指令句」形式撰寫的 prompt hook 與 agent hook（例如「Block commands that...」）會誤放行本應攔截內容的問題。第二，改善 Stop 與 SubagentStop 事件上以指令句撰寫的 prompt hook（例如「Carry on if the build is broken」）的判斷方式，讓 Claude 較不會提早停止。實務上，使用指令式語句撰寫 hook 規則的開發者應升級，以避免攔截失效。"
key_points:
  - "修正指令式 prompt/agent hook（如「Block commands that...」）反而放行應攔截內容的問題"
  - "改善 Stop 與 SubagentStop 的指令式 prompt hook 判斷，降低 Claude 提早停止的機率"
tags: [claude-code, hooks, bugfix, release-notes]
topics: [agents.coding_agents]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.294

Claude Code v2.1.294 發布，內容為兩項 hook 相關修正。第一，修正以「指令句」形式撰寫的 prompt hook 與 agent hook（例如「Block commands that...」）會誤放行本應攔截內容的問題。第二，改善 Stop 與 SubagentStop 事件上以指令句撰寫的 prompt hook（例如「Carry on if the build is broken」）的判斷方式，讓 Claude 較不會提早停止。實務上，使用指令式語句撰寫 hook 規則的開發者應升級，以避免攔截失效。

### 重點
- 修正指令式 prompt/agent hook（如「Block commands that...」）反而放行應攔截內容的問題
- 改善 Stop 與 SubagentStop 的指令式 prompt hook 判斷，降低 Claude 提早停止的機率

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.294)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Fixed prompt and agent hooks written as instructions (such as "Block commands that...") allowing what they should block 
 Improved how prompt hooks on Stop and SubagentStop written as instructions (such as "Carry on if the build is broken") are judged, so Claude is less likely to stop early

</details>