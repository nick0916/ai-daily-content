---
id: inbox_62ebce13
date: 2026-10-28
source_ref: "[[00-inbox/2026-10-28/0016-simon-willison-github-octoverse-2026-faa4]]"
title: "GitHub Octoverse 2026"
url: https://simonwillison.net/2026/Oct/28/github-octoverse-2026/
source: simon-willison
published_at: 2026-10-28T16:45:23+00:00
fetched_at: 2026-10-29T00:21:41.193626+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitHub 年度報告顯示，AI agent 讓程式碼產出量在一年內暴增約三倍。 **How** Octoverse 方法論用 LLM 從使用者個人檔案萃取國家代碼以修正 VPN 偏差；用微調的多語 embedding 模型把 2022–2026 建立的公開 repo 依 NAICS 產業分類；並以關鍵字統計 interoperability／reverse engineering 相關 repo。 **What** GitHub Octoverse 2026（由 EVP Jay Parikh 在 GitHub Universe 公布）：merged PR 不到一年成長三倍，達每月 2.2 億；commits 超過三倍，達每月 73.8 億，且多數增長出現在 2026 下半年；新 repo 建立速度翻倍，達每月 3,030 萬。Simon Willison 視此為 agentic engineering 對 GitHub 影響的明確證據。"
key_points:
  - "merged PR 不到一年成長三倍，達每月 2.2 億"
  - "commits 超過三倍至每月 73.8 億，多數增長在 2026 下半年；新 repo 速率翻倍至每月 3,030 萬"
  - "方法論：以 LLM 從個人檔案抽取國家碼修正 VPN 偏差，並用微調 embedding 模型依 NAICS 分類 repo"
tags: [github, octoverse, agentic-engineering, coding-agents, developer-stats]
topics: [agents.coding_agents, product_and_org.adoption]
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## GitHub Octoverse 2026

GitHub 年度報告顯示，AI agent 讓程式碼產出量在一年內暴增約三倍。

**How** Octoverse 方法論用 LLM 從使用者個人檔案萃取國家代碼以修正 VPN 偏差；用微調的多語 embedding 模型把 2022–2026 建立的公開 repo 依 NAICS 產業分類；並以關鍵字統計 interoperability／reverse engineering 相關 repo。

**What** GitHub Octoverse 2026（由 EVP Jay Parikh 在 GitHub Universe 公布）：merged PR 不到一年成長三倍，達每月 2.2 億；commits 超過三倍，達每月 73.8 億，且多數增長出現在 2026 下半年；新 repo 建立速度翻倍，達每月 3,030 萬。Simon Willison 視此為 agentic engineering 對 GitHub 影響的明確證據。

### 重點
- merged PR 不到一年成長三倍，達每月 2.2 億
- commits 超過三倍至每月 73.8 億，多數增長在 2026 下半年；新 repo 速率翻倍至每月 3,030 萬
- 方法論：以 LLM 從個人檔案抽取國家碼修正 VPN 偏差，並用微調 embedding 模型依 NAICS 分類 repo

**原文：** [simon-willison](https://simonwillison.net/2026/Oct/28/github-octoverse-2026/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

GitHub Octoverse 2026 
I'm at GitHub Universe today (GitHub gave me a free ticket through their "GitHub Stars" program). EVP Jay Parikh just announced this year's Octoverse report, and highlighted these numbers in particular: 
 
 This is a pretty stark representation of the impact of agentic engineering on GitHub. In 2026, merged pull requests tripled in less than a year to 220 million per month. Commits more than tripled to 7.38 billion per month, with most of that increase in the second half of this year. New repository rate doubled this year, to 30.3 million per month. 
 The report includes new numbers by industry, and breaks out numbers for repositories that involve "interoperability or reverse engineering". The methodology section includes notes about how they did this: 
 
 Top countries by pushes to public repositories, adjusted by profile location . Pushes from each country were summed across the Octoverse year. To adjust for biases caused by VPN usage, LLM classification was used to extract the ISO 3166-1 alpha-2 code from the profiles of GitHub users who contributed pushes during this period [...] 
 Industry . Public repositories created 2022 to 2026 were sorted into NAICS sectors by a fine-tuned multilingual embedding model using name, description, topics, and README, from random samples per year. [...] 
 Interoperability . Counts public repositories created each year whose name, description, topics, or README mention interoperability or reverse engineering, or related terms, such as clean room implementation, drop-in replacement, or protocol re-implementation. 
 

 Tags: github , ai , generative-ai , llms , coding-agents , disclosures , agentic-engineering

</details>