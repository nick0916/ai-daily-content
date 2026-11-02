---
id: inbox_db7e21b8
date: 2026-11-01
source_ref: "[[00-inbox/2026-11-01/0002-lobsters-ai-an-easy-way-to-try-local-ai-with-brainde-3bb3]]"
title: "An easy way to try local AI with braindead-local-intelligence"
url: https://dataswamp.org/~solene/2026-11-01-braindead-local-intelligence.html
source: lobsters-ai
published_at: 2026-11-01T14:26:47-06:00
fetched_at: 2026-11-02T00:08:49.974193+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用一套 podman 容器，讓一般人在自家 Linux 機器上快速試用本地 LLM 與圖像生成。 **Why** 作者想省去挑選大量模型檔與逐一安裝元件的步驟，只需要簡單試玩本地 AI。 **How** 以 rootless podman 組合 OpenAI 相容的 LLM 伺服器、圖像生成伺服器、SearXNG 網搜與 Open WebUI，同一時間只在記憶體載入一個模型，請求到達時才載入，閒置數分鐘後卸載。 **What** 指令為 `bin/ia install`、`ia doctor`、`ia start`、`ia info`；需 podman 5.0+，目前只在 AMD 顯卡測試，最高測到 12GB VRAM，最小模型約需 4GB VRAM 與 8GB RAM；作者以 Qwen3.6 35B-A3B 搭配網搜，回答慢（部分模型跑在 RAM，常需數分鐘），但資料不離開本機（網搜除外）。"
key_points:
  - "一個入口整合 LLM、圖像生成、SearXNG 網搜與 Open WebUI，同一時間只載入一個模型，請求時載入、閒置數分鐘後卸載以釋放 GPU 記憶體"
  - "需求：Linux + podman 5.0+（rootless）；目前僅針對 AMD GPU，未測 NVIDIA；測試上限 12GB VRAM，最小模型約 4GB VRAM / 8GB RAM"
  - "作者實測 Qwen3.6 35B-A3B 配合網搜效果不錯，但因一半模型在 RAM，單次回答可能需要數分鐘"
tags: [local-llm, podman, open-webui, self-hosted, amd-gpu, searxng]
topics: [engineering.inference, foundation_models.open_weights]
importance: 3
novelty: 2
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## An easy way to try local AI with braindead-local-intelligence

用一套 podman 容器，讓一般人在自家 Linux 機器上快速試用本地 LLM 與圖像生成。

**Why** 作者想省去挑選大量模型檔與逐一安裝元件的步驟，只需要簡單試玩本地 AI。

**How** 以 rootless podman 組合 OpenAI 相容的 LLM 伺服器、圖像生成伺服器、SearXNG 網搜與 Open WebUI，同一時間只在記憶體載入一個模型，請求到達時才載入，閒置數分鐘後卸載。

**What** 指令為 `bin/ia install`、`ia doctor`、`ia start`、`ia info`；需 podman 5.0+，目前只在 AMD 顯卡測試，最高測到 12GB VRAM，最小模型約需 4GB VRAM 與 8GB RAM；作者以 Qwen3.6 35B-A3B 搭配網搜，回答慢（部分模型跑在 RAM，常需數分鐘），但資料不離開本機（網搜除外）。

### 重點
- 一個入口整合 LLM、圖像生成、SearXNG 網搜與 Open WebUI，同一時間只載入一個模型，請求時載入、閒置數分鐘後卸載以釋放 GPU 記憶體
- 需求：Linux + podman 5.0+（rootless）；目前僅針對 AMD GPU，未測 NVIDIA；測試上限 12GB VRAM，最小模型約 4GB VRAM / 8GB RAM
- 作者實測 Qwen3.6 35B-A3B 配合網搜效果不錯，但因一半模型在 RAM，單次回答可能需要數分鐘

