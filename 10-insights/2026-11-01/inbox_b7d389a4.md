---
id: inbox_b7d389a4
date: 2026-11-01
source_ref: "[[00-inbox/2026-11-01/0001-simon-willison-if-in-doubt-delete-the-uv-lock-file-3dec]]"
title: "If in doubt, delete the uv.lock file"
url: https://simonwillison.net/2026/Nov/1/delete-uv-lock-first/
source: simon-willison
published_at: 2026-11-01T23:24:22+00:00
fetched_at: 2026-11-02T00:05:42.684871+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "遇到 Python 依賴怪錯誤時，先刪掉 uv.lock 再重跑。 **Why** 升級到 Python 3.15 後，舊的 uv.lock 可能鎖住尚無 3.15 wheel 的依賴版本，造成建置失敗。 **How** uv run pytest 會留下被 .gitignore 忽略的 uv.lock；刪除後重跑，uv 會重新解析出相容的版本。 **What** Simon Willison 的 TIL：例子是 watchfiles==1.1.1 建置失敗，錯誤為 PyO3 最高支援 Python 3.14 但直譯器是 3.15。他的專案多為 library，本來就不提交 uv.lock。"
key_points:
  - "症狀：Failed to build watchfiles==1.1.1，maturin.build_wheel 失敗，因 Python 3.15 超過 PyO3 最高支援的 3.14"
  - "解法：刪除 uv.lock 後重跑 uv run pytest，通常即可解決"
  - "library 專案不應提交 uv.lock，避免替下游使用者鎖版本"
tags: [uv, python, python-3-15, dependency-management, til]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## If in doubt, delete the uv.lock file

遇到 Python 依賴怪錯誤時，先刪掉 uv.lock 再重跑。

**Why** 升級到 Python 3.15 後，舊的 uv.lock 可能鎖住尚無 3.15 wheel 的依賴版本，造成建置失敗。

**How** uv run pytest 會留下被 .gitignore 忽略的 uv.lock；刪除後重跑，uv 會重新解析出相容的版本。

**What** Simon Willison 的 TIL：例子是 watchfiles==1.1.1 建置失敗，錯誤為 PyO3 最高支援 Python 3.14 但直譯器是 3.15。他的專案多為 library，本來就不提交 uv.lock。

### 重點
- 症狀：Failed to build watchfiles==1.1.1，maturin.build_wheel 失敗，因 Python 3.15 超過 PyO3 最高支援的 3.14
- 解法：刪除 uv.lock 後重跑 uv run pytest，通常即可解決
- library 專案不應提交 uv.lock，避免替下游使用者鎖版本

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/1/delete-uv-lock-first/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

I've been getting the occasional confusing Python dependency error since switching over to Python 3.15 and the rule I'm having to remember is: 
 If in doubt, delete the uv.lock file 
 Most of my projects are libraries which don't include a uv.lock file, since it's rude for a library dependency to lock versions for anything else that uses it. 
 Running uv run pytest etc tends to leave uv.lock files lying around, which are listed in .gitignore and so do not get committed to my repositories. 
 But... sometimes that uv.lock pins a version of a dependency that doesn't yet have a Python 3.15 wheel. An example from earlier today: 
 error: Failed to build `watchfiles==1.1.1`
 cause: Call to `maturin.build_wheel` failed

error: the configured Python interpreter version (3.15) is newer
than PyO3's maximum supported version (3.14)
 
 Deleting that file and running uv run pytest again usually fixes the problem. 

 Tags: uv , til , python

</details>