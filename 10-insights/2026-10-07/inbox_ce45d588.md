---
id: inbox_ce45d588
date: 2026-10-07
source_ref: "[[00-inbox/2026-10-07/0256-simon-willison-quoting-ben-affleck-479a]]"
title: "Quoting Ben Affleck"
url: https://simonwillison.net/2026/Oct/7/ben-affleck/
source: simon-willison
published_at: 2026-10-07T23:14:58+00:00
fetched_at: 2026-10-18T03:05:49.279281+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 引用演員 Ben Affleck 在 Pythonista 的訪談片段。Affleck 說自己從小就對電腦有興趣，電影從類比轉數位後更關注這一面，而視覺特效工作流程多年來就包含機器學習。他表示自己能寫「相當糟的 Python 腳本」，並解釋卷積神經網路（CNN，transformer 的前身）如何處理影像：把影像轉成 tensor，即以批次編號、影格編號與每個像素的紅綠藍數值表示的數字。CNN 在 tensor 中找出模式以做邊緣偵測與特徵擷取，例如辨識窗台位置，以便更容易摳除綠幕並替換背景。這則內容屬科普性訪談引文，沒有新產品或數據，僅呈現影視特效與機器學習的長期關聯。"
key_points:
  - "視覺特效工作流程多年來已包含機器學習"
  - "Affleck 以 tensor（批次、影格、每像素 RGB 值）說明 CNN 影像處理"
  - "CNN 的邊緣偵測與特徵擷取用於辨識窗台等物件，以便摳除綠幕並替換背景"
tags: [machine-learning, cnn, visual-effects, python]
topics: [research.training]
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting Ben Affleck

Simon Willison 引用演員 Ben Affleck 在 Pythonista 的訪談片段。Affleck 說自己從小就對電腦有興趣，電影從類比轉數位後更關注這一面，而視覺特效工作流程多年來就包含機器學習。他表示自己能寫「相當糟的 Python 腳本」，並解釋卷積神經網路（CNN，transformer 的前身）如何處理影像：把影像轉成 tensor，即以批次編號、影格編號與每個像素的紅綠藍數值表示的數字。CNN 在 tensor 中找出模式以做邊緣偵測與特徵擷取，例如辨識窗台位置，以便更容易摳除綠幕並替換背景。這則內容屬科普性訪談引文，沒有新產品或數據，僅呈現影視特效與機器學習的長期關聯。

### 重點
- 視覺特效工作流程多年來已包含機器學習
- Affleck 以 tensor（批次、影格、每像素 RGB 值）說明 CNN 影像處理
- CNN 的邊緣偵測與特徵擷取用於辨識窗台等物件，以便摳除綠幕並替換背景

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/7/ben-affleck/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I've always been kind of into computers since I was young. And then when film started to move from analog film to digital, I became more interested in that aspect of it. And the visual effects workflow for many years has included machine learning. 
 So I can write like pretty shitty Python scripts and stuff like that because with convolutional neural networks, which were the sort of precursors to what the transformer can do, which is just much more computation simultaneously, you would do things like look at what's called a tensor, which is just the numerical translation of a visual image in numbers — like the batch number, the frame number, the red, green, and blue values of each pixel in each frame. 
 And a tensor, you use a convolutional neural network to identify patterns in that that would reveal what's called edge detection or feature extraction, which is just identifying patterns enough to know like this is where the window ledge is, so we can more easily take the green screen image out and replace it with something. 
 &mdash; Ben Affleck , Pythonista 

 Tags: machine-learning , python

</details>