**原文：** [lobsters-ai](https://dataswamp.org/~solene/2026-11-01-braindead-local-intelligence.html)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Table of contents

1. Introduction §

2. What it does §

3. Requirements §

4. Getting started §

5. Usage §

6. Conclusion §

I wanted a simple way to try local AI on my computer when I need to experiment, both a LLM to chat with (with web search and image recognition) and a model to generate or modify images. Most guides require installing a lot of things and choosing models among thousands of files, so I made a small project doing it for me.

braindead-local-intelligence project page

The name is a bad pun, "braindead" because you just start it to try without much thinking about it, and "local intelligence" because it runs some "intelligence" on your own computer :)

In this blog post, I present the project and how to get started with it.

The project runs a few containers with podman: a LLM server compatible with the OpenAI API, an image generation server, SearXNG for the web search and Open WebUI as a web interface. Everything is behind a single address, protected by a token if you need to expose it to an external service.

A feature I really like is that you do not have to choose between the LLM and the image model, or to switch from one to the other. Only one model is loaded in memory at a time, the right model is loaded when a request arrives, and it is unloaded after a few minutes without any request, so your GPU memory is free again when you do not use it.

There is a list of ready to use models in the documentation, chosen for regular hardware people have at home and for different needs: small text models, models understanding images, image generation models, and two models able to modify an existing image. Changing the model is a matter of copying a block of configuration and restarting, the clients do not need to change anything.

List of the proposed models

On the software side, you only need a Linux system with podman 5.0 or newer using rootless mode (everything runs under your own user, no root involved). The project currently targets AMD graphics cards, it was never tested with NVIDIA cards because I do not have one.

On the hardware side, you still need a GPU with some memory (VRAM), the models were tested up to 12 GB of VRAM, and you also need RAM because the biggest models run partly in RAM. The list should allow you to try a few things without a powerful gaming computer, although the smallest models need something like 4 GB of VRAM and 8 GB of RAM. I use a computer I built in 2021 with 32 GB of RAM and a Radeon RX 6700 XT (released in January 2021), it still works very well.

The project has its own documentaiton, but here are the main steps.

Your user needs to access the GPU, and to be in the groups render and video , then log out and log in again:

From the project directory, install it and check that everything is fine, the second command should list your AMD graphics card:

The copy/paste commands will download the models in ~/.local/share/ia-locale/models , the default ones weigh about 8 GB. Then start the services, it can take several minutes to download the containers for all runtimes:

The command ia info displays the address, the token and the model names to use in a client compatible with the OpenAI API.

The simplest way to use it is the web interface Open WebUI at http://127.0.0.1:3000, only reachable from the computer itself. You can chat, send a picture, and enable the web search or the image generation from the + menu in the input box.

I got good results so far with Qwen3.6 35B-A3B, coupled with the web search it does a pretty good job. It is slow though, it "thinks" before answering, and as half of the model runs in RAM, an answer can take a few minutes, but it runs locally. Having a 35B model with web search allows it to be smart enough to gather information and "understand it", without having to know everything and serve outdated information.

I also use it with Camille, a Mattermost bot used within a community of friends, which replies when pinged. Everyone configures it as they want to use the model of their choice, it uses two different models depending on the request depending if it is for text or image. Mistral have a free API that allows to use ministral on it, it is a bit too dumb though, but nice if you want to give it a try.

Camille GitHub page

Do not expect miracles, this is slow and your computer will get hot and noisy while crunching for a reply. This will always be very far from the LLMs as a service that use much more advanced models and a context window (the amount of text a model can handle at once) way bigger than what you can run at home. Even spending a few dozen of thousand of euros or dollars would not approach it.

But it is a nice way to play with local AI and see what your hardware can do, and nothing leaves your computer except the web searches.

As stupid as small models might sound, they could still be used for some tasks, for instance if you just need it to understand a context and say yes or no , this can be well integrated into a CI or maybe filtering local SPAM. If you can run the 35B model, it opens to a lot more of cool stuff.

1. Introduction 

2. What it does 

3. Requirements 

4. Getting started 

5. Usage 

6. Conclusion 

sudo usermod -aG render,video $USER

bin/ia install
ia doctor

ia start

</details>