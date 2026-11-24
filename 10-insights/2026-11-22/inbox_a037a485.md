---
id: inbox_a037a485
date: 2026-11-22
source_ref: "[[00-inbox/2026-11-22/0210-tomasz-tunguz-what-kind-of-factory-will-you-build-4bcf]]"
title: "What Kind of Factory Will You Build?"
url: https://tomtunguz.com/what-kind-of-factory-will-you-build/
source: tomasz-tunguz
published_at: 2026-11-22T00:00:00+00:00
fetched_at: 2026-11-24T02:16:26.725038+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把「軟體工廠」的做法搬到公司其他工作上：讓 agent 做事、記錄結果、再回頭改進規則。 **Why** 工程團隊已經不再逐行寫程式，而是建系統來寫、測、出貨；作者問為什麼其他團隊不照做。 **How** 四步循環：shared context（規格、文件、歷史）→ agent 執行 → execution trace（記錄出貨、出錯與成本）→ curator 讀 trace 改寫 skills 與 specs。後兩步會複利，讓系統每週變好，否則只是一次性的 workflow。 **What** Tomasz Tunguz 引用 11/21 Notion 的「A New Shape for Work」與 LangChain 的「How to Build a Knowledge Factory」，兩者描述同一個循環；作者也在註腳指出兩篇都沒有 benchmark、客戶成果或獨立驗證，只是廠商的架構論述。他認為工廠是營運專案而非買模型，需要有人負責 context、spec、trace 與定期執行 curator。"
key_points:
  - "工廠四要素：shared context、agent、execution trace、curator loop；trace 把工作變成資料，curator 把資料變成更好的系統"
  - "Notion（A New Shape for Work）與 LangChain（How to Build a Knowledge Factory）於 2026-11-21 發表，描述同一個 context→agent→trace→curator 循環，但作者註明兩篇都無 benchmark、客戶成果或獨立驗證"
  - "作者論點：工廠是營運專案不是買模型，需有人擁有 context、寫 spec、讀 trace、定期跑 curator；可類推到行銷、廣告（ROAS）、銷售簡報"
tags: [software-factory, knowledge-factory, agent-loop, execution-trace, curator]
topics: [agents.frameworks, product_and_org.adoption]
importance: 3
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## What Kind of Factory Will You Build?

把「軟體工廠」的做法搬到公司其他工作上：讓 agent 做事、記錄結果、再回頭改進規則。

**Why** 工程團隊已經不再逐行寫程式，而是建系統來寫、測、出貨；作者問為什麼其他團隊不照做。

**How** 四步循環：shared context（規格、文件、歷史）→ agent 執行 → execution trace（記錄出貨、出錯與成本）→ curator 讀 trace 改寫 skills 與 specs。後兩步會複利，讓系統每週變好，否則只是一次性的 workflow。

**What** Tomasz Tunguz 引用 11/21 Notion 的「A New Shape for Work」與 LangChain 的「How to Build a Knowledge Factory」，兩者描述同一個循環；作者也在註腳指出兩篇都沒有 benchmark、客戶成果或獨立驗證，只是廠商的架構論述。他認為工廠是營運專案而非買模型，需要有人負責 context、spec、trace 與定期執行 curator。

### 重點
- 工廠四要素：shared context、agent、execution trace、curator loop；trace 把工作變成資料，curator 把資料變成更好的系統
- Notion（A New Shape for Work）與 LangChain（How to Build a Knowledge Factory）於 2026-11-21 發表，描述同一個 context→agent→trace→curator 循環，但作者註明兩篇都無 benchmark、客戶成果或獨立驗證
- 作者論點：工廠是營運專案不是買模型，需有人擁有 context、寫 spec、讀 trace、定期跑 curator；可類推到行銷、廣告（ROAS）、銷售簡報

**原文：** [tomasz-tunguz](https://tomtunguz.com/what-kind-of-factory-will-you-build/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Read on tomtunguz.com → Before AI, we wrote software line by line. After AI, the best engineering teams stopped writing code & started building software factories : systems that write, test, & ship the code for them. 
 So why don’t other teams build factories? 
 They are. On November 21, Notion published “A New Shape for Work” 1 & LangChain published “How to Build a Knowledge Factory” 2 . One is a manifesto, the other a build guide. Both describe the exact same four-step loop applied to company knowledge : context, agent, trace, curator. 
 This is the plan for shipping a factory. 3 
 

 Notion puts it bluntly : 
 
 “This structure is among the most valuable IP any modern organization can have, because it defines the limit of what is possible for agents to do within that company.” 
 
 LangChain frames the same loop from the other side : 
 
 “The goal isn’t to document everything before agents can start working. It’s to build a system where doing the work reveals what knowledge is missing, & resolving those gaps makes future work better.” 
 
 A software factory has four components. A shared context : the specs, docs & history an agent reads before it starts. An agent that runs the skills & specs to do the work. An execution trace that flags what shipped, what broke, & what it cost. A curator loop that reads the trace & rewrites the skills & specs for the next run. 
 The last two steps compound. A prompt with a document attached is a one-off. The trace turns the work into data. The curator turns the data into a better system. That is the difference between a factory that improves every week & a workflow that stays flat. 
 The loop is not a vendor’s idea. It is what the work looks like once an agent does most of it. A knowledge factory has the same four parts as a code factory. The context is the docs. The agent is the answer. The trace is the wrong answer. The curator is the fix. 
 Once you see the loop, it generalizes everywhere. A marketing factory turns campaign performance into better copy. An online ads factory turns ROAS 4 traces into new creative. A sales pitch factory turns call transcripts into sharper decks. 
 Satya Nadella described the same shift at Microsoft Ignite 5 : 
 
 “The new company looks like there’s a founder. The founder has a token budget. Then the founder hires somebody. That person also comes in, & then they have a token budget, & they figure out how to add the tokens & the wages & then keep building.” 
 
 Factories are still rare because a factory is an operations project, not a model purchase. Someone has to own the context, write the specs, read the traces & run the curator on a cadence. This is the reinvention of work : defining & operating the factory for each team. 
 Different departments, identical architecture. The question is no longer whether AI can do the work : it is what kind of factory you will build. 
 
 
 
 
 A New Shape for Work , Notion, Nov 21, 2026. ↩︎ 
 
 
 How to build a knowledge factory , LangChain, Nov 21, 2026. ↩︎ 
 
 
 Neither post includes a benchmark, a customer result, or independently verified outcome. Both are vendor arguments about architecture. ↩︎ 
 
 
 Return on ad spend measures revenue generated for each dollar spent on advertising. ↩︎ 
 
 
 Satya Nadella, Microsoft Ignite roundtable, Nov 17, 2026. ↩︎

</details>