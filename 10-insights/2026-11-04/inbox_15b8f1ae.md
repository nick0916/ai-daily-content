---
id: inbox_15b8f1ae
date: 2026-11-04
source_ref: "[[00-inbox/2026-11-04/0003-hackernews-tell-hn-gemini-trains-on-chat-history-ev-1c54]]"
title: "Tell HN: Gemini trains on chat history, even for subscribers (personal accounts)"
url: https://news.ycombinator.com/item?id=50363461
source: hackernews
published_at: 2026-11-04T10:10:27+00:00
fetched_at: 2026-11-06T00:09:51.170143+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Gemini 個人帳號即使付費訂閱，只要開著聊天記錄，對話就可能被拿去訓練，也可能被人工審閱。 **Why** 發文者原以為付費訂閱就不會被當成產品，事後才發現並非如此。 **How** 依 Google 支援頁面，Keep Activity 開啟時 Gemini 活動會用於改進服務，包括訓練生成式 AI 模型；要避免只能關閉 Keep Activity 或使用暫時聊天。 **What** 發文者引用 Google 文件：部分對話會由人工審閱，被審閱的聊天刪除活動後仍保留最多三年，且官方警告不要輸入機密資訊；關閉 Keep Activity 後對話約 72 小時後消失。"
key_points:
  - "Keep Activity 開啟時，Gemini app 活動會用於訓練生成式 AI 模型；個人訂閱者除了關閉聊天記錄或用暫時聊天外，沒有其他退出方式（依發文者）"
  - "被人工審閱的聊天不會因刪除活動而刪除，最多保留三年；Google 警告勿輸入機密資訊"
  - "關閉 Keep Activity 可停止訓練使用，但對話約 72 小時後即遺失"
tags: [gemini, data-privacy, training-data, human-review]
topics: [foundation_models.gemini, security]
importance: 3
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Tell HN: Gemini trains on chat history, even for subscribers (personal accounts)

Gemini 個人帳號即使付費訂閱，只要開著聊天記錄，對話就可能被拿去訓練，也可能被人工審閱。

**Why** 發文者原以為付費訂閱就不會被當成產品，事後才發現並非如此。

**How** 依 Google 支援頁面，Keep Activity 開啟時 Gemini 活動會用於改進服務，包括訓練生成式 AI 模型；要避免只能關閉 Keep Activity 或使用暫時聊天。

**What** 發文者引用 Google 文件：部分對話會由人工審閱，被審閱的聊天刪除活動後仍保留最多三年，且官方警告不要輸入機密資訊；關閉 Keep Activity 後對話約 72 小時後消失。

### 重點
- Keep Activity 開啟時，Gemini app 活動會用於訓練生成式 AI 模型；個人訂閱者除了關閉聊天記錄或用暫時聊天外，沒有其他退出方式（依發文者）
- 被人工審閱的聊天不會因刪除活動而刪除，最多保留三年；Google 警告勿輸入機密資訊
- 關閉 Keep Activity 可停止訓練使用，但對話約 72 小時後即遺失

**原文：** [hackernews](https://news.ycombinator.com/item?id=50363461)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

If you have a personal Google AI subscription, all your saved chat history in Gemini can be used for training and there is no way to opt out unless you turn off chat history or use temporary chat sessions. These chat transcripts may even be read by human reviewers. Although Google claims to disconnect them from your account when human-reviewed, they explicitly warn not to enter confidential information . https://support.google.com/gemini/answer/16836988 “[Gemini app activity] is used to improve Google services for everyone, including by training generative AI models, if your Keep Activity setting is on.“ https://support.google.com/gemini/answer/13594961?hl=en#human_review “A subset of chats are reviewed by human reviewers” https://support.google.com/gemini/answer/13594961?hl=en#pn_retain_data “Chats reviewed by human reviewers [...] are not deleted when you delete your activity. Instead, they are retained for up to three years.” https://support.google.com/gemini/answer/13594961?hl=en#pn_data_usage “Please don’t enter confidential information that you wouldn’t want a reviewer to see or Google to use to improve our services, including machine-learning technologies.” To disable their training on your chat sessions, you need to turn off “Keep Activity” in Gemini’s settings. Turning that off means you’ll lose any chat sessions after 72 hours. I learned this too late, thinking that having a paid subscription = not being turned into the product. Apparently paying is not enough. Thank you to this user on HN for mentioning in another thread: https://news.ycombinator.com/item?id=50355424

</details>