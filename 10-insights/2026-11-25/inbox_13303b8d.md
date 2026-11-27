---
id: inbox_13303b8d
date: 2026-11-25
source_ref: "[[00-inbox/2026-11-25/0052-infoq-main-aws-lambda-doubles-its-timeout-to-30-min-4475]]"
title: "AWS Lambda Doubles Its Timeout to 30 Minutes after Eight Years at 15"
url: https://www.infoq.com/news/2026/11/aws-lambda-30-minute-timeout/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-11-25T07:02:00+00:00
fetched_at: 2026-11-27T00:59:38.366077+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "AWS Lambda 單次執行時間上限從 15 分鐘延長到 30 分鐘，不用設定也不加價。 **Why** 15 分鐘的限制自 2018 年沿用至今，長任務常得改用其他服務。 **What** AWS 將 on-demand Lambda Event Functions 的最大 timeout 從 15 提高到 30 分鐘，所有商業區域適用，無需 opt-in、無新定價。AWS 文章列出代價：相同請求率下並行數加倍、SQS visibility timeout 需三小時、Kafka mapping 必須重建；實務者歡迎此變更，也在討論哪些工作仍不該放在 Lambda。"
key_points:
  - "Lambda Event Functions timeout 由 15 分鐘提高至 30 分鐘，自 2018 年以來首次調整"
  - "所有商業區域適用，無需 opt-in，無新定價"
  - "代價：相同請求率下並行數加倍、SQS visibility timeout 三小時、Kafka mapping 需重建"
tags: [aws-lambda, serverless, timeout, sqs, kafka]
topics: [engineering.architecture]
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## AWS Lambda Doubles Its Timeout to 30 Minutes after Eight Years at 15

AWS Lambda 單次執行時間上限從 15 分鐘延長到 30 分鐘，不用設定也不加價。

**Why** 15 分鐘的限制自 2018 年沿用至今，長任務常得改用其他服務。

**What** AWS 將 on-demand Lambda Event Functions 的最大 timeout 從 15 提高到 30 分鐘，所有商業區域適用，無需 opt-in、無新定價。AWS 文章列出代價：相同請求率下並行數加倍、SQS visibility timeout 需三小時、Kafka mapping 必須重建；實務者歡迎此變更，也在討論哪些工作仍不該放在 Lambda。

### 重點
- Lambda Event Functions timeout 由 15 分鐘提高至 30 分鐘，自 2018 年以來首次調整
- 所有商業區域適用，無需 opt-in，無新定價
- 代價：相同請求率下並行數加倍、SQS visibility timeout 三小時、Kafka mapping 需重建

**原文：** [infoq-main](https://www.infoq.com/news/2026/11/aws-lambda-30-minute-timeout/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

AWS has raised the maximum timeout of on-demand Lambda Event Functions from 15 to 30 minutes in all commercial regions, with no opt-in and no new pricing. The limit had stood since 2018. AWS's post lists the costs: twice the concurrency at the same request rate, three-hour SQS visibility timeouts, and Kafka mappings that must be recreated. Practitioners welcome it and ask what belongs elsewhere. By Steef-Jan Wiggers

</details>