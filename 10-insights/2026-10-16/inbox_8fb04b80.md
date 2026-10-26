---
id: inbox_8fb04b80
date: 2026-10-16
source_ref: "[[00-inbox/2026-10-16/2336-simon-willison-sparqlite-sparql-1-1-inside-sqlite-writt-022e]]"
title: "sparqlite: SPARQL 1.1 inside SQLite, written in Rust"
url: https://simonwillison.net/2026/Oct/16/sqlite-sparql-rust/
source: simon-willison
published_at: 2026-10-16T01:58:00+00:00
fetched_at: 2026-10-21T23:41:44.131213+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 Claude Code 網頁版自己編排一群子代理，連跑 12 小時以上做出一個 SQLite 的 SPARQL 擴充，成果大到人根本無法審查。 **Why** Simon Willison 想實驗 Claude Code 的「Ultracode」模式，看動態 workflow 能把複雜任務推到多遠。 **How** 開啟 Ultracode 後，Claude Code 會產生 JavaScript 來定義並協調一組子代理（dynamic workflows）；他只下了一個初始 prompt，之後補一個要求加 README 與教學的 follow-up。 **What** 成果是 sparqlite，一個用 Rust 寫的 SQLite 擴充，實作完整的 SPARQL 1.1。原 prompt 因手機打字錯誤把「hit the rows directly」寫成「delete」，Claude Code 仍跑了超過 12 小時並產出大量 Rust crates。作者認為這是「next-level vibe coding」：程式碼無法逐行審查，連跟著文件操作都要投入可觀時間，他也不確定隨興做出又沒時間理解的東西有多少價值。"
key_points:
  - "Claude Code for web 的 Ultracode 模式用動態 workflow 生成 JavaScript 協調多個子代理，初始 prompt 讓它運作超過 12 小時"
  - "成果 sparqlite 是 Rust 寫的 SQLite 擴充，實作 SPARQL 1.1；follow-up prompt 要求每個 crates/ 資料夾都有 README、tutorial.md 與範例資料腳本"
  - "作者反思：產出規模大到無法審查，隨興生成又無暇理解的程式碼，價值存疑"
tags: [claude-code, ultracode, subagents, sparql, sqlite, vibe-coding]
topics: [agents.coding_agents]
importance: 3
novelty: 4
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## sparqlite: SPARQL 1.1 inside SQLite, written in Rust

讓 Claude Code 網頁版自己編排一群子代理，連跑 12 小時以上做出一個 SQLite 的 SPARQL 擴充，成果大到人根本無法審查。

**Why** Simon Willison 想實驗 Claude Code 的「Ultracode」模式，看動態 workflow 能把複雜任務推到多遠。

**How** 開啟 Ultracode 後，Claude Code 會產生 JavaScript 來定義並協調一組子代理（dynamic workflows）；他只下了一個初始 prompt，之後補一個要求加 README 與教學的 follow-up。

**What** 成果是 sparqlite，一個用 Rust 寫的 SQLite 擴充，實作完整的 SPARQL 1.1。原 prompt 因手機打字錯誤把「hit the rows directly」寫成「delete」，Claude Code 仍跑了超過 12 小時並產出大量 Rust crates。作者認為這是「next-level vibe coding」：程式碼無法逐行審查，連跟著文件操作都要投入可觀時間，他也不確定隨興做出又沒時間理解的東西有多少價值。

### 重點
- Claude Code for web 的 Ultracode 模式用動態 workflow 生成 JavaScript 協調多個子代理，初始 prompt 讓它運作超過 12 小時
- 成果 sparqlite 是 Rust 寫的 SQLite 擴充，實作 SPARQL 1.1；follow-up prompt 要求每個 crates/ 資料夾都有 README、tutorial.md 與範例資料腳本
- 作者反思：產出規模大到無法審查，隨興生成又無暇理解的程式碼，價值存疑

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/16/sqlite-sparql-rust/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Research: sparqlite: SPARQL 1.1 inside SQLite, written in Rust 
 This research task is really an experiment in running Claude Code for web in "Ultracode" mode, as described in Orchestrate subagents at scale with dynamic workflows in the Claude Code documentation. 
 With Ultracode turned on, Claude Code makes aggressive use of dynamic workflows - it generates JavaScript that defines and coordinates a network of subagents to take on complex problems. 
 My initial prompt was this - I meant "hit the rows directly", the word "delete" was an accidental typo on my phone: 
 
 Write a SQLite extension in Rust that implants SPARQL and runs really fast because it can hit the delete rows directly 
 
 This caused Claude Code for web to churn for over 12 hours. I checked in on its progress the next day and sent a single follow-up prompt when I noticed how many Rust crates it had built: 
 
 Every folder in the crates/ directory needs a README 
 Include a tutorial.md teaching users how to install the extension and how to run it in the SQLite CLI and then teaching them SPARQL in addition to how to use the SQLite extension 
 Include a script with the tutorial for populating a SQLite database with useful and realistic example data for that tutorial 
 
 This project feels like next-level vibe coding - it's not remotely feasible to review the code that was produced here, and even following the documentation is a significant investment in work. I'm not entirely sure what to do with this - I appear to have a full SPARQL implementation in Rust inside SQLite now, but how valuable is that if I created it on a whim and can't (or won't) invest the necessary time to understand what it can do? 
 
 
 Tags: rdf , semantic-web , sqlite , ai , rust , generative-ai , llms , coding-agents , claude-code

</details>