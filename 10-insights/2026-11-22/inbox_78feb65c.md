---
id: inbox_78feb65c
date: 2026-11-22
source_ref: "[[00-inbox/2026-11-22/0054-hackernews-gpt-6-2-astra-is-the-first-model-to-beat-ca48]]"
title: "GPT-6.2 Astra is the first model to beat Googlers' code golf records"
url: https://bjin.github.io/go-codegolf-benchmark/#leaderboard
source: hackernews
published_at: 2026-11-22T16:44:48+00:00
fetched_at: 2026-11-27T01:01:00.402868+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把 2015 年 Google 內部每週 code golf 的人類最短紀錄拿來當 benchmark，看 LLM 能不能寫出更短的程式。 **Why** Code golf 獎勵換個角度看問題，也獎勵寫搜尋程式做實驗，這類能力沒有公開訓練資料教模型怎麼做，因此可作為前沿模型的補充評測。 **How** 作者把當年 Googler 的週題與紀錄做成 benchmark（go-codegolf-benchmark），讓各前沿模型挑戰；模型找出新解法，例如在 Python 與 Ruby 用內建複數解 \"Surviving Queens\" 與 \"The Rolling Dice\"。 **What** 作者表示 GPT-6.2 Astra 是第一個超越人類紀錄的前沿模型。在 \"(-5)-Smooth Numbers\" 一題，多數解法用巢狀迴圈或集合再排序，Astra 改從 4 的冪次取得，以 `g=lambda n:sorted(4**i%(2**999-5)%(2**49-3)for i in range(7000))[:n]` 拿下唯一最短。"
key_points:
  - "GPT-6.2 Astra 為第一個在 code golf 上超越 2015 年 Googler 人類紀錄的前沿模型（依作者說法）"
  - "\"(-5)-Smooth Numbers\" 題：Astra 用 4 的冪次加兩次取模的 lambda 取得唯一最短解，而多數解法是巢狀迴圈或集合後排序"
  - "\"Surviving Queens\"、\"The Rolling Dice\" 兩題中，前沿模型在 Python 與 Ruby 用內建複數運算解題"
tags: [code-golf, benchmark, gpt-6-2-astra, frontier-models, creative-problem-solving]
topics: [foundation_models.gpt, engineering.evals]
importance: 3
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## GPT-6.2 Astra is the first model to beat Googlers' code golf records

把 2015 年 Google 內部每週 code golf 的人類最短紀錄拿來當 benchmark，看 LLM 能不能寫出更短的程式。

**Why** Code golf 獎勵換個角度看問題，也獎勵寫搜尋程式做實驗，這類能力沒有公開訓練資料教模型怎麼做，因此可作為前沿模型的補充評測。

**How** 作者把當年 Googler 的週題與紀錄做成 benchmark（go-codegolf-benchmark），讓各前沿模型挑戰；模型找出新解法，例如在 Python 與 Ruby 用內建複數解 "Surviving Queens" 與 "The Rolling Dice"。

**What** 作者表示 GPT-6.2 Astra 是第一個超越人類紀錄的前沿模型。在 "(-5)-Smooth Numbers" 一題，多數解法用巢狀迴圈或集合再排序，Astra 改從 4 的冪次取得，以 `g=lambda n:sorted(4**i%(2**999-5)%(2**49-3)for i in range(7000))[:n]` 拿下唯一最短。

### 重點
- GPT-6.2 Astra 為第一個在 code golf 上超越 2015 年 Googler 人類紀錄的前沿模型（依作者說法）
- "(-5)-Smooth Numbers" 題：Astra 用 4 的冪次加兩次取模的 lambda 取得唯一最短解，而多數解法是巢狀迴圈或集合後排序
- "Surviving Queens"、"The Rolling Dice" 兩題中，前沿模型在 Python 與 Ruby 用內建複數運算解題

**原文：** [hackernews](https://bjin.github.io/go-codegolf-benchmark/#leaderboard)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Back in 2015, when I was still at Google, there was a small group of code-golf enthusiasts spending hours trying to save just one byte on their solutions for weekly code-golf problems. No matter how hard you tried, there always seemed to be another Googler who found a shorter solution. And once a problem entered the challenge phase and every solution became public, it was always astonishing to read how brilliant other people's solutions were. 11 years later, LLMs are evolving fast. A recent OpenAI post ("Perplexity and Intelligence", https://openai.com/index/perplexity-and-intelligence/ ) described researchers watching a model solve open math problems one after another in a Slack thread. I started to wonder: how would frontier models compete with the records that a small group of brilliant minds created with hours of effort each week? So I built this benchmark. Frontier models do find a lot of new approaches (and very brilliant ones) to solve these problems. For example, in two problems ("Surviving Queens" and "The Rolling Dice"), frontier models use complex numbers to solve them in Python and Ruby (both languages have built-in complex number support). And for the "(-5)-Smooth Numbers" problem, where you have to write code to list the first n positive integers of the form (-2)^x⋅(-3)^y⋅(-5)^z, most solutions build them with nested loops or by growing a set, then sort. GPT-6.2 Astra gets them all from powers of 4, and earns a sole best with this brilliant solution: g=lambda n:sorted(4**i%(2**999-5)%(2**49-3)for i in range(7000))[:n]
 
There is a dedicated section for this: https://bjin.github.io/go-codegolf-benchmark/#why/finding-a-... It's nice to see GPT-6.2 Astra become the first frontier model to beat the human records in code golfing. Along with other frontier models, it finds a lot of interesting solutions that Googlers back in 2015 didn't. On the other hand, I also believe code golfing can be a good benchmark (not a comprehensive one, of course) for frontier models. Code golfing rewards thinking differently, because a shorter solution usually comes from looking at the problem from a different angle. It also rewards running experiments, not just thinking: writing a search program to find a shorter expression, or exploring lesser-known features and functions in the target compiler, interpreter, or library. Human code golfers do this a lot, and no public training data tells a frontier model how to do so.

</details>