---
id: inbox_7b9fdcb6
date: 2026-10-13
source_ref: "[[00-inbox/2026-10-13/0258-hackernews-wanted-to-download-an-iso-ended-up-writi-141c]]"
title: "Wanted to download an ISO, ended up writing a kernel exploit"
url: https://blog.dfb.sh/blog/eap770-root-for-two-zeros/
source: hackernews
published_at: 2026-10-13T12:30:08+00:00
fetched_at: 2026-10-18T03:24:01.922126+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "作者原本只想下載一個 ISO，最後寫成了一個 kernel exploit，文章標題指向 eap770 的 root 漏洞。作者在 HN 留言中說，他在核心樹內找到至少 13 個有相同 bug 類型的 driver。這類 bug 在 x86 上運作正常，但在 arm 等非 cache-coherent 架構上會靜默破壞資料，作者沒有硬體可測試。作者的推測是，這正是 DMA API 存在的原因，driver 不應該手動做 cache maintenance，但他自稱不是 kernel 開發者，也在求教是否漏掉什麼。輸入資料沒有說明 exploit 的具體細節，這部分需讀原文。實務上，維護或移植 driver 到 arm 平台的人應檢查是否有手動 cache 操作。"
key_points:
  - "作者在核心樹內找到至少 13 個有相同 bug 類型的 in-tree driver"
  - "此類 bug 在 x86 無症狀，但在 arm 等非 coherent 架構會靜默破壞資料"
  - "作者推測應透過 DMA API 處理，而非 driver 手動做 cache maintenance（自述非 kernel 開發者，未確認）"
tags: [kernel-exploit, linux-drivers, dma-api, non-coherent-arch, arm]
topics: [security]
importance: 3
novelty: 3
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Wanted to download an ISO, ended up writing a kernel exploit

作者原本只想下載一個 ISO，最後寫成了一個 kernel exploit，文章標題指向 eap770 的 root 漏洞。作者在 HN 留言中說，他在核心樹內找到至少 13 個有相同 bug 類型的 driver。這類 bug 在 x86 上運作正常，但在 arm 等非 cache-coherent 架構上會靜默破壞資料，作者沒有硬體可測試。作者的推測是，這正是 DMA API 存在的原因，driver 不應該手動做 cache maintenance，但他自稱不是 kernel 開發者，也在求教是否漏掉什麼。輸入資料沒有說明 exploit 的具體細節，這部分需讀原文。實務上，維護或移植 driver 到 arm 平台的人應檢查是否有手動 cache 操作。

### 重點
- 作者在核心樹內找到至少 13 個有相同 bug 類型的 in-tree driver
- 此類 bug 在 x86 無症狀，但在 arm 等非 coherent 架構會靜默破壞資料
- 作者推測應透過 DMA API 處理，而非 driver 手動做 cache maintenance（自述非 kernel 開發者，未確認）

**原文：** [hackernews](https://blog.dfb.sh/blog/eap770-root-for-two-zeros/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Author here. Does anyone know what to do with the rest of the drivers? I found at least 13 in-tree drivers with the same bug class. The nasty part is they work fine on x86 and silently corrupt data on arm and other non-coherent archs, and I don&#x27;t have the hardware to test them. I&#x27;d guess that&#x27;s what the DMA API is for and drivers shouldn&#x27;t be doing cache maintenance by hand, but I&#x27;m not a kernel dev, so maybe I&#x27;m missing something.

</details>