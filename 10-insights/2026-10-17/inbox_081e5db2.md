---
id: inbox_081e5db2
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-rtk-releases-dev-1-0-2-rc-552-1573]]"
title: "dev-1.0.2-rc.552"
url: https://github.com/rtk-ai/rtk/releases/tag/dev-1.0.2-rc.552
source: rtk-releases
published_at: 2026-10-17T13:25:15+00:00
fetched_at: 2026-10-18T03:22:01.935141+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "RTK（rtk-ai/rtk）發布 dev-1.0.2-rc.552 預發布版本，內容為合併 PR #3879（作者 b3hz4d，分支 fix/worktree-git-rewrite-3864）。修正為「fix(hooks): leave git unrewritten in Claude Code managed worktrees」，即在 Claude Code 管理的 worktree 中，hook 不再改寫 git 指令。原文只有這一行說明，未提供更多細節，影響對象推測為在 Claude Code worktree 中使用 RTK hook 的使用者（這是推論）。"
key_points:
  - "dev-1.0.2-rc.552 合併 PR #3879，對應 issue #3864"
  - "Claude Code managed worktrees 中的 hook 不再改寫 git 指令"
tags: [rtk, claude-code, hooks, git-worktree]
topics: [agents.coding_agents]
importance: 2
novelty: 1
insight_quality: 1
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## dev-1.0.2-rc.552

RTK（rtk-ai/rtk）發布 dev-1.0.2-rc.552 預發布版本，內容為合併 PR #3879（作者 b3hz4d，分支 fix/worktree-git-rewrite-3864）。修正為「fix(hooks): leave git unrewritten in Claude Code managed worktrees」，即在 Claude Code 管理的 worktree 中，hook 不再改寫 git 指令。原文只有這一行說明，未提供更多細節，影響對象推測為在 Claude Code worktree 中使用 RTK hook 的使用者（這是推論）。

### 重點
- dev-1.0.2-rc.552 合併 PR #3879，對應 issue #3864
- Claude Code managed worktrees 中的 hook 不再改寫 git 指令

**原文：** [rtk-releases](https://github.com/rtk-ai/rtk/releases/tag/dev-1.0.2-rc.552)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge pull request #3879 from b3hz4d/fix/worktree-git-rewrite-3864 

 fix(hooks): leave git unrewritten in Claude Code managed worktrees

</details>