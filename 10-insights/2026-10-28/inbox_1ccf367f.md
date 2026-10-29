---
id: inbox_1ccf367f
date: 2026-10-28
source_ref: "[[00-inbox/2026-10-28/0016-simon-willison-quoting-ted-sanders-1c3e]]"
title: "Quoting Ted Sanders"
url: https://simonwillison.net/2026/Oct/28/ted-sanders/
source: simon-willison
published_at: 2026-10-28T23:23:21+00:00
fetched_at: 2026-10-29T00:21:41.193099+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "模型越大通常越強、越貴、越記得冷門知識；版本號則代表發布順序與改進幅度。 **Why** LLM 能力是多維度的，不保證數學最強的模型也最會講笑話，使用者難以判斷模型間的關係。 **How** Ted Sanders 指出大部分表現差異可由單一變數「模型大小」解釋；版本號同時表示發布先後、與其他版本的相似度（訓練資料、個性），以及進步幅度。 **What** Simon Willison 引述 OpenAI 的 Ted Sanders 說明模型命名慣例：較大的模型 (a) 更可靠、(b) 每 token 更貴、(c) 對冷門事實記得更好。例如 6.1 代表發布在 5.6 之後、與其他 6.1 模型相似，但還不到值得 7 那種headline 與期待的大躍進。"
key_points:
  - "模型大小解釋大部分表現差異：更可靠、每 token 更貴、更能回憶冷門事實"
  - "版本號同時傳達發布順序、模型間關聯（訓練資料/個性）與進步幅度"
  - "6.1 晚於 5.6 發布，因與其他 6.1 模型相似所以不叫 5.7，且進步不足以稱 7"
tags: [openai, model-naming, model-size, llm-selection, ted-sanders]
topics: [foundation_models.gpt]
importance: 2
novelty: 3
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting Ted Sanders

模型越大通常越強、越貴、越記得冷門知識；版本號則代表發布順序與改進幅度。

**Why** LLM 能力是多維度的，不保證數學最強的模型也最會講笑話，使用者難以判斷模型間的關係。

**How** Ted Sanders 指出大部分表現差異可由單一變數「模型大小」解釋；版本號同時表示發布先後、與其他版本的相似度（訓練資料、個性），以及進步幅度。

**What** Simon Willison 引述 OpenAI 的 Ted Sanders 說明模型命名慣例：較大的模型 (a) 更可靠、(b) 每 token 更貴、(c) 對冷門事實記得更好。例如 6.1 代表發布在 5.6 之後、與其他 6.1 模型相似，但還不到值得 7 那種headline 與期待的大躍進。

### 重點
- 模型大小解釋大部分表現差異：更可靠、每 token 更貴、更能回憶冷門事實
- 版本號同時傳達發布順序、模型間關聯（訓練資料/個性）與進步幅度
- 6.1 晚於 5.6 發布，因與其他 6.1 模型相似所以不叫 5.7，且進步不足以稱 7

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/28/ted-sanders/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

In general, LLM performance is incredibly multidimensional. There's no guarantee of a fixed ordering where the model that is best at math is also the model that's best at jokes. Despite that complexity, much of the variation in performance is explained by just a single variable: model size. In general, models that are bigger will (a) be more performant / reliable, (b) cost more per token, and (c) have better recall of esoteric facts. As you note, our models are ordered: 
 Luna 
 [ ... ] These days, version number signifies a few things at once: the order of release, the relationship to other releases, and the magnitude of improvement. So something like 6.1 would indicate it was launched after 5.6, may share some similarities to other 6.1 models in terms of training data / personality (which is why it's not 5.7), and isn't a giant enough leap to merit the headlines and expectations that would come with a 7. 
 — Ted Sanders , explaining OpenAI's model naming conventions 

 Tags: generative-ai , gpt , openai , ai , llms , ted-sanders

</details>