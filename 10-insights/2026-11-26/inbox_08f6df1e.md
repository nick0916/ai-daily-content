---
id: inbox_08f6df1e
date: 2026-11-26
source_ref: "[[00-inbox/2026-11-26/0052-claude-mem-releases-v17-0-1-ac8e]]"
title: "v17.0.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v17.0.1
source: claude-mem-releases
published_at: 2026-11-26T18:49:44+00:00
fetched_at: 2026-11-27T01:03:08.509373+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude-Mem 17.0.1 修正 cmem.ai 裝置碼顯示與 Windows 上的多項問題。 **Why** 裝置碼只印在終端機，設定頁面的使用者看不到；Windows 上特定文字會造成讀取卡住，OMP 與 Screenpipe 也無法送達 worker。 **What** 設定頁現在顯示裝置碼並可重新產生；Windows 上 OMP 與 Screenpipe 改用與 worker 相同的預設 port 計算方式（port 37777 不再是預設）；Claude 的 condense 請求改依 CLAUDE_MEM_OBSERVER_MAX_OUTPUT_TOKENS 決定長度（預設 8,192 字元）。"
key_points:
  - "設定頁顯示 cmem.ai 裝置碼與複製按鈕，過期後 Reopen 會產生新碼（#6500）"
  - "Windows 上 OMP hook 與 Screenpipe 的預設 port 改由資料夾雜湊計算，修正 OMP 工作階段無法記錄（#6481）；OMP 使用者更新後需執行一次 npx claude-mem install --ide omp"
  - "Claude provider 的 condense 請求改為 8,192 字元（預設值），不再要求完整 12,800 字元（#6508）"
tags: [claude-mem, windows, device-code, port-config, bug-fix]
topics: [agents.coding_agents, product_and_org.product]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v17.0.1

Claude-Mem 17.0.1 修正 cmem.ai 裝置碼顯示與 Windows 上的多項問題。

**Why** 裝置碼只印在終端機，設定頁面的使用者看不到；Windows 上特定文字會造成讀取卡住，OMP 與 Screenpipe 也無法送達 worker。

**What** 設定頁現在顯示裝置碼並可重新產生；Windows 上 OMP 與 Screenpipe 改用與 worker 相同的預設 port 計算方式（port 37777 不再是預設）；Claude 的 condense 請求改依 CLAUDE_MEM_OBSERVER_MAX_OUTPUT_TOKENS 決定長度（預設 8,192 字元）。

