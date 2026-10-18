---
id: inbox_a33f4c50
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-claude-mem-releases-v14-0-0-5c8d]]"
title: "v14.0.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v14.0.0
source: claude-mem-releases
published_at: 2026-10-17T15:50:36+00:00
fetched_at: 2026-10-18T03:20:52.723287+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude-Mem 發布 14.0.0，主打兩項功能：My Work 與 TeamBrain。Claude-Mem 現在預設開啟 My Work，這是一個本機、人類可讀的視圖，列出你交給 agent 的請求與目前進度，提供 Cards、List、Agents 三種檢視，並有「Attention first」排序把需要你處理的項目置頂。每個請求會由你已設定的模型產生日常語言摘要，狀態分為 In progress、Needs you、No recent update、Ready to check、Checked；Review 功能讓使用者自行標記「已確認」，避免把 agent 回報的「done」誤當成人工確認。TeamBrain 為選用的團隊共享功能，只共享團隊選擇分享的工作、脈絡與交接，團隊可自助訂閱，費用為每位成員每月 $50。其他更新包含 Codex 跳過 next-message suggestion 與 rollout-consolidation 的 helper prompt（#4812），以及 Windows 測試直接 spawn 執行中的 Bun（#4814）。升級指令為 npx claude-mem@latest install。"
key_points:
  - "My Work（免費、開源、本機執行）：Cards／List／Agents 三種檢視、「Attention first」排序、五種狀態（In progress、Needs you、No recent update、Ready to check、Checked）"
  - "Review 機制：由人手動標記「已檢查」，區分 agent 回報 done 與人員實際確認"
  - "TeamBrain：選用的團隊共享功能，定價每位成員每月 $50，只分享團隊選擇的內容"
tags: [claude-mem, my-work, teambrain, agent-oversight, human-in-the-loop]
topics: [product_and_org.product, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v14.0.0

Claude-Mem 發布 14.0.0，主打兩項功能：My Work 與 TeamBrain。Claude-Mem 現在預設開啟 My Work，這是一個本機、人類可讀的視圖，列出你交給 agent 的請求與目前進度，提供 Cards、List、Agents 三種檢視，並有「Attention first」排序把需要你處理的項目置頂。每個請求會由你已設定的模型產生日常語言摘要，狀態分為 In progress、Needs you、No recent update、Ready to check、Checked；Review 功能讓使用者自行標記「已確認」，避免把 agent 回報的「done」誤當成人工確認。TeamBrain 為選用的團隊共享功能，只共享團隊選擇分享的工作、脈絡與交接，團隊可自助訂閱，費用為每位成員每月 $50。其他更新包含 Codex 跳過 next-message suggestion 與 rollout-consolidation 的 helper prompt（#4812），以及 Windows 測試直接 spawn 執行中的 Bun（#4814）。升級指令為 npx claude-mem@latest install。

### 重點
- My Work（免費、開源、本機執行）：Cards／List／Agents 三種檢視、「Attention first」排序、五種狀態（In progress、Needs you、No recent update、Ready to check、Checked）
- Review 機制：由人手動標記「已檢查」，區分 agent 回報 done 與人員實際確認
- TeamBrain：選用的團隊共享功能，定價每位成員每月 $50，只分享團隊選擇的內容

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v14.0.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Claude-Mem 14.0.0: My Work and TeamBrain 
 My Work: see what you asked for, and where it stands 
 Claude-Mem now opens on My Work , a local, human-readable view of the requests you've given your agents. 
 
 Cards, List and Agents views. Full-width request cards with the title, a plain-language summary, who worked on it and the project. Switch to a sortable list or a view by agent. "Attention first" sorting brings anything that needs you to the top. 
 Readable summaries. Each request gets a short everyday-language summary of what happened and the next step, written by the model you've already configured. The last good summary stays visible while a new one is written. With no compatible provider, you see the recorded wording. 
 Live status. In progress, Needs you, No recent update, Ready to check and Checked update as work is recorded, without the page jumping while you read. 
 Review. Mark a result as checked yourself, so an agent reporting "done" is never mistaken for a person confirming it. 
 Drill down. Open any request to see the work behind it: workstreams, recorded evidence and the original request. 
 
 My Work is free, open source and runs on your machine. 
 TeamBrain: shared work for teams (optional) 
 TeamBrain brings the work your team chooses to share into the same experience: open work, useful context and handoffs, without anyone's private work being broadcast. Teams can set it up self-serve at $50 per seat per month at https://cmem.ai/teambrain . 
 Also in this release 
 
 Codex: skips next-message suggestion and rollout-consolidation helper prompts ( #4812 ). 
 Windows tests now spawn the running Bun directly ( #4814 ). 
 
 Upgrade: npx claude-mem@latest install

</details>