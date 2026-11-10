---
id: inbox_d53bde22
date: 2026-11-10
source_ref: "[[00-inbox/2026-11-10/2322-simon-willison-quoting-prompting-claude-fable-5-2-3d52]]"
title: "Quoting Prompting Claude Fable 5.2"
url: https://simonwillison.net/2026/Nov/10/prompting-claude-fable-52/
source: simon-willison
published_at: 2026-11-10T05:34:14+00:00
fetched_at: 2026-11-10T23:28:41.356140+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "在提示詞裡說明程式碼歸誰，會改變模型要不要重構。 **Why** Claude Fable 5.2 對提示中「誰擁有這份程式碼」很敏感；沒提或當成別人的程式碼時，它傾向沿用既有結構、即使重複也照加。 **How** 在提示中加一句「這份程式碼是你的」，例如：This codebase is yours: what it's for and how it's built are your call, and you'll keep building on it. **What** Anthropic 在小型程式任務的測試中，加這句後模型約半數嘗試會合併重複程式碼，沒加則不到一成。出自 Anthropic 文件 Prompting Claude Fable 5.2。"
key_points:
  - "加入「程式碼是你的」一句後，約半數嘗試會合併重複程式碼"
  - "未加該句時，合併比例不到一成"
  - "未提或視為他人程式碼時，模型傾向沿用既有結構、持續新增"
tags: [claude-fable-5-2, prompt-engineering, coding-agents, refactoring]
topics: [foundation_models.claude, agents.coding_agents]
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting Prompting Claude Fable 5.2

在提示詞裡說明程式碼歸誰，會改變模型要不要重構。

**Why** Claude Fable 5.2 對提示中「誰擁有這份程式碼」很敏感；沒提或當成別人的程式碼時，它傾向沿用既有結構、即使重複也照加。

**How** 在提示中加一句「這份程式碼是你的」，例如：This codebase is yours: what it's for and how it's built are your call, and you'll keep building on it.

**What** Anthropic 在小型程式任務的測試中，加這句後模型約半數嘗試會合併重複程式碼，沒加則不到一成。出自 Anthropic 文件 Prompting Claude Fable 5.2。

### 重點
- 加入「程式碼是你的」一句後，約半數嘗試會合併重複程式碼
- 未加該句時，合併比例不到一成
- 未提或視為他人程式碼時，模型傾向沿用既有結構、持續新增

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/10/prompting-claude-fable-52/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Claude Fable 5.2 responds closely to what the prompt says about who owns the code it works on. In Anthropic’s testing on small coding tasks, when a prompt said nothing about ownership or presented the code base as someone else’s, the model tended to add to the existing structure, even when that repeated existing code. [...] 
 If you want the model to improve the structure as it works, say that the code is its own: 
 
 This codebase is yours: what it's for and how it's built are your call, and you'll keep building on it. 
 
 In Anthropic’s testing on small coding tasks, the model merged repeated code in about half of the tries with this sentence, and in under a tenth of the tries without it. 
 — Prompting Claude Fable 5.2 , Anthropic documentation 

 Tags: prompt-engineering , anthropic , generative-ai , ai , llms , claude-mythos-fable

</details>