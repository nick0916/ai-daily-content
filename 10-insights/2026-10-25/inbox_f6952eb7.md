---
id: inbox_f6952eb7
date: 2026-10-25
source_ref: "[[00-inbox/2026-10-25/0250-claude-mem-releases-v15-2-1-npm-trusted-publishing-87f5]]"
title: "v15.2.1 — npm trusted publishing"
url: https://github.com/thedotmack/claude-mem/releases/tag/v15.2.1
source: claude-mem-releases
published_at: 2026-10-25T19:45:33+00:00
fetched_at: 2026-10-26T02:58:59.315596+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem 改用 npm 信任發布（OIDC），取代長效 NPM_TOKEN。 **Why** 原 NPM_TOKEN 自 v13.26.1 起每次 tag 發布都失敗。 **How** 發布工作流程以短效 OIDC token 向 npm 驗證，並附上 provenance 證明，連結套件與建置它的 commit 和 workflow。 **What** 此版本無執行期行為變更，只是讓發布走新管道。"
key_points:
  - "改用 OIDC trusted publishing，以短效 token 取代長效 NPM_TOKEN"
  - "新增 npm provenance attestation，連結套件與建置的 commit、workflow"
  - "無執行期行為變更；相關 PR 為 #5063"
tags: [npm, oidc, supply-chain, ci-cd, provenance]
topics: [security, engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v15.2.1 — npm trusted publishing

claude-mem 改用 npm 信任發布（OIDC），取代長效 NPM_TOKEN。

**Why** 原 NPM_TOKEN 自 v13.26.1 起每次 tag 發布都失敗。

**How** 發布工作流程以短效 OIDC token 向 npm 驗證，並附上 provenance 證明，連結套件與建置它的 commit 和 workflow。

**What** 此版本無執行期行為變更，只是讓發布走新管道。

### 重點
- 改用 OIDC trusted publishing，以短效 token 取代長效 NPM_TOKEN
- 新增 npm provenance attestation，連結套件與建置的 commit、workflow
- 無執行期行為變更；相關 PR 為 #5063

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v15.2.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What changed 
 
 npm publishing now uses trusted publishing (OIDC). The "Publish to npm" GitHub Actions workflow authenticates to npm with a short-lived OIDC token issued for this repository's workflow instead of the long-lived NPM_TOKEN secret, which had been failing on every tag since v13.26.1. Trusted publishes also carry an npm provenance attestation linking the package to the commit and workflow that built it. ( #5063 ) 
 
 No runtime behavior changes in the plugin or worker; this release exists to ship through the new publishing path. 
 Full Changelog : v15.2.0...v15.2.1

</details>