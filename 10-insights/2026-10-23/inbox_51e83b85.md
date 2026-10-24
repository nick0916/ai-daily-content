---
id: inbox_51e83b85
date: 2026-10-23
source_ref: "[[00-inbox/2026-10-23/0346-claude-code-releases-v2-1-310-ce76]]"
title: "v2.1.310"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.310
source: claude-code-releases
published_at: 2026-10-23T23:39:00+00:00
fetched_at: 2026-10-24T03:51:18.232255+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 2.1.310 修補多項穩定性與權限顯示問題，並擴大 Monitor 工具與雲端 session 的管理能力。 **Why** 在第三方雲端、企業 gateway 與不同終端環境下，請求相容性、壓縮與權限提示的細節問題會直接造成任務失敗或安全疑慮。 **How** 遇到 gateway 拒絕 effort-2025-11-24 beta 值或 mid-conversation system message 時改為去除後重試；壓縮在遇到 base64、SVG 等高密度文字時保留更少內容，避免下一次請求再度超長。 **What** Claude Code v2.1.310：Monitor 工具與 plugin monitors 現可用於 Bedrock、Vertex、Foundry 及停用 telemetry 的情境；修正 cleanupPeriodDays 過大時誤刪貼上圖片、讀檔權限提示不顯示 symlink 目標，以及 Windows 缺少 Git Bash 時 PreToolUse/PermissionRequest hook 放行工具呼叫的問題。Enterprise 自訂角色新增 Cloud sessions 與 Remote Control 權限，另有 VSCode、Claude Tag、Code Review 管理頁多項修正。"
key_points:
  - "Gateway 拒絕 effort-2025-11-24 beta 值或 mid-conversation system message 時，Claude Code 會去除後自動重試"
  - "安全相關修正：Windows 缺 Git Bash 時 PreToolUse/PermissionRequest hook 會誤放行工具呼叫；讀檔權限提示現在會顯示 symlink 指向位置"
  - "Enterprise 自訂角色新增 Cloud sessions 與 Remote Control 權限，Owner 可依角色控管存取"
tags: [claude-code, release-notes, monitor-tool, cloud-sessions, permissions]
topics: [agents.coding_agents, security]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.310

Claude Code 2.1.310 修補多項穩定性與權限顯示問題，並擴大 Monitor 工具與雲端 session 的管理能力。 **Why** 在第三方雲端、企業 gateway 與不同終端環境下，請求相容性、壓縮與權限提示的細節問題會直接造成任務失敗或安全疑慮。 **How** 遇到 gateway 拒絕 effort-2025-11-24 beta 值或 mid-conversation system message 時改為去除後重試；壓縮在遇到 base64、SVG 等高密度文字時保留更少內容，避免下一次請求再度超長。 **What** Claude Code v2.1.310：Monitor 工具與 plugin monitors 現可用於 Bedrock、Vertex、Foundry 及停用 telemetry 的情境；修正 cleanupPeriodDays 過大時誤刪貼上圖片、讀檔權限提示不顯示 symlink 目標，以及 Windows 缺少 Git Bash 時 PreToolUse/PermissionRequest hook 放行工具呼叫的問題。Enterprise 自訂角色新增 Cloud sessions 與 Remote Control 權限，另有 VSCode、Claude Tag、Code Review 管理頁多項修正。

### 重點
- Gateway 拒絕 effort-2025-11-24 beta 值或 mid-conversation system message 時，Claude Code 會去除後自動重試
- 安全相關修正：Windows 缺 Git Bash 時 PreToolUse/PermissionRequest hook 會誤放行工具呼叫；讀檔權限提示現在會顯示 symlink 指向位置
- Enterprise 自訂角色新增 Cloud sessions 與 Remote Control 權限，Owner 可依角色控管存取

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.310)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added the Monitor tool and plugin monitors on Bedrock, Vertex, and Foundry, and when telemetry or nonessential traffic is disabled; long foreground sleeps are now blocked there too 
 Fixed requests failing behind some gateways and compatible servers that reject the effort-2025-11-24 beta value or mid-conversation system messages; Claude Code now retries without them 
 Fixed background cleanup deleting some recent files, such as pasted images, when cleanupPeriodDays is set to a very large value 
 Fixed compaction after a "Prompt is too long" error keeping too much of a conversation with dense text, such as base64 or SVG, so the next request could fail again 
 Fixed file read permission prompts not showing where a symbolic link leads 
 Fixed a question's auto-continue timeout firing the moment the external editor closed after a long edit 
 Windows: Fixed PreToolUse and PermissionRequest hooks letting a tool call through when Git Bash is missing and the hook's command is only quoted strings, such as a quoted path 
 Improved auto mode's prompt before the first read outside the working directories: it now says when blocking those reads makes shell commands ask for permission 
 Improved memory use of non-interactive sessions ( -p , Agent SDK) during compaction when the transcript file is very large 
 Improved a mod's Image to draw inside tmux with allow-passthrough and focus-events on, in kitty, Ghostty, and iTerm2 3.5+ with fullscreen rendering, where it showed only its alt text 
 Linux: Improved /sandbox and the sandbox startup warning to name Ubuntu's AppArmor restriction on user namespaces, and how to lift it, when it keeps bubblewrap from starting the sandbox 
 Changed the error for an MCP tool call that times out in a non-interactive session while the server's elicitation is unanswered: it now tells Claude that no answer came and not to repeat the call 
 [VSCode] Fixed pressing Enter on the plan review card's "Send feedback and keep planning" button approving the plan instead of sending your comments back 
 [VSCode] Fixed the panel showing "Something went wrong" after "Switch branch &amp; continue" on a cloud session opened from Session history's Web tab 
 [Cloud sessions] Added Claude Code cloud sessions and Remote Control permissions to Enterprise custom roles, so Owners can control access to each by role 
 [Cloud sessions] Added a Choose file button to load a cloud environment's setup script from a file 
 [Cloud sessions] Fixed failed saves and archives in the cloud environment edit dialog showing no error inside the dialog 
 [Cloud sessions] Fixed failed routine API token actions showing only a toast; the error now appears in the routine edit dialog 
 [Cloud sessions] Improved the session start checklist to show a cloud environment's setup script output in a scrolling box 
 [Cloud sessions] Changed turning on Cloud sessions or Remote Control in admin settings to ask for confirmation and list the custom roles that have that permission 
 [Cloud sessions] Changed the cloud environment dialog to open network access, setup script and environment variables from rows instead of listing every editor at once 
 [Claude Tag] Fixed Claude Tag treating ! commands such as !restart and !help as ordinary messages when sent in bold, italic or strikethrough 
 [Claude Tag] Fixed Claude Tag admin channel and workspace pages being replaced by a load error when a background refresh of the bundle list fails 
 [Claude Tag] Fixed Claude Tag's spend limits page in admin settings reporting that no channels match a filter while channel names are still loading 
 [Code Review] Fixed the Code Review admin section hiding its repositories and switches after a failed refresh of the repository list 
 [Code Review] Improved the Code Review admin section to retry the first load and show one Try again banner when it still fails

</details>