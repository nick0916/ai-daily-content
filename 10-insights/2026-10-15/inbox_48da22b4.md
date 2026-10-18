---
id: inbox_48da22b4
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0256-rtk-releases-dev-1-0-2-rc-549-67a4]]"
title: "dev-1.0.2-rc.549"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-1.0.2-rc.549
source: rtk-releases
published_at: 2026-10-15T17:56:49+00:00
fetched_at: 2026-10-18T03:22:18.330626+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "rtk-ai/rtk 發布開發預覽版 dev-1.0.2-rc.549，內容為合併 PR #4203（來自 Protocol-zero-0/chore/rewrite-exit-code-regression-test）。該 PR 新增一項 hook 測試，用來固定（pin）rtk rewrite 流程中的 exit code，對應 issue #3492。這屬於回歸測試性質的變更，目的是避免日後改動 rewrite 時 exit code 行為被意外改變。原文未提供更多功能面細節，主要影響 rtk 的 hook 整合與維護者。"
key_points:
  - "合併 PR #4203，新增 hook 測試固定 rtk rewrite 的 exit code"
  - "對應 issue #3492，屬回歸測試而非新功能"
  - "版本為 dev-1.0.2-rc.549 預發布版"
tags: [rtk, release-candidate, regression-test, hook, exit-code]
topics: [agents.coding_agents]
importance: 1
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-1.0.2-rc.549

rtk-ai/rtk 發布開發預覽版 dev-1.0.2-rc.549，內容為合併 PR #4203（來自 Protocol-zero-0/chore/rewrite-exit-code-regression-test）。該 PR 新增一項 hook 測試，用來固定（pin）rtk rewrite 流程中的 exit code，對應 issue #3492。這屬於回歸測試性質的變更，目的是避免日後改動 rewrite 時 exit code 行為被意外改變。原文未提供更多功能面細節，主要影響 rtk 的 hook 整合與維護者。

### 重點
- 合併 PR #4203，新增 hook 測試固定 rtk rewrite 的 exit code
- 對應 issue #3492，屬回歸測試而非新功能
- 版本為 dev-1.0.2-rc.549 預發布版

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-1.0.2-rc.549)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #4203 from Protocol-zero-0/chore/rewrite-exit-code... 

 ...-regression-test 

 test(hook): pin exit codes across rtk rewrite ( #3492 )

</details>