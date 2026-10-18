---
id: inbox_32c912df
date: 2026-10-12
source_ref: "[[00-inbox/2026-10-12/0256-simon-willison-llm-meta-ai-0-2-d23d]]"
title: "llm-meta-ai 0.2"
url: https://simonwillison.net/2026/Oct/12/llm-meta-ai/
source: simon-willison
published_at: 2026-10-12T23:58:46+00:00
fetched_at: 2026-10-18T03:04:53.005433+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 發布 llm-meta-ai 0.2，以支援 Meta AI 新發布的 Muse Wonder 與 Muse Wonder Full（Meta 稱為「most capable models」）。Simon 認為這可能是 Meta 第一批 Fable 等級模型，並引述 Artificial Analysis 的評分：Muse Wonder (Max) 與 GPT-6.1 Sol 相當。他照例用「騎腳踏車的鵜鶘」測試，產出六個推理等級（minimal、low、medium、high、xhigh、max）的圖，並與 Muse 1.3（9 月 2 日發布）、Muse 1.2（8 月 5 日發布）比較。他觀察到 Meta AI 大約每月推出一個新模型，且至少在畫鵜鶘這項測試上，每代進步都相當明顯。對 LLM CLI 使用者而言，更新外掛即可呼叫新模型。"
key_points:
  - "llm-meta-ai 0.2 支援 Muse Wonder 與 Muse Wonder Full，提供 minimal/low/medium/high/xhigh/max 六個推理等級"
  - "Artificial Analysis 評分：Muse Wonder (Max) 相當於 GPT-6.1 Sol"
  - "Meta 發布節奏約每月一版：Muse 1.2（8/5）→ Muse 1.3（9/2）→ Muse Wonder（10 月）"
tags: [meta, muse-wonder, llm-plugin, model-release, pelican-benchmark]
topics: [foundation_models.open_weights]
importance: 3
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-meta-ai 0.2

Simon Willison 發布 llm-meta-ai 0.2，以支援 Meta AI 新發布的 Muse Wonder 與 Muse Wonder Full（Meta 稱為「most capable models」）。Simon 認為這可能是 Meta 第一批 Fable 等級模型，並引述 Artificial Analysis 的評分：Muse Wonder (Max) 與 GPT-6.1 Sol 相當。他照例用「騎腳踏車的鵜鶘」測試，產出六個推理等級（minimal、low、medium、high、xhigh、max）的圖，並與 Muse 1.3（9 月 2 日發布）、Muse 1.2（8 月 5 日發布）比較。他觀察到 Meta AI 大約每月推出一個新模型，且至少在畫鵜鶘這項測試上，每代進步都相當明顯。對 LLM CLI 使用者而言，更新外掛即可呼叫新模型。

### 重點
- llm-meta-ai 0.2 支援 Muse Wonder 與 Muse Wonder Full，提供 minimal/low/medium/high/xhigh/max 六個推理等級
- Artificial Analysis 評分：Muse Wonder (Max) 相當於 GPT-6.1 Sol
- Meta 發布節奏約每月一版：Muse 1.2（8/5）→ Muse 1.3（9/2）→ Muse Wonder（10 月）

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/12/llm-meta-ai/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm-meta-ai 0.2 
 Meta AI release Muse Wonder (and Muse Wonder Full), their new "most capable models". These look like they may be Meta's first Fable class models - Artificial Analysis scores Muse Wonder (Max) as equivalent to GPT-6.1 Sol. 
 I updated my llm-meta-ai plugin for the new model. Here are pelicans for Muse Wonder for the six reasoning levels: minimal, low, medium, high, xhigh, max. This is the max one: 
 
 For comparison, here are pelicans for Muse 1.3 (released September 2nd) and Muse 1.2 (released August 5th). Meta AI are putting out a new model a month, and the improvements between each model (at least in terms of drawing pelicans) are material. 
 
 
 Tags: ai , generative-ai , llms , meta , pelican-riding-a-bicycle , llm-release

</details>