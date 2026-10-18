---
id: inbox_2eacc868
date: 2026-10-08
source_ref: "[[00-inbox/2026-10-08/0256-simon-willison-ttok-0-4-3ed6]]"
title: "ttok 0.4"
url: https://simonwillison.net/2026/Oct/8/ttok/
source: simon-willison
published_at: 2026-10-08T23:34:28+00:00
fetched_at: 2026-10-18T03:05:49.277955+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 發布 ttok 0.4。ttok 是他用來計算 token 數的 CLI 工具，底層使用 OpenAI 開源的 tiktoken 函式庫。該工具已有數年未更新，這次修正了 Click 警告、更新 CI，並新增 --list-models 指令列出可用模型。它支援 uvx，可直接用 cat file.txt | uvx ttok 計算任何文字的 token 數。這是一次小幅維護性更新，對經常需要估算 prompt 長度或成本的開發者有實用性，且隔天他又發布了修正預設 tokenizer 的 1.0 版。"
key_points:
  - "新增 --list-models 指令列出可用模型，並修正 Click 警告、更新 CI"
  - "可用 uvx 免安裝執行：cat file.txt | uvx ttok"
  - "底層使用 OpenAI 的 tiktoken 函式庫"
tags: [ttok, tokenization, tiktoken, cli-tool, uvx]
topics: [engineering.inference]
importance: 1
novelty: 1
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## ttok 0.4

Simon Willison 發布 ttok 0.4。ttok 是他用來計算 token 數的 CLI 工具，底層使用 OpenAI 開源的 tiktoken 函式庫。該工具已有數年未更新，這次修正了 Click 警告、更新 CI，並新增 --list-models 指令列出可用模型。它支援 uvx，可直接用 cat file.txt | uvx ttok 計算任何文字的 token 數。這是一次小幅維護性更新，對經常需要估算 prompt 長度或成本的開發者有實用性，且隔天他又發布了修正預設 tokenizer 的 1.0 版。

### 重點
- 新增 --list-models 指令列出可用模型，並修正 Click 警告、更新 CI
- 可用 uvx 免安裝執行：cat file.txt | uvx ttok
- 底層使用 OpenAI 的 tiktoken 函式庫

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/8/ttok/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: ttok 0.4 
 ttok is my CLI tool for counting tokens, using OpenAI's open source tiktoken library. 
 It hasn't been in updated in a couple of years, but I finally fixed a Click warning, updated CI, and added a --list-models command to list available models. 
 It works with uvx , so you can count tokens in anything like this: 
 cat file.txt | uvx ttok
 
 
 
 Tags: projects , ai , openai , generative-ai , llms , tokenization

</details>