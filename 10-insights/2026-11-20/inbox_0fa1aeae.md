---
id: inbox_0fa1aeae
date: 2026-11-20
source_ref: "[[00-inbox/2026-11-20/0047-claude-code-releases-v2-1-330-e182]]"
title: "v2.1.330"
url: https://github.com/anthropics/claude-code/releases/tag/v2.1.330
source: claude-code-releases
published_at: 2026-11-20T22:32:56+00:00
fetched_at: 2026-11-21T00:52:26.524678+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude Code 這版以修復穩定性問題為主，同時加入企業登入與內建圖表功能。 **Why** 多個 Claude Code 行程同時寫入設定、plugin、task 時會遺失資料，長對話 compact 後也會卡住數分鐘。 **What** Claude Code v2.1.330：新增登入 Enterprise Admin Console 管理的組織（`claude auth login` 後套用組織設定）、內建 easel 圖表 mod（Pro、Max，Team/Enterprise 視情況，macOS 與 Linux，可在 /config 關閉）、`CLAUDE_CODE_FULL_SIGN_IN_LINK=1`。self-hosted runner 新增 `--start-dir` 與兩個 /metrics 指標。修復項目包含 compact 後卡頓、WebFetch 卡住、ExitWorktree 誤刪他人使用中的 worktree、/rewind 還原舊版檔案，並還原 2.1.329 移除的 max_tokens 超限自動重試。（原文結尾被截斷，部分內容未涵蓋）"
key_points:
  - "新增 Enterprise Admin Console 組織登入：`claude auth login` 後套用組織設定，並使用其雲端供應商或 gateway"
  - "新增內建圖表 mod easel（Pro/Max，Team/Enterprise 視情況；macOS、Linux），可在 /config 關閉自動圖表"
  - "修復多行程併發寫入造成設定、plugin 清單、task 相依資料遺失，並還原 2.1.329 移除的 max_tokens 自動重試"
tags: [claude-code, release, self-hosted-runner, enterprise, bug-fix]
topics: [agents.coding_agents]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.1.330

Claude Code 這版以修復穩定性問題為主，同時加入企業登入與內建圖表功能。

**Why** 多個 Claude Code 行程同時寫入設定、plugin、task 時會遺失資料，長對話 compact 後也會卡住數分鐘。

**What** Claude Code v2.1.330：新增登入 Enterprise Admin Console 管理的組織（`claude auth login` 後套用組織設定）、內建 easel 圖表 mod（Pro、Max，Team/Enterprise 視情況，macOS 與 Linux，可在 /config 關閉）、`CLAUDE_CODE_FULL_SIGN_IN_LINK=1`。self-hosted runner 新增 `--start-dir` 與兩個 /metrics 指標。修復項目包含 compact 後卡頓、WebFetch 卡住、ExitWorktree 誤刪他人使用中的 worktree、/rewind 還原舊版檔案，並還原 2.1.329 移除的 max_tokens 超限自動重試。（原文結尾被截斷，部分內容未涵蓋）

### 重點
- 新增 Enterprise Admin Console 組織登入：`claude auth login` 後套用組織設定，並使用其雲端供應商或 gateway
- 新增內建圖表 mod easel（Pro/Max，Team/Enterprise 視情況；macOS、Linux），可在 /config 關閉自動圖表
- 修復多行程併發寫入造成設定、plugin 清單、task 相依資料遺失，並還原 2.1.329 移除的 max_tokens 自動重試

