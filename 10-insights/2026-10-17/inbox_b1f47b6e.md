---
id: inbox_b1f47b6e
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-rtk-releases-dev-1-0-2-rc-551-a42c]]"
title: "dev-1.0.2-rc.551"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-1.0.2-rc.551
source: rtk-releases
published_at: 2026-10-17T00:42:13+00:00
fetched_at: 2026-10-18T03:22:01.935794+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK（rtk-ai/rtk）發布 dev-1.0.2-rc.551 預發布版本，內容為合併 PR #4308（作者 tayfuryldz，分支 fix/4297-hook-background-work）。修正為「fix(hook): skip background checks in hook commands」，也就是在 hook 指令執行時跳過背景檢查。原文僅有這一行，未說明具體是哪些背景檢查，也未提供效能數據。"
key_points:
  - "dev-1.0.2-rc.551 合併 PR #4308，對應 issue #4297"
  - "hook 指令不再執行背景檢查"
tags: [rtk, hooks, release]
topics: [agents.coding_agents]
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-1.0.2-rc.551

RTK（rtk-ai/rtk）發布 dev-1.0.2-rc.551 預發布版本，內容為合併 PR #4308（作者 tayfuryldz，分支 fix/4297-hook-background-work）。修正為「fix(hook): skip background checks in hook commands」，也就是在 hook 指令執行時跳過背景檢查。原文僅有這一行，未說明具體是哪些背景檢查，也未提供效能數據。

### 重點
- dev-1.0.2-rc.551 合併 PR #4308，對應 issue #4297
- hook 指令不再執行背景檢查

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-1.0.2-rc.551)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #4308 from tayfuryldz/fix/4297-hook-background-work 

 fix(hook): skip background checks in hook commands

</details>