---
id: inbox_54ab9bfe
date: 2026-10-24
source_ref: "[[00-inbox/2026-10-24/0100-simon-willison-battledrones-v14-compass-rose-a-four-pla-4f66]]"
title: "battledrones v14: Compass Rose, a four player map"
url: https://simonwillison.net/2026/Oct/24/battledrones/
source: simon-willison
published_at: 2026-10-24T03:59:57+00:00
fetched_at: 2026-10-25T01:07:27.306488+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 的對戰遊戲 Battledrones 新增四人連線地圖，由 AI 依一句 prompt 寫出新地圖與網路程式碼。 **Why** 先前地圖只支援兩名玩家，無法四人同玩。 **How** 他用一段 prompt 要求四向旋轉對稱地圖、最多四個 AI 玩家、沿用 WebSocket 非音訊多人模式（人類不足的位置由 AI 補上）；Claude Opus 5.5 新增地圖並修改多人網路程式碼。 **What** Battledrones v14 推出「Compass Rose」四人地圖，玩家可透過分享連結或 QR code 加入。新增紫色與綠色機器人隊伍，加入原有的藍、紅。作者另附開啟「Goliath Armada」mutator（每方起始四台巨型 Goliath 機甲）的四方 AI 對戰重播連結。"
key_points:
  - "v14 新增「Compass Rose」四人地圖，設計為四向旋轉對稱，最多四名人類玩家，空位由 AI 補上"
  - "Claude Opus 5.5 同時新增地圖並修改 WebSocket 多人網路程式碼，支援分享連結與 QR code 加入"
  - "新增紫色與綠色機器人隊伍，並提供開啟 Goliath Armada mutator 的四方 AI 對戰重播"
tags: [battledrones, claude-opus-5-5, game-design, multiplayer, websocket]
topics: [agents.coding_agents, foundation_models.claude]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## battledrones v14: Compass Rose, a four player map

Simon Willison 的對戰遊戲 Battledrones 新增四人連線地圖，由 AI 依一句 prompt 寫出新地圖與網路程式碼。 **Why** 先前地圖只支援兩名玩家，無法四人同玩。 **How** 他用一段 prompt 要求四向旋轉對稱地圖、最多四個 AI 玩家、沿用 WebSocket 非音訊多人模式（人類不足的位置由 AI 補上）；Claude Opus 5.5 新增地圖並修改多人網路程式碼。 **What** Battledrones v14 推出「Compass Rose」四人地圖，玩家可透過分享連結或 QR code 加入。新增紫色與綠色機器人隊伍，加入原有的藍、紅。作者另附開啟「Goliath Armada」mutator（每方起始四台巨型 Goliath 機甲）的四方 AI 對戰重播連結。

### 重點
- v14 新增「Compass Rose」四人地圖，設計為四向旋轉對稱，最多四名人類玩家，空位由 AI 補上
- Claude Opus 5.5 同時新增地圖並修改 WebSocket 多人網路程式碼，支援分享連結與 QR code 加入
- 新增紫色與綠色機器人隊伍，並提供開啟 Goliath Armada mutator 的四方 AI 對戰重播

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/24/battledrones/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: battledrones v14: Compass Rose, a four player map 
 I added four player online mode to Battledrones - previous maps were limited to two. 
 Here's the initial prompt I used: 
 
 Add a new map for a four player battle - four way rotational symmetry, up to four AI players, works with the WebSocket non-audio based multiplayer mode so up to four human players can join (any spare slots use AI) 
 
 Claude Opus 5.5 added a new map called "Compass Rose" and modified the WebSockets multiplayer network code to support up to four players for that map, joining via share links or QR codes. 
 
 The new teams use robots themed in purple and green, joining the existing blue and red designs. You can preview those colors in the updated model browser . 
 Here's a replay link to watch a four way AI battle with the "Goliath Armada" mutator turned on, where each side starts with four giant Goliath mech units. 
 
 
 Tags: game-design , projects , claude

</details>