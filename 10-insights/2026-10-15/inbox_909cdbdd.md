---
id: inbox_909cdbdd
date: 2026-10-15
source_ref: "[[00-inbox/2026-10-15/0256-hermes-agent-releases-hermes-agent-v0-22-2-98ad]]"
title: "Hermes Agent v0.22.2"
url: https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.2
source: hermes-agent-releases
published_at: 2026-10-15T08:21:32+00:00
fetched_at: 2026-10-18T03:19:09.990527+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hermes Agent（NousResearch）於 2026-10-15 發布 v0.22.2。原文說明 v0.22.1 是從錯誤的 commit 建置，帶出了尚未發布的 gateway 工作，且 Microsoft Store 版 app 可能卡在「Connecting」；0.22.2 就是 0.22.1 原本該發布的版本。已知問題：在 0.22.1 gateway 下執行過的 session 無法在 0.22.2 刪除。兩大重點：(1) gateway 重開機後可正常啟動——Linux 重啟後可能把早期 PID 分配給無關程序，gateway 誤判為已有 gateway 在執行，導致 systemd、launchd、Docker 下的受監管 gateway 拒絕啟動；現在會記錄啟動時的 boot，無法判斷時改問只有存活 gateway 才持有的 host lock（#138594，修正 #133744）。(2) 筆電上長時間本地模型 turn 更穩定：本地請求一律 streaming 並在狀態列顯示 prompt 讀取進度、stall timer 略過機器休眠時間、本地伺服器恢復後可重試而非讓 circuit breaker 讓後續訊息全失敗、壓縮不再於伺服器仍在讀長對話時逾時；Windows 統一記憶體機器的模型啟動與 prompt cache 依可用記憶體調整（#138560）。其餘包含 nemotron super 3.5 預設參數、NVIDIA NIM 模型清單、韓文與巴西葡萄牙文語言包等 plugin catalog 新增，以及 Mistral tool id 配對、profile 端點繼承、httpx2/httpcore2 由 2.7.0 升至 2.12.0 等修正。對自行託管 Hermes gateway 或在筆電跑本地模型的使用者，建議升級並避開 0.22.1。"
key_points:
  - "v0.22.1 由錯誤 commit 建置、Microsoft Store 版可能卡在「Connecting」；v0.22.2 為其修正版，但 0.22.1 gateway 下的 session 在 0.22.2 無法刪除"
  - "gateway 重開機後 PID 重用誤判問題：改記錄 boot epoch，無法判斷時以 host lock 決定（#138594，修正 #133744）"
  - "本地模型長 turn：一律 streaming 顯示 prompt 讀取進度、stall timer 略過休眠時間、breaker 恢復後可重試（#138560）"
tags: [hermes-agent, patch-release, gateway, local-models, windows-store]
topics: [agents.frameworks, engineering.inference]
importance: 3
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Hermes Agent v0.22.2

Hermes Agent（NousResearch）於 2026-10-15 發布 v0.22.2。原文說明 v0.22.1 是從錯誤的 commit 建置，帶出了尚未發布的 gateway 工作，且 Microsoft Store 版 app 可能卡在「Connecting」；0.22.2 就是 0.22.1 原本該發布的版本。已知問題：在 0.22.1 gateway 下執行過的 session 無法在 0.22.2 刪除。兩大重點：(1) gateway 重開機後可正常啟動——Linux 重啟後可能把早期 PID 分配給無關程序，gateway 誤判為已有 gateway 在執行，導致 systemd、launchd、Docker 下的受監管 gateway 拒絕啟動；現在會記錄啟動時的 boot，無法判斷時改問只有存活 gateway 才持有的 host lock（#138594，修正 #133744）。(2) 筆電上長時間本地模型 turn 更穩定：本地請求一律 streaming 並在狀態列顯示 prompt 讀取進度、stall timer 略過機器休眠時間、本地伺服器恢復後可重試而非讓 circuit breaker 讓後續訊息全失敗、壓縮不再於伺服器仍在讀長對話時逾時；Windows 統一記憶體機器的模型啟動與 prompt cache 依可用記憶體調整（#138560）。其餘包含 nemotron super 3.5 預設參數、NVIDIA NIM 模型清單、韓文與巴西葡萄牙文語言包等 plugin catalog 新增，以及 Mistral tool id 配對、profile 端點繼承、httpx2/httpcore2 由 2.7.0 升至 2.12.0 等修正。對自行託管 Hermes gateway 或在筆電跑本地模型的使用者，建議升級並避開 0.22.1。

