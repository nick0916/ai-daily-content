---
id: inbox_b815fdba
date: 2026-11-26
source_ref: "[[00-inbox/2026-11-26/0052-claude-mem-releases-v16-2-0-88c9]]"
title: "v16.2.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v16.2.0
source: claude-mem-releases
published_at: 2026-11-26T02:48:38+00:00
fetched_at: 2026-11-27T01:03:08.511122+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude-Mem 16.2.0 推出 iMessage 群組對話觀察器與 Mac 版 Messages 應用程式。 **Why** 群組對話中的決定、計畫與分工常散落在聊天紀錄中，難以回頭查找。 **What** 加入 Photon iMessage 線路並執行 npx claude-mem imessage setup 後，每個群組會有獨立的 Claude-Mem 專案，記錄決定、計畫、請求與分享內容；Mac 版應用程式可挑選對話與觀察重點，只讀取新訊息，不發送、不反應、不修改群組。"
key_points:
  - "iMessage 群組觀察器只讀不寫，每個群組對應一個 Claude-Mem 專案（#6457）"
  - "Mac 版 Claude-Mem Messages 可勾選對話並設定觀察重點，例如「誰付款、誰欠錢」（#6482）"
  - "終端機指令 npx claude-mem imessage mac 提供 check、chats、pick、observe、contacts 等子命令"
tags: [imessage, group-chat, macos, claude-mem, read-only-observer]
topics: [product_and_org.product, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v16.2.0

Claude-Mem 16.2.0 推出 iMessage 群組對話觀察器與 Mac 版 Messages 應用程式。

**Why** 群組對話中的決定、計畫與分工常散落在聊天紀錄中，難以回頭查找。

**What** 加入 Photon iMessage 線路並執行 npx claude-mem imessage setup 後，每個群組會有獨立的 Claude-Mem 專案，記錄決定、計畫、請求與分享內容；Mac 版應用程式可挑選對話與觀察重點，只讀取新訊息，不發送、不反應、不修改群組。

### 重點
- iMessage 群組觀察器只讀不寫，每個群組對應一個 Claude-Mem 專案（#6457）
- Mac 版 Claude-Mem Messages 可勾選對話並設定觀察重點，例如「誰付款、誰欠錢」（#6482）
- 終端機指令 npx claude-mem imessage mac 提供 check、chats、pick、observe、contacts 等子命令

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v16.2.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

iMessage group chats 
 
 The iMessage group chat observer keeps Claude-Mem notes on a group chat ( #6457 ). Add a Photon iMessage line to the group and run npx claude-mem imessage setup . Each group chat gets its own Claude-Mem project with what the group decided, planned, asked for and shared, and who said what. It only reads: it never sends, reacts or changes a group. See docs/imessage-group-observer.md . 
 
 iMessage on your Mac 
 
 Claude-Mem Messages, a Mac app that keeps notes on the iMessage chats you pick ( #6482 ). It lists your chats and group chats from the Messages app on your own Mac. Tick the ones to observe and write what to watch for in each ("plans and who's bringing what", "money: who paid, who owes"). New messages in those chats become notes in one Claude-Mem project per chat. It only reads: it never sends, reacts or changes a chat, and nothing is added to the group. Only new messages are read, from when it starts listening. The app needs Full Disk Access, and its setup screen walks you through turning it on. Download the unsigned build from the "iMessage Mac app" check, or build it with integrations/imessage-mac/scripts/build-app.sh . See docs/imessage-mac-app.md . 
 claude-mem imessage mac commands do the same from Terminal: check , chats , pick (with --focus for what to watch for), observe and contacts .

</details>