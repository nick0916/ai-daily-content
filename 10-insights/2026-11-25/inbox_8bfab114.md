---
id: inbox_8bfab114
date: 2026-11-25
source_ref: "[[00-inbox/2026-11-25/0052-infoq-main-github-ditches-css-in-js-for-css-modules-49e2]]"
title: "GitHub Ditches CSS-in-JS for CSS Modules, Reports 55% Faster SSR after Three-Year Migration"
url: https://www.infoq.com/news/2026/11/github-css-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-25T15:29:00+00:00
fetched_at: 2026-11-27T00:59:38.361593+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitHub 花三年把網站樣式從執行時才算的 CSS-in-JS 換成編譯期就產生的 CSS Modules，讓伺服器渲染變快。 **Why** CSS-in-JS（styled-components）在伺服器端渲染與元件初始化時要即時計算樣式，造成效能負擔。 **How** 以 feature flag 逐步轉換 Primer 元件，並用 codemod 搭配 Copilot agents 遷移約 7,760 處 sx prop 用法。 **What** github.com 從 styled-components 遷移到 CSS Modules，伺服器端渲染時間減少 55%，元件初始化快 25%。留言者質疑對實際使用者的影響，以及 hash 化 class name 的問題。"
key_points:
  - "github.com 由 styled-components 遷至 CSS Modules，歷時三年"
  - "SSR 時間降低 55%，元件初始化加快 25%"
  - "Primer 元件以 feature flag 轉換，約 7,760 處 sx prop 用 codemod 與 Copilot agents 遷移"
tags: [css-modules, styled-components, github, ssr, migration]
topics: [engineering.architecture, agents.coding_agents]
importance: 3
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## GitHub Ditches CSS-in-JS for CSS Modules, Reports 55% Faster SSR after Three-Year Migration

GitHub 花三年把網站樣式從執行時才算的 CSS-in-JS 換成編譯期就產生的 CSS Modules，讓伺服器渲染變快。

**Why** CSS-in-JS（styled-components）在伺服器端渲染與元件初始化時要即時計算樣式，造成效能負擔。

**How** 以 feature flag 逐步轉換 Primer 元件，並用 codemod 搭配 Copilot agents 遷移約 7,760 處 sx prop 用法。

**What** github.com 從 styled-components 遷移到 CSS Modules，伺服器端渲染時間減少 55%，元件初始化快 25%。留言者質疑對實際使用者的影響，以及 hash 化 class name 的問題。

### 重點
- github.com 由 styled-components 遷至 CSS Modules，歷時三年
- SSR 時間降低 55%，元件初始化加快 25%
- Primer 元件以 feature flag 轉換，約 7,760 處 sx prop 用 codemod 與 Copilot agents 遷移

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/github-css-migration/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

GitHub migrated github.com from styled-components to CSS Modules over three years, reporting a 55% cut in server-side rendering time and 25% faster component initialisation. Primer components were converted behind feature flags, and about 7,760 sx prop usages were migrated with codemods and Copilot agents. Commenters questioned user impact and hashed class names. By Daniel Curtis

</details>