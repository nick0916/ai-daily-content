---
id: inbox_ed60afbb
date: 2026-11-03
source_ref: "[[00-inbox/2026-11-03/2347-simon-willison-qwen-3-8-27b-on-my-laptop-can-interpret-45da]]"
title: "Qwen 3.8 27B on my laptop can interpret model weights, too"
url: https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/
source: simon-willison
published_at: 2026-11-03T16:29:48+00:00
fetched_at: 2026-11-03T23:53:01.630822+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把一大串模型權重數字直接貼給 AI 看，不給工具，它也能猜出這個網路是在玩哪款遊戲。 **Why** 一篇熱門論文宣稱前沿模型能直接讀寫神經網路權重（Weight-Space Programming），但論文把「不用工具直接讀權重」與「有程式碼工具去改模型」兩件事混在一起，Simon 認為應分開看。 **How** 他用論文 repo 的 exp1_which_game prompt（四款簡化 10x10 遊戲的策略網路權重，禁用工具、單次回答），透過 llm 的 -f 選項搭配 LM Studio 與 llm-lmstudio plugin，在筆電上跑 Qwen 3.8 27B（17GB），並把 timeout 調到 900 秒、context 拉長（預設 8192 會出錯）。 **What** Qwen 3.8 27B 答對 Pac-Man（46 分、43,506 reasoning tokens）、Pong（約 65 分）、Breakout（約 52 分，信心 88%），Freeway 答錯；Kimi K3.1 Pro 經 OpenRouter 約 9 分 41 秒答對 Breakout。Simon 認為有經驗的人用紙筆也可能做到，不認同「原始碼時代結束」的評論。"
key_points:
  - "論文 Sparks of Weight-Space Programming（Takehi、Teoh、Zhang、Khattab）稱 GPT-6 Astra 改 Qwen3.5-0.8B 約 0.016% 權重，MATH-500 由 7.9% 升至 48.1%"
  - "Qwen 3.8 27B（17GB）本機跑 Pac-Man 耗時 46m12s、43,506 reasoning tokens，Pong 1h4m54s、Breakout 52m25s，Freeway 答錯"
  - "重點區分「無工具直接讀權重」與「有程式碼工具改模型」兩個問題；Honnibal 批評論文混為一談"
tags: [weight-space-programming, qwen, local-llms, paper-review, interpretability]
topics: [research.interpretability, foundation_models.open_weights]
importance: 3
novelty: 4
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen 3.8 27B on my laptop can interpret model weights, too

把一大串模型權重數字直接貼給 AI 看，不給工具，它也能猜出這個網路是在玩哪款遊戲。

**Why** 一篇熱門論文宣稱前沿模型能直接讀寫神經網路權重（Weight-Space Programming），但論文把「不用工具直接讀權重」與「有程式碼工具去改模型」兩件事混在一起，Simon 認為應分開看。

**How** 他用論文 repo 的 exp1_which_game prompt（四款簡化 10x10 遊戲的策略網路權重，禁用工具、單次回答），透過 llm 的 -f 選項搭配 LM Studio 與 llm-lmstudio plugin，在筆電上跑 Qwen 3.8 27B（17GB），並把 timeout 調到 900 秒、context 拉長（預設 8192 會出錯）。

**What** Qwen 3.8 27B 答對 Pac-Man（46 分、43,506 reasoning tokens）、Pong（約 65 分）、Breakout（約 52 分，信心 88%），Freeway 答錯；Kimi K3.1 Pro 經 OpenRouter 約 9 分 41 秒答對 Breakout。Simon 認為有經驗的人用紙筆也可能做到，不認同「原始碼時代結束」的評論。

