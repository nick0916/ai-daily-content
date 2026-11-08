---
id: inbox_fee8b5b3
date: 2026-11-08
source_ref: "[[00-inbox/2026-11-08/2347-simon-willison-parse-number-as-a-sqlite-extension-c-vs-f37b]]"
title: "parse_number() as a SQLite extension: C vs Rust"
url: https://simonwillison.net/2026/Nov/8/sqlite-parse-number-c-vs-rust/
source: simon-willison
published_at: 2026-11-08T22:26:00+00:00
fetched_at: 2026-11-08T23:52:41.940034+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "請 AI 寫 SQLite 字串轉數字的擴充，並比較 C 與 Rust 的檔案大小與速度。 **Why** 作者想知道寫一個能把 -$1,234.56 或 '12.5%' 轉成可加總、可排序數值的 parse_number() 有多難。 **How** 用 Claude chat (Opus 5.5) 先比較 C 與 Rust 兩種做法，發現 Rust 較快是因為其對應 C strtod 的函式「快兩倍」，再要求它自寫 C 版的小數解析以追上或超越 Rust。 **What** 初版 C 擴充 14 KB，Rust 版為 321 KB (rusqlite) 與 298 KB (sqlite-loadable-rs)。兩百萬列的每列成本，新版 C 在混合資料為 19 ns，優於 rusqlite 的 46 ns 與 sqlite-loadable 的 41 ns；整理成 simonw/research 風格的研究報告。"
key_points:
  - "檔案大小：C 擴充 14 KB，Rust 版 321 KB (rusqlite) / 298 KB (sqlite-loadable-rs)"
  - "每列成本（200 萬列）：新版 C 混合 19 ns、整數 16 ns、小數 18 ns；初版 C 小數 106 ns，rusqlite 小數 55 ns"
  - "Rust 初版較快的原因是標準庫的字串轉浮點比 C strtod 快約兩倍，要求 AI 自寫解析即可追平"
tags: [sqlite, c, rust, benchmark, claude]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## parse_number() as a SQLite extension: C vs Rust

請 AI 寫 SQLite 字串轉數字的擴充，並比較 C 與 Rust 的檔案大小與速度。

**Why** 作者想知道寫一個能把 -$1,234.56 或 '12.5%' 轉成可加總、可排序數值的 parse_number() 有多難。

**How** 用 Claude chat (Opus 5.5) 先比較 C 與 Rust 兩種做法，發現 Rust 較快是因為其對應 C strtod 的函式「快兩倍」，再要求它自寫 C 版的小數解析以追上或超越 Rust。

**What** 初版 C 擴充 14 KB，Rust 版為 321 KB (rusqlite) 與 298 KB (sqlite-loadable-rs)。兩百萬列的每列成本，新版 C 在混合資料為 19 ns，優於 rusqlite 的 46 ns 與 sqlite-loadable 的 41 ns；整理成 simonw/research 風格的研究報告。

### 重點
- 檔案大小：C 擴充 14 KB，Rust 版 321 KB (rusqlite) / 298 KB (sqlite-loadable-rs)
- 每列成本（200 萬列）：新版 C 混合 19 ns、整數 16 ns、小數 18 ns；初版 C 小數 106 ns，rusqlite 小數 55 ns
- Rust 初版較快的原因是標準庫的字串轉浮點比 C strtod 快約兩倍，要求 AI 自寫解析即可追平

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/8/sqlite-parse-number-c-vs-rust/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Research: parse_number() as a SQLite extension: C vs Rust 
 I was out walking the dog when I got curious about how easy/difficult it would be to write a SQLite C extension that adds a parse_number() function for turning strings like -$1,234.56 or '12.5%' into numeric values that could be summed and sorted. 
 I fired up regular Claude chat (Opus 5.5) and prompted : 
 
 I'm thinking about a SQLite custom function 'parse_number(value)' that strips ',', '$', '£' and '%', handles a leading '-', and returns 'NULL' for anything it can’t parse 
 Explore the difference between building this as a SQLite extension in C v.s. in Rust - I want to compare performance and code complexity and size of the resulting .so (or whatever) file 
 
 This gave me a solid starting point - the Rust extension was 321 KB (using Rusqlite ) and 298 KB (using sqlite-loadable-rs ), while the C extension was 14 KB. But the Rust extension was faster! 
 Turns out that's because the Rust equivalent of C's strtod is "twice as fast". So I prompted: 
 
 Try writing your own C function for parsing text into a decimal number that catches up to or beats the Rust implementation 
 
 And it did: 
 
 Net cost per row over 2 million rows, lower is better: 
 
 
 
 
 first C 
 new C 
 rusqlite 
 sqlite-loadable 
 
 
 
 
 Mixed data 
 67 ns 
 19 ns 
 46 ns 
 41 ns 
 
 
 Integers only 
 25 ns 
 16 ns 
 36 ns 
 32 ns 
 
 
 Decimals only 
 106 ns 
 18 ns 
 55 ns 
 47 ns 
 
 
 
 

 Finally, I had it rewrite the prototype as a research report to match the others in simonw/research by prompting this: 
 
 Clone simonw/research from GitHub and turn your above investigation into a research report as seen in that repository - you can give me a zip file to download that contains your new folder 
 
 Here's the resulting report . 
 
 
 Tags: c , research , sqlite , rust , claude

</details>