**原文：** [claude-code-releases](https://github.com/anthropics/claude-code/releases/tag/v2.1.330)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What's changed 
 
 Added sign-in to organizations managed in Anthropic's Enterprise Admin Console: after claude auth login , Claude Code applies the organization's settings and uses its cloud provider or gateway 
 Added easel, a built-in mod that draws charts when asked and under MCP metrics results, on Pro, Max and, where available, Team and Enterprise on macOS and Linux; turn automatic charts off in /config 
 Added CLAUDE_CODE_FULL_SIGN_IN_LINK=1 to print the full sign-in link, if the short one shows an error or a script reads values from it 
 Self-hosted runner: Added --start-dir / SELF_HOSTED_RUNNER_START_DIR to have Claude start its work in a folder of a repository, while settings and hooks load as without it 
 Added a notice in cloud and self-hosted runner sessions when a plugin marketplace can't be fetched because its repository isn't one of the session's 
 Self-hosted runner: Added a notice when Anthropic-managed git refuses a plugin's own repository, naming the plugin and what to do 
 Added commandPrinted to claude plugin install --json results, true when the plugin's install command wrote to stderr, and commandFailed when it exited with an error, was killed or timed out 
 Added claude_code_self_hosted_runner_order_to_registered_seconds to the self-hosted runner's /metrics : seconds from work order issued to registration accepted, on orchestrator-spawned runners 
 Added claude_code_self_hosted_runner_order_to_first_session_seconds to the self-hosted runner's /metrics : seconds from work order to first session handed over, on runners started for a session 
 Fixed Claude Code freezing for up to several minutes right after compacting a very long conversation 
 Fixed WebFetch freezing the session for minutes on some pages, and returning an empty result for some others 
 Fixed ExitWorktree and the worktree exit dialog deleting a worktree that another running Claude Code session was working in 
 Fixed changes to user settings being lost when several Claude Code processes saved them at the same time 
 Fixed --continue and --resume opening an empty session or failing when the last saved message had a missing or invalid timestamp 
 Fixed the first prompt after a sleep of two minutes or more waiting three minutes on a connection that had died, on Linux and WSL 
 Fixed turns failing with "JSON schema is invalid", and session files growing by many megabytes, when many MCP tools have an input schema that the API refuses 
 Linux: Fixed Bash commands waiting seconds and showing no file diff for the rest of a session in slow repositories with large ignored folders such as node_modules 
 Windows: Fixed Bash commands running slower for the rest of a session after Git Bash took 10 to 60 seconds to start, on machines with no custom start-up files 
 Fixed /rewind sometimes restoring an older version of a file when two queued prompts, or stacked skills, ran together right after a turn that changed it 
 Fixed text and images added when approving a permission prompt being dropped when the approved command or tool then failed 
 Fixed MCP resources from claude.ai connectors and plugin servers not being attached when @-mentioned in the terminal's prompt box 
 Fixed an MCP server that subagents declare being shut down when one of them finished, while other subagents or the session were still using it 
 Fixed Claude in Chrome staying "not connected" after a brief connection problem, even though Chrome was open and signed in 
 Fixed terminal sessions on Amazon Bedrock (Mantle) started with no model selected ignoring a pinned Opus model, and still calling an unavailable default model after announcing a fallback 
 Fixed the rest of what you were typing being lost when a plan arrived in fullscreen mode 
 Fixed claude.ai connectors with different names being dropped when they share a server URL ( #101856 ) 
 Fixed plugins going missing from the installed list when several claude plugin commands ran at the same time 
 Fixed task dependencies and metadata being lost when several task updates ran at the same time 
 Fixed incomplete backups of ~/.claude.json being kept, and displacing good ones, when the disk was full 
 Fixed a long pause in Code Mode after code that read hundreds of files in projects with path-scoped rules or Read deny rules 
 Fixed the built-in chart tool failing when Claude called it in Code Mode 
 Fixed Code Mode ignoring an MCP tool's request to end the turn from a script in auto and bypass permissions modes 
 Fixed Code Mode in auto mode dropping earlier thinking and rewriting the prompt cache when a mod added a note after a script loaded a skill 
 Fixed Code Mode not restoring a file that a script had read after Esc and /compact 
 Fixed /context undercounting system tools in Code Mode before Claude's first reply 
 Fixed a stopped background subagent sometimes not staying stopped 
 Fixed Claude still waiting for a background agent that was stopped just as it finished, in sessions run by an app or the SDK 
 Fixed background sessions sometimes waking in their previous permission mode after approving a plan 
 Remote Control: Fixed the note about background agents ended by a Stop from a phone or the web showing in the terminal as if you had typed it 
 Remote Control: Fixed the mobile apps hiding the Diff and pull request buttons, or showing a stopped session as working, after turning it on mid-conversation 
 Fixed environment variables written by a SessionStart hook being lost with claude -p --continue 
 Fixed claude -p exiting 0 with no message when its output went to a file on a full disk: it now prints an error and exits 1, though a full NFS export may go unnoticed 
 Fixed the system prompt keeping the earlier model's instructions when the model was changed after /context but before the first message 
 Fixed Claude sometimes replying to its commit attribution reminder and ending the turn early after the model changed mid-turn; it can still happen where managed settings set the PR attribution line 
 Fixed Esc not ending an LSP tool call that was waiting for a slow or stuck language server 
 Fixed LSP tool calls and diagnostics failing when several calls or edits arrived while a language server was still starting 
 Fixed /mcp listing plugin servers as built-in: they now stand under "Plugin MCPs", --mcp-config and built-in servers under "Other MCPs", and a server's page names its plugin 
 Fixed an "MCP server blocked by enterprise policy: easel" warning showing at every start when an MCP allowlist or denylist excludes the built-in chart tool, which stays blocked 
 Fixed /stats counting new activity in UTC days instead of your local time zone 
 Fixed /ultrareview failing or reviewing the wrong code after the shell moved into another repository: it now stops and names both folders 
 Fixed Grep reporting no matches when the pattern held a line break without multiline mode; it now reports the rejected pattern 
 Fixed Jupyter notebooks saved with a byte order mark being reported as invalid JSON by the Read and NotebookEdit tools 
 Fixed link reference definitions being dropped from CLAUDE.md and memory files that contain an HTML comment 
 Fixed running Monitors keeping the earlier conversation in memory until they end 
 Fixed some Claude Desktop sessions on third-party providers, other than scheduled tasks, ending a turn with "Prompt is too long" when a PDF larger than the context window followed a long conversation 
 Fixed the choice between two user or project agent files declaring the same name depending on the order the file search listed them 
 Fixed claude daemon logs never exiting inside a git repository when there is no log file 
 Fixed markdown hiding a character or two after bold or italic text when a backslash came before an emoji later in the paragraph 
 Fixed Edit refusing some valid hook commands in Claude settings files 
 Fixed Read with a page range showing both halves of a scanned two-page spread on each of its pages 
 Fixed line breaks and class stereotypes missing from Mermaid diagrams in HTML artifacts 
 Fixed the Project instructions picker in /config showing only one of its four choices in a 24-row fullscreen window 
 Fixed a subagent's own subagents and forks running on the plan-mode model in plan mode under opusplan or haiku 
 Fixed WebFetch page summaries ignoring the /effort level when a gateway refuses the small fast model 
 Fixed claude -p on Google Cloud's Agent Platform ignoring --settings '{"fastMode":true}' when the model comes from ANTHROPIC_MODEL or a settings file; such runs now bill at the fast mode price 
 Fixed startup under forceLoginOrgUUID being refused after one temporary server error or dropped connection 
 Fixed claude mcp remove giving no way forward for a claude.ai connector: it now says to turn it off in /mcp or remove it on claude.ai 
 Fixed the /mcp "Connect on claude.ai" check saying "not connected" when claude.ai has a connector at the server's URL without its query 
 Fixed /install-github-app and /design-login showing a generic failure for an account on hold instead of the on-hold notice and appeal link 
 Fixed a running MCP task being reported as stopped when you move a session to the background; the background session can now follow the task, but not if its server uses stdio or sets headers 
 Fixed self-hosted runners ignoring a session until they exited, after its failure report was lost or the session was given back to the same runner 
 Fixed self-hosted sessions losing the prompt cache and earlier thinking when the list of repositories a restart couldn't prepare changed 
 Self-hosted runner: Fixed tool calls behind a permission prompt vanishing with no result when a new runner took over the prompt, in sessions with telemetry off 
 Fixed resumed self-hosted runner sessions starting without their pushed work in large repositories when --push-outcome-on-release is set 
 Fixed self-hosted runner sessions being shown as working when Claude Code hangs at every start and --startup-timeout-min is from 2 to about 6 
 Fixed pkill -f in self-hosted runner sessions on Linux ending its own shell with exit code 144, or the runner (needs a pkill with --ignore-ancestors ) 
 Fixed scheduled tasks on self-hosted runners having no tool to notify their owner when telemetry is off or a third-party provider is used 
 Self-hosted runner: Fixed one slow spawn-runner hook keeping the orchestrator from claiming sessions for its free slots; it now polls every 4 to 6 seconds while a slot is free 
 Self-hosted runner: Fixed a 403, such as an IP allowlist's, logged as a bad secret or token: most such lines now lead with the server's reason, so update log alerts that match the old words 
 Fixed self-hosted runners' warn mode for repository settings stopping at the first finding of most kinds: it now goes on, up to 50 for a session, and says if it stops early 
 Self-hosted runner: Fixed runners that start on a full disk taking sessions and failing them; they now wait for room and exit 1 after a minute with no session, unless started from a work order 
 Self-hosted runner: Fixed a failed start suggesting a retry when the runner's machine had no git credentials; the error now says whom to ask and what to do if the repository is wrong 
 Fixed the self-hosted runner's last_poll_age_seconds reading 0 while the runner had never polled successfully 
 Fixed the notice about a skipped scheduled task that names no organization: it now says to start Claude Code with --resume , because /resume inside a running session doesn't run the task 
 Fixed claude plugin validate wrongly warning that a mod's AbovePrompt or AbovePromptList hook never runs in VS Code 
 Fixed /design-sync deleting a file it had just uploaded when Claude Design stored that file under a changed name 
 Reverted 2.1.329's removal of the automatic retry when max_tokens exceeds a model's or gateway's limit 
 Improved the claude.ai sign-in link shown by /login, claude auth login and claude setup-token : it is

[... truncated for safety ...]

</details>