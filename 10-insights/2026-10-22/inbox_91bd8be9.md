---
id: inbox_91bd8be9
date: 2026-10-22
source_ref: "[[00-inbox/2026-10-22/0102-bluesky-ai-curated-oracle-security-alert-advisory-cve-2026-91b4]]"
title: "Oracle Security Alert Advisory - CVE-2026-91403"
url: https://www.oracle.com/security-alerts/alert-cve-2026-91403.html
source: bluesky-ai-curated
published_at: 2026-10-22T10:24:43.783000+00:00
fetched_at: 2026-10-25T01:11:09.602284+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "Oracle 發布 Java SE 緊急安全更新，不再信任 eMudhra 相關的一組中繼 CA 憑證。 **Why** 受影響的中繼 CA 憑證被視為不可信，必須在 Java 端撤銷信任以避免風險。 **How** 透過 Java 更新把這組 eMudhra 相關中繼 CA 憑證列為不受信任；使用者需更新到最新 Java 版本或套用建議的緩解措施。 **What** Oracle Security Alert 針對 CVE-2026-91403，內含 1 個 Oracle Java SE 新安全補丁；該弱點可在無需認證下由網路遠端利用，也影響執行不受信任程式碼並依賴 Java sandbox 的情境（如 sandboxed Java Web Start / applet）。補丁僅提供給 Premier Support 或 Extended Support 涵蓋的版本；公告未列出回報者。"
key_points:
  - "CVE-2026-91403：Java 更新將 eMudhra 相關中繼 CA 憑證列為不信任"
  - "Java SE 1 個新補丁，可無認證遠端利用"
  - "補丁僅涵蓋 Premier/Extended Support 版本，其他版本建議升級"
tags: [java, oracle, cve, ca-certificate, security-alert]
topics: [security]
importance: 3
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Oracle Security Alert Advisory - CVE-2026-91403

Oracle 發布 Java SE 緊急安全更新，不再信任 eMudhra 相關的一組中繼 CA 憑證。

**Why** 受影響的中繼 CA 憑證被視為不可信，必須在 Java 端撤銷信任以避免風險。

**How** 透過 Java 更新把這組 eMudhra 相關中繼 CA 憑證列為不受信任；使用者需更新到最新 Java 版本或套用建議的緩解措施。

**What** Oracle Security Alert 針對 CVE-2026-91403，內含 1 個 Oracle Java SE 新安全補丁；該弱點可在無需認證下由網路遠端利用，也影響執行不受信任程式碼並依賴 Java sandbox 的情境（如 sandboxed Java Web Start / applet）。補丁僅提供給 Premier Support 或 Extended Support 涵蓋的版本；公告未列出回報者。

### 重點
- CVE-2026-91403：Java 更新將 eMudhra 相關中繼 CA 憑證列為不信任
- Java SE 1 個新補丁，可無認證遠端利用
- 補丁僅涵蓋 Premier/Extended Support 版本，其他版本建議升級

**原文：** [bluesky-ai-curated](https://www.oracle.com/security-alerts/alert-cve-2026-91403.html)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

timkellogg.me 在 Bluesky 分享:Java too www.oracle.com/security-ale...

Oracle Security Alert Advisory - CVE-2026-91403

Description

Affected Products and Patch Information

Security Alert Supported Products and Versions

References

Risk Matrix Content

Credit Statement

Modification History

This Security Alert addresses CVE-2026-91403 by providing Java updates which distrusts the set of impacted intermediate CA certificates related to eMudhra. To address this CVE, update to the latest Java version or apply the recommended mitigations. For more information refer to https://ops.java/emudhra and the Patch Availability Document below.

Security vulnerabilities addressed by this Security Alert affect the products listed below.

Please click on the links in the Patch Availability Document column below to access the documentation for patch availability information and installation instructions.

Patches released through the Security Alert program are provided only for product versions that are covered under the Premier Support or Extended Support phases of the Lifetime Support Policy . Oracle recommends that customers plan product upgrades to ensure that patches released through the Security Alert program are available for the versions they are currently running.

Product releases that are not under Premier Support or Extended Support are not tested for the presence of vulnerabilities addressed by this Security Alert. However, it is likely that earlier versions of affected releases are also affected by these vulnerabilities. As a result, Oracle recommends that customers upgrade to supported versions.

Risk matrices list only security vulnerabilities that are newly addressed by the patches associated with this advisory. Risk matrices for previous security patches can be found in previous Critical Patch Update advisories, Critical Security Patch Update advisories and Alerts . An English text version of the risk matrices provided in this document is here .

Security vulnerabilities are scored using CVSS version 3.1 (see Oracle CVSS Scoring for an explanation of how Oracle applies CVSS version 3.1).

Oracle conducts an analysis of each security vulnerability addressed by a Security Alert. Oracle does not disclose detailed information about this security analysis to customers, but the resulting Risk Matrix and associated documentation provide information about conditions required to exploit the vulnerability and the potential impact of a successful exploit. Oracle provides this information so that customers may conduct their own risk analysis based on the particulars of their product usage. For more information, see Oracle vulnerability disclosure policies .

Third party component vulnerabilities that are deemed not exploitable in the context of their inclusion in an Oracle product are listed, with VEX justifications, below the respective Oracle product's risk matrix.

The protocol in the risk matrix implies that all of its secure variants are affected as well. For example, if HTTP is listed as an affected protocol, it implies that HTTPS is also affected. The secure variant of a protocol is listed in the risk matrix only if it is the only variant affected.

The following people or organizations reported security vulnerabilities addressed by this Security Alert to Oracle: None credited in this Security Alert.

This Security Alert contains 1 new security patch for Oracle Java SE. This vulnerability is remotely exploitable without authentication, i.e., may be exploited over a network without requiring user credentials. The English text form of this Risk Matrix can be found here.

Oracle Critical Patch Updates, Critical Security Patch Updates, Security Alerts and Bulletins

Oracle Critical Patch Updates, Critical Security Patch Updates and Security Alerts - Frequently Asked Questions

Risk Matrix Definitions

Use of Common Vulnerability Scoring System (CVSS) by Oracle

English text version of the risk matrices

CSAF JSON version of the risk matrices

Map of CVE to Advisory/Alert

Oracle Lifetime Support Policy

JEP 290 Reference Blocklist Filter

This vulnerability can be exploited by using APIs in the specified Component, e.g., through a web service which supplies data to the APIs. This vulnerability also applies to Java deployments, typically in clients running sandboxed Java Web Start applications or sandboxed Java applets, that load and run untrusted code (e.g., code that comes from the internet) and rely on the Java sandbox for security.

</details>