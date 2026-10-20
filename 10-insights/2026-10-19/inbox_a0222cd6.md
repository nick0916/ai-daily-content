---
id: inbox_a0222cd6
date: 2026-10-19
source_ref: "[[00-inbox/2026-10-19/0205-infoq-main-jep-543-finalizes-structured-concurrency-20f6]]"
title: "JEP 543 Finalizes Structured Concurrency in JDK 28, Ending Seven Preview Rounds"
url: https://www.infoq.com/news/2026/10/jep-543-jdk-28/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-10-19T14:30:00+00:00
fetched_at: 2026-10-20T02:09:40.413672+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Java 的「結構化並行」功能經過七輪預覽後正式定案，讓多執行緒任務像一般程式區塊一樣有清楚的開始與結束。 **What** JEP 543 在 JDK 28 將 structured concurrency 定案，API 與 JDK 27 相比沒有變動；JDK 27 使用者只需移除 --enable-preview 並重新編譯。為 JDK 25 或 26 撰寫的程式碼則需調整 R_X 例外型別參數、ExecutionException 包裝，以及抽象的 timeout() joiner callback。"
key_points:
  - "JEP 543 於 JDK 28 定案 structured concurrency，結束七輪預覽"
  - "JDK 27 → 28：API 無變動，僅需移除 --enable-preview 並重新編譯"
  - "JDK 25/26 的程式碼需調整 R_X 例外型別參數、ExecutionException 包裝、抽象 timeout() joiner callback"
tags: [java, jdk-28, jep-543, structured-concurrency]
topics: [engineering.architecture]
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## JEP 543 Finalizes Structured Concurrency in JDK 28, Ending Seven Preview Rounds

Java 的「結構化並行」功能經過七輪預覽後正式定案，讓多執行緒任務像一般程式區塊一樣有清楚的開始與結束。 **What** JEP 543 在 JDK 28 將 structured concurrency 定案，API 與 JDK 27 相比沒有變動；JDK 27 使用者只需移除 --enable-preview 並重新編譯。為 JDK 25 或 26 撰寫的程式碼則需調整 R_X 例外型別參數、ExecutionException 包裝，以及抽象的 timeout() joiner callback。

### 重點
- JEP 543 於 JDK 28 定案 structured concurrency，結束七輪預覽
- JDK 27 → 28：API 無變動，僅需移除 --enable-preview 並重新編譯
- JDK 25/26 的程式碼需調整 R_X 例外型別參數、ExecutionException 包裝、抽象 timeout() joiner callback

**原文：** [infoq-main](https://www.infoq.com/news/2026/10/jep-543-jdk-28/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

JDK 28 finalizes structured concurrency through JEP 543, with no API changes from JDK 27. Teams on JDK 27 only need to drop --enable-preview and recompile. Code written for JDK 25 or 26 must adapt to the R_X exception type parameter, ExecutionException wrapping, and the abstract timeout() joiner callback. By A N M Bazlur Rahman

</details>