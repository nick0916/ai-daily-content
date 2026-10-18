---
id: inbox_9d9072ad
date: 2026-10-14
source_ref: "[[00-inbox/2026-10-14/0256-rtk-releases-v1-0-1-766e]]"
title: "v1.0.1"
url: https://github.com/rtk-ai/rtk/releases/tag/v1.0.1
source: rtk-releases
published_at: 2026-10-14T13:45:44+00:00
fetched_at: 2026-10-18T03:22:18.332134+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "rtk-ai/rtk 於 2026-10-14 發布穩定版 v1.0.1，為 bug fix 版本。第一項修正是 gain 指令只在 rtk pipeline share 指令存在的情況下才建議使用它（commit 2d352df，closes #4557）。第二項修正是 proxy 在 llm-proxy start 與各 agent launcher 中現在會遵守 RTK_PROXY_BIND 環境變數（commit 4a583f8，closes #4556）。對使用 rtk llm-proxy 並需要自訂綁定位址的使用者較有實務意義，其餘為小幅修正。"
key_points:
  - "gain：僅在 rtk pipeline share 指令存在時才提示（2d352df，closes #4557）"
  - "proxy：llm-proxy start 與 agent launchers 現在遵守 RTK_PROXY_BIND（4a583f8，closes #4556）"
  - "v1.0.1 發布於 2026-10-14，為 bug fix 版"
tags: [rtk, bugfix, llm-proxy, release, v1-0-1]
topics: [agents.coding_agents]
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v1.0.1

rtk-ai/rtk 於 2026-10-14 發布穩定版 v1.0.1，為 bug fix 版本。第一項修正是 gain 指令只在 rtk pipeline share 指令存在的情況下才建議使用它（commit 2d352df，closes #4557）。第二項修正是 proxy 在 llm-proxy start 與各 agent launcher 中現在會遵守 RTK_PROXY_BIND 環境變數（commit 4a583f8，closes #4556）。對使用 rtk llm-proxy 並需要自訂綁定位址的使用者較有實務意義，其餘為小幅修正。

### 重點
- gain：僅在 rtk pipeline share 指令存在時才提示（2d352df，closes #4557）
- proxy：llm-proxy start 與 agent launchers 現在遵守 RTK_PROXY_BIND（4a583f8，closes #4556）
- v1.0.1 發布於 2026-10-14，為 bug fix 版

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/v1.0.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

1.0.1 (2026-10-14) 
 Bug Fixes 
 -* gain: only suggest rtk pipeline share where the command exists ( 2d352df ), closes #4557 
 
 proxy: honour RTK_PROXY_BIND in llm-proxy start and the agent launchers ( 4a583f8 ), closes #4556

</details>