### 重點
- 論文 Sparks of Weight-Space Programming（Takehi、Teoh、Zhang、Khattab）稱 GPT-6 Astra 改 Qwen3.5-0.8B 約 0.016% 權重，MATH-500 由 7.9% 升至 48.1%
- Qwen 3.8 27B（17GB）本機跑 Pac-Man 耗時 46m12s、43,506 reasoning tokens，Pong 1h4m54s、Breakout 52m25s，Freeway 答錯
- 重點區分「無工具直接讀權重」與「有程式碼工具改模型」兩個問題；Honnibal 批評論文混為一談

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Yesterday's hot paper was Sparks of Weight-Space Programming: LLMs can natively read & write neural network weights by Rikiya Takehi, Jayden Teoh, Alex Zhang, and Omar Khattab. The paper (OK, the authors classify is as a "blog post", but it's paper-shaped) found that frontier models, in particular GPT-6 Astra, can both interpret and modify the raw weights of a machine learning model - literally a text description of the model containing a bunch of floating point numbers. I've been playing with one of the examples from the paper and I'm delighted to share that Qwen 3.8 27B running on my laptop can do this as well! 
 Weight-Space Programming 
 Here's the highlight from their abstract, describing impressive capabilities for GPT-6 Astra and coining the term Weight-Space Programming for when LLMs analyze and modify model weights: 
 
 Just by looking at the raw weights, GPT-6 Astra can tell what a network was trained to do . And without any environment feedback, it has no trouble writing, from scratch, small game-playing networks that outplay networks trained with PPO for 100 million steps. 
 Likewise, asked to make Qwen3.5-0.8B better at math without gradients, Astra identifies an issue in its weights causing reasoning loops that Qwen’s own model card warns about, and fixes this by natively editing 0.016% of the weights . With the same sampling settings, this weight correction raises MATH-500 from 7.9% to 48.1% and generalizes out of the box to instruction following, raising IFEval by 3x. 
 All of this is possible without allowing Astra to write training loops. It uses its reasoning to figure out what each part of a neural network computes, or should compute, and changes the weights accordingly. We call this Weight-Space Programming . 
 
 The paper combines two topics that I think deserve to be treated separately. The first is what models can do with raw weights without running tools or executing code. The second explores how well models, once armed with code, can run operations to update and improve other models. 
 spaCy author Matthew Honnibal called the paper misleading for conflating the two, and Sean Goedecke deconstructed the Qwen3.5-0.8B update example as taking the same steps that a human ML researcher would use. 
 I'm going to focus on the no-tools question, which I think is the more interesting of the two. 
 The paper presents the first question as Can LLMs understand model behaviors from weights? They trained four neural networks to play simplified 10x10 grid versions of four classic computer games - Breakout, Pong, Pac-Man, and Freeway (I had to look that one up , it's an Atari 2600 game from 1981). Then they fed those weights (as floating point numbers) to an LLM along with the following question: 
 
 The weights below belong to one policy network that was trained with reinforcement learning to play a game on this grid. Which game was it trained on? Work from the weights. You have no tools: no code execution, no calculator, nothing to run. This is a single response. 
 
 The GitHub repository that accompanies the paper is RikiyaT/lm_understand-logs . The exp1_which_game folder contains the prompts they used, with weights for the four games: 
 
 breakout/prompt.txt 
 freeway/prompt.txt 
 pacman/prompt.txt 
 pong/prompt.txt 
 
 I checked and, aside from the weights, each prompt is identical to the others. 
 Trying it out with Qwen 3.8 27B and other models 
 The prompts on GitHub are self-contained. My LLM tool has a -f/--fragment option which can be passed the URL to a text file to use as a prompt, which means I can run any of the above like this: 
 llm -f https://raw.githubusercontent.com/RikiyaT/lm_understand-logs/refs/heads/main/exp1_which_game/runs/breakout/prompt.txt \
 -m openrouter/moonshotai/kimi-k3.1-pro 
 This example requires the llm-openrouter plugin installed, and runs the Breakout prompt against Kimi K3.1 Pro via OpenRouter. Here's what I got back from Kimi K3.1 Pro , which successfully guessed Breakout after 9m 41s and 19,493 reasoning tokens. 
 But how about Qwen 3.8 27B ? That's still my favorite model to run on my own laptop - it's just 17GB (I use this version ) and somehow feels close to the leading proprietary models of 2025. 
 I fired up LM Studio , ensured Qwen 3.8 27B was loaded with a long context window (the default 8192 context failed with errors), installed the llm-lmstudio plugin and ran this command: 
 LMSTUDIO_TIMEOUT=900 \
 llm -f https://raw.githubusercontent.com/RikiyaT/lm_understand-logs/refs/heads/main/exp1_which_game/runs/pacman/prompt.txt \
 -m lmstudio/qwen/qwen3.8-27b 
 (I had to bump the timeout up using an environment variable, see this issue .) 
 After 46m 12s and 43,506 reasoning tokens, Qwen on my laptop returned a response that ended like this (here's the reasoning trace ): 
 
 Game: A simplified Pac-Man-style gridworld: an agent moves through a fixed 8x8 maze with central and corner wall blocks, moving objects/ghosts, and reward targets/pellets. 
 Description: The agent navigates a fixed maze-like 8x8 board, using current agent/moving-object/previous-frame cues to move through corridors, collect reward-target cells, and avoid moving objects or hazards. 
 Confidence: 72% 
 
 This is impressive. I tried it on two of the other games as well. It identified Pong ( reasoning ) in 1h 4m 54s: 
 
 Pong — specifically a Pong-like paddle/ball game where the agent controls a vertical paddle on the right side and must move up/down to intercept or return a moving ball/reward object. 
 Description: 
 The agent moves a right-side paddle vertically to hit or catch a moving ball-like reward target moving across the 8×8 field, while a left-side moving object/opponent and wall borders define the play; reward is obtained by successfully intercepting/returning/scoring the ball, and missing or failing to hit it is penalized. 
 Confidence: 
 75% 
 
 And Breakout ( reasoning ) in 52m 25s: 
 
 Game: Breakout, or an Arkanoid-like paddle/ball/brick game. 
 Description: The agent is a paddle on the bottom row and moves left/right to keep a ball in play; the ball moves around the upper grid, and bricks/reward targets in the top rows give reward when hit, while missing the ball/hitting the bottom wall ends the episode or gives penalty. 
 Confidence: 88% 
 
 Qwen failed at the Freeway prompt, which didn't surprise me considering that game is more obscure than the other three. Here's that transcript - Qwen thought it was "A simplified Pac-Man-like grid game: agent moves 4-directionally". 
 The reasoning traces are fun to skim, and almost incomprehensible. Here's a sample: 
 
 What about agent channel0? We see some large channel0 rows near row8 col7/8 and maybe bottom? Let's list channel0 large: line436 input435 (row8 col7 ch0) -2.107,1.169,0.513...; line441 input440 (row8 col8 ch0) -0.376,0.010,1.564,3.855...; line445 input444 (row8 col8 ch4) 0.142,0.491...; line382? input381 ch0? Wait line382 input381: 381//5=76 (row7 col6), ch1? 381%5=1? 76 * 5=380, ch1. So not. Channel0 large maybe at row8 col7/8 only. Also top row? line44 input43 ch3, line49 ch3. Channel0 large maybe not many. Agent position could be near bottom-right? If the agent is typically at bottom-right? 
 
 That said though, I expect a sufficiently experienced human being armed with a notepad and a pencil could get there with enough effort. 
 It's a cool paper, but some of the wider commentary I've seen around it does not feel justified. I'm not ready to declare that the age of source code is over and our future involves incomprehensible machines editing their own model weights in incomprehensible ways. 
 
 Tags: machine-learning , ai , generative-ai , local-llms , llms , qwen , paper-review

</details>