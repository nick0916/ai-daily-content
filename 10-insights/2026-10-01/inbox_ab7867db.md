---
id: inbox_ab7867db
date: 2026-10-01
source_ref: "[[00-inbox/2026-10-01/0256-ecc-releases-v2-2-3-c234]]"
title: "v2.2.3"
url: https://github.com/affaan-m/ECC/releases/tag/v2.2.3
source: ecc-releases
published_at: 2026-10-01T23:59:38+00:00
fetched_at: 2026-10-18T03:19:47.136456+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "ECC（affaan-m/ECC）於 2026-10-01 發布 v2.2.3，屬於命名與發布可靠度更新。第一，專案名稱在所有發布處統一稱為 ECC，從 pi/core profile 開始：其 README 與內建 blueprint skill 不再展開專案全名。profile 內容不變，仍為 123 個精選 skills、24 個 prompt commands，skill 描述文字共 35,006 字元；套件名 ecc-pi-core、目錄 pi/core/ 與安裝路徑都不變，下游打包者無需調整。第二，發布流程修正：npm publish 後會輪詢 registry 最多五分鐘才驗證發布產物；2.2.2 只等約 30 秒，npm 尚在處理上傳就放棄，導致在升級 latest 與建立 GitHub Release 之前失敗，需要重跑。實務教訓是 publish 後的驗證要容許 registry 的最終一致性延遲。下游取用方式不變：輪詢 /releases、下載 tag tar.gz、固定 sha256、複製 pi/core/ 後離線載入。"
key_points:
  - "發布 workflow 在 npm publish 後輪詢 registry 最多 5 分鐘（2.2.2 僅約 30 秒導致 run 失敗需重跑）"
  - "pi/core 內容不變：123 skills、24 prompt commands、35,006 字元描述；套件名 ecc-pi-core 與路徑 pi/core/ 不變"
  - "pi/core README 與 blueprint skill 只稱 ECC，不再展開專案名稱"
tags: [ecc, release-workflow, npm, pi-core, packaging]
topics: [agents.coding_agents]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v2.2.3

ECC（affaan-m/ECC）於 2026-10-01 發布 v2.2.3，屬於命名與發布可靠度更新。第一，專案名稱在所有發布處統一稱為 ECC，從 pi/core profile 開始：其 README 與內建 blueprint skill 不再展開專案全名。profile 內容不變，仍為 123 個精選 skills、24 個 prompt commands，skill 描述文字共 35,006 字元；套件名 ecc-pi-core、目錄 pi/core/ 與安裝路徑都不變，下游打包者無需調整。第二，發布流程修正：npm publish 後會輪詢 registry 最多五分鐘才驗證發布產物；2.2.2 只等約 30 秒，npm 尚在處理上傳就放棄，導致在升級 latest 與建立 GitHub Release 之前失敗，需要重跑。實務教訓是 publish 後的驗證要容許 registry 的最終一致性延遲。下游取用方式不變：輪詢 /releases、下載 tag tar.gz、固定 sha256、複製 pi/core/ 後離線載入。

### 重點
- 發布 workflow 在 npm publish 後輪詢 registry 最多 5 分鐘（2.2.2 僅約 30 秒導致 run 失敗需重跑）
- pi/core 內容不變：123 skills、24 prompt commands、35,006 字元描述；套件名 ecc-pi-core 與路徑 pi/core/ 不變
- pi/core README 與 blueprint skill 只稱 ECC，不再展開專案名稱

**原文：** [ecc-releases](https://github.com/affaan-m/ECC/releases/tag/v2.2.3)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

ECC 2.2.3 
 ECC 2.2.3 is a naming and release-reliability update. The project is called ECC 
everywhere it ships, starting with the pi/core profile, and the release 
workflow now waits long enough for npm to serve a freshly published version. 
 Naming 
 
 pi/core no longer expands the project name: its README and the bundled 
 blueprint skill refer to ECC only. The profile contents are otherwise 
unchanged: 123 curated skills and 24 prompt commands, 35,006 characters of 
skill description text. 
 Downstream packagers need no changes. The package is still ecc-pi-core , the 
directory is still pi/core/ , and existing install paths keep working. 
 
 Release workflow 
 
 After npm publish , the release workflow polls the registry for up to five 
minutes before verifying the published artifact. In 2.2.2 it gave up after 
about 30 seconds while npm was still processing the upload, so the run failed 
before promoting latest and creating the GitHub Release, and had to be 
re-run. 
 
 Downstream consumption is unchanged: poll /releases , download 
 archive/refs/tags/vX.Y.Z.tar.gz , pin its sha256, copy pi/core/ , and load it 
offline.

</details>