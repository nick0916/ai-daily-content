---
id: inbox_635fcac5
date: 2026-10-30
source_ref: "[[00-inbox/2026-10-30/2251-simon-willison-dbreunig-nesformer-a14d]]"
title: "dbreunig/nesformer"
url: https://simonwillison.net/2026/Oct/30/nesformer/
source: simon-willison
published_at: 2026-10-30T21:59:22+00:00
fetched_at: 2026-10-30T22:56:01.138248+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "有人把 NES 的 6502 CPU 模擬器直接做進 Qwen3.5-4B 的權重裡，讓模型自己跑 NES 遊戲。 **Why** 原文說明這是受 qwenputer 啟發的好玩實驗，用來探索能否用這種技術模擬 NES 的 CPU 與 RAM。 **How** Drew Breunig 用 Opus 5.5 提示詞，先讓它閱讀 qwenputer 文章與原始碼評估可行性，再要求實作；Opus 找到並使用 Christopher Pow 15 年前釋出的 NES CPU conformance tests 來驗證。 **What** dbreunig/nesformer 讓 Qwen3.5-4B 內建 NES 6502 CPU 模擬器，可跑 Super Mario Bros 等 ROM，但速度非常慢。"
key_points:
  - "nesformer 將 NES 6502 CPU 模擬器烘進 Qwen3.5-4B 權重，可執行 Super Mario Bros（很慢）"
  - "由 Drew Breunig 以兩段 Opus 5.5 prompt 建成：先評估可行性與模型大小，再「just for fun」實作並提供 CLI"
  - "Opus 自行找到 15 年前 Christopher Pow 的 NES CPU conformance tests 作為驗證"
tags: [qwen, nesformer, llm-experiment, conformance-tests, emulator]
topics: [foundation_models.open_weights, agents.coding_agents]
importance: 2
novelty: 4
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## dbreunig/nesformer

有人把 NES 的 6502 CPU 模擬器直接做進 Qwen3.5-4B 的權重裡，讓模型自己跑 NES 遊戲。

**Why** 原文說明這是受 qwenputer 啟發的好玩實驗，用來探索能否用這種技術模擬 NES 的 CPU 與 RAM。

**How** Drew Breunig 用 Opus 5.5 提示詞，先讓它閱讀 qwenputer 文章與原始碼評估可行性，再要求實作；Opus 找到並使用 Christopher Pow 15 年前釋出的 NES CPU conformance tests 來驗證。

**What** dbreunig/nesformer 讓 Qwen3.5-4B 內建 NES 6502 CPU 模擬器，可跑 Super Mario Bros 等 ROM，但速度非常慢。

### 重點
- nesformer 將 NES 6502 CPU 模擬器烘進 Qwen3.5-4B 權重，可執行 Super Mario Bros（很慢）
- 由 Drew Breunig 以兩段 Opus 5.5 prompt 建成：先評估可行性與模型大小，再「just for fun」實作並提供 CLI
- Opus 自行找到 15 年前 Christopher Pow 的 NES CPU conformance tests 作為驗證

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/30/nesformer/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

dbreunig/nesformer 
Inspired by qwenputer by Divyansh Agrawal, Drew Breunig baked a working emulator for a Nintendo Entertainment System 6502 CPU into the weights of Qwen3.5-4B. You can now play NES ROMs such as Super Mario Bros (very slowly) running inside Qwen! 
 In a comment on Hacker News Drew reveals the Opus 5.5 prompts he used to build this system: 
 
 Read this article and any relevant source code: https://divagr.com/blog/qwenputer. Then explore if you could emulate the chip and ram in a Nintendo Entertainment System (as people do today with FPGAs in MISTRs) using this technique. If so, what size model would you have to build and if you could use smaller faster ones, could you get it to be at the standard clockspeed. 
 
 Followed by: 
 
 I think we should build it! Just for fun. It's okay if it's not fast. We want to be able to have the weights, and a cli to run them that we can point at a ROM. 
 
 Apparently Opus found and then used this collection of conformance tests for the NES CPU released 15 years ago by Christopher Pow.

 Via Hacker News 

 Tags: games , ai , generative-ai , llms , drew-breunig , qwen , conformance-suites

</details>