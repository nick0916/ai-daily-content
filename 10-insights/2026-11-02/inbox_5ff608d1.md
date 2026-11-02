---
id: inbox_5ff608d1
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2325-simon-willison-the-u-s-census-bureau-and-super-intellig-0ca2]]"
title: "The U.S. Census Bureau and “Super Intelligence”"
url: https://simonwillison.net/2026/Nov/2/census-bureau-super-intelligence/
source: simon-willison
published_at: 2026-11-02T13:31:26+00:00
fetched_at: 2026-11-02T23:29:51.340010+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "美國普查局的 AI 採用率調查因行政命令，把題目中的「AI」改成「Super Intelligence」，歷年數據更難比較。 **Why** 這份調查是追蹤美國企業 AI 採用趨勢的少數官方資料，題目措辭改動會影響數字能否跨期比較。 **How** Simon Willison 用最新 BTOS 數據（2026/10/22 發布）搭配 GPT-6 Astra Extra High 重做去年的圖表，並比對問卷題目的前後版本。 **What** BTOS 每兩週調查 20 萬家企業（共 120 萬家，每家每 12 週填一次）。2025/11/17 題目由「用於生產商品或服務」改為「用於任何業務功能」，250 人以上大企業回答「是」的比例從約 12% 升至 2026/2 約 30%、2026/10 約 40%；自 2026/10/19 起因 Executive Order 14434 改問 Super Intelligence (SI)，首批新措辭結果預計本週四公布，目前數字仍是舊措辭。"
key_points:
  - "2025/11/17 題目由「producing goods or services」改為「any of its business functions」，前後數據不可直接比較"
  - "250+ 員工企業：2025/9 約 12% → 2026/2 約 30% → 2026/10 約 40%"
  - "2026/10/19 起問卷依 Executive Order 14434 改用「Super Intelligence or SI」；新措辭首批結果本週四公布"
tags: [census-bureau, btos, ai-adoption, survey-methodology, simon-willison]
topics: [product_and_org.adoption]
importance: 3
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## The U.S. Census Bureau and “Super Intelligence”

美國普查局的 AI 採用率調查因行政命令，把題目中的「AI」改成「Super Intelligence」，歷年數據更難比較。

**Why** 這份調查是追蹤美國企業 AI 採用趨勢的少數官方資料，題目措辭改動會影響數字能否跨期比較。

**How** Simon Willison 用最新 BTOS 數據（2026/10/22 發布）搭配 GPT-6 Astra Extra High 重做去年的圖表，並比對問卷題目的前後版本。

**What** BTOS 每兩週調查 20 萬家企業（共 120 萬家，每家每 12 週填一次）。2025/11/17 題目由「用於生產商品或服務」改為「用於任何業務功能」，250 人以上大企業回答「是」的比例從約 12% 升至 2026/2 約 30%、2026/10 約 40%；自 2026/10/19 起因 Executive Order 14434 改問 Super Intelligence (SI)，首批新措辭結果預計本週四公布，目前數字仍是舊措辭。

### 重點
- 2025/11/17 題目由「producing goods or services」改為「any of its business functions」，前後數據不可直接比較
- 250+ 員工企業：2025/9 約 12% → 2026/2 約 30% → 2026/10 約 40%
- 2026/10/19 起問卷依 Executive Order 14434 改用「Super Intelligence or SI」；新措辭首批結果本週四公布

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/2/census-bureau-super-intelligence/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I was reminded today of AI Adoption Rate Trending Down for Large Companies , a chart produced by Apollo Global Management in September 2025, which appeared to show a slowdown in U.S. corporate AI adoption based on numbers collected by the U.S. Census Bureau. At the time I used that chart to demonstrate GPT-5 data analysis , and then to experiment with Claude's new Code Interpreter . I decided to try running those numbers again to see what had changed over the past year, and in doing so learned that the Bureau has fallen foul of Executive Order 14434 , aka the asinine Super Intelligence one. 
 First, the updated chart 
 Every two weeks the U.S. Census Bureau runs a survey called the Business Trends and Outlook Survey (aka BTOS). Each time it goes to 200,000 businesses out of 1.2 million total - the surveyed group (a "panel") cycles such that an individual business only completes the survey every twelve weeks. 
 The latest data is published on alternating Thursdays at 10am. 
 I used the most recent numbers (published October 22, 2026) to create a new version ( GPT-6 Astra Extra High transcript ) of the AI adoption chart, updated to reflect both the last twelve months and a change that was made to the survey question sent out by the Bureau: 
 

 For comparison, here's that AI adoption chart from last year (my GPT-5 version):
 

 In September 2025 the largest (250+ employees) companies answered "yes" around 12% of the time to the question about whether they used AI in "producing goods or services". 
 Under the new "any business function" wording, by February 2026, those same large companies answered "yes" around 30% of the time, and by October 2026 that had increased to around 40%. 
 The data in the above chart comes from the "Employment size class" XLSX file, available from here . Here's a copy of the file I used. 
 You can view the survey document that is sent out to businesses - here's my snapshot copy of that 346KB PDF. 
 The changing language of the questions 
 As the chart demonstrates, the question asked by the Bureau changed in a material way on November 17th, 2025. Prior to that date, the question they asked was this (emphasis mine): 
 
 In the last two weeks, did this business use Artificial Intelligence (AI) in producing goods or services ? (Examples of AI: machine learning, natural language processing, virtual agents, voice recognition, etc.) 
 
 On December 3rd, 2025, the Bureau announced a significant change to that question. Here's the replacement: 
 
 In the last two weeks, did this business use Artificial Intelligence (AI) in any of its business functions ? (Examples of AI: machine learning, natural language processing, virtual agents, voice recognition, etc.) 
 
 No more "producing goods or services" - now it's "in any of its business functions"! This means that the answers to the question before and after November 17th are not directly comparable. 
 From October 19, 2026, they ask about Super Intelligence 
 When I went looking for the updated question language in the latest XLSX file, I couldn't find it. I found this instead: 
 
 In the last two weeks, did this business use Super Intelligence or SI (formerly referred to as Artificial Intelligence or AI) in any of its business functions? (Examples of SI use include: SI-powered data analysis; generative SI for marketing, product design, or coding; virtual SI agents for customer service; SI-powered forecasting or pricing; SI-driven computer vision for quality control, etc.) 
 
 The BTOS about page explains what happened: 
 
 Beginning with the October 19, 2026 collection, instrument wording was updated due to Executive Order 14434 . 
 
 The current numbers reflect the old Artificial Intelligence survey wording - the first survey results reflecting the Super Intelligence wording are due for publication on Thursday. 
 Is this going to affect the survey? 
 The obvious open question here is whether this wording change is going to affect the survey results. 
 The businesses answering this survey will have last seen that question twelve weeks ago, when it was still called AI. Hopefully the new language isn't going to confuse them, especially since the survey helpfully spells out "formerly referred to as Artificial Intelligence or AI". 
 I can't help but laugh at the absurdity of "SI-powered data analysis; generative SI for marketing, product design, or coding; virtual SI agents for customer service" though. 
 
 Tags: census , surveys , ai , generative-ai , llms

</details>