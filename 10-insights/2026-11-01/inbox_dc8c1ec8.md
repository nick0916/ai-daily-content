---
id: inbox_dc8c1ec8
date: 2026-11-01
source_ref: "[[00-inbox/2026-11-01/2327-hackernews-show-hn-omnidiff-opensource-super-fast-c-3cd6]]"
title: "Show HN: OmniDiff – Opensource, super fast, content aware Git difftool, in Rust"
url: https://github.com/ivankovic/omnidiff
source: hackernews
published_at: 2026-11-01T13:02:30+00:00
fetched_at: 2026-11-02T23:31:36.873494+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一個用 Rust 寫的 git 差異比對工具，能看懂程式碼以外的圖片、PDF、字型等檔案差異。 **Why** 作者想知道「理想的 diff 工具」該長什麼樣，因此以真實開源 repo 的 diff 為依據來設計。 **How** 他從 Gentoo 套件列出的 7,400 個 repo 抽樣 2,000 筆 diff 並手動解讀，據此為每種內容類型建立 diff pipeline；這套樣本同時作為 CI pipeline 的基礎。 **What** OmniDiff v0.3.0，AGPLv3 開源，可比對 25 種語言的程式碼、設定檔、圖片、PDF、壓縮檔、游標與字型。作者表示在 2023 年 ThinkPad T14s 上，數萬行 C++ 檔案 diff 不到 100ms，並已當作 git difftool 日常使用數月；作者也聲明有使用 AI 但非 vibecode。"
key_points:
  - "支援 25 種程式語言，另含設定檔、圖片、PDF、壓縮檔、游標、字型"
  - "效能：數萬行 C++ 檔案 diff 低於 100ms（2023 ThinkPad T14s）"
  - "設計依據：Gentoo 套件列出的 7,400 個 repo，抽樣 2,000 筆 diff 手動解讀；授權 AGPLv3，版本 v0.3.0"
tags: [git, difftool, rust, open-source, show-hn]
topics: [product_and_org.product]
importance: 2
novelty: 3
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: OmniDiff – Opensource, super fast, content aware Git difftool, in Rust

一個用 Rust 寫的 git 差異比對工具，能看懂程式碼以外的圖片、PDF、字型等檔案差異。

**Why** 作者想知道「理想的 diff 工具」該長什麼樣，因此以真實開源 repo 的 diff 為依據來設計。

**How** 他從 Gentoo 套件列出的 7,400 個 repo 抽樣 2,000 筆 diff 並手動解讀，據此為每種內容類型建立 diff pipeline；這套樣本同時作為 CI pipeline 的基礎。

**What** OmniDiff v0.3.0，AGPLv3 開源，可比對 25 種語言的程式碼、設定檔、圖片、PDF、壓縮檔、游標與字型。作者表示在 2023 年 ThinkPad T14s 上，數萬行 C++ 檔案 diff 不到 100ms，並已當作 git difftool 日常使用數月；作者也聲明有使用 AI 但非 vibecode。

### 重點
- 支援 25 種程式語言，另含設定檔、圖片、PDF、壓縮檔、游標、字型
- 效能：數萬行 C++ 檔案 diff 低於 100ms（2023 ThinkPad T14s）
- 設計依據：Gentoo 套件列出的 7,400 個 repo，抽樣 2,000 筆 diff 手動解讀；授權 AGPLv3，版本 v0.3.0

**原文：** [hackernews](https://github.com/ivankovic/omnidiff)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I have been researching what the ultimate diff tool would look like, based on actual diffs in open source repositories. OmniDiff can diff: code (25 languages), config, images, PDFs, archives, cursors, fonts... It's fast. It can diff C++ files of tens of thousands of lines in under 100ms, on a 2023 ThinkPad T14s. It's open source. AGPLv3. It's based on real diffs. I looked at the 7400 repositories that are listed in Gentoo packages, sampled 2000 diffs and solved them manually to get a good understanding of what is needed, before putting together the diff pipelines for each content type. Incidentally, this also forms the basis of the CI pipeline, so the robustness of the codebase is quite high. I'm still developing it. It's v0.3.0 at this time. But I have been using it daily as my git difftool for months now, and it works well. AI Disclosure: Yes, I do use AI. No, I do not vibecode.

</details>