### 重點
- 設定頁顯示 cmem.ai 裝置碼與複製按鈕，過期後 Reopen 會產生新碼（#6500）
- Windows 上 OMP hook 與 Screenpipe 的預設 port 改由資料夾雜湊計算，修正 OMP 工作階段無法記錄（#6481）；OMP 使用者更新後需執行一次 npx claude-mem install --ide omp
- Claude provider 的 condense 請求改為 8,192 字元（預設值），不再要求完整 12,800 字元（#6508）

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v17.0.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Critical fixes 
 
 The setup page shows your cmem.ai device code, and reopening after it expires gets a fresh one ( #6500 , @thedotmack ). After you pick Cloud Sync and start the free trial, cmem.ai asks for a device code. That code was only printed in the terminal, which most people never look at because setup runs in the browser. The checkout step now shows Your device code with a copy button, next to "Waiting for this device to connect...". If the code expired, Reopen sent you back to a dead link with the same expired code. It now starts a new pairing with a new code. The code is never put in a URL, log line or analytics event, and the page reads it from a route only this machine can reach. 
 Windows: My Work reads no longer hang when a recent Bash command holds regex-shaped text ( #6471 , thanks @zhangkom , closes #6470 reported by @ingermaa ). Shell text such as s.replace(/\r\n/g, ' ') was taken for an absolute path. Resolving /\r\n/g, could produce a UNC network path, and project discovery stalled while Windows tried a network lookup. Text that starts with a slash and a backslash is now ignored on Windows. Drive paths and POSIX paths are read as before. 
 Windows: OMP capture and Screenpipe saves reach the worker again ( #6481 , thanks @AyhamJo7 , refs #6477 reported by @Jumpstile ). On Windows the OMP hook and the Screenpipe skill posted to port 37777 by default. The worker picks its default port from a hash of the data folder, so on a default Windows install nothing listened on 37777 and OMP sessions were not recorded, with no error shown. Both now work out the default port the same way the worker does. A port saved in settings.json is still used first, and macOS and Linux are unchanged. OMP users on Windows: run npx claude-mem install --ide omp once after updating. The OMP hook is a copied file, so an update alone does not replace it. 
 
 Fixes 
 
 Claude provider: condensing an oversized field now follows CLAUDE_MEM_OBSERVER_MAX_OUTPUT_TOKENS ( #6508 , thanks @0xABCD01 , closes #6503 reported by @JonT6 ). The setting sized the condense request on the HTTP providers, but the Claude call never passed it. The request asked for the full 12,800 characters, and the extra output was billed and then clipped. At the default setting the Claude condense request now asks for 8,192 characters, the same as the HTTP providers. The Agent SDK has no per-request output cap, so on this path the setting sizes the request and is not a hard limit. 
 My Work keeps a cut-off answer for diagnosis, and Focus can skip a request it cannot place ( #6441 , thanks @0xABCD01 , part of #6432 reported by @hello-sebastian ). When an API answer ran out of tokens, its text was discarded and the error read as "raise the limit". The partial answer is now saved under failed-answers/ , the step fails with that file's path first, and the error says a run-out almost always means the model's output degenerated, which a higher limit does not fix. The focus step now accepts an ignored list with a reason. An ignored request goes to Other, where you can move it. 
 The SessionStart timeline lists one turn's observations oldest first ( #6495 , thanks @HEOJUNFO ). Turns ran oldest to newest, but the observations inside one turn ran newest to oldest, so the last row was not the newest entry. The newest entry is now last, as the timeline's own instructions say. 
 claude-mem server jobs retry no longer reports requeued while a worker still holds the job ( #6494 , thanks @HEOJUNFO ). Cancelling a processing job and retrying it before the provider call returned left the job queued for good, and it never ran. The command now sets the job back to failed with retry_republish_failed , prints the reason and exits 1. Run it again after the provider call has returned and the job is requeued and runs. 
 Server: CLAUDE_MEM_MONTHLY_REQUEST_CAP works without CLAUDE_MEM_USAGE_METERING=1 ( #6489 , thanks @kevincommits ). With only the cap set, no requests were counted, so the cap was never reached and no request was answered with 402. Setting the cap now also counts requests. CLAUDE_MEM_MONTHLY_TOKEN_CAP still needs metering on. 
 Server: GET /v1/jobs answers 400 for a since that is not a date ( #6484 , thanks @kevincommits ). A value such as last-week or 2026-13-45 dropped the filter and returned jobs from every date. It now answers 400 INVALID_DATE . A day that is not on the calendar, such as 2026-02-30 , also gets a 400, and epoch milliseconds are now accepted. 
 OpenClaw: uninstalling gives the memory slot back to the plugin that had it ( #6445 , thanks @DeryFerd ). Installing took plugins.slots.memory from another memory plugin with no record of it, and uninstalling deleted the slot. Install now remembers the previous owner and uninstall restores it. When there was no previous owner, the slot is deleted as before. 
 Install: the marketplace manifest and package.json are written atomically ( #6475 , thanks @DeryFerd ). A crash, a killed process or a full disk in the middle of a write could leave a truncated file. These were the last two plain writes in the install flow. 
 My Work names the event type when it drops an unreadable stream frame ( #6476 , thanks @DeryFerd ). A frame that was not JSON was dropped without a trace, so a feed could stop updating with nothing to say why. The browser console now gets a warning that names the event type. 
 Messages on Mac: someone leaving a group now reaches the transcript ( #6509 , thanks @chuenchen309 ). The Mac source skipped the leave rows in chat.db. They now read "(Ben left the group)", the same as from the Photon source. Group photo and background changes are still skipped. 
 
 Contributors 
 Thank you to everyone whose work is in this release: @zhangkom , @AyhamJo7 , @0xABCD01 , @HEOJUNFO , @kevincommits , @DeryFerd and @chuenchen309 for the fixes, and @ingermaa , @Jumpstile , @JonT6 and @hello-sebastian for the reports. 
 Full changelog : v17.0.0...v17.0.1

</details>