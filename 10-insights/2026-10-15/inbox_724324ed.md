---
id: inbox_724324ed
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0256-medium-towards-data-science-i-tested-four-ways-to-give-an-ai-assista-865e]]"
title: "I Tested Four Ways to Give an AI Assistant a Memory. The Obvious One Was the Worst Value."
url: https://towardsdatascience.com/i-tested-four-ways-to-give-an-ai-assistant-a-memory-the-obvious-one-was-the-worst-value/
source: medium-towards-data-science
published_at: 2026-10-15T11:00:00+00:00
fetched_at: 2026-10-18T03:15:53.726800+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者測試了四種替 AI 助理加上記憶的方法。結果顯示，最直覺的做法是把整段聊天紀錄全部貼進去，這種方式的成本是查詢筆記（looking up notes）的 20 到 31 倍，在任務表現上卻沒有比較好。因此作者認為這個直覺做法的性價比最差。原文摘要沒有列出另外三種方法的完整名稱與各自的任務成績。對建構 AI 助理的開發者而言，這是一個具體的成本數據：記憶機制採用檢索式筆記，可能比塞入完整對話歷史划算很多。"
key_points:
  - "共測試 4 種 AI 助理記憶方式"
  - "貼入完整聊天歷史的成本是查詢筆記的 20–31 倍，任務表現沒有更好"
tags: [ai-memory, context-cost, retrieval, chat-history, cost-benchmark]
topics: [engineering.rag, agents.frameworks]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## I Tested Four Ways to Give an AI Assistant a Memory. The Obvious One Was the Worst Value.

作者測試了四種替 AI 助理加上記憶的方法。結果顯示，最直覺的做法是把整段聊天紀錄全部貼進去，這種方式的成本是查詢筆記（looking up notes）的 20 到 31 倍，在任務表現上卻沒有比較好。因此作者認為這個直覺做法的性價比最差。原文摘要沒有列出另外三種方法的完整名稱與各自的任務成績。對建構 AI 助理的開發者而言，這是一個具體的成本數據：記憶機制採用檢索式筆記，可能比塞入完整對話歷史划算很多。

### 重點
- 共測試 4 種 AI 助理記憶方式
- 貼入完整聊天歷史的成本是查詢筆記的 20–31 倍，任務表現沒有更好

**原文：** [medium-towards-data-science](https://towardsdatascience.com/i-tested-four-ways-to-give-an-ai-assistant-a-memory-the-obvious-one-was-the-worst-value/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Pasting in the whole chat history cost 20 to 31 times more than looking up notes, and it did no better on the tasks. 
 The post I Tested Four Ways to Give an AI Assistant a Memory. The Obvious One Was the Worst Value. appeared first on Towards Data Science .

</details>