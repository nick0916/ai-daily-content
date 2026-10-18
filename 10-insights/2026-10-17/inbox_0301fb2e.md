---
id: inbox_0301fb2e
date: 2026-10-17
source_ref: "[[00-inbox/2026-10-17/0256-gitnexus-releases-rc-2251adeeb2fb50cc8bbf52060f066dfe88997-3609]]"
title: "rc/2251adeeb2fb50cc8bbf52060f066dfe88997f6e: fix(eval): grade real C include provenance (#3611)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F2251adeeb2fb50cc8bbf52060f066dfe88997f6e
source: gitnexus-releases
published_at: 2026-10-17T14:03:42+00:00
fetched_at: 2026-10-18T03:18:24.534911+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 的 rc 標籤 rc/2251adeeb2fb50cc8bbf52060f066dfe88997f6e，對應 PR #3611「fix(eval): grade real C include provenance」。原文只列出 commit 訊息，沒有額外說明。內容都圍繞 eval 中的 C 語言 oracle：以 C include provenance（真實 include 來源）行為取代無效的合成 C 任務、移除 type-invalid 的 C reference 與無效的合成 oracle，並新增獨立的 typed C reference repairs，用來驗證獨立修復並拒絕壞掉的 control。另有文件記錄 C oracle evidence contract、移除 C oracle 規劃文件，以及讓 C oracle mutants 的測試能容忍格式差異、釐清 node 與 file 的綁定。對維護 GitNexus 評測的人來說，這顯示 eval 的正確性是靠「獨立 reference 能通過、壞 control 必須失敗」來把關；細節與數字原文未提供。"
key_points:
  - "PR #3611：以真實 C include provenance 行為取代無效的合成 C 任務"
  - "新增獨立 typed C reference repairs，並讓 eval 驗證獨立修復、拒絕壞掉的 control"
  - "記錄 C oracle evidence contract，並讓 oracle mutants 測試容忍格式差異"
tags: [gitnexus, eval, c-language, oracle, include-provenance]
topics: [engineering.evals, agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/2251adeeb2fb50cc8bbf52060f066dfe88997f6e: fix(eval): grade real C include provenance (#3611)

GitNexus 的 rc 標籤 rc/2251adeeb2fb50cc8bbf52060f066dfe88997f6e，對應 PR #3611「fix(eval): grade real C include provenance」。原文只列出 commit 訊息，沒有額外說明。內容都圍繞 eval 中的 C 語言 oracle：以 C include provenance（真實 include 來源）行為取代無效的合成 C 任務、移除 type-invalid 的 C reference 與無效的合成 oracle，並新增獨立的 typed C reference repairs，用來驗證獨立修復並拒絕壞掉的 control。另有文件記錄 C oracle evidence contract、移除 C oracle 規劃文件，以及讓 C oracle mutants 的測試能容忍格式差異、釐清 node 與 file 的綁定。對維護 GitNexus 評測的人來說，這顯示 eval 的正確性是靠「獨立 reference 能通過、壞 control 必須失敗」來把關；細節與數字原文未提供。

### 重點
- PR #3611：以真實 C include provenance 行為取代無效的合成 C 任務
- 新增獨立 typed C reference repairs，並讓 eval 驗證獨立修復、拒絕壞掉的 control
- 記錄 C oracle evidence contract，並讓 oracle mutants 測試容忍格式差異

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F2251adeeb2fb50cc8bbf52060f066dfe88997f6e)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(eval): verify independent C repairs and reject broken controls 
 
 
 fix(eval): replace invalid C task with provenance behavior 
 
 
 fix(eval): grade real C include provenance 
 
 
 test(eval): add independent typed C reference repairs 
 
 
 docs(eval): record C oracle evidence contract 
 
 
 fix(eval): remove invalid synthetic C oracle 
 
 
 fix(eval): remove type-invalid C reference 
 
 
 docs: remove C oracle planning document 
 
 
 test(eval): tolerate formatting in C oracle mutants 
 
 
 test(eval): clarify C oracle node and file bindings

</details>