---
id: inbox_e1d51b03
date: 2026-09-30
source_ref: "[[00-inbox/2026-09-30/0256-ecc-releases-v2-2-2-3353]]"
title: "v2.2.2"
url: https://github.com/affaan-m/ECC/releases/tag/v2.2.2
source: ecc-releases
published_at: 2026-09-30T19:05:42+00:00
fetched_at: 2026-10-18T03:19:47.137408+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "ECC（affaan-m/ECC）於 2026-09-30 發布 v2.2.2，新增 pi/core：一個精選、僅含 skills 與 prompts 的 Pi 原生 profile（套件 ecc-pi-core），專為鏡像 GitHub Releases 的下游打包者設計，無 build 步驟、extensions、hooks、執行期下載或網路/SaaS 依賴。內容為 123 個精選 skills（語言與框架模式、測試/TDD、code review、非攻擊性資安審查、規劃、重構、文件、git/PR 工作流）與 24 個純 prompt 指令，由 manifests/pi-core.json 的 include/exclude 清單經 scripts/build-pi-core.js 確定性產生並提交；CURATION.md 列出每個被排除項目的原因，council skill 在 pi/core 內改名 ecc-council 以避免名稱衝突。build 會在遇到非允許清單的 URL host、pipe-to-shell 或 fetch-and-run 形式、secrets/token、使用者家目錄絕對路徑、symlink、無效 SKILL.md frontmatter、重複 skill 名稱時失敗。CI 每個 PR 都重建並驗證 pi/core 為最新，並在 PI_OFFLINE=1 下安裝 Pi coding agent CLI 驗證完全離線載入且每個指令都成功註冊。另有修正：OpenCode 編譯產物明確納入 npm 套件、memory MCP ping 接受保留的 _meta 參數、hooks.json 維持在 Claude Code schema 內、no-verify guard 處理邊角案例、Windows linter 路徑與 ESLint 9 支援，並升級 lru 至 0.18.2（RUSTSEC-2026-0253）、js-yaml 至 4.3.2（GHSA-2883-xcg3-v3hh）。"
key_points:
  - "pi/core：123 skills + 24 prompt commands，由 manifests/pi-core.json 經 scripts/build-pi-core.js 確定性產生，release tarball 逐字包含"
  - "build 安全閘門：擋非允許清單 URL host、pipe-to-shell、secrets、絕對家目錄路徑、symlink、重複 skill 名；CI 以 PI_OFFLINE=1 驗證離線載入且所有指令註冊"
  - "依賴安全修補：lru 0.18.2（RUSTSEC-2026-0253）、js-yaml 4.3.2（GHSA-2883-xcg3-v3hh）"
tags: [ecc, pi-coding-agent, skills, supply-chain, offline-install]
topics: [agents.coding_agents, security]
importance: 2
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.2.2

ECC（affaan-m/ECC）於 2026-09-30 發布 v2.2.2，新增 pi/core：一個精選、僅含 skills 與 prompts 的 Pi 原生 profile（套件 ecc-pi-core），專為鏡像 GitHub Releases 的下游打包者設計，無 build 步驟、extensions、hooks、執行期下載或網路/SaaS 依賴。內容為 123 個精選 skills（語言與框架模式、測試/TDD、code review、非攻擊性資安審查、規劃、重構、文件、git/PR 工作流）與 24 個純 prompt 指令，由 manifests/pi-core.json 的 include/exclude 清單經 scripts/build-pi-core.js 確定性產生並提交；CURATION.md 列出每個被排除項目的原因，council skill 在 pi/core 內改名 ecc-council 以避免名稱衝突。build 會在遇到非允許清單的 URL host、pipe-to-shell 或 fetch-and-run 形式、secrets/token、使用者家目錄絕對路徑、symlink、無效 SKILL.md frontmatter、重複 skill 名稱時失敗。CI 每個 PR 都重建並驗證 pi/core 為最新，並在 PI_OFFLINE=1 下安裝 Pi coding agent CLI 驗證完全離線載入且每個指令都成功註冊。另有修正：OpenCode 編譯產物明確納入 npm 套件、memory MCP ping 接受保留的 _meta 參數、hooks.json 維持在 Claude Code schema 內、no-verify guard 處理邊角案例、Windows linter 路徑與 ESLint 9 支援，並升級 lru 至 0.18.2（RUSTSEC-2026-0253）、js-yaml 至 4.3.2（GHSA-2883-xcg3-v3hh）。

