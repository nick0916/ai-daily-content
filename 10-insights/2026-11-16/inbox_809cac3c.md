---
id: inbox_809cac3c
date: 2026-11-16
source_ref: "[[00-inbox/2026-11-16/2317-substack-dev-leader-c-refactoring-operators-and-ai-coding-ag-872f]]"
title: "C# Refactoring, Operators, and AI Coding Agents"
url: https://devleader.substack.com/p/c-refactoring-operators-and-ai-coding
source: substack-dev-leader
published_at: 2026-11-16T06:36:17+00:00
fetched_at: 2026-11-17T23:23:57.987945+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Dev Leader 的每週回顧，整理 C# 重構與運算子文章，以及用 AI 寫程式代理的實驗影片。 **What** 文章涵蓋 C# 安全重構流程、重構前的 characterization tests、diff review 找隱藏行為變更、相等性、算術與邏輯運算子、事件訂閱、concurrent collections、MongoDB 索引、composition 的依賴擁有權。影片包含讓 AI 代理在通勤時開發產品、用 Copilot 在 Godot 做遊戲、讓 AI 全權重新設計部落格，以及 Rider x Air x Junie 多代理協作修 UI。"
key_points:
  - "重構系列：先寫 characterization tests 記錄可觀察行為，再小步修改，最後用 diff review 檢查求值順序、null 處理、例外、迴圈出口等隱藏行為變更"
  - "影片實驗：ChatGPT mockup 加 Copilot Autopilot 讓 AI 半自主重新設計部落格，並檢討哪裡出狀況"
  - "另有 Rider x Air x Junie 多個代理 session 同時修錯誤與改 UI 的實測"
tags: [csharp, refactoring, characterization-tests, ai-coding-agents, weekly-recap]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 2
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## C# Refactoring, Operators, and AI Coding Agents

Dev Leader 的每週回顧，整理 C# 重構與運算子文章，以及用 AI 寫程式代理的實驗影片。

**What** 文章涵蓋 C# 安全重構流程、重構前的 characterization tests、diff review 找隱藏行為變更、相等性、算術與邏輯運算子、事件訂閱、concurrent collections、MongoDB 索引、composition 的依賴擁有權。影片包含讓 AI 代理在通勤時開發產品、用 Copilot 在 Godot 做遊戲、讓 AI 全權重新設計部落格，以及 Rider x Air x Junie 多代理協作修 UI。

### 重點
- 重構系列：先寫 characterization tests 記錄可觀察行為，再小步修改，最後用 diff review 檢查求值順序、null 處理、例外、迴圈出口等隱藏行為變更
- 影片實驗：ChatGPT mockup 加 Copilot Autopilot 讓 AI 半自主重新設計部落格，並檢討哪裡出狀況
- 另有 Rider x Air x Junie 多個代理 session 同時修錯誤與改 UI 的實測

**原文：** [substack-dev-leader](https://devleader.substack.com/p/c-refactoring-operators-and-ai-coding)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

This week: The articles dig into safe C# refactoring, characterization tests, and the details of equality, arithmetic, and logical operators. There’s also reading on event subscriptions, concurrent collections, MongoDB indexes, and dependency ownership. On the video side, I experiment with AI coding agents, build games in Godot, and look at what worked and what went wrong when AI tackled a blog redesign. Like what you read or watched from the recap? I’d love if you helped share on Reddit or Daily.dev so others can see! Weekly Recap I Let AI Agents Build My Products While I Commute In this video, I talk through some of the things I am building with agents -- including some games and agent tools. Building Godot Games With Copilot - Principal Engineering Manager AMA We’re heading to the terminal to build some pixel art games in Godot! Let’s have some fun and make something cool. As with all livestreams, I’m looking forward to answering YOUR questions! So join me live and ask in the chat, or you can comment now, and I can try to get it answered while I stream. I Gave AI Full Control of My Blog Design, Big Mistake? From ChatGPT mockups to Copilot Autopilot... The result? Well, let’s see how it did working mostly autonomously and where things were rough. Rider x Air x Junie: Will AI Fix My Mess? In this video, we check out Rider x Air x Junie in a practical setup where multiple agent sessions help us fix some errors and redesign some UI elements. The AI Mistakes I Made So You Don’t Have To In this video, I talk through some of the agentic development I am doing between several agents working in parallel on some hobby game development. Equality in C#: Reference, Value, and Operator Semantics Understand equality in C# through static operand types, reference identity, Equals, strings, records, structs, and boxed values with practical examples. Refactoring Diff Review in C#: Find Hidden Behavior Changes Learn refactoring diff review in C# by checking evaluation order, null handling, exceptions, loop exits, and targeted examples that expose behavior changes. Arithmetic Operators in C#: Numeric Types, Division, and Overflow Learn arithmetic operators in C# through numeric promotion, integer division, remainder, zero division, and checked overflow with clear practical examples. Characterization Tests Before Refactoring C# Code Learn characterization tests for C# refactoring: choose observable behavior, capture outputs and exceptions, control unstable data, and avoid false confidence. Testing C# Events: Notification, Failure, and Subscription Behavior Learn testing C# events with complete deterministic examples for payloads, counts, removal, synchronous failures, and task outcomes without sleeps or GC. Logical Operators in C#: Short-Circuiting and Boolean Conditions Understand logical operators in C#, including short-circuiting, Boolean guards, eager evaluation, and nullable bool rules, through practical code examples. Concurrent Collections in C#: Safe Operations and Workflow Boundaries Understand concurrent collections in C# by separating safe operations, repeatable factories, enumeration, shared values, and multi-step workflow boundaries. C# Event Subscriptions: Identity, Unsubscription, and Lifetime Understand C# event subscriptions with complete examples for handler identity, duplicate removal, retained wrappers, owned lifetime, and dispatch snapshots. MongoDB Indexes in C#: Query Shapes and Explain Evidence Understand MongoDB indexes in C# through query shapes, compound key order, write maintenance, and explain evidence without inventing performance guarantees. Safe Refactoring in C#: A Workflow for Behavior-Preserving Changes Learn safe refactoring in C# with a worked workflow for recording behavior, making small changes, reviewing semantic differences, and preserving API contracts. Composition in C#: Owning Versus Borrowing Dependencies Learn composition in C# through dependency ownership, shared references, and disposal boundaries, including why borrowers should not dispose injected services. Join me and other software engineers in the private Discord community ! Resume reviews and interview guidance ! Software engineering podcast and livestreams ! My Code Commute vlogs are on YouTube ! All of my weekly vlogs are on YouTube ! Remember to check out my courses , including this awesome discounted bundle for C# developers : Get this DISCOUNTED course bundle NOW!

</details>