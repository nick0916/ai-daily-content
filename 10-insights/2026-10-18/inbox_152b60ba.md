---
id: inbox_152b60ba
date: 2026-10-18
source_ref: "[[00-inbox/2026-10-18/0256-medium-tag-claude-one-misplaced-block-made-every-message-r-2fb2]]"
title: "One Misplaced Block Made Every Message Rewrite 19,000 Cached Tokens"
url: https://medium.com/@amariah.abish/one-misplaced-block-made-every-message-rewrite-19-000-cached-tokens-b85dc98a9457?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-10-18T01:13:44+00:00
fetched_at: 2026-10-18T03:17:34.731493+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章指出，在 AI coding agent 中，prompt caching 是最便宜的優化手段，因為 system prompt 與 tool definitions 在每次請求中都相同，可被快取。標題陳述的案例是：一個放錯位置的 block 導致每則訊息都重寫 19,000 個 cached tokens，使快取失效。原文片段沒有說明那個 block 具體是什麼、放在哪裡，也沒有給出成本影響的數字，這些細節無法確定。可抽象出的原則是：快取依賴穩定的前綴，任何變動內容若出現在穩定內容之前，就可能讓整段快取被重寫。這個「前綴穩定性」的推論來自 prompt caching 的一般運作方式，並非原文片段明載。"
key_points:
  - "案例數字：單一放錯位置的 block 造成每則訊息重寫 19,000 個 cached tokens"
  - "System prompt 與 tool definitions 每次請求相同，是 prompt caching 的主要受益對象"
  - "具體是哪個 block、如何修正，原文片段未提供（無法確定）"
tags: [prompt-caching, coding-agent, token-cost, context-engineering]
topics: [engineering.inference, agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## One Misplaced Block Made Every Message Rewrite 19,000 Cached Tokens

文章指出，在 AI coding agent 中，prompt caching 是最便宜的優化手段，因為 system prompt 與 tool definitions 在每次請求中都相同，可被快取。標題陳述的案例是：一個放錯位置的 block 導致每則訊息都重寫 19,000 個 cached tokens，使快取失效。原文片段沒有說明那個 block 具體是什麼、放在哪裡，也沒有給出成本影響的數字，這些細節無法確定。可抽象出的原則是：快取依賴穩定的前綴，任何變動內容若出現在穩定內容之前，就可能讓整段快取被重寫。這個「前綴穩定性」的推論來自 prompt caching 的一般運作方式，並非原文片段明載。

### 重點
- 案例數字：單一放錯位置的 block 造成每則訊息重寫 19,000 個 cached tokens
- System prompt 與 tool definitions 每次請求相同，是 prompt caching 的主要受益對象
- 具體是哪個 block、如何修正，原文片段未提供（無法確定）

**原文：** [medium-tag-claude](https://medium.com/@amariah.abish/one-misplaced-block-made-every-message-rewrite-19-000-cached-tokens-b85dc98a9457?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Prompt caching is the cheapest win in an AI coding agent. The system prompt and tool definitions are the same on every request, so the&#x2026; Continue reading on Medium »

</details>