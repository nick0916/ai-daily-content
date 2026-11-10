---
id: inbox_f7f7a583
date: 2026-11-09
source_ref: "[[00-inbox/2026-11-09/2322-simon-willison-llm-anthropic-0-31-c888]]"
title: "llm-anthropic 0.31"
url: https://simonwillison.net/2026/Nov/9/llm-anthropic/
source: simon-willison
published_at: 2026-11-09T23:58:46+00:00
fetched_at: 2026-11-10T23:29:20.364003+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 更新 llm 外掛，讓指令列能直接呼叫 Anthropic 新發布的 Fable 5.2 與 Mythos 5.2。 **How** 在 llm-anthropic 0.31 加入新模型，用 `llm -m claude-fable-5.2` 即可送出 prompt；他以「騎腳踏車的鵜鶘 SVG」在 low、medium、high、xhigh、max 五個推理等級測試。 **What** llm-anthropic 0.31 支援 Fable 5.2 / Mythos 5.2；Fable 5.2 定價 $8 / $40 每百萬 token（輸入/輸出），比 Fable 5.1 的 $10 / $50 便宜 20%。max 等級花了 128,000 token 思考後沒回傳圖片，與他在 Opus 5.5 看過的 bug 相同，但 Fable 5 與 5.1 沒有此問題；最佳結果來自 xhigh。"
key_points:
  - "Fable 5.2 定價 $8 輸入 / $40 輸出（每百萬 token），較 Fable 5.1（$10/$50）降價 20%"
  - "max 推理等級耗盡 128,000 token 仍未回傳圖片，Fable 系列新出現的問題（Fable 5、5.1 的 max 正常）"
  - "安裝與使用：`llm install llm-anthropic`，再執行 `llm -m claude-fable-5.2 \"...\"`"
tags: [llm-anthropic, fable-5-2, mythos-5-2, simon-willison, pricing]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-anthropic 0.31

Simon Willison 更新 llm 外掛，讓指令列能直接呼叫 Anthropic 新發布的 Fable 5.2 與 Mythos 5.2。

**How** 在 llm-anthropic 0.31 加入新模型，用 `llm -m claude-fable-5.2` 即可送出 prompt；他以「騎腳踏車的鵜鶘 SVG」在 low、medium、high、xhigh、max 五個推理等級測試。

**What** llm-anthropic 0.31 支援 Fable 5.2 / Mythos 5.2；Fable 5.2 定價 $8 / $40 每百萬 token（輸入/輸出），比 Fable 5.1 的 $10 / $50 便宜 20%。max 等級花了 128,000 token 思考後沒回傳圖片，與他在 Opus 5.5 看過的 bug 相同，但 Fable 5 與 5.1 沒有此問題；最佳結果來自 xhigh。

### 重點
- Fable 5.2 定價 $8 輸入 / $40 輸出（每百萬 token），較 Fable 5.1（$10/$50）降價 20%
- max 推理等級耗盡 128,000 token 仍未回傳圖片，Fable 系列新出現的問題（Fable 5、5.1 的 max 正常）
- 安裝與使用：`llm install llm-anthropic`，再執行 `llm -m claude-fable-5.2 "..."`

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/9/llm-anthropic/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm-anthropic 0.31 
 Anthropic released Fable 5.2 and Mythos 5.2 today. Fable 5.2 is currently ranked first on Artificial Analysis . Anthropic say it "solved two open problems in the physics of black holes", so clearly their internal benchmarks have become more ambitious! 
 I've added the new models to llm-anthropic , so you can now run prompts through Fable 5.2 like this: 
 uv tool install llm
llm install llm-anthropic
llm keys set anthropic
# paste key here
llm -m claude-fable-5.2 "Generate an SVG of a pelican riding a bicycle"
 
 I ran pelicans at all five reasoning levels - low , medium , high , xhigh , and max . You can see them all here - here's the best result I got, from xhigh : 
 
 max failed to return an image at all, running out of tokens after spending 128,000 thinking about them . That's the same bug that I saw with Opus 5.5 - but it's new for the Fable series, both Fable 5 and Fable 5.1 returned max effort pelicans just fine. 
 It's priced at $8/million input and $40/million output, which is a 20% discount on the previous Fable 5.1 ($10/$50). 
 I also used Fable 5.2 to help identify the source of a mysterious beep . 
 
 
 Tags: llm-release , llm , anthropic , claude , generative-ai , pelican-riding-a-bicycle , ai , llms , claude-mythos-fable

</details>