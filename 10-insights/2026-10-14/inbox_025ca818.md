---
id: inbox_025ca818
date: 2026-10-14
source_ref: "[[00-inbox/2026-10-14/0256-rtk-releases-dev-1-0-1-rc-534-6a3d]]"
title: "dev-1.0.1-rc.534"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-1.0.1-rc.534
source: rtk-releases
published_at: 2026-10-14T10:54:43+00:00
fetched_at: 2026-10-18T03:22:43.602102+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK（rtk-ai/rtk）發布開發預覽版 dev-1.0.1-rc.534。此版本合併 PR #4563（分支 fix/proxy-bind-env），修正 proxy 相關問題：`llm-proxy start` 指令與各 agent launcher 現在會遵循 `RTK_PROXY_BIND` 環境變數。原文僅有這一項變更，未提供更多細節。對象是使用 RTK 的 LLM proxy 並透過環境變數指定綁定位址的使用者。"
key_points:
  - "dev-1.0.1-rc.534 合併 PR #4563（fix/proxy-bind-env）"
  - "`llm-proxy start` 與 agent launchers 現在會遵循 `RTK_PROXY_BIND` 環境變數"
tags: [rtk, llm-proxy, release-candidate, bugfix]
topics: [agents.coding_agents]
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-1.0.1-rc.534

RTK（rtk-ai/rtk）發布開發預覽版 dev-1.0.1-rc.534。此版本合併 PR #4563（分支 fix/proxy-bind-env），修正 proxy 相關問題：`llm-proxy start` 指令與各 agent launcher 現在會遵循 `RTK_PROXY_BIND` 環境變數。原文僅有這一項變更，未提供更多細節。對象是使用 RTK 的 LLM proxy 並透過環境變數指定綁定位址的使用者。

### 重點
- dev-1.0.1-rc.534 合併 PR #4563（fix/proxy-bind-env）
- `llm-proxy start` 與 agent launchers 現在會遵循 `RTK_PROXY_BIND` 環境變數

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-1.0.1-rc.534)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #4563 from rtk-ai/fix/proxy-bind-env 

 fix(proxy): honour RTK_PROXY_BIND in `llm-proxy start` and the agent launchers

</details>