### 重點
- pi/core：123 skills + 24 prompt commands，由 manifests/pi-core.json 經 scripts/build-pi-core.js 確定性產生，release tarball 逐字包含
- build 安全閘門：擋非允許清單 URL host、pipe-to-shell、secrets、絕對家目錄路徑、symlink、重複 skill 名；CI 以 PI_OFFLINE=1 驗證離線載入且所有指令註冊
- 依賴安全修補：lru 0.18.2（RUSTSEC-2026-0253）、js-yaml 4.3.2（GHSA-2883-xcg3-v3hh）

**原文：** [ecc-releases](https://github.com/affaan-m/ECC/releases/tag/v2.2.2)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

ECC 2.2.2 
 ECC 2.2.2 adds pi/core , a curated Pi-native skills+prompts-only profile built for 
downstream packagers that mirror GitHub Releases, plus a set of packaging, memory, 
hooks, and Windows compatibility fixes. 
 Pi core profile 
 pi/core/ is a self-contained package ( ecc-pi-core ) that downstream mirrors of the release 
tarball can copy directly: no build step, no extensions, no hooks, no runtime 
downloads, and no network or SaaS dependencies. 
 
 123 curated skills (language and framework patterns, testing/TDD, code review, 
non-offensive security review, planning, refactoring, docs, and git/PR workflows) 
and 24 prompt commands that are pure prompt workflows. 
 Generated deterministically from the explicit include/exclude lists in 
 manifests/pi-core.json by scripts/build-pi-core.js and committed, so the 
release tarball contains it verbatim. pi/core/CURATION.md lists every excluded 
skill and command with its reason; the council skill ships as ecc-council 
inside pi/core to avoid catalog name clashes. 
 The build fails on safety violations: non-allowlisted URL hosts, pipe-to-shell 
or fetch-and-run download forms, secrets or tokens, absolute per-user home 
paths, symlinks, invalid SKILL.md frontmatter, and duplicate skill names. 
 CI rebuilds pi/core on every PR and verifies it is up to date, then installs 
the Pi coding agent CLI and proves the profile loads fully offline 
( PI_OFFLINE=1 ), asserting that every curated command actually registers. 
 The release workflow additionally verifies that VERSION matches the tag and 
that pi/core is current before publishing. 
 
 Downstream consumption: poll /releases , download 
 archive/refs/tags/vX.Y.Z.tar.gz , pin its sha256, copy pi/core/ , and load it 
offline with pi --offline --skill pi/core/skills --prompt-template pi/core/commands . 
 Packaging 
 
 The compiled OpenCode payload is explicitly included in the npm package, and 
packing is verified from a clean state with lifecycle scripts enabled. 
 
 Memory and MCP 
 
 Incomplete memory reads are distinguished from missing records, and directory 
traversal failures are classified. 
 The reserved _meta parameter is accepted on memory MCP ping requests. 
 
 Hooks and Windows compatibility 
 
 hooks.json stays within Claude Code's schema; stable hook metadata moved into 
a validated sidecar. 
 The no-verify guard handles stuck optional values and long-option prefixes. 
 Windows linter paths and ESLint 9 are supported, and settings updates tolerate 
missing Windows device IDs while retaining full-precision inode checks. 
 
 Workflow guidance, catalog, and dependency security 
 
 Epic sync filters issues by label; dependency bumps no longer document 
auto-merge; naming and Boolean guidance is language-neutral; the prp-pr 
command alias is distinguished; Rails skill discovery, invoice tax calculation 
order, and framework documentation were corrected; Serply and Squish catalog 
entries were removed. 
 lru updated to 0.18.2 (RUSTSEC-2026-0253) and js-yaml to 4.3.2 
( GHSA-2883-xcg3-v3hh ).

</details>