---
id: inbox_6e409b67
date: 2026-10-23
source_ref: "[[00-inbox/2026-10-23/0347-ruflo-releases-v3-60-1-cleanup-keep-config-and-console-0ef7]]"
title: "v3.60.1 — cleanup --keep-config and console Windows fixes"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.60.1
source: ruflo-releases
published_at: 2026-10-23T19:04:25+00:00
fetched_at: 2026-10-24T03:56:32.980735+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo 3.60.1 修補清理指令誤刪設定檔，並改善 Windows 相容性。 **Why** 旗標在解析器中存為 keepConfig，動作端卻讀取 keep-config，導致 --keep-config 失效、設定檔被刪。 **What** 修正 cleanup --force --keep-config 誤刪 claude-flow.config.json 與 .claude/settings.json 的 hooks／claudeFlow 區塊；ruflo-console 0.45.1 改用新的 host-fs 寫入模式，使 ADR init、儲存與匯出在 Windows 可用；autopilot 接受 Windows 路徑，Autopilot 在 Windows 上仍維持關閉。"
key_points:
  - "cleanup --force --keep-config 因旗標名稱不一致（keepConfig 與 keep-config）而誤刪設定檔（#4435）"
  - "原寫入層呼叫 dd、install、sh，這些指令在 Windows 不存在；新增 host-fs 寫入模式取代（#4433、#4434、#4429）"
  - "autopilot envelope 接受 C:\ 與 UNC 路徑並忽略大小寫比較；Autopilot 在 Windows 仍受閘門限制（#4436）"
tags: [ruflo, windows-support, bugfix, cli, config-safety]
topics: [agents.frameworks]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.60.1 — cleanup --keep-config and console Windows fixes

ruflo 3.60.1 修補清理指令誤刪設定檔，並改善 Windows 相容性。 **Why** 旗標在解析器中存為 keepConfig，動作端卻讀取 keep-config，導致 --keep-config 失效、設定檔被刪。 **What** 修正 cleanup --force --keep-config 誤刪 claude-flow.config.json 與 .claude/settings.json 的 hooks／claudeFlow 區塊；ruflo-console 0.45.1 改用新的 host-fs 寫入模式，使 ADR init、儲存與匯出在 Windows 可用；autopilot 接受 Windows 路徑，Autopilot 在 Windows 上仍維持關閉。

### 重點
- cleanup --force --keep-config 因旗標名稱不一致（keepConfig 與 keep-config）而誤刪設定檔（#4435）
- 原寫入層呼叫 dd、install、sh，這些指令在 Windows 不存在；新增 host-fs 寫入模式取代（#4433、#4434、#4429）
- autopilot envelope 接受 C:\ 與 UNC 路徑並忽略大小寫比較；Autopilot 在 Windows 仍受閘門限制（#4436）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.60.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Patch release: @claude-flow/cli , claude-flow , ruflo 3.60.1. No leaf package changed, so no standalone publishes. 
 Fixed 
 
 ruflo cleanup --force --keep-config deleted the config files it is meant to keep ( claude-flow.config.json , the hooks / claudeFlow blocks of .claude/settings.json ): the parser stores the flag as keepConfig and the action read keep-config ( #4435 ). 
 ruflo-console 0.45.1: ADR init, saves and exports work on Windows. The write layer shelled out to dd , install and sh , which do not exist there; a new host-fs write flavor uses the host filesystem ( #4433 , #4434 , carries #4429 ). 
 ruflo-console : the autopilot envelope accepts Windows paths ( C:\work\app , UNC) and compares them ignoring case and separator style; a POSIX-rooted path containing a backslash is still refused ( #4436 ). Autopilot start stays gated off on Windows.

</details>