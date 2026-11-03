---
id: inbox_735eb718
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2347-simon-willison-llm-0-37-1a99]]"
title: "llm 0.37"
url: https://simonwillison.net/2026/Nov/2/llm/
source: simon-willison
published_at: 2026-11-02T23:49:30+00:00
fetched_at: 2026-11-03T23:53:01.634910+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon 的 LLM 命令列工具發布新版，並分享他把 AI 輔助 PR 當成「附範例的 bug 回報」來處理。 **Why** 許多開源維護者抱怨 AI 輔助 PR 氾濫，但 Simon 發現自己並未感受到負擔。 **How** 他請 Opus 5.5 或 GPT-6 Astra 協助 triage，挑出最有用的修正；有時直接合併，有時自己另寫修正。 **What** LLM 0.37 新增 gpt-6.1-sol 與 gpt-6.1-terra、`llm openai endpoint add` 指令；預設模型改為 gpt-6-luna（價格為舊預設 gpt-5.6-luna 的一半）；embeddings 支援不同 content-type 的二進位內容（如 Gemini Embedding 2）。此版含 12 位貢獻者的修正，幾乎都是 AI 輔助。"
key_points:
  - "LLM 0.37 新增 gpt-6.1-sol、gpt-6.1-terra 與 `llm openai endpoint add`；預設模型改為 gpt-6-luna，價格為前預設 gpt-5.6-luna 的一半"
  - "embeddings 支援不同 content-type，以配合可嵌入文字、音訊、圖片、影片的 Gemini Embedding 2"
  - "12 位貢獻者、幾乎全為 AI 輔助的 PR，靠 Opus 5.5 / GPT-6 Astra triage，審查負擔低於預期"
tags: [llm-cli, release-notes, open-source, ai-assisted-pr, embeddings]
topics: [agents.coding_agents, product_and_org.adoption]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## llm 0.37

Simon 的 LLM 命令列工具發布新版，並分享他把 AI 輔助 PR 當成「附範例的 bug 回報」來處理。

**Why** 許多開源維護者抱怨 AI 輔助 PR 氾濫，但 Simon 發現自己並未感受到負擔。

**How** 他請 Opus 5.5 或 GPT-6 Astra 協助 triage，挑出最有用的修正；有時直接合併，有時自己另寫修正。

**What** LLM 0.37 新增 gpt-6.1-sol 與 gpt-6.1-terra、`llm openai endpoint add` 指令；預設模型改為 gpt-6-luna（價格為舊預設 gpt-5.6-luna 的一半）；embeddings 支援不同 content-type 的二進位內容（如 Gemini Embedding 2）。此版含 12 位貢獻者的修正，幾乎都是 AI 輔助。

### 重點
- LLM 0.37 新增 gpt-6.1-sol、gpt-6.1-terra 與 `llm openai endpoint add`；預設模型改為 gpt-6-luna，價格為前預設 gpt-5.6-luna 的一半
- embeddings 支援不同 content-type，以配合可嵌入文字、音訊、圖片、影片的 Gemini Embedding 2
- 12 位貢獻者、幾乎全為 AI 輔助的 PR，靠 Opus 5.5 / GPT-6 Astra triage，審查負擔低於預期

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/2/llm/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm 0.37 
 There's a lot of stuff in this new release of my LLM CLI tool and Python library, representing around two months of accumulated features and fixes. 
 I added gpt-6.1-sol and gpt-6.1-terra , plus a new llm openai endpoint add command to make it easier to configure additional models that use OpenAI-compatible endpoints. 
 I switched the default model (if you have not set your own default) to gpt-6-luna - half the price of the previous default, gpt-5.6-luna . 
 LLM's support for embeddings now accepts that different binary content may have different content-type - necessary for models like Gemini Embedding 2 , which can embed text, audio, images, and video. 
 A lot of open source maintainers complain about a flood of AI-assisted PRs. LLM is my project that has been most affected by this and, to be honest, I'm not finding it to be a problem. That's mainly because I have Opus 5.5 or GPT-6 Astra help me with triage to spot the most useful fixes! 
 This release includes fixes from 12 authors - almost all AI-assisted - and the burden of reviewing them wasn't nearly as great as I expected. I really see them as bug reports with attached examples - sometimes I land them, sometimes I implement my own fix. 
 So thanks to 0d00ciallo0721 , ac1982 , Allen Flux , Bian Yuhan , Bishop Kammeraad , Chen Yufeiyang , Christopher Krah , Ethan Stoner , Jiachen Xie , Olamide Faniyan , Sharat Chandra Sai Boddu , nosmile99 for helping out with (or spending tokens on) this release! 
 
 
 Tags: open-source , projects , ai , annotated-release-notes , generative-ai , llms , embeddings , llm

</details>