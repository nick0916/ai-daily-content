---
id: inbox_432c0e6c
date: 2026-11-02
source_ref: "[[00-inbox/2026-11-02/2326-lobsters-ai-sparks-of-weight-space-programming-llms-4f56]]"
title: "Sparks of Weight-Space Programming: LLMs can natively read & write neural network weights"
url: https://rikiyat.github.io/blog/weight-space-programming/
source: lobsters-ai
published_at: 2026-11-02T13:24:33-06:00
fetched_at: 2026-11-02T23:35:04.910432+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓 LLM 用推理直接讀寫神經網路權重，不經梯度下降。 **Why** 權重過去只能靠最佳化器或訓練程式產生，人難以直接理解或修改，這項研究測試前沿 LLM 能否直接處理。 **How** 把權重以自然語言提示交給模型，要求它判斷訓練任務、找出失效原因並改寫權重；部分實驗不允許執行網路或輸入任何資料。 **What** 作者為 MIT CSAIL；僅憑權重即可辨識四款 PPO 策略的訓練遊戲；修改 Qwen3.5-0.8B 的 0.016% 權重後，MATH-500 由 7.9% 升至 48.1%，IFEval 約提升 3 倍；零樣本寫出的 MinAtar 網路在 Breakout、Seaquest、Asterix 三款遊戲皆勝過 100M 步 PPO 訓練的網路。"
key_points:
  - "僅憑權重讀取：GPT-6 Astra（文中模型名）能從四個 PPO 遊戲策略的原始權重判斷訓練遊戲，也能辨識 DDPM 擴散模型生成的形狀，以及三個字元級語言模型的語言與 attention head 功能（含 induction head）。"
  - "權重修正：在 Qwen3.5-0.8B 上找出導致推理迴圈的權重問題，編輯 0.016% 權重，MATH-500 由 7.9% 升至 48.1%，IFEval 約提升 3 倍；Kinetix 車輛任務改寫 3.5% 權重後 1,024 回合全部成功。"
  - "零樣本撰寫：在不給資料、梯度或 rollout 的條件下，依遊戲規則與原始碼寫出 MinAtar 網路，三款遊戲皆優於 100M 步 PPO；Breakout 中第一層計算球的落點、第二層控制球拍移動。"
tags: [weight-space-programming, interpretability, model-editing, llm-reasoning, neural-network-weights]
topics: [research.interpretability, research.training]
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Sparks of Weight-Space Programming: LLMs can natively read & write neural network weights

讓 LLM 用推理直接讀寫神經網路權重，不經梯度下降。

**Why** 權重過去只能靠最佳化器或訓練程式產生，人難以直接理解或修改，這項研究測試前沿 LLM 能否直接處理。

**How** 把權重以自然語言提示交給模型，要求它判斷訓練任務、找出失效原因並改寫權重；部分實驗不允許執行網路或輸入任何資料。

**What** 作者為 MIT CSAIL；僅憑權重即可辨識四款 PPO 策略的訓練遊戲；修改 Qwen3.5-0.8B 的 0.016% 權重後，MATH-500 由 7.9% 升至 48.1%，IFEval 約提升 3 倍；零樣本寫出的 MinAtar 網路在 Breakout、Seaquest、Asterix 三款遊戲皆勝過 100M 步 PPO 訓練的網路。

### 重點
- 僅憑權重讀取：GPT-6 Astra（文中模型名）能從四個 PPO 遊戲策略的原始權重判斷訓練遊戲，也能辨識 DDPM 擴散模型生成的形狀，以及三個字元級語言模型的語言與 attention head 功能（含 induction head）。
- 權重修正：在 Qwen3.5-0.8B 上找出導致推理迴圈的權重問題，編輯 0.016% 權重，MATH-500 由 7.9% 升至 48.1%，IFEval 約提升 3 倍；Kinetix 車輛任務改寫 3.5% 權重後 1,024 回合全部成功。
- 零樣本撰寫：在不給資料、梯度或 rollout 的條件下，依遊戲規則與原始碼寫出 MinAtar 網路，三款遊戲皆優於 100M 步 PPO；Breakout 中第一層計算球的落點、第二層控制球拍移動。

