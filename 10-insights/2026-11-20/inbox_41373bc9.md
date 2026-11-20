---
id: inbox_41373bc9
date: 2026-11-20
source_ref: "[[00-inbox/2026-11-20/0106-github-trending-agent-tools-mjmirza-app-store-compliance-1-846-377-8fe1]]"
title: "mjmirza/app-store-compliance ⭐ 1,846(今日 +377)"
url: https://github.com/mjmirza/app-store-compliance
source: github-trending-agent-tools
published_at: 2026-11-20T01:06:35.868592+00:00
fetched_at: 2026-11-20T01:15:02.251886+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "把 App Store 與 Google Play 常見退審規則整理成提交前守門檢查，讓 AI coding agent 上傳前自動執行。 **Why** 原文指出一次退審常耗時一週：送審、等待、收到一行退件理由、猜測修正後重送。 **How** 以 git clone 與 bash 安裝；安裝後，agent 在執行 App Store Connect 或 Google Play 上傳指令前會先掃描，遇到關鍵退審風險即阻擋該指令。 **What** 收錄 117 項退審模式與修正方式、95 個追蹤期限（如 EU AI Act、DSA、COPPA）、隱私清單與 Data safety 檢查；支援 Claude Code、Gemini CLI、OpenCode、Copilot；GitHub 今日 +377 星，總數 1,846。"
key_points:
  - "一行指令安裝（需 git、bash；Claude Code 以外的工具另需 python3），可用 install.sh --tool 指定工具，並以 uninstall 移除"
  - "守門檢查無法自行驗證的項目（如 App Store Connect 內的審核備註）會列為需人工確認，而非預設通過"
  - "無法確認某工具 hook 格式時，會給手動步驟而非猜測；作者另提供 verify-citations.py 檢查來源是否可達"
tags: [app-store, google-play, mobile-release, pre-submit-check, agent-hooks]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## mjmirza/app-store-compliance ⭐ 1,846(今日 +377)

把 App Store 與 Google Play 常見退審規則整理成提交前守門檢查，讓 AI coding agent 上傳前自動執行。

**Why** 原文指出一次退審常耗時一週：送審、等待、收到一行退件理由、猜測修正後重送。

**How** 以 git clone 與 bash 安裝；安裝後，agent 在執行 App Store Connect 或 Google Play 上傳指令前會先掃描，遇到關鍵退審風險即阻擋該指令。

**What** 收錄 117 項退審模式與修正方式、95 個追蹤期限（如 EU AI Act、DSA、COPPA）、隱私清單與 Data safety 檢查；支援 Claude Code、Gemini CLI、OpenCode、Copilot；GitHub 今日 +377 星，總數 1,846。

### 重點
- 一行指令安裝（需 git、bash；Claude Code 以外的工具另需 python3），可用 install.sh --tool 指定工具，並以 uninstall 移除
- 守門檢查無法自行驗證的項目（如 App Store Connect 內的審核備註）會列為需人工確認，而非預設通過
- 無法確認某工具 hook 格式時，會給手動步驟而非猜測；作者另提供 verify-citations.py 檢查來源是否可達

