---
id: inbox_8538f93e
date: 2026-11-12
source_ref: "[[00-inbox/2026-11-12/youtube/0255-youtube-ai-engineer-stop-shipping-llm-settings-that-only-win-8c77]]"
title: "Stop Shipping LLM Settings That Only Win on Paper - Rohan Pandey & Balaji Varadarajan, DigitalOcean"
url: https://www.youtube.com/watch?v=cWrYEBlWpcY
source: youtube-ai-engineer
published_at: 2026-11-12T01:00:00+00:00
fetched_at: 2026-11-12T03:00:22.270672+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用貝氏最佳化讓 agent 自動調出模型推論服務的最佳參數，取代人工試錯。 **Why** 手動尋找 VLM serving 的最佳設定（recipe）非常耗時，自動化可在背景跑完省下大量時間。 **How** 用 Optuna 以貝氏最佳化縮小搜索空間，每輪 trial 對現行 recipe 評分後調整並重跑，涵蓋 chat short、chat long、rag、batch classify 四種情境，執行 tuner.py 並指定 study 名稱、起始 YAML、硬體與 trial 數。 **What** DigitalOcean 的優化 agent demo：GPT OSS 模型經 50 trials（約 4–5 小時）後 goodput tokens 較初始設定提升 17.5%；DeepSeek R1 distill 模型僅 9 trials，token throughput 翻倍、ITL 幾乎減半。輸出為 HTML 報告與最佳化後的 YAML recipe。"
key_points:
  - "用 Optuna + 貝氏最佳化在搜索迴圈中逐 trial 評分並調整 VLM serving recipe"
  - "GPT OSS：50 trials、約 4–5 小時，goodput tokens 較初始設定提升 17.5%"
  - "DeepSeek R1 distill：9 trials 後 token throughput 翻倍、ITL 降近一半"
tags: [inference-optimization, bayesian-optimization, optuna, vlm-serving, digitalocean]
topics: [engineering.inference]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Stop Shipping LLM Settings That Only Win on Paper - Rohan Pandey & Balaji Varadarajan, DigitalOcean

用貝氏最佳化讓 agent 自動調出模型推論服務的最佳參數，取代人工試錯。

**Why** 手動尋找 VLM serving 的最佳設定（recipe）非常耗時，自動化可在背景跑完省下大量時間。

**How** 用 Optuna 以貝氏最佳化縮小搜索空間，每輪 trial 對現行 recipe 評分後調整並重跑，涵蓋 chat short、chat long、rag、batch classify 四種情境，執行 tuner.py 並指定 study 名稱、起始 YAML、硬體與 trial 數。

**What** DigitalOcean 的優化 agent demo：GPT OSS 模型經 50 trials（約 4–5 小時）後 goodput tokens 較初始設定提升 17.5%；DeepSeek R1 distill 模型僅 9 trials，token throughput 翻倍、ITL 幾乎減半。輸出為 HTML 報告與最佳化後的 YAML recipe。

### 重點
- 用 Optuna + 貝氏最佳化在搜索迴圈中逐 trial 評分並調整 VLM serving recipe
- GPT OSS：50 trials、約 4–5 小時，goodput tokens 較初始設定提升 17.5%
- DeepSeek R1 distill：9 trials 後 token throughput 翻倍、ITL 降近一半

**原文：** [youtube-ai-engineer](https://www.youtube.com/watch?v=cWrYEBlWpcY)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Right. Hello everyone. So my name is Rohan and this is a quick demo on the optimization agent that what has been recently built. So a quick intro into what the purpose is and what the goal is of this agent and then I'll get into a brief demo and results that uh from a previous run that we just did. So what the goal is here is to build an agent that helps um find the best VLM serving config for any given model. Uh the purpose is to reduce the time it takes to manually um find the best configs and the VLM serving recipe. And if we can automate this and have it run in the background and um have the agent find the recipes and the optimized parameters faster, then it will save a lot of time. So that's the goal of the agent and a little bit more into how the agent actually does this. So the strategy that the agent uses is called Beijian optimization and bian optimization is a technique um that's used to find the most optimal numbers um in any given situation. So in our situation it's to find the optimal numbers in this uh VLM recipe. Uh it uses mathematical steps that essentially minimizes the search space. So by minimizing the search space it uh reduces a lot of the time that it takes in finding the optimized uh numbers in this uh recipe during the run. So B uh basian optimization is a strategy that is used but optuna is the tool that uses a strategy in the search loop. So optuna uses beijan optimization it feeds it the current recipe the starting recipe. uh Beijian optimization runs on that and over many iterations or many trials, it eventually finds the optimized recipe and Optina basically takes each recipe after every trial, assesses it, gets a score, um uses a strategy to change the recipe, improve it and then it reruns it within the uh search loop um until the trials is done. So let's go a little bit into how uh we do this. So I'm currently in a droplet here and this droplet for example has GPT OSS uh 12B model loaded up. So what we can do is uh we can look at the current um recipe. So what we see here is four regimes right that we're testing it on. So there's chat short, there's chat long, there's rag and batch classify. Uh they have their own set of ISL OSL tokens that we're feeding it through. Uh all these um can be changed depending on what uh we want to see. But essentially this is the starting uh config starting recipe that you would get when you download the weights of the model. Um so moving once you have the model downloaded in your droplet and you're ready to run this agent you paste in this command uh which essentially tells you you know where the where the weights are coming from. um activate a virtual um environment and have um uh or not have but run the script called tuner.py. Uh this script essentially tells you or it has a couple of things you have to tell it. So you you want to give it the name of the study. You want to tell it the starting uh YAML file which we just saw above here. You want to tell it the hardware that it's running on and you want to tell it the number of trials that you want. So uh in this example we have 24. Um, briefly I'll show you another example of a past run that was run uh that had only nine trials. So um uh anyway uh this is the command that's that's run. Uh typically these commands take um a couple hours to run. I think for the GPTO it says it took about four or five hours and then for the other model it took a couple hours as well. So we can go into the HTML report that's generated after the uh agent finishes its work. Um so this one is for the GPTOSS model that I mentioned. Uh what what we see in the HTML report is which trial number was the best trial out of the total of how many trials. So in this case it was 50 trials. uh you get so at the end of the run you get an optimized uh YAML file which includes all the numbers that we currently look for in the BLM serving recipe. So in this case we found or the agent found that 256 was the optimized number uh so on and so forth and the way that it's getting the accuracy is the amount of goodput tokens that's being generated. So uh overall we found that from the first config we had an improvement of 17.5% in terms of uh tokens generated and this one as I mentioned is for GPOSS. We have another HTML report here which is for the deepseek R1 distill uh model. In here we found that or in here we had uh nine trials that was run and out of the nine the ninth one was the best. uh we found that token throughput uh doubled and ITL was improved by almost half aka it was reduced by almost half. So this is the quick intro and brief demo on the commands you run and what the output looks like in in in general you get a HTML report that tells you um how each trial went and then you also get um a YAML file that has the optimized recipe at the end of the day. So hopefully that was helpful. Thank you.

</details>