**原文：** [lobsters-ai](https://rikiyat.github.io/blog/weight-space-programming/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Sparks of Weight-Space Programming: LLMs can natively read & write neural network weights

Weight-Space Programming

Can LLMs understand model behaviors from weights?

Can an LLM write neural network weights?

Real-World Relevant Scenarios (Scaling Up and Tool-use)

Background and Related Works

What Comes Next?

Logs

Acknowledgements

Authors

Affiliations

Published

Can Astra tell which game the network was trained on just from the weights?

Can Astra tell what the diffusion model will generate?

Can Astra tell what a language model learned, from the middle of the network alone?

Can Astra fix a failing network by editing its weights?

Can the LLM write weights from scratch?

Writing a Go algorithm

Which language model is sycophantic?

Make a language model better at math

Raising math capability of a model that does not loop

Citation

Rikiya Takehi *

Jayden Teoh *

Alex Zhang

Omar Khattab 

MIT CSAIL

MIT CSAIL

MIT CSAIL

MIT CSAIL

November 2, 2026

We find that frontier LLMs are surprisingly good at natively reading and writing neural network weights , well past what we’d expect from humans or conventional algorithms. This might be a big deal for both optimization and interpretability.

Just by looking at the raw weights, GPT-6 Astra can tell what a network was trained to do . And without any environment feedback, it has no trouble writing, from scratch, small game-playing networks that outplay networks trained with PPO for 100 million steps.

Likewise, asked to make Qwen3.5-0.8B better at math without gradients, Astra identifies an issue in its weights causing reasoning loops that Qwen’s own model card warns about, and fixes this by natively editing 0.016% of the weights . With the same sampling settings, this weight correction raises MATH-500 from 7.9% to 48.1% and generalizes out of the box to instruction following, raising IFEval by 3x.

All of this is possible without allowing Astra to write training loops. It uses its reasoning to figure out what each part of a neural network computes, or should compute, and changes the weights accordingly. We call this Weight-Space Programming .

Throughout the history of deep learning, we encoded our simplistic inductive biases into tiny symbolic optimizers like Adam or Muon. This is changing: our neural network weights will soon be natively optimized by LLMs that deliberately reason about their weights .

If you were asked to handcraft a neural network that plays Go, what would you do? If you were handed raw neural network weights and asked to predict their behavior, where would you even start? For almost any human, this is practically impossible.

Today, weights are written by optimization , by custom networks trained to write them , or by compilers from formal programs . In this post, we find that the current generation of frontier LLMs, used natively in natural language, are starting to become eerily good at understanding and crafting neural network weights around natural-language goals.

For a few years now, we’ve all been using LLMs to optimize text artifacts like prompts and the programs built around them . More recently, we’ve started using them to optimize whole harnesses and the training code and hyperparameters that train ML models .

We often justified these methods by reference to the fact that we don’t know other principled ways to hill-climb on text artifacts, unlike for updating the weights of differentiable neural networks . After all, humans can “optimize” code by hand, for example, so it made sense to ask LLMs to do it, but they can’t “optimize” neural weights by hand, so those remained largely in the realm of symbolic algorithms.

In this post, we share very early results that allow us to argue that the paradigm of reasoning-driven optimization is now coming even for differentiable neural networks .

In Weight-Space Programming , a general-purpose LLM reads and writes a network’s weights directly (i.e., not through an optimizer, and in particular not with gradient descent) around some natural language spec, sometimes even with no environment feedback at all.

In natural language, it’s becoming possible to “just ask” an LLM to natively find a hidden trait or failure inside the weights of a neural network, to fix that failure, or to write a new network from scratch . We report early, exciting results on each of these below, first on small networks and then even on real language models:

We start with a small-scale experiment to see if LLMs can understand the continuous weight space, which is essentially just a list of numbers.

In our first experiments, we train some neural network with some algorithm. It would be extremely exciting if the LLM is able to tell its behavior just from the weights.

We trained neural network policies with PPO to play four computer games. All four networks take the same input channels, choose from the same actions, and have exactly the same network dimensions, so that it is not able to tell unless the weights are read.

For each of these networks, we pass its raw weights into Astra as a prompt, and ask: Which game was this neural network trained on? Without revealing the options of the games we consider, Astra was still able to name the right game for all four networks. This is exciting particularly because there are so many games out there that Astra could choose from.

It seems that Astra was able to work out what game each network was built to play, just from features of its weights. For example, where each input channel’s first-layer weights concentrate (e.g., for Breakout, the agent’s weights lie along the bottom row, a paddle), and which actions the output layer tells apart.

Next, we wanted to see if this generalizes to other tasks and models.

We train diffusion models (DDPM) to generate circle, triangle, and square images independently. We then ask Astra if it could tell what the DDPMs are trained to generate, just from the weights alone. We do not allow tool use or forward passes.

Astra was able to tell what each model generates, from the weights alone. It finds the shape in the output layer, where each hidden unit’s weights draw one piece of the shape’s edge, and it draws just those edges. Interestingly, it draws every shape as an outline, ignoring that the actual models generate filled shapes. This mistake kind of shows it does not rely on calculating the forward pass, but rather it actually reads the structure/geometry of the weights.

Now, in the first two experiments above, Astra was not really looking at the full network and could get away with only reading the first or the last layers. This is not a scalable strategy for larger (particularly language) models and problems we really care about, as how they process and think through their input often happens in the intermediate layers. So next, we take the first and last layers away and leave Astra with only the middle layers.

We train three small language models (7.2M parameters) to predict the next character, one each on Python code The Python code dataset, as a list of its files with a script that rebuilds it: GitHub . , Japanese in alphabet (romaji) , and English . We then remove the input and output layers and give Astra only the four transformer blocks in between. Without these two layers, nothing in the weights says which character is which, and the model cannot be run on any text. Astra may analyze the weights with Python, but it may not run the network or any of its layers on any input.

We ask: which language was this network trained on, and what each of its 24 attention heads does . Astra names the right language for all three networks, in both of its attempts. It also finds every copying head (induction head), the heads that let a model repeat text it has seen earlier, and names no other head as one. 

The reasoning went like this. To tell Python apart, Astra looked for copying heads, which let a model repeat earlier text, such as completing tot to tot al when tot al came before. Without running anything, it found a first-layer head that looks one character back and then, by multiplying weight matrices, the later heads that search using what that head brings along ( Figure 1 ). We find that this is actually a method presented by Elhage et al. , which we never mentioned to Astra. Code repeats names far more than prose, so many copying heads pointed to Python.

Romaji stood out instead because the last of the four blocks it was given (not the output layer, which was removed) writes in fewer distinct directions, as if the model had fewer letters to tell apart. Indeed, romaji never uses some letters like q, l, v and x.

So far, Astra has only read weights. Now, we ask if Astra knows how to write the weights.

We train a PPO network to operate a car such that it can scale a ramp in a Kinetix environment . To do so, it needs to reverse the car for some distance, such that it has enough runway to accelerate long enough to overcome the ramp. However, the PPO network converges to a local-minimum policy where it drives straight at the ramp and gets stuck.

We give GPT-6 Astra the weights, a description of the scene and one recorded episode, and ask it to explain why the network fails, then fix it by writing new weights. In a single try with no tools, Astra’s edit makes the car succeed in all 1,024 episodes, changing 3.5% of the weights.

From the environment context and the PPO network’s trajectory, Astra identifies that the network has converged to a local minimum. Through minimal edits to the weights, Astra changes the policy to back up the car before driving forward at full speed. Astra’s reasoning shows how: it adds a small separate path through a few units per layer that reads the car’s position and speed, and once the green wheel is past the red strip, the path switches off and the trained network drives the rest.

Now let's see if Astra can write a neural network from scratch in zero-shot.

We take three MinAtar games : Breakout, Seaquest and Asterix. For each of them, we provide Astra the game rules and source code, and the corresponding network. There is no access to data, loss, gradients, and tools. We also do not allow Astra to roll out the network in the environment. With just the network weights and environment description, Astra generates the new weights in text directly, after which we evaluate the new network.

Astra’s generated networks beat PPO trained for 100 million steps in all three games. Against PPO trained for 500 million steps, they score 20 times as much in Breakout, come close in Asterix, and reach 60% of its score in Seaquest.

How does it do it: Astra reasons about the desired programs it wants each network to implement and converts them into neural form. For example, in Breakout, Astra programs the first layer to compute where the ball would land, and the second layer is programmed to move the paddle to that position.

So far, most networks we have examined have weights that fit into Astra’s context directly, and we have not enabled tool use. Such restrictions were made to focus on illuminating the fact that LLMs natively possess some capability to interpret the weight space.

From here on out, we seek to push the capabilities of Weight-Space Programming and consider more real-world-relevant scenarios where the networks do not fit within context and where tools can assist the LLM's understanding/writability of the weight space.

We now test Astra’s capability to edit weights at the 1.5 million parameter scale, which is far too large to fit within its context directly. Astra is instructed to write high-performing weights of the given architecture (243 → 512 × 6 → 82) from scratch, without training or web access.

Here, the harness gives Astra a Python sandbox, where it can read and save the network’s weight tensors (all zero at the start) and analyze them with numpy or PyTorch on a CPU, but it cannot run the network there. To see what the network actually does, it has to sp

[... truncated for safety ...]

</details>