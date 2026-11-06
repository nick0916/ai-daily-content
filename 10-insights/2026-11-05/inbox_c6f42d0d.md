---
id: inbox_c6f42d0d
date: 2026-11-05
source_ref: "[[00-inbox/2026-11-05/0003-lobsters-ai-software-line-specialist-fc60]]"
title: "Software Line Specialist"
url: https://lovro-bikic.github.io/software-line-specialist/
source: lobsters-ai
published_at: 2026-11-05T10:32:29-06:00
fetched_at: 2026-11-06T00:14:24.031766+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "ACME Inc. 招募 TypeScript 除錯專員，處理 AI 代理反覆迴圈、無法解決的疑難問題。 **Why** 公司表示部分問題不受 prompt 影響，代理會陷入迴圈，修好一處又壞另一處。 **How** 由人類工程師讀取程式碼、查看日誌與資料庫列，獨立完成修正與 postmortem。 **What** 職缺為單一議題、不含功能開發的全職角色，要求 5 年以上 pre-2022 TypeScript 經驗與 Postgres 管理經驗；流程含 CV 篩選、電話面試、現場除錯與 CTO 面試。"
key_points:
  - "公司自稱兩年來全面 AI-first，設計、開發、QA、CI/CD 與資料分析皆由代理參與，並表示「我們的技術棧是英文」。"
  - "職位任務包括接手代理未解決的 issue、撰寫 postmortem 以訓練代理，並可一次只處理一個問題。"
  - "面試含無 AI 的現場除錯題：找出並修正刻意植入的錯誤。"
tags: [hiring, ai-native-engineering, debugging, typescript, agent-failure-modes]
topics: [agents.coding_agents, product_and_org.adoption]
importance: 2
novelty: 2
insight_quality: 2
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Software Line Specialist

ACME Inc. 招募 TypeScript 除錯專員，處理 AI 代理反覆迴圈、無法解決的疑難問題。

**Why** 公司表示部分問題不受 prompt 影響，代理會陷入迴圈，修好一處又壞另一處。

**How** 由人類工程師讀取程式碼、查看日誌與資料庫列，獨立完成修正與 postmortem。

**What** 職缺為單一議題、不含功能開發的全職角色，要求 5 年以上 pre-2022 TypeScript 經驗與 Postgres 管理經驗；流程含 CV 篩選、電話面試、現場除錯與 CTO 面試。

### 重點
- 公司自稱兩年來全面 AI-first，設計、開發、QA、CI/CD 與資料分析皆由代理參與，並表示「我們的技術棧是英文」。
- 職位任務包括接手代理未解決的 issue、撰寫 postmortem 以訓練代理，並可一次只處理一個問題。
- 面試含無 AI 的現場除錯題：找出並修正刻意植入的錯誤。

**原文：** [lobsters-ai](https://lovro-bikic.github.io/software-line-specialist/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Software Line Specialist

Your responsibilities

We think you’d be great if you...

Nice to have

Interview process

This is a code-only role; for AI-native jobs, please look at our other listings

We’re looking for a senior software line specialist, in TypeScript !

ACME Inc. is a fast-growing startup helping small businesses monitor their financials. We work with business owners across the globe, turning their feedback into actionable insights. Backed by Maltese Falcon Capital, we recently raised a $15M Series A to bring effortless monitoring to every brick-and-mortar store.

You’ll be joining a high-performance, close-knit team of AI natives! We’ve been AI-first for the past 2 years, with every part of the product agent-friendly and interconnected: design, development, QA, CI/CD, infra, data analysis. We like to say that our stack is English!

While English has gotten us 99.5% of the way there, we’re in need of a hands-on engineer ready to close the final 0.5%. Over time, we’ve noticed some issues that are immune to prompts and catch agents in loops. Sometimes, the issue at hand gets fixed, but it results in another issue. This is where you step in. As a line specialist, your job will be to investigate and fix complex issues, primarily by reading the underlying code.

We’re looking for someone ready to open an IDE and dive deep into an unknown codebase — a fearless detective who is comfortable inspecting logs and database rows, and has the know-how to piece all the information together. The perfect candidate should be willing to work on a problem for hours, sometimes even days.

This is a new position for us. We expect someone who works autonomously, makes sound decisions independently and takes full ownership of their work. We are happy to help in any way we can (you’ll have access to agents’ reasoning traces), but ultimately we depend on your confidence in understanding the problem and shipping a solution.

We feel it prudent to point out that you will be allowed to work on one thing at a time in this role. While parallel development is the default, we understand line specialists prefer to tackle problems in a single-threaded manner, so we will do our best to provide a distraction-free environment for your best work.

To be clear, this role does not include feature development. You’re welcome to look at our AI-native listings if you have more interest in such work!

Think you’re the IDEal fit? Apply now!

take over unresolved issues from agents

read the codebase, go over application logs, query the database

prepare, test, review and ship fixes by yourself

write postmortems for agent training

occasionally consult on unreleased features

onboard and mentor a future junior line specialist

have at least 5 years of pre-2022 TypeScript experience

are comfortable running tests manually and using a “debugger”

can reason from first principles

can work on a problem with sustained attention for hours

are autonomous and an independent thinker

previous experience as a line specialist

DB administration experience (our agents say it’s Postgres)

AI prompting basics

CV screening

HR phone screen

In-house paper-and-pencil exam multiple-choice questions (e.g. you’re given a TypeScript expression, choose the correct result) explain concepts in your own words (for example, ACID) complete the code block find the bug in a function 

multiple-choice questions (e.g. you’re given a TypeScript expression, choose the correct result)

explain concepts in your own words (for example, ACID)

complete the code block

find the bug in a function

Live debugging assignment application with an intentional defect; candidates are required to find and fix the issue without the use of AI 

application with an intentional defect; candidates are required to find and fix the issue without the use of AI

Culture fit interview

CTO interview

Offer

</details>