---
id: inbox_c9e01f53
date: 2026-10-12
source_ref: "[[00-inbox/2026-10-12/0256-ruflo-releases-ruflo-console-0-43-0-orbital-look-and-th-ab27]]"
title: "ruflo-console 0.43.0: Orbital look and Theme Studio"
url: https://github.com/ruvnet/ruflo/releases/tag/ruflo-console-v0.43.0
source: ruflo-releases
published_at: 2026-10-12T12:55:22+00:00
fetched_at: 2026-10-18T03:20:23.509455+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo-console 0.43.0 加入可選的 Orbital 外觀與 Theme Studio，預設仍為 Classic BBS，不主動選擇則無任何改變。Orbital 外觀包含黑底遙測面板、方形邊框、旋轉地球、掃描線、開機後仍保留的 RUFLO 陰影標題、動畫化的真實開機檢查，以及透視 swarm 預覽。Theme Studio 可從 Main Menu → Tools、Settings 或 `/ruflo themes` 進入：可選 Classic BBS、Terminal plain、Orbital；提供六組內建色彩預設、最多十二組自訂主題（透過 host storage 儲存）、最低 3:1 對比度的色彩選擇器，以及動態層與速度調整（fps 0 會凍結畫面）。內附 generate-console-theme skill（allowed-tools: Read），回傳僅含資料的 palette/motion JSON 給 Claude 或 Codex，匯入需通過嚴格且上限 4096 字元的 schema。驗證方面：console 測試 0 失敗、3193 通過（+77），smoke 20/20，CI 114 項檢查通過，並在真實 Claude Code 2.1.289 內以 tmux 驗證；45 項對抗式 spec 未發現缺陷。未驗證項目包括 Windows/macOS 終端、desktop 與 VS Code 介面，以及真實由 AI 生成主題的來回流程。安裝方式為 marketplace plugin（非 npm）：`claude plugin marketplace update ruflo` 後 `claude plugin update ruflo-console@ruflo` 並重啟 Claude Code。"
key_points:
  - "Theme Studio：六組內建預設、最多 12 組自訂主題、色彩選擇器強制 3:1 最低對比度，fps 0 可凍結動畫"
  - "generate-console-theme skill 僅允許 Read，輸出 data-only JSON，匯入 schema 上限 4096 字元，惡意或畸形 JSON 被拒且主題不變"
  - "測試 3193 通過（+77）、CI 114 checks 綠燈；明列未驗證範圍（Windows/macOS、desktop/VS Code、AI 生成主題 round trip）"
tags: [ruflo-console, theme-studio, claude-code-plugin, terminal-ui, skill]
topics: [agents.coding_agents, product_and_org.product]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## ruflo-console 0.43.0: Orbital look and Theme Studio

ruflo-console 0.43.0 加入可選的 Orbital 外觀與 Theme Studio，預設仍為 Classic BBS，不主動選擇則無任何改變。Orbital 外觀包含黑底遙測面板、方形邊框、旋轉地球、掃描線、開機後仍保留的 RUFLO 陰影標題、動畫化的真實開機檢查，以及透視 swarm 預覽。Theme Studio 可從 Main Menu → Tools、Settings 或 `/ruflo themes` 進入：可選 Classic BBS、Terminal plain、Orbital；提供六組內建色彩預設、最多十二組自訂主題（透過 host storage 儲存）、最低 3:1 對比度的色彩選擇器，以及動態層與速度調整（fps 0 會凍結畫面）。內附 generate-console-theme skill（allowed-tools: Read），回傳僅含資料的 palette/motion JSON 給 Claude 或 Codex，匯入需通過嚴格且上限 4096 字元的 schema。驗證方面：console 測試 0 失敗、3193 通過（+77），smoke 20/20，CI 114 項檢查通過，並在真實 Claude Code 2.1.289 內以 tmux 驗證；45 項對抗式 spec 未發現缺陷。未驗證項目包括 Windows/macOS 終端、desktop 與 VS Code 介面，以及真實由 AI 生成主題的來回流程。安裝方式為 marketplace plugin（非 npm）：`claude plugin marketplace update ruflo` 後 `claude plugin update ruflo-console@ruflo` 並重啟 Claude Code。

### 重點
- Theme Studio：六組內建預設、最多 12 組自訂主題、色彩選擇器強制 3:1 最低對比度，fps 0 可凍結動畫
- generate-console-theme skill 僅允許 Read，輸出 data-only JSON，匯入 schema 上限 4096 字元，惡意或畸形 JSON 被拒且主題不變
- 測試 3193 通過（+77）、CI 114 checks 綠燈；明列未驗證範圍（Windows/macOS、desktop/VS Code、AI 生成主題 round trip）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/ruflo-console-v0.43.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

ruflo-console 0.43.0: optional Orbital look and Theme Studio 
 Classic BBS stays the default. Orbital is opt-in; nothing changes until you pick it. 
 Changelog 
 
 feat: an optional Orbital look: black telemetry panels, square borders, a rotating globe, a scan sweep and a shaded RUFLO header that stays visible after boot (Main Menu, Theme Studio, Swarm), animated real boot checks, a perspective swarm preview. 
 feat: Theme Studio (Main Menu → Tools, Settings, or /ruflo themes ): pick Classic BBS, Terminal plain or Orbital; six bundled color presets; up to twelve named custom themes saved through host storage; a color picker with a 3:1 minimum contrast; motion layers and speed; fps 0 freezes the frame. 
 feat: a bundled generate-console-theme skill ( allowed-tools: Read ) returns data-only palette/motion JSON for Claude or Codex; import goes through a strict, 4096-character-bounded schema. 
 fix: Theme Studio has a boot-log line and a help guide and is reached by name; the wide Orbital header says RUFLO, not RUVNET. 
 chore: the globe reads a one-degree land mask built once (about a third less time per frame); scripts/bench-theme.mjs ; no Python in the repo (the SVG demo exporter is Node). 
 
 Validation 
 
 Console tests: 0 failing (main and this release both skip 29 files that need claude-code/testing ); 3193 pass (+77). Console smoke 20/20; manifest, mcp-prefix, skill-frontmatter, hook audits and claude plugin validate pass; CI 114 checks green. 
 Checked in the real Claude Code 2.1.289 (isolated config, directory marketplace, tmux, frames viewed): /ruflo , Orbital and Classic, Tools → Theme Studio, /ruflo themes , colour edit, contrast guard, save and reload across a full restart, "Use configured look", malformed/hostile JSON rejected with the theme unchanged, animation running (12/12 distinct frames) and stopped at fps 0, resizes 300→150 columns, clean model-facing console_state (no escapes, no theme JSON). 
 45 adversarial specs on import, stores and model-facing text found no defect. Classic BBS per-tick cost is unchanged from before. 
 
 Not verified 
 Windows and macOS terminals, other emulators (tmux 256-colour only), the desktop and VS Code surfaces, a real AI-generated theme round trip (Generate with Claude/Codex was not run), and some stray │ cells right of the pane after a shrink-resize in tmux (looks like host diff-render residue). The side-by-side editor layout needs a pane of 100+ columns (the host's default share is narrower; RUFLO_CONSOLE_COLUMNS widens it). 
 Install 
 Marketplace plugin, not npm: claude plugin marketplace update ruflo then claude plugin update ruflo-console@ruflo , and restart Claude Code. 
 PR #4079 . Orbital and Theme Studio by @ruvnet (with Codex); review, fixes, validation and optimization by RuFlo.

</details>