**原文：** [github-trending-agent-tools](https://github.com/mjmirza/app-store-compliance)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Avoid common App Store and Google Play rejections. Open playbook and pre-submission guard with 117 documented rejection patterns and fixes, privacy manifest and Data safety checks, 95 tracked deadlines (EU AI Act, DSA, COPPA, age laws), and a skill for AI coding agents.

App Store Compliance Playbook

Start here

What you get

Install it into your AI coding tool

It works. Approved on the first try

Found this useful? Three taps that help a lot

Why this is urgent right now (2026)

How you actually use this

If something goes wrong

Words used here

What is inside

The first principle

Contributing

Logo attribution

Credits

License

Or let your agent do it

Check, update, or remove it

If you are not a developer

If you use Claude Code or another AI coding tool

No AI tool. Run it by hand

Apple Developer Requirements Monitor

Other continuous monitors

Citation integrity

Stop getting your iOS and Android apps rejected. The enterprise reference and automated guard that turns App Store and Google Play rejection into a designed out failure mode.

Read it as a website at mjmirza.github.io/app-store-compliance .

 

 

If this saves you even one rejection, leave a star, fork it, and follow along. That is the whole ask.

Star this repo | Fork it | Follow on GitHub | Follow on X | next8n.com

Pick one row. The time shown is for that first step.

The two commands. Needs git and bash. The first downloads this playbook. The second scans your app. Nothing is installed and nothing in your app is changed.

Replace only /path/to/your/app , with the folder that holds your Xcode project or your Android app. Keep the quotes, they keep a folder name with a space in it whole. To get the path without typing it, drag the folder from Finder or your file manager into the terminal window. A small project scans in about a second, a large one can take up to a minute, and the guard prints the time it took. Findings print first, critical ones on top, each with the file and line that triggered it when there is one. The last lines tell you where you stand.

A rejection costs a week. You submit, you wait days in review, you get a one line rejection, you guess at the fix, you resubmit, you wait again. This playbook turns that loop into a check you run before you ever submit.

If it saves you one rejection, it has paid for the ten minutes it takes to read.

This puts the check in front of every submit. Your agent runs the guard before any submit command, such as an upload to App Store Connect or Google Play, and stops the command when a critical rejection risk stands. For a one-time scan, skip this section and use Start here.

One command per tool, about a minute. Needs git and bash. Every tool other than Claude Code also needs python3.

--tool all installs into every supported tool it finds in your home folder. To pick one, pass its name instead.

Every run ends with Install verified. only after it has fed a submit command to the hook in that tool's own payload format and seen it blocked. For OpenCode that check runs the plugin under node, so without node the run says Installed, but not fully verified. instead. If you see a FAIL line instead, fix that line and run the same command with doctor added.

What it writes, so you can check it.

Each of these was checked against its own documentation. Where a tool can block a command but its format could not be confirmed, you get the manual step rather than a guess.

It never touches your GitHub account or your credentials. Undo it with the same command and uninstall , for example install.sh --tool gemini uninstall . The shared skill stays until the last tool using it is removed.

Paste this into your AI coding tool. Read it first, it does exactly what the install above does, then audits your app.

Each command ends with one line that tells you whether it worked. Add --tool to act on a tool other than Claude Code.

To update later, run git -C ~/repositories/app-store-compliance pull and then the same install command again. On Windows, run it from Git Bash. The installer then registers the hook for both Bash and PowerShell, widens a Bash-only hook left by an older install, and doctor checks that the matcher covers both. Copilot gets a powershell handler next to its bash one.

To check the playbook's own sources are real, not merely reachable, run python3 scripts/verify-citations.py --files docs/ data/ from the checkout. It takes a few minutes and needs network access.

Want only a one time check, no install? Paste this instead.

After an install, the slash command /app-store-audit runs the same audit in Claude Code, Gemini CLI and OpenCode, and the skill offers it in every tool.

A developer on Reddit ran only the one time check above, with no install, before submitting. The audit surfaced weaknesses they had not caught. They fixed them, and the app went through on the first attempt.

It noticed some weaknesses in my submission that I was able to fix. [...] My app was approved on first try!

The same thread is worth reading for the part that is not praise. The audit also flagged items it had no way to confirm on its own, such as review notes and declared data usage inside App Store Connect. Those reads look like false positives. They are deliberate. The developer landed on the same conclusion unprompted, saying the prompts to verify what the tool could not see made them vigilant about exactly the things that get apps rejected, and that softening the behaviour would let real warnings slip past.

An item that cannot be verified is surfaced rather than assumed clean. A missed warning costs a rejection. A surfaced one costs a minute.

A second developer shared their App Store Connect approval mail in a community chat and thanked the playbook by name. The sender's name is removed. The message is in German.

I just got the mail from the Apple Store that my app is "finally" approved! [...] Thanks for your compliance repo.

Sharing it with one teammate who is about to submit an app is the highest compliment.

AI coding tools changed the math. Anyone can build a mobile app in an afternoon now, and they are. App releases in the first quarter of 2026 were up about 60 percent year over year across both stores, and around 80 percent on iOS alo

</details>