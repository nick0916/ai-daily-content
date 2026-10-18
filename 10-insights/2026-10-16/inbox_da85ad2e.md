---
id: inbox_da85ad2e
date: 2026-10-16
source_ref: "[[00-inbox/2026-10-16/0256-simon-willison-quoting-addy-osmani-morgan-westlee-lunt-98ff]]"
title: "Quoting Addy Osmani, Morgan Westlee Lunt, and Qing Wang"
url: https://simonwillison.net/2026/Oct/16/code-review/
source: simon-willison
published_at: 2026-10-16T22:06:37+00:00
fetched_at: 2026-10-18T03:03:45.774738+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 引用 Addy Osmani、Morgan Westlee Lunt、Qing Wang 的文章〈How the Claude Code team does code review〉。核心論點是：「有沒有人類讀過程式碼？」只是一個不精確的代理指標，真正該問的是「這個變更可能出什麼錯，哪一種檢查（自動或人工）最適合抓到它？」這個提問也改變了 review 發生的時間點：過去是路尾的關卡（寫程式、開 PR、等同事），現在則像寫作時的拼字檢查一樣持續進行。多數變更在請人類看之前，已經被 Claude 審查並修正過至少一次，用來攔截常規錯誤，並把團隊的注意力保留給更高層次的問題。對導入 coding agent 的團隊而言，這是重新設計 review 流程的參考框架。"
key_points:
  - "把「人類有沒有讀過程式碼」改為「這個變更可能出什麼錯，哪個檢查（自動或人工）最適合抓」"
  - "Review 從 PR 末端的關卡，變成寫作過程中持續執行、類似拼字檢查"
  - "多數變更在人類審查前，已先由 Claude 審查並修正至少一次，人類注意力留給高層次問題"
tags: [code-review, claude-code, agentic-engineering, coding-agents, review-workflow]
topics: [agents.coding_agents, engineering.evals]
importance: 3
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting Addy Osmani, Morgan Westlee Lunt, and Qing Wang

Simon Willison 引用 Addy Osmani、Morgan Westlee Lunt、Qing Wang 的文章〈How the Claude Code team does code review〉。核心論點是：「有沒有人類讀過程式碼？」只是一個不精確的代理指標，真正該問的是「這個變更可能出什麼錯，哪一種檢查（自動或人工）最適合抓到它？」這個提問也改變了 review 發生的時間點：過去是路尾的關卡（寫程式、開 PR、等同事），現在則像寫作時的拼字檢查一樣持續進行。多數變更在請人類看之前，已經被 Claude 審查並修正過至少一次，用來攔截常規錯誤，並把團隊的注意力保留給更高層次的問題。對導入 coding agent 的團隊而言，這是重新設計 review 流程的參考框架。

### 重點
- 把「人類有沒有讀過程式碼」改為「這個變更可能出什麼錯，哪個檢查（自動或人工）最適合抓」
- Review 從 PR 末端的關卡，變成寫作過程中持續執行、類似拼字檢查
- 多數變更在人類審查前，已先由 Claude 審查並修正至少一次，人類注意力留給高層次問題

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/16/code-review/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

We think "did a human read the code?" is an imprecise proxy for "what could go wrong with this change, and which check—automated or human—is the right one to catch it?" 
 Asking that question also changed when review happens. Before, review was a gate at the end of the road: write the code, open a PR, wait for your colleague. 
 Now, review runs continuously, more like spellcheck while you write. Most changes have been reviewed and fixed by Claude at least once before a human is asked to look. This catches most routine mistakes, and saves team attention for higher-level questions and scrutiny. 
 &mdash; Addy Osmani, Morgan Westlee Lunt, and Qing Wang , How the Claude Code team does code review 

 Tags: anthropic , claude , ai , claude-code , llms , addy-osmani , coding-agents , generative-ai , agentic-engineering , code-review

</details>