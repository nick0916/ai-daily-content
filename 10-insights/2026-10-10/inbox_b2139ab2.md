---
id: inbox_b2139ab2
date: 2026-10-10
source_ref: "[[00-inbox/2026-10-10/0256-simon-willison-python-3-15-0-added-to-actions-python-ve-518a]]"
title: "Python 3.15.0 added to actions/python-versions"
url: https://simonwillison.net/2026/Oct/10/python-actions/
source: simon-willison
published_at: 2026-10-10T23:58:04+00:00
fetched_at: 2026-10-18T03:05:17.819495+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 指出 Python 3.15.0 已加入 GitHub 的 actions/python-versions 儲存庫。他自承這是小眾連結，但已等了好幾天，甚至請 ChatGPT 去 clone 該 repo，並每小時 git pull 一次，直到穩定版 3.15 出現再通知他。現在 3.15 已上線，開發者可以在 GitHub Actions 的測試矩陣中加入 \"3.15\"，針對新的 Python 3.15.0 正式版跑測試。對維護 Python 專案 CI 的人來說，這代表可以開始驗證相容性。附帶一個小技巧：用 ChatGPT 做定時輪詢任務來等待某個上游發布。"
key_points:
  - "actions/python-versions 已收錄 Python 3.15.0"
  - "GitHub Actions 測試矩陣可直接加入 \"3.15\""
  - "Simon 用 ChatGPT 指令每小時 git pull 該 repo 來等待發布"
tags: [python-3-15, github-actions, ci, chatgpt]
topics: [engineering.evals]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Python 3.15.0 added to actions/python-versions

Simon Willison 指出 Python 3.15.0 已加入 GitHub 的 actions/python-versions 儲存庫。他自承這是小眾連結，但已等了好幾天，甚至請 ChatGPT 去 clone 該 repo，並每小時 git pull 一次，直到穩定版 3.15 出現再通知他。現在 3.15 已上線，開發者可以在 GitHub Actions 的測試矩陣中加入 "3.15"，針對新的 Python 3.15.0 正式版跑測試。對維護 Python 專案 CI 的人來說，這代表可以開始驗證相容性。附帶一個小技巧：用 ChatGPT 做定時輪詢任務來等待某個上游發布。

### 重點
- actions/python-versions 已收錄 Python 3.15.0
- GitHub Actions 測試矩陣可直接加入 "3.15"
- Simon 用 ChatGPT 指令每小時 git pull 該 repo 來等待發布

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/10/python-actions/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Python 3.15.0 added to actions/python-versions 
Bit of a niche link, but I've been waiting for this for a couple of days - I even told ChatGPT to check for it: 
 
 Clone https://github.com/actions/python-versions and git pull once an hour until they add the stable 3.15 - then tell me about it 
 
 Now that this has landed, you can add "3.15" to a GitHub Actions testing matrix to run tests against the new Python 3.15.0 release .

 Tags: github , python , github-actions , chatgpt

</details>