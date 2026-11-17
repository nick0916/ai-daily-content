---
id: inbox_584e554d
date: 2026-11-16
source_ref: "[[00-inbox/2026-11-16/2317-infoq-main-github-rebuilds-the-copilot-app-s-diff-s-fbd0]]"
title: "GitHub Rebuilds the Copilot App's Diff Surface to Open Million-Line Pull Requests Without Jank"
url: https://www.infoq.com/news/2026/11/github-pull-requests-rebuild/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-16T10:32:00+00:00
fetched_at: 2026-11-17T23:25:04.130714+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitHub 重寫 Copilot app 的 diff 畫面，讓超大 PR 也能順暢開啟。 **Why** 一個 PR 可能有數千檔案、上百萬行變更，傳統 diff 畫面會卡頓。 **How** 把固定高度的程式碼列與可變高度的留言區塊分開處理，留言區塊只在視窗附近批次量測；並用 CI 效能預算與自動化 app 執行來把關效能。 **What** 測試案例為 2,200 個檔案、逾 100 萬行變更、400 則行內留言的 PR，在 Copilot app 中可順暢開啟。"
key_points:
  - "測試規模：2,200 檔案、100 萬+ 變更行、400 則行內留言"
  - "固定高度程式碼列與可變高度留言區塊分離"
  - "留言區塊於視窗附近批次量測，效能以 CI budget 與自動化 app 執行檢查"
tags: [github, copilot, diff-view, performance, virtualization]
topics: [product_and_org.product, engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## GitHub Rebuilds the Copilot App's Diff Surface to Open Million-Line Pull Requests Without Jank

GitHub 重寫 Copilot app 的 diff 畫面，讓超大 PR 也能順暢開啟。

**Why** 一個 PR 可能有數千檔案、上百萬行變更，傳統 diff 畫面會卡頓。

**How** 把固定高度的程式碼列與可變高度的留言區塊分開處理，留言區塊只在視窗附近批次量測；並用 CI 效能預算與自動化 app 執行來把關效能。

**What** 測試案例為 2,200 個檔案、逾 100 萬行變更、400 則行內留言的 PR，在 Copilot app 中可順暢開啟。

### 重點
- 測試規模：2,200 檔案、100 萬+ 變更行、400 則行內留言
- 固定高度程式碼列與可變高度留言區塊分離
- 留言區塊於視窗附近批次量測，效能以 CI budget 與自動化 app 執行檢查

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/github-pull-requests-rebuild/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

GitHub engineers rebuilt the diff view in the Copilot app to handle a pull request with 2,200 files, over a million changed lines and 400 inline comments. The design separates fixed-height code rows from variable-height comment blocks, which are measured in batches near the viewport. Performance is checked through CI budgets and automated app runs. By Daniel Curtis

</details>