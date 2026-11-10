---
id: inbox_f7344f46
date: 2026-11-09
source_ref: "[[00-inbox/2026-11-09/2342-hackernews-show-hn-every-satellite-that-passed-over-d105]]"
title: "Show HN: Every satellite that passed over any place this week, and its photos"
url: https://www.watched.earth
source: hackernews
published_at: 2026-11-09T17:51:31+00:00
fetched_at: 2026-11-10T00:04:44.629424+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "輸入任何地點，就能看到過去 7 天飛越該處的衛星與它們實際拍到的照片。 **How** 在瀏覽器用 SGP4 搭配 CelesTrak 星曆目錄計算過境，約半秒完成，再抓取這些過境的 Sentinel-2、Landsat 與 NASA 影像；約 1.7 萬個在軌物體以 GPU 每幀解 Kepler 方程式繪出。 **What** Show HN 專案 watched.earth，作者說對照暴力法驗證（極區、反子午線、窄幅帶）0 次漏掉過境；只有確實有影像才標示「watched」，且不儲存使用者位置。作者另指出 Sentinel-2 時間戳常與衛星實際通過時間差 5–10 分鐘。"
key_points:
  - "SGP4 + CelesTrak 在瀏覽器端運算，約 0.5 秒找出 7 天內所有過境衛星"
  - "與暴力搜尋比對（極區、反子午線、小幅寬）0 次漏掉；Sentinel-2 時間戳常偏差 5–10 分鐘"
  - "約 17k 個在軌物體在 GPU 上逐幀解 Kepler 方程式；不儲存使用者位置"
tags: [satellite-tracking, show-hn, sgp4, sentinel-2, webgpu]
topics: [engineering.architecture]
importance: 1
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Show HN: Every satellite that passed over any place this week, and its photos

輸入任何地點，就能看到過去 7 天飛越該處的衛星與它們實際拍到的照片。

**How** 在瀏覽器用 SGP4 搭配 CelesTrak 星曆目錄計算過境，約半秒完成，再抓取這些過境的 Sentinel-2、Landsat 與 NASA 影像；約 1.7 萬個在軌物體以 GPU 每幀解 Kepler 方程式繪出。

**What** Show HN 專案 watched.earth，作者說對照暴力法驗證（極區、反子午線、窄幅帶）0 次漏掉過境；只有確實有影像才標示「watched」，且不儲存使用者位置。作者另指出 Sentinel-2 時間戳常與衛星實際通過時間差 5–10 分鐘。

### 重點
- SGP4 + CelesTrak 在瀏覽器端運算，約 0.5 秒找出 7 天內所有過境衛星
- 與暴力搜尋比對（極區、反子午線、小幅寬）0 次漏掉；Sentinel-2 時間戳常偏差 5–10 分鐘
- 約 17k 個在軌物體在 GPU 上逐幀解 Kepler 方程式；不儲存使用者位置

**原文：** [hackernews](https://www.watched.earth)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

hey HN, i built this because i wanted to know what had actually photographed my street. type in any place and it finds every satellite that passed over it in the last 7 days (SGP4 on the CelesTrak catalog, runs in your browser in about half a second), then pulls the real Sentinel-2 / Landsat / NASA images from those passes. some fun bits:
- the pass search can't skip a pass. checked it against a brute force on poles, the antimeridian and tiny swaths: 0 missed
- all ~17k objects in orbit are drawn on the GPU, solving Kepler's equation every frame
- Sentinel-2 timestamps are often 5-10 min off from when the sat actually crosses your spot, which was a fun one to figure out it only says "watched" if a real image exists, and it doesn't store your location. code: https://github.com/dev-Armaan/satellites would love feedback, especially on what data sources to add

</details>