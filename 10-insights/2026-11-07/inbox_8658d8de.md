---
id: inbox_8658d8de
date: 2026-11-07
source_ref: "[[00-inbox/2026-11-07/0149-infoq-main-varlock-releases-bumpy-a-file-based-vers-652a]]"
title: "Varlock Releases Bumpy: A File-Based Versioning Alternative to Changesets"
url: https://www.infoq.com/news/2026/11/bumpy-changesets-alternative/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-07T06:54:00+00:00
fetched_at: 2026-11-08T01:53:36.763311+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Varlock 推出 Bumpy，用 markdown 檔管理 monorepo 的版本號與 changelog，是 Changesets 的替代品。 **Why** 原文指 Changesets v3（2026 年 8 月發布）已補上許多早期缺口，但仍有差異。 **How** Bumpy 沿用 changesets 流程，以 markdown bump 檔記錄版本變更，並加入 workspace 與 catalog protocol 支援、自訂 publish 指令與以分支為基礎的 prerelease。 **What** Bumpy 為 MIT 授權、TypeScript 撰寫的工具，由 Varlock 發布，用於 monorepo 版本管理與 changelog。"
key_points:
  - "Bumpy：MIT 授權、TypeScript 寫成，沿用 changesets 的 markdown bump 檔流程"
  - "新增 workspace 與 catalog protocol 支援、自訂 publish 指令、分支式 prerelease"
  - "Changesets v3 於 2026 年 8 月發布，補上多數早期缺口但仍有差異"
tags: [bumpy, changesets, monorepo, versioning, varlock]
topics: [engineering.architecture]
importance: 1
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Varlock Releases Bumpy: A File-Based Versioning Alternative to Changesets

Varlock 推出 Bumpy，用 markdown 檔管理 monorepo 的版本號與 changelog，是 Changesets 的替代品。

**Why** 原文指 Changesets v3（2026 年 8 月發布）已補上許多早期缺口，但仍有差異。

**How** Bumpy 沿用 changesets 流程，以 markdown bump 檔記錄版本變更，並加入 workspace 與 catalog protocol 支援、自訂 publish 指令與以分支為基礎的 prerelease。

**What** Bumpy 為 MIT 授權、TypeScript 撰寫的工具，由 Varlock 發布，用於 monorepo 版本管理與 changelog。

### 重點
- Bumpy：MIT 授權、TypeScript 寫成，沿用 changesets 的 markdown bump 檔流程
- 新增 workspace 與 catalog protocol 支援、自訂 publish 指令、分支式 prerelease
- Changesets v3 於 2026 年 8 月發布，補上多數早期缺口但仍有差異

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/bumpy-changesets-alternative/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Bumpy is an MIT-licensed, TypeScript tool for version management and changelogs in monorepos. It follows the changesets workflow, using markdown bump files, and adds support for workspace and catalog protocols, custom publish commands, and branch-based prereleases. Changesets v3, released in August 2026, closed many earlier gaps, though differences remain. By Daniel Curtis

</details>