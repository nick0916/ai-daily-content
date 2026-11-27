---
id: inbox_d167f848
date: 2026-11-26
source_ref: "[[00-inbox/2026-11-26/0052-claude-mem-releases-v17-0-0-133a]]"
title: "v17.0.0"
url: https://github.com/thedotmack/claude-mem/releases/tag/v17.0.0
source: claude-mem-releases
published_at: 2026-11-26T05:00:39+00:00
fetched_at: 2026-11-27T01:03:08.510092+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude-Mem 17.0.0 推出 My Work 的 Review Stack 與 macOS iMessage 整合。 **Why** 代理產生的檔案與連結需要集中審閱，而 iMessage 群組對話中的決策也常被遺漏。 **What** Review Stack 可在本機或 Cloud Sync 的 Work View 中逐張檢視、標記已閱或留下後續追蹤；新增 Claude-Mem Messages macOS 應用程式，可選擇 iMessage 對話並把新訊息寫成可搜尋的筆記，需要完整磁碟取用權限。"
key_points:
  - "Review Stack：按住 Seen 三秒可將整個 Focus Area 標為已閱，可還原群組操作"
  - "Claude-Mem Messages for macOS 讀取 Mac 上你選的 iMessage 對話，每個群組各為一個專案，只讀不寫，需 Full Disk Access"
  - "Photon iMessage 來源需使用 Photon 憑證，並把該線路加入要觀察的群組"
tags: [claude-mem, review-stack, imessage, macos, major-release]
topics: [product_and_org.product, agents.coding_agents]
importance: 4
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v17.0.0

Claude-Mem 17.0.0 推出 My Work 的 Review Stack 與 macOS iMessage 整合。

**Why** 代理產生的檔案與連結需要集中審閱，而 iMessage 群組對話中的決策也常被遺漏。

**What** Review Stack 可在本機或 Cloud Sync 的 Work View 中逐張檢視、標記已閱或留下後續追蹤；新增 Claude-Mem Messages macOS 應用程式，可選擇 iMessage 對話並把新訊息寫成可搜尋的筆記，需要完整磁碟取用權限。

### 重點
- Review Stack：按住 Seen 三秒可將整個 Focus Area 標為已閱，可還原群組操作
- Claude-Mem Messages for macOS 讀取 Mac 上你選的 iMessage 對話，每個群組各為一個專案，只讀不寫，需 Full Disk Access
- Photon iMessage 來源需使用 Photon 憑證，並把該線路加入要觀察的群組

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v17.0.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Review Stack in My Work 
 
 Open Review Stack in local My Work or in your signed-in Cloud Sync Work View to review files, images, links and other work your agents submit. Browse lets you flip through a stack. Switch to Work to mark a card Seen, save it for later or leave a follow-up. 
 Hold Seen for three seconds to mark a whole Focus Area seen. You can undo the group action, revisit a card and find saved items and follow-ups across paired devices. 
 
 Claude-Mem Messages for macOS 
 
 Choose Messages on your Mac or an authorized Photon iMessage line in the app. For Mac Messages, select the chats and the topics to watch. For Photon, add the line to the groups you want to observe. New group conversations become searchable Claude-Mem notes in a project for each chat. 
 The read-only observer starts with new messages when you begin listening. From Terminal, use npx claude-mem imessage mac to check access, list chats, save picks, listen and import contact names. npx claude-mem imessage setup configures the Photon line. 
 The Mac app includes the observer for Apple silicon and Intel. The Messages source requires Full Disk Access. The Photon source uses your Photon credentials. Download Claude-Mem Messages for macOS .

</details>