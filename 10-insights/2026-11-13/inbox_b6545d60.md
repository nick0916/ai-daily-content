---
id: inbox_b6545d60
date: 2026-11-13
source_ref: "[[00-inbox/2026-11-13/0145-simon-willison-datasette-leaflet-0-3-0576]]"
title: "datasette-leaflet 0.3"
url: https://simonwillison.net/2026/Nov/13/datasette-leaflet/
source: simon-willison
published_at: 2026-11-13T22:30:54+00:00
fetched_at: 2026-11-14T01:51:35.020017+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "讓地圖外掛在載入 OpenStreetMap 圖磚時帶上正確的來源標頭，符合對方使用規範。 **Why** OpenStreetMap 規定對其圖磚伺服器的請求應送出 referrer header，但 Datasette 表格頁使用 `Referrer-Policy: no-referrer`，導致依賴 OSM 圖磚的外掛違反政策。 **How** 在圖磚請求本身設定 referrer policy 為 `strict-origin-when-cross-origin`，只傳送主機而不帶完整頁面路徑。 **What** datasette-leaflet 0.3 發布；此外掛內含 Leaflet 供其他 Datasette 外掛依賴，此版修正了 OSM 圖磚請求的 referrer 問題。"
key_points:
  - "OpenStreetMap 政策要求對其圖磚伺服器的請求帶 referrer header"
  - "Datasette 表格頁的 Referrer-Policy: no-referrer 會讓 OSM 圖磚外掛違反該政策"
  - "0.3 在圖磚請求上設 strict-origin-when-cross-origin，只傳主機、不傳完整路徑"
tags: [datasette, datasette-leaflet, openstreetmap, referrer-policy, release]
topics: [product_and_org.product]
importance: 1
novelty: 1
insight_quality: 2
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette-leaflet 0.3

讓地圖外掛在載入 OpenStreetMap 圖磚時帶上正確的來源標頭，符合對方使用規範。

**Why** OpenStreetMap 規定對其圖磚伺服器的請求應送出 referrer header，但 Datasette 表格頁使用 `Referrer-Policy: no-referrer`，導致依賴 OSM 圖磚的外掛違反政策。

**How** 在圖磚請求本身設定 referrer policy 為 `strict-origin-when-cross-origin`，只傳送主機而不帶完整頁面路徑。

**What** datasette-leaflet 0.3 發布；此外掛內含 Leaflet 供其他 Datasette 外掛依賴，此版修正了 OSM 圖磚請求的 referrer 問題。

### 重點
- OpenStreetMap 政策要求對其圖磚伺服器的請求帶 referrer header
- Datasette 表格頁的 Referrer-Policy: no-referrer 會讓 OSM 圖磚外掛違反該政策
- 0.3 在圖磚請求上設 strict-origin-when-cross-origin，只傳主機、不傳完整路徑

**原文：** [simon-willison](https://simonwillison.net/2026/Nov/13/datasette-leaflet/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: datasette-leaflet 0.3 
 OpenStreetMap have a very reasonable policy that hits to their hosted tile server should send a referrer header . Datasette table pages used the Referrer-Policy: no-referrer HTTP header, causing plugins that loaded tiles from OpenStreetMap to violate that policy. 
 datasette-leaflet is the plugin that loads a bundled Leaflet so other Datasette plugins can depend on it. It now sets the referrer policy on the tile requests themselves to strict-origin-when-cross-origin , passing the host but not the full path to the page. 
 
 
 Tags: leaflet , datasette , openstreetmap

</details>