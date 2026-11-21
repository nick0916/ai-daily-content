---
id: inbox_94dad2a4
date: 2026-11-20
source_ref: "[[00-inbox/2026-11-20/0047-substack-product-growth-crash-course-in-design-for-pms-8103]]"
title: "Crash Course in Design for PMs"
url: https://www.news.aakashg.com/p/design-sense
source: substack-product-growth
published_at: 2026-11-20T03:01:38+00:00
fetched_at: 2026-11-21T00:53:03.131202+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AI 還不會做設計，PM 得自己培養設計眼光。 **Why** PM 越來越常自己做設計（小公司直接上線 production，大企業則做 AI 原型），但不能指望 AI 處理設計。 **How** 作者用一句 prompt 請 Claude Code 做回饋分類 app「Signal」，再拆解結果的問題，並整理出學設計的順序：學會看、訓練眼力、套用到 AI 工具、與設計師協作。 **What** 作者指出輸出的三個問題：PRD 在摺線下約 470px、排名與自己的數字不符（#1 $895K ARR 卻排在 #2 $1.00M 之前）、輸入區占半個畫面且是小字 monospace 原始文字。文章共 4,400 字、33 張圖，涵蓋 12 個設計概念與訓練眼力的練習。"
key_points:
  - "實測：單一 prompt 讓 Claude Code 做 Signal app，結果三個設計缺陷（核心 PRD 在摺線下 ~470px、排名邏輯與 ARR 數字矛盾、輸入區占半屏）"
  - "引用 Emil Kowalski：「Agents don't have great taste」；作者稱現有 PM 設計資源多停留在 2020 年手繪線框或未提及 AI"
  - "作者整理 8 所頂尖學程與自學課程後發現，教學順序高度一致，並據此編排全文"
tags: [design-sense, ai-pm, claude-code, ai-prototyping, ux]
topics: [agents.coding_agents, product_and_org.product]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Crash Course in Design for PMs

AI 還不會做設計，PM 得自己培養設計眼光。

**Why** PM 越來越常自己做設計（小公司直接上線 production，大企業則做 AI 原型），但不能指望 AI 處理設計。

**How** 作者用一句 prompt 請 Claude Code 做回饋分類 app「Signal」，再拆解結果的問題，並整理出學設計的順序：學會看、訓練眼力、套用到 AI 工具、與設計師協作。

**What** 作者指出輸出的三個問題：PRD 在摺線下約 470px、排名與自己的數字不符（#1 $895K ARR 卻排在 #2 $1.00M 之前）、輸入區占半個畫面且是小字 monospace 原始文字。文章共 4,400 字、33 張圖，涵蓋 12 個設計概念與訓練眼力的練習。

### 重點
- 實測：單一 prompt 讓 Claude Code 做 Signal app，結果三個設計缺陷（核心 PRD 在摺線下 ~470px、排名邏輯與 ARR 數字矛盾、輸入區占半屏）
- 引用 Emil Kowalski：「Agents don't have great taste」；作者稱現有 PM 設計資源多停留在 2020 年手繪線框或未提及 AI
- 作者整理 8 所頂尖學程與自學課程後發現，教學順序高度一致，並據此編排全文

**原文：** [substack-product-growth](https://www.news.aakashg.com/p/design-sense)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Really quickly. The fifth and final cohort of my Land PM Job program starts Monday. If you want 1:1 support from me, plus a structured program to get everything right in your job search, join me . We've helped 41 PMs and aspiring PMs land jobs in the last 12 months. And this is the last time I'll ever be offering this: Join the final cohort Marc Andreessen has this great quote describing the Mexican standoff happening between PM, designers, and engineers: Here's the thing though: most PMs still aren't good enough at design. So today's piece is to help you fix that. Subscribe now Why This Matters Now Should design sense matter for a PM now? I say yes. And not because designers don't matter anymore. But because PMs ARE designing more. And yes, I know it's different where you work... In smaller AI-native companies, PMs are shipping to production . We all know that. But in big enterprise, PMs are also designing, just in a different way. They are building AI prototypes. Now with the advance of AI, you would've thought it would have design sense, right? But right now, the fact is... you can't rely on the AI to handle design for you. AI is (Still) Bad at Design You'd think, with all the "RIP designers" social media posts over the last few years that AI could design by now. So I tested it for this piece. I asked Claude Code for a feedback triage app in one prompt: Build me a single-file web app called Signal for product managers. I paste in customer feedback (or load the sample data), and AI groups it into themes, ranks the themes by how many customers mention them and the ARR of those accounts, and lets me click a theme to draft a one-page PRD from it.

Use realistic sample data from a B2B SaaS company (about 40 feedback items). Fake the AI with a short delay so it works offline. One index.html, no build step.
 This was the output: And this simple example proves my larger point (which you probably intuitively already agree with): "Agents don't have great taste." —Emil Kowalski, who teaches animations.dev and runs this Claude skills repo Now we can all say this is a bad design, but can you articulate why? As an exercise, consider diagnosing them yourself before reading the answer. From a design sense POV, I would point to three major ones: The answer is below the fold. The PRD, the whole point of the screen, is ~470px under the fold. The ranking doesn't match its own numbers. #1 is worth $895K in ARR and #2 is... $1.00M. Why does it have a lower score? We don't know. Our input is half the screen. The same feedback a user pasted in is shown as raw pipe-separated text in tiny monospace on half the surface area. Basically, the design stinks. Instead, we must be able to create something like this: Look at how much better it uses the space: The PRD output sits beside the themes, the ranking shows its math, and your pasted feedback collapses into one line. In today's post, I show you how to design like this. Why I Needed to Write This Search "design sense for product managers" on Google and there is literally nothing: If you dig deeper than Google, there are some great resources out there, but... they have not been updated for the age of AI! Vikram Goyal's 5 tactics for PMs to improve their design sense is from 2020 and focused on sketching wireframes by hand Mind the Product's design fundamentals every PM should know is from 2025, but doesn't even have the word AI in it This guide plugs that gap. Today's Deep Dive Word count: 4,400 | Image count: 33 | Time to Complete: 3-5 hrs I've been talking to design leaders, researching design, and building my own skill over the past 16 years in product to put together this crash course in design for you: Learn design like a designer The 12 most important concepts in design The drills designers use to train their eye How to get AI tools to design well Working with your designer Where to go from here Subscribe now 1. Learn design like a designer I went through every resource I could to learn how designers learn. I started with the courses at 8 of the top degree programs from Carnegie Mellon and Stanford to TU Delft and ArtCenter . I also went through the self-taught courses: Google's UX Design Certificate (1.57M learners on Coursera), Apple's Human Interface Guidelines , NN/g , Laws of UX , plus recent courses from Emil Kowalski , Rauno Freiberg and Josh Puckett . Each has its own tools and its own taste... but what I found insane is the order they teach in is close to identical : This newsletter-as-course follows the same order, compressed into one sitting: Section 2 teaches you to see Section 3 trains your eye Section 4 applies it to your AI tools and section 5 to working with your designer Section 6 shows where to go from here So let's start with helping you see better. This is just one of 70+ career deep dives I send you every year with your subscription. Recent pieces have covered product leadership interviews and PM pay and hiring in 2026 . Plus, you get access to my bundle , including Mobbin, Magic Patterns, Reforge Build, Linear, Airtable, Dovetail, Arize, Descript and Speechify. 
 
 
 Read more

</details>