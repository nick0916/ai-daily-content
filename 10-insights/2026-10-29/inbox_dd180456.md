---
id: inbox_dd180456
date: 2026-10-29
source_ref: "[[00-inbox/2026-10-29/0035-medium-tag-llm-a-citation-that-survives-a-lookup-can-st-74ed]]"
title: "A citation that survives a lookup can still be wrong: measuring a citation gate for legal RAG"
url: https://medium.com/@nejc.fosnaric/a-citation-that-survives-a-lookup-can-still-be-wrong-measuring-a-citation-gate-for-legal-rag-5847d00d510a?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-10-29T18:28:23+00:00
fetched_at: 2026-10-30T00:42:23.916383+00:00
model: claude-haiku-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "法律 RAG 的引用可能真實存在，卻被用來支持與判決結論相反的主張，而存在性檢查會放行這類錯誤。 **Why** 只確認引用存在，不足以保證引用內容正確。 **How** 作者量測了一道能攔截此類錯誤的引用閘門（gate），並說明其限制；具體方法未在摘要中說明。 **What** 摘要未提供量化結果，只提到已測量該閘門的效果與限制。"
key_points:
  - "真實存在的判決若被用來支持相反結論，會通過所有存在性檢查"
  - "作者測量了能攔截此類錯誤的引用閘門並說明其限制（摘要未提供數字）"
tags: [legal-rag, citation-verification, hallucination-detection]
topics: [engineering.rag, engineering.evals]
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## A citation that survives a lookup can still be wrong: measuring a citation gate for legal RAG

法律 RAG 的引用可能真實存在，卻被用來支持與判決結論相反的主張，而存在性檢查會放行這類錯誤。

**Why** 只確認引用存在，不足以保證引用內容正確。

**How** 作者量測了一道能攔截此類錯誤的引用閘門（gate），並說明其限制；具體方法未在摘要中說明。

**What** 摘要未提供量化結果，只提到已測量該閘門的效果與限制。

### 重點
- 真實存在的判決若被用來支持相反結論，會通過所有存在性檢查
- 作者測量了能攔截此類錯誤的引用閘門並說明其限制（摘要未提供數字）

**原文：** [medium-tag-llm](https://medium.com/@nejc.fosnaric/a-citation-that-survives-a-lookup-can-still-be-wrong-measuring-a-citation-gate-for-legal-rag-5847d00d510a?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A real decision cited for the opposite of its holding passes every existence check. We measured the gate that catches it, and its limits. Continue reading on Medium »

</details>