---
id: inbox_dc0da888
date: 2026-11-12
source_ref: "[[00-inbox/2026-11-12/0146-lobsters-ai-libreagi-save-os-models-03eb]]"
title: "libreagi - save OS models"
url: https://libreagi.com/
source: lobsters-ai
published_at: 2026-11-12T09:35:46-06:00
fetched_at: 2026-11-14T01:57:58.077677+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "用 BitTorrent 私有 tracker 讓成員保存最可能消失的開源模型權重。 **Why** 作者主張開源模型應該比託管它的地方存活更久。 **How** 成員做種（seed）累積積分，積分隨檔案大小與時間增加；只剩一份副本的模型可獲得四倍基本積分，每個檔案會比對來源 commit，並由工作人員審核。 **What** 接受 safetensors、GGUF、ONNX 等格式，授權限 Apache-2.0、MIT 或 Qwen Community License；另有含雜湊與來源的簽署公開目錄，可在網站消失後重建 swarm。"
key_points:
  - "稀缺性定價：單一副本的模型獲得四倍基本積分，越稀少越受激勵做種"
  - "每個檔案比對來源 commit，且每個模型經工作人員審核，授權範圍限定三種"
  - "簽署的公開目錄列出所有模型、雜湊與來源，讓社群可在網站消失後重建 swarm"
tags: [open-weights, bittorrent, model-preservation, seeding, archive]
topics: [foundation_models.open_weights]
importance: 2
novelty: 3
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## libreagi - save OS models

用 BitTorrent 私有 tracker 讓成員保存最可能消失的開源模型權重。

**Why** 作者主張開源模型應該比託管它的地方存活更久。

**How** 成員做種（seed）累積積分，積分隨檔案大小與時間增加；只剩一份副本的模型可獲得四倍基本積分，每個檔案會比對來源 commit，並由工作人員審核。

**What** 接受 safetensors、GGUF、ONNX 等格式，授權限 Apache-2.0、MIT 或 Qwen Community License；另有含雜湊與來源的簽署公開目錄，可在網站消失後重建 swarm。

### 重點
- 稀缺性定價：單一副本的模型獲得四倍基本積分，越稀少越受激勵做種
- 每個檔案比對來源 commit，且每個模型經工作人員審核，授權範圍限定三種
- 簽署的公開目錄列出所有模型、雜湊與來源，讓社群可在網站消失後重建 swarm

**原文：** [lobsters-ai](https://libreagi.com/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

LibreAGI

Seeding pays by scarcity

Weights from a known source

A catalog that survives us

Talk to us on IRC

Open weights, members only

Open models should outlive the places that host them. LibreAGI is a private BitTorrent
 tracker where members keep copies of the models most likely to disappear.

$ mktorrent -p -s libreagi -l 24 ./model

Credit grows with size and time, and a model with one copy earns four times the base rate. The rare ones need the most help.

Any format, from safetensors and GGUF to ONNX, under Apache-2.0, MIT or the Qwen Community License. Each file is checked against its source commit, and staff review every model.

A signed public catalog lists every model, hash and source, so anyone can rebuild the swarms if this site goes away.

The public channel is open to anyone, with no account needed. Come and ask questions before you apply.

</details>