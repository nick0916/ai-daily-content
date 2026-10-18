---
id: inbox_b4c35507
date: 2026-10-09
source_ref: "[[00-inbox/2026-10-09/0256-simon-willison-ttok-1-0-800f]]"
title: "ttok 1.0"
url: https://simonwillison.net/2026/Oct/9/ttok/
source: simon-willison
published_at: 2026-10-09T00:34:43+00:00
fetched_at: 2026-10-18T03:05:49.277128+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 發布 CLI 工具 ttok 1.0。ttok 是以 OpenAI 開源 tiktoken 函式庫計算 token 數的命令列工具。起因是他剛發布 0.4 版，升級後把檔案 pipe 進新版，才發現預設仍是 GPT-4 tokenizer，應改為 GPT-5/GPT-6，於是以切換預設值為由順勢發布 1.0。他指出 OpenAI 尚未正式確認 GPT-6 與 GPT-5 系列使用相同 tokenizer（有一則抱怨此事的 issue）。不過他引用 William Liu 的 commit，內容是一項實驗：七個 GPT 模型（5.5、5.6 Sol/Terra/Luna、6 Astra/Sol/Luna）在 31 個 fixture 上都回報 44,794 tokens 且彼此一致，顯示 GPT-6 在該語料上沒有輸入 token 數的變化。對需要估算 OpenAI 模型成本的開發者而言，這提供了 GPT-6 tokenizer 很可能沿用 GPT-5 的實測佐證，但仍非官方確認。"
key_points:
  - "ttok 1.0 將預設 tokenizer 由 GPT-4 改為 GPT-5/GPT-6"
  - "William Liu 實驗：7 個 GPT 模型（5.5、5.6 Sol/Terra/Luna、6 Astra/Sol/Luna）在 31 個 fixture 上皆為 44,794 tokens，GPT-6 無輸入 token 數變化"
  - "OpenAI 尚未官方確認 GPT-6 沿用 GPT-5 tokenizer，目前僅為實測推斷"
tags: [ttok, tokenization, tiktoken, gpt-6, cli-tool]
topics: [foundation_models.gpt, engineering.inference]
importance: 2
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## ttok 1.0

Simon Willison 發布 CLI 工具 ttok 1.0。ttok 是以 OpenAI 開源 tiktoken 函式庫計算 token 數的命令列工具。起因是他剛發布 0.4 版，升級後把檔案 pipe 進新版，才發現預設仍是 GPT-4 tokenizer，應改為 GPT-5/GPT-6，於是以切換預設值為由順勢發布 1.0。他指出 OpenAI 尚未正式確認 GPT-6 與 GPT-5 系列使用相同 tokenizer（有一則抱怨此事的 issue）。不過他引用 William Liu 的 commit，內容是一項實驗：七個 GPT 模型（5.5、5.6 Sol/Terra/Luna、6 Astra/Sol/Luna）在 31 個 fixture 上都回報 44,794 tokens 且彼此一致，顯示 GPT-6 在該語料上沒有輸入 token 數的變化。對需要估算 OpenAI 模型成本的開發者而言，這提供了 GPT-6 tokenizer 很可能沿用 GPT-5 的實測佐證，但仍非官方確認。

### 重點
- ttok 1.0 將預設 tokenizer 由 GPT-4 改為 GPT-5/GPT-6
- William Liu 實驗：7 個 GPT 模型（5.5、5.6 Sol/Terra/Luna、6 Astra/Sol/Luna）在 31 個 fixture 上皆為 44,794 tokens，GPT-6 無輸入 token 數變化
- OpenAI 尚未官方確認 GPT-6 沿用 GPT-5 tokenizer，目前僅為實測推斷

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/9/ttok/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: ttok 1.0 
 I released ttok 0.4 , ran uv tool upgrade ttok , piped a file into the new version... and realized that it was defaulting to the GPT-4 tokenizer when it should very clearly default to GPT-5/GPT-6 instead! 
 I figured switching the default was a reasonable excuse to finally ship a 1.0. 
 OpenAI haven't actually confirmed that GPT-6 uses the same tokenizer as the GPT-5 family yet - there's an angry issue about it - but I found this commit by William Liu which reports on an experiment he ran confirming that the tokenizers are likely the same: 
 
 All seven GPT models (5.5, 5.6 Sol/Terra/Luna, 6 Astra/Sol/Luna) report 44,794 tokens and match each other on every one of the 31 fixtures. GPT-6 introduces no input-count change on this corpus. 
 
 
 
 Tags: projects , ai , openai , generative-ai , llms , tokenization

</details>