### 重點
- v0.22.1 由錯誤 commit 建置、Microsoft Store 版可能卡在「Connecting」；v0.22.2 為其修正版，但 0.22.1 gateway 下的 session 在 0.22.2 無法刪除
- gateway 重開機後 PID 重用誤判問題：改記錄 boot epoch，無法判斷時以 host lock 決定（#138594，修正 #133744）
- 本地模型長 turn：一律 streaming 顯示 prompt 讀取進度、stall timer 略過休眠時間、breaker 恢復後可重試（#138560）

**原文：** [hermes-agent-releases](https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Hermes Agent v0.22.2 
 Release Date: October 15, 2026 
 v0.22.1 was built from the wrong commit. It shipped unreleased gateway work, and the Microsoft Store app could stick on "Connecting." 0.22.2 is the release 0.22.1 was meant to be. 
 
 Known issue: Sessions that ran under the 0.22.1 gateway can't be deleted in 0.22.2. 
 

 Highlights 
 
 The gateway starts after a reboot again. After a restart, Linux can hand an early PID to an unrelated process, and the gateway could mistake it for a running gateway, so a supervised gateway (systemd, launchd, Docker) refused to start. Hermes now records the boot it started in, and when it can't tell, it asks the host lock, which only a live gateway holds. ( #138594 , fixes #133744 ) 
 Long local-model turns survive on laptops. Local requests always stream with prompt-reading progress (shown in the status line), stall timers skip time the machine was asleep, a recovered local server gets another try instead of a breaker that failed every later message, and compression no longer times out while the server is still reading a long conversation. On Windows unified-memory machines, model launch and the prompt cache are sized to free memory. ( #138560 ) 
 
 Below is everything in the 0.22 release line since v0.22.0: the fixes 0.22.1 was meant to ship, plus the two above. Work that is only on main ships with v0.23.0. 
 ✨ Features 
 
 Release: split the Microsoft Store bundle into its own windows-store lane ( f9d8a740 ) — @ethernet8023 
 Agent: add nemotron super 3.5 default parameters ( c59d2994 ) — @elisam0 
 Cli: add nemotron to NVIDIA NIM default model list ( cc55270e ) — @elisam0 
 Cli: add curated model list at the top in the model picker list ( e6835fd3 ) — @elisam0 
 Release: choose what a stable release builds and tests with lanes ( 36a8ee18 ) — @ethernet8023 
 Plugin-catalog: add hermes-lang-ko — Korean Desktop language pack ( e5f49b6a ) — @dandacompany 
 Plugin-catalog: add hermes-lang-pt-br (Brazilian Portuguese language pack) ( 0169e80c ) — @StudioCodeAI 
 Contributors: add 2867297362mjb-sketch email mapping ( 9ab40641 ) — @2867297362mjb-sketch 
 Plugin-catalog: add teamorouter (TeamoRouter model providers) ( ef223406 ) — @2867297362mjb-sketch 
 Plugin-catalog: add author-feed ( 5f6d6836 ) — @TakeshiTGAL 
 Plugin-catalog: bump aux-ledger to 1.4.0 ( 6048066e ) — @olric3015 
 Plugin-catalog: add the wait-ledger catalog card ( 77cb58e5 ) — @olric3015 
 Plugin-catalog: add wait-ledger ( 97e65322 ) — @olric3015 
 Community plugin: lightningai + lightningai-rate-limit ( 07515466 ) — @dinosauria123 
 Catalog: add Hermes AAC 0.1.0 at reviewed exact source pin ( 7c9adda8 ) — @TREE-Ind 
 Plugin-catalog: add openinvest ( b6e86101 ) — @longsizhuo 
 Catalog: add hermes-agent-mixer (v0.2.0 @ 04c4e13) ( 2e7e3859 ) — @Sahil-SS9 
 Plugins: move Kumiho Memory to memory catalog shelf ( 46f95e08 ) — @kaveone 
 Release: dispatch Stable Release from the default branch ( 667e6639 ) — @ethernet8023 
 
 🔧 Improvements 
 
 Agent: keep the Mistral tool-id rule beside its only consumer ( c5fc0958 ) — @kshitijk4poor 
 Profiles: build the seed routing view once; expand enabled too ( 311155fa ) — @kshitijk4poor 
 Profiles: simplify the model seed and trim its tests ( d9dfb124 ) — @kshitijk4poor 
 Update nemotron super 3.5 name ( 3224993a ) — @elisam0 
 Hermes_cli: update nemotron 3.5 name ( 108ae4e7 ) — @elisam0 
 Catalog: re-pin showly to the build without the upstream self-update check ( 6462f64a ) — @slchris 
 Catalog: update Model Router to v0.4.3 native preferences ( 6a097ee9 ) — @metamindedu 
 
 🐛 Bug Fixes 
 
 Gateway: a recorded boot epoch that cannot be compared is unprovable ( 79b3b724 ) — @ethernet8023 
 Local: keep long local-model turns alive on laptops ( 518ce272 ) — @emozilla 
 Gateway: a read-only host-record check never creates the lock file ( 91e63f84 ) — @kshitijk4poor 
 Gateway: let the host lock decide a legacy record that looks older than this boot ( 4d984677 ) — @ethernet8023 
 Gateway: anchor the legacy host-record check on boot time, not a live create_time ( 5b416e42 ) — @ethernet8023 
 Gateway: drop argv identity from host rendezvous liveness ( c7fa3cbf ) — @sin5ddd 
 Gateway: reject a recycled PID that only matches start ticks ( 7934442e ) — @sin5ddd 
 Tui: keep a ${VAR} bare-custom endpoint as a ref in the new profile ( dd2db134 ) — @kshitijk4poor 
 Tui: a new profile inherits a bare custom launch model with its endpoint ( 463d4019 ) — @kshitijk4poor 
 Release: a Store-only Windows build gets no signing vars; Store-plus-macOS smokes record only macOS ( a8cc19eb ) — @ethernet8023 
 Agent: keep composite tool ids paired on Mistral routes ( 0c1bfb7d ) — @kshitijk4poor 
 Agent: rewrite split tool ids before Mistral sees them ( b33ed359 ) — @xxxigm 
 Release: macOS smoke runs when no receipt was staged ( f546ea2f ) — @ethernet8023 
 Install-e2e: preserve bundled Windows process arrays ( 6db1934d ) — @Oceanswave 
 Profiles: match env-referenced endpoint names when seeding a profile ( 7b755ed5 ) — @kshitijk4poor 
 Profiles: drop every same-identity destination entry when merging ( 9a9a6e43 ) — @kshitijk4poor 
 Profiles: match endpoint identity the way runtime does when merging ( ef57cbd9 ) — @kshitijk4poor 
 Profiles: keep URL-less destination entries when merging the endpoint seed ( 2aa469f7 ) — @kshitijk4poor 
 Profiles: inherited endpoint is not shadowed by the profile's own entries ( ac0b63af ) — @kshitijk4poor 
 Profiles: select the seeded endpoint from an env-referenced provider ( c85302a2 ) — @kshitijk4poor 
 Profiles: keep bare custom provider tuning in the model seed ( 424aa90f ) — @kshitijk4poor 
 Profiles: reuse named provider lookup without credential reads ( c8a777ff ) — @helix4u 
 Profiles: align model seed with provider resolution ( 5fee8d77 ) — @helix4u 
 Profiles: inherit canonical and legacy custom endpoints ( 2d3e75aa ) — @helix4u 
 Drop the VPN/proxy advice from the CDN-block message ( 300228d2 ) 
 Scope the no-cf-cache-status block signal to our R2 host; keep it on 429s ( ec5fa1e4 ) 
 Name a CDN firewall block instead of a bare HTTP 403 ( #128295 ) ( #128295 ) 
 Release: termux-only claims finish and partial releases keep the shared downloads page ( 6743ab71 ) — @ethernet8023 
 Ci: packaged-update acceptance retries a download whose connection resets ( db4a6a9e ) — @ethernet8023 
 Catalog: re-pin Agent Mixer after maintainer review ( 4297a692 ) — @Sahil-SS9 
 Pin Activity v0.2.1 public credential routes ( 3dac1f07 ) — @hassan-kamel 
 Plugin-catalog: update jp-egov-law to f1dd47e ( c029046d ) — @TakeshiTGAL 
 Plugin-catalog: update switchbot-control to d0e6f77 ( c4bf61b1 ) — @TakeshiTGAL 
 Install-e2e: the Windows packaged-app feed serves byte ranges ( 1f6c02c0 ) 
 Pm: re-merge the uv cache seed on volumes marked by a seedless image ( 1226894b ) — @ethernet8023 
 Release: publish replaces the stable head instead of create-only ( df8c3ca5 ) 
 Release: keep a stable run on main from using the controller commit or cancelling pushes ( 0dbd96ab ) — @ethernet8023 
 Pm: stage a version for version-less buildable plugin members too ( 3d8dfc1d ) — @ethernet8023 
 Pm: don't stamp project.version on members declaring it dynamic ( 2a10164c ) — @Ieqzya 
 Pm: give generated virtual workspace members a project.version ( 357986e5 ) — @Ieqzya 
 Pm: retry sync without bytecode compile when that step fails ( 10619939 ) — @smfworks 
 Deps: bump httpx2/httpcore2 2.7.0 -&gt; 2.12.0 for the audit advisories ( bc8545bd ) — @guthixboss1 
 Doctor: stop mislabeling the root npm audit row as agent-browser ( 7b1dc974 ) — @chelsealong 
 Doctor: say recreating the same Docker image does not fix npm findings ( dee35e1d ) — @ethernet8023 
 Doctor: describe full workspace npm audit scope ( b9dda06b ) — @dwaxe 
 Doctor: clarify Docker npm audit remediation ( e21caa27 ) — @KoNit-K 
 Deps: bump the WhatsApp bridge lock past its npm-audit findings ( 231cb757 ) — @ethernet8023 
 Deps: land source-map-js 1.2.2 and sync the workspace pins to the overrides ( f57d12eb ) — @ethernet8023 
 Deps: bump pinned npm packages to clear npm audit findings ( 732f0f17 ) — @sajidhaleem 
 Windows: packaged-npx install failures degrade to plain npx; payload venv must be real ( 84e2250b ) — @ethernet8023 
 Docker: ship the build's uv cache at the PM seed path ( f4e70b9d ) — @ethernet8023 
 Release: publish the final vX.Y.Z Docker tag again ( c1100232 ) — @ethernet8023 
 Pm: npm on PATH is the pinned npm, not the copy bundled inside node ( 8d3b5ab5 ) — @ethernet8023 
 Windows: an MSIX with no Node to copy runs npx MCP servers on its packaged node ( 8ef7654b ) — @ethernet8023 
 Windows: MSIX terminal and MCP children get node, npm and python copied outside the package ( c7abf4fb ) — @ethernet8023 
 Terminal: the user's own tools come before Hermes's in the terminal ( 162b457c ) — @ethernet8023 
 Search: local file search runs Hermes's pinned ripgrep, not the first rg on PATH ( 9b4710b8 ) — @ethernet8023 
 Terminal: strip a sealed payload's venv from child PYTHONPATH ( 671996b1 ) — @ethernet8023 
 
 📚 Documentation 
 
 Agent: use the released model name Nemotron 3.5 Super VL ( 79651b71 ) — @j-nolan 
 Agent: name the guidance blocks and drop the unsupported claims ( ba498735 ) — @j-nolan 
 Agent: note that the guidance blocks were tested on Nemotron without effect ( 2b57b0db ) — @j-nolan 
 Providers: rephrased content ( 4f8df7e1 ) — @nv-pberard 
 Env: add NVIDIA NIM to .env example ( 3dd96101 ) — @elisam0 
 Providers: use a non-cloud example key for local NIM ( da463310 ) — @rroverin 
 Providers: update NVIDIA NIM example to Nemotron 3.5 Super VL ( c5bab4af ) — @rroverin 
 Local Models is on by default on macOS, Windows and Linux ( 1e8bf3ee ) 
 
 🧪 Tests 
 
 Agent: pin Mistral's 9-character tool id on the wire ( 9a90a825 ) — @xxxigm 
 Profiles: pin same-identity eviction of URL-less and disabled entries ( 0f447876 ) — @kshitijk4poor 
 Profiles: pin that the model seed copies only the selected endpoint ( 29db211b ) — @kshitijk4poor 
 Agent: add reasoning timeout default test ( 73a07104 ) — @elisam0 
 Relay: the OpenAI-stream e2e no longer self-deadlocks when the stream is buffered ( 6e84ce66 ) 
 Pm: one streamed-sync test covers the bytecode-compile retry ( 7f21aad1 ) — @ethernet8023 
 Deps: fail the build if an httpx2 pin or lock entry drops below 2.12.0 ( 3ca10d88 ) — @jarvistwil 
 Doctor: point the root-row label test at the staged-npm seam ( 40441695 ) — @ethernet8023 
 Pm: allow-list the packaged-npx node lookups in the resolution ratchet ( c4f9a169 ) — @ethernet8023 
 
 🏗️ Infrastructure 
 
 Release: admit stable releases from release/* branches, not just main ( 9686d55c ) — @ethernet8023 
 Map contributor email for sin5ddd ( #133750 salvage) ( #133750 ) — @kshitijk4poor 
 Map Oceanswave noreply email to GitHub login ( f343bdff ) — @ethernet8023 
 Map contributor email for ashmoonori-afk ( 6a1ee825 ) 
 Plugins: pin birkin-mnemosyne to core 0.7.1 ( e216cd74 ) — @ashmoonori-afk 
 Catalog: review disclosure for huddo ( 85d27a51 ) 
 Map contributor email for StudioCodeAI ( c708b34f ) 
 Plugin-catalog: update Telegram Client to 1.3.1 ( 27aaade9 ) — @guberm 
 Plugin-catalog: bump Gmail to v1.0.20 ( c6ac0565 ) — @guberm 
 Plugin-catalog: bump Gmail to v1.0.19 ( 74324f11 ) — @guberm 
 Plugin-catalog: update Gmail to v1.0.18 ( 8050d9ea ) — @guberm 
 Kiwi: bump pin to kiwi@0.12.5, plugin v1.2.2 ( a08f5894 ) — @harrylabsj 
 Map contributor email for dinosauria123 ( 06c81873 ) 
 Lightningai-rate-limit to v1.1.0 (wall-clock aligned window) ( e28d64e8 ) — @dinosauria123 
 Map contributor email for TREE-Ind ( 71f78b3f ) 
 Catalog: review disclosure for hermes-aac ( 0567d017 ) 
 Catalog: review disclosure for openinvest ( c179b286 ) 
 Map contributor email for Sahil-SS9 ( d8b5bd8a ) 
 Catalog: review disclosure for hermes-agent-mixer ( a98cc310 ) 
 Catalog: review disclosure for hermes-activity ( e891815c ) 
 Update Activity catalog to v0.2.0 ( 908c525d ) — @hassan-kamel 
 Map contributor e

[... truncated for safety ...]

</details>