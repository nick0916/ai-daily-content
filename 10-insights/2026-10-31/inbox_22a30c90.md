---
id: inbox_22a30c90
date: 2026-10-31
source_ref: "[[00-inbox/2026-10-31/0019-simon-willison-datasette-llm-0-1a9-5e65]]"
title: "datasette-llm 0.1a9"
url: https://simonwillison.net/2026/Oct/31/datasette-llm/
source: simon-willison
published_at: 2026-10-31T22:10:01+00:00
fetched_at: 2026-11-01T00:24:08.901284+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "datasette-llm 現在會沿用 LLM 的預設模型，用 Datasette Agent 不必再手動指定模型。 **Why** 以前每次啟動 Datasette Agent 都要額外設定預設模型，多一道門檻。 **How** datasette-llm 外掛改為直接讀取 LLM 所設定的 default model。 **What** datasette-llm 0.1a9 發布，可直接執行 `uvx --with datasette-agent datasette content.db --internal internal.db`；作者表示 Datasette Agent 另有較大的升級正在準備中。"
key_points:
  - "datasette-llm 0.1a9 會自動採用 LLM 的預設模型，不再需要 `-s plugins.datasette-agent.default_model ...`"
  - "最小啟動指令：uvx --with datasette-agent datasette content.db --internal internal.db"
  - "作者預告 Datasette Agent 有更大的升級在籌備中"
tags: [datasette, datasette-llm, datasette-agent, llm-cli, release]
topics: [agents.frameworks]
importance: 1
novelty: 1
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-llm 0.1a9

datasette-llm 現在會沿用 LLM 的預設模型，用 Datasette Agent 不必再手動指定模型。

**Why** 以前每次啟動 Datasette Agent 都要額外設定預設模型，多一道門檻。

**How** datasette-llm 外掛改為直接讀取 LLM 所設定的 default model。

**What** datasette-llm 0.1a9 發布，可直接執行 `uvx --with datasette-agent datasette content.db --internal internal.db`；作者表示 Datasette Agent 另有較大的升級正在準備中。

### 重點
- datasette-llm 0.1a9 會自動採用 LLM 的預設模型，不再需要 `-s plugins.datasette-agent.default_model ...`
- 最小啟動指令：uvx --with datasette-agent datasette content.db --internal internal.db
- 作者預告 Datasette Agent 有更大的升級在籌備中

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/31/datasette-llm/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-llm 0.1a9 
 I have some big upgrades to Datasette Agent in the pipeline, but in the meantime here's a tiny user experience improvement to the underlying datasette-llm plugin. 
 It now picks up the default model used by LLM , which means you can start using Datasette Agent without needing to explicitly configure a default model: 
 uvx --with datasette-agent datasette content.db --internal internal.db
 
 Previously you would also need to specify a model with -s plugins.datasette-agent.default_model gpt-6-astra . 
 
 
 Tags: datasette , llm , datasette-agent

</details>