---
id: inbox_4f8d4121
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0256-simon-willison-chirp-pong-0007]]"
title: "Chirp Pong"
url: https://simonwillison.net/2026/Oct/15/chirp-pong/
source: simon-willison
published_at: 2026-10-15T19:47:52+00:00
fetched_at: 2026-10-18T03:03:45.775746+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 發布小工具 Chirp Pong，是一個遊戲實驗：兩位玩家用各自的手機，在靜態 HTML 中透過麥克風接收「啁啾聲 (chirps)」傳遞網路資料，進行雙人對戰的類 Pong 遊戲，結果「看起來可行」。他給的 prompt 要求做出雙人競技、手機靠近、遊戲狀態以網頁麥克風 API 可解讀的聲音傳送，並加入比 Pong 更有趣的畫面與玩法變化。原文註明使用的是 Claude Code 中的「Claude Opus 5.5 Extra」。實務意義在於展示純靜態 HTML 加音訊通道，即可在不需伺服器的情況下做近距離雙機同步，也是 coding agent 快速原型實驗的一例。"
key_points:
  - "雙手機、純靜態 HTML，用麥克風接收的聲音 chirps 作為網路傳輸層"
  - "以單一 prompt 在 Claude Code 中由 Claude Opus 5.5 Extra 產出"
  - "驗證近距離、無伺服器的音訊通道同步遊戲狀態可行"
tags: [chirp-pong, audio-networking, claude-code, game-design, prototype]
topics: [agents.coding_agents]
importance: 2
novelty: 3
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Chirp Pong

Simon Willison 發布小工具 Chirp Pong，是一個遊戲實驗：兩位玩家用各自的手機，在靜態 HTML 中透過麥克風接收「啁啾聲 (chirps)」傳遞網路資料，進行雙人對戰的類 Pong 遊戲，結果「看起來可行」。他給的 prompt 要求做出雙人競技、手機靠近、遊戲狀態以網頁麥克風 API 可解讀的聲音傳送，並加入比 Pong 更有趣的畫面與玩法變化。原文註明使用的是 Claude Code 中的「Claude Opus 5.5 Extra」。實務意義在於展示純靜態 HTML 加音訊通道，即可在不需伺服器的情況下做近距離雙機同步，也是 coding agent 快速原型實驗的一例。

### 重點
- 雙手機、純靜態 HTML，用麥克風接收的聲音 chirps 作為網路傳輸層
- 以單一 prompt 在 Claude Code 中由 Claude Opus 5.5 Extra 產出
- 驗證近距離、無伺服器的音訊通道同步遊戲狀態可行

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/15/chirp-pong/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Tool: Chirp Pong 
 Another game experiment - I wanted to see if it was feasible to have a two player game on two separate phones running in static HTML where the networking code uses chirps sent via the microphone. It seems to work! 
 
 Build a two player competitive pong like game where two players use their phones close to each other and the game state is sent via audio noises which the web microphone API can interpret - but add graphical and gameplay twists to make it a lot more fun and intertwine than pong 
 
 Claude Opus 5.5 Extra in Claude Code . 
 
 
 Tags: game-design , ai , generative-ai , llms , claude-code

</details>