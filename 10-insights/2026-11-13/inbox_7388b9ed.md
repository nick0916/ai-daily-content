---
id: inbox_7388b9ed
date: 2026-11-13
source_ref: "[[00-inbox/2026-11-13/0145-simon-willison-datasette-cluster-map-0-19-7ca6]]"
title: "datasette-cluster-map 0.19"
url: https://simonwillison.net/2026/Nov/13/datasette-cluster-map/
source: simon-willison
published_at: 2026-11-13T23:02:45+00:00
fetched_at: 2026-11-14T01:51:03.097150+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 地圖外掛 datasette-cluster-map 發布 0.19，相容新版 Datasette 並修正地圖圖磚請求。 **Why** OpenStreetMap 圖磚請求需要帶 referrer header。 **How** 改為依賴新的 datasette-leaflet 套件來確保送出 referrer header。 **What** datasette-cluster-map 0.19 支援 Datasette 1.0a42；作者以 PG&E 所屬發電廠地圖示範，同時展示 Datasette 最近重新設計的 facets。"
key_points:
  - "datasette-cluster-map 0.19 支援 Datasette 1.0a42"
  - "新依賴 datasette-leaflet，確保 OpenStreetMap 圖磚請求帶 referrer header"
  - "示範為加州 PG&E 發電廠地圖，並展示重新設計的 facets"
tags: [datasette, simon-willison, geospatial, openstreetmap, plugin]
topics: [product_and_org.product]
importance: 1
novelty: 1
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-cluster-map 0.19

Datasette 地圖外掛 datasette-cluster-map 發布 0.19，相容新版 Datasette 並修正地圖圖磚請求。

**Why** OpenStreetMap 圖磚請求需要帶 referrer header。

**How** 改為依賴新的 datasette-leaflet 套件來確保送出 referrer header。

**What** datasette-cluster-map 0.19 支援 Datasette 1.0a42；作者以 PG&E 所屬發電廠地圖示範，同時展示 Datasette 最近重新設計的 facets。

### 重點
- datasette-cluster-map 0.19 支援 Datasette 1.0a42
- 新依賴 datasette-leaflet，確保 OpenStreetMap 圖磚請求帶 referrer header
- 示範為加州 PG&E 發電廠地圖，並展示重新設計的 facets

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/13/datasette-cluster-map/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-cluster-map 0.19 
 One of the oldest Datasette plugins, and still one of my favorites. It now works with Datasette 1.0a42, and depends on the new datasette-leaflet to ensure OpenStreetMap tiles are requested with a referrer header. 
 Here's a map of power plants owned by California's PG&E , also demonstrating Datasette's recently redesigned facets : 
 
 
 
 Tags: datasette , geospatial , openstreetmap

</details>