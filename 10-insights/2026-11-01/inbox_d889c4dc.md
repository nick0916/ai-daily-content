---
id: inbox_d889c4dc
date: 2026-11-01
source_ref: "[[00-inbox/2026-11-01/0001-claude-mem-releases-v15-8-1-26ff]]"
title: "v15.8.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.8.1
source: claude-mem-releases
published_at: 2026-11-01T20:04:20+00:00
fetched_at: 2026-11-02T00:08:26.811957+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v15.8.1 整理專案目錄結構，執行行為與 npm 套件內容不變。 **Why** 根目錄條目過多，README 在 GitHub 頁面位置偏下。 **What** 根目錄由 60 項減為 36 項；文件與測試資產移入 docs/、tests/、.github/、.claude/、docker/；CHANGELOG 移至 docs/CHANGELOG.md，安全政策移至 .github/SECURITY.md；Cloudflare sync hub 原始碼移至 services/sync-hub（PR #5259）。"
key_points:
  - "根目錄條目由 60 減為 36"
  - "CHANGELOG 移至 docs/CHANGELOG.md，SECURITY 政策移至 .github/SECURITY.md"
  - "Cloudflare sync hub 原始碼移至 services/sync-hub，npm 套件內容未變"
tags: [claude-mem, repo-structure, release-notes]
topics: [agents.coding_agents]
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.8.1

claude-mem v15.8.1 整理專案目錄結構，執行行為與 npm 套件內容不變。

**Why** 根目錄條目過多，README 在 GitHub 頁面位置偏下。

**What** 根目錄由 60 項減為 36 項；文件與測試資產移入 docs/、tests/、.github/、.claude/、docker/；CHANGELOG 移至 docs/CHANGELOG.md，安全政策移至 .github/SECURITY.md；Cloudflare sync hub 原始碼移至 services/sync-hub（PR #5259）。

### 重點
- 根目錄條目由 60 減為 36
- CHANGELOG 移至 docs/CHANGELOG.md，SECURITY 政策移至 .github/SECURITY.md
- Cloudflare sync hub 原始碼移至 services/sync-hub，npm 套件內容未變

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.8.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Repository cleanup. No changes to how claude-mem runs. 
 
 The repo root drops from 60 entries to 36, so the README sits much higher on the GitHub page. 
 Old plans, reports, playbooks and generated files are gone, along with the superseded cursor-hooks/ and ragtime/ directories. 
 Docs, test assets and Docker files moved into docs/ , tests/ , .github/ , .claude/ and docker/ . The changelog now lives at docs/CHANGELOG.md , and the security policy at .github/SECURITY.md . 
 The Cloudflare sync hub source moved to services/sync-hub . 
 The npm package contents are unchanged. 
 
 Full PR: #5259

</details>