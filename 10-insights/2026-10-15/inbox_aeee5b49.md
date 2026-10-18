---
id: inbox_aeee5b49
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0256-rtk-releases-dev-1-0-2-rc-548-9c4a]]"
title: "dev-1.0.2-rc.548"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-1.0.2-rc.548
source: rtk-releases
published_at: 2026-10-15T00:11:06+00:00
fetched_at: 2026-10-18T03:22:18.333010+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "rtk-ai/rtk 發布開發預覽版 dev-1.0.2-rc.548，合併 PR #3613（來自 rhishi99/fix/build-mingw-stack-arg）。修正內容為建置時改傳 MinGW linker 的 --stack 參數，而非 MSVC 的 /STACK: 參數。這是針對 Windows 上使用 MinGW 工具鏈編譯時 linker 參數不相容的建置修正。主要影響以 MinGW 自行編譯 rtk 的 Windows 開發者，一般使用者影響有限。"
key_points:
  - "合併 PR #3613，修正建置時 stack 參數"
  - "MinGW 使用 --stack，取代 MSVC 專用的 /STACK:"
  - "影響 Windows MinGW 工具鏈的編譯"
tags: [rtk, build-fix, mingw, windows, release-candidate]
topics: [agents.coding_agents]
importance: 1
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-1.0.2-rc.548

rtk-ai/rtk 發布開發預覽版 dev-1.0.2-rc.548，合併 PR #3613（來自 rhishi99/fix/build-mingw-stack-arg）。修正內容為建置時改傳 MinGW linker 的 --stack 參數，而非 MSVC 的 /STACK: 參數。這是針對 Windows 上使用 MinGW 工具鏈編譯時 linker 參數不相容的建置修正。主要影響以 MinGW 自行編譯 rtk 的 Windows 開發者，一般使用者影響有限。

### 重點
- 合併 PR #3613，修正建置時 stack 參數
- MinGW 使用 --stack，取代 MSVC 專用的 /STACK:
- 影響 Windows MinGW 工具鏈的編譯

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-1.0.2-rc.548)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #3613 from rhishi99/fix/build-mingw-stack-arg 

 fix(build): send the MinGW linker --stack, not MSVC's /STACK:

</details>