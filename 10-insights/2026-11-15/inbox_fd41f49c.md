---
id: inbox_fd41f49c
date: 2026-11-15
source_ref: "[[00-inbox/2026-11-15/2316-simon-willison-datasette-maplibre-0-1a0-bb83]]"
title: "datasette-maplibre 0.1a0"
url: https://simonwillison.net/2026/Nov/15/datasette-maplibre/
source: simon-willison
published_at: 2026-11-15T23:58:36+00:00
fetched_at: 2026-11-17T23:22:14.567155+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "一個把互動式地圖顯示加進 Datasette 的新外掛，幾乎由一段 prompt 讓 AI 寫出來。 **Why** Datasette 的地理空間外掛已久未更新，且既有的 cluster-map 與 leaflet-geojson 外掛功能各自分散。 **How** 以 MapLibre GL 搭配 OpenFreeMap（Zsolt Ero 營運的免費向量地圖伺服器），並給 Claude Fable 5.2 一段 prompt：參考兩個既有外掛與一個 demo 頁面，合併功能並「be creative and think outside the box」。 **What** datasette-maplibre 0.1a0 發布。AI 自行想出的功能包括：先顯示 GeoJSON 形狀的 SVG 預覽，捲動進可視範圍才載入 WebGL 預覽；另附可在 Datasette Lite（Pyodide + WebAssembly）中執行的完整 demo，同一張地圖可同時顯示 GeoJSON 形狀與經緯度點位。"
key_points:
  - "datasette-maplibre 0.1a0：結合 MapLibre GL 與 OpenFreeMap，合併 datasette-cluster-map 與 datasette-leaflet-geojson 的功能"
  - "作者用單一 prompt 交給 Claude Fable 5.2 完成大部分開發，prompt 中加上「be creative and think outside the box」引出額外功能"
  - "AI 想出的亮點：先顯示 SVG 預覽，捲動進視窗才載入 WebGL 預覽；demo 可在 Datasette Lite 中透過 Pyodide/WebAssembly 直接於瀏覽器執行"
tags: [datasette, maplibre, geospatial, claude-fable, vibe-coding]
topics: [agents.coding_agents]
importance: 2
novelty: 3
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-maplibre 0.1a0

一個把互動式地圖顯示加進 Datasette 的新外掛，幾乎由一段 prompt 讓 AI 寫出來。

**Why** Datasette 的地理空間外掛已久未更新，且既有的 cluster-map 與 leaflet-geojson 外掛功能各自分散。

**How** 以 MapLibre GL 搭配 OpenFreeMap（Zsolt Ero 營運的免費向量地圖伺服器），並給 Claude Fable 5.2 一段 prompt：參考兩個既有外掛與一個 demo 頁面，合併功能並「be creative and think outside the box」。

**What** datasette-maplibre 0.1a0 發布。AI 自行想出的功能包括：先顯示 GeoJSON 形狀的 SVG 預覽，捲動進可視範圍才載入 WebGL 預覽；另附可在 Datasette Lite（Pyodide + WebAssembly）中執行的完整 demo，同一張地圖可同時顯示 GeoJSON 形狀與經緯度點位。

### 重點
- datasette-maplibre 0.1a0：結合 MapLibre GL 與 OpenFreeMap，合併 datasette-cluster-map 與 datasette-leaflet-geojson 的功能
- 作者用單一 prompt 交給 Claude Fable 5.2 完成大部分開發，prompt 中加上「be creative and think outside the box」引出額外功能
- AI 想出的亮點：先顯示 SVG 預覽，捲動進視窗才載入 WebGL 預覽；demo 可在 Datasette Lite 中透過 Pyodide/WebAssembly 直接於瀏覽器執行

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/15/datasette-maplibre/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-maplibre 0.1a0 
 The first new Datasette geospatial plugin in quite a while! This one combines the excellent MapLibre GL library with OpenFreeMap , the free vector map server operated by Zsolt Ero (you should sponsor Zsolt on GitHub .) 
 I built most of this with a single prompt to Claude Fable 5.2: 
 
 Look at datasette-cluster-map and datasette-leaflet-geojson plugins, then look at ~/dev/tools/openfreemap-demo.html - then build a brand new Datasette plugin that uses maplibreGL and openfreemap and combines the features of those other two plugins - but be creative and think outside the box for other useful features the plugin might have 
 
 "Be creative and think outside the box" resulted in a few neat ideas - my favorite is that it displays SVG previews of GeoJSON shapes, then loads a WebGL preview only when they scroll into view. 
 I also had Claude build a comprehensive demo which works in the latest Datasette Lite, so you can visit this link to load the plugin and a demo database in your browser via Pyodide and WebAssembly. 
 I like this demo page showing both GeoJSON shapes and lat/lon points on the same map: 
 
 
 
 Tags: visualization , generative-ai , datasette-lite , claude-mythos-fable , ai , llms , geospatial , openstreetmap , datasette

</details>