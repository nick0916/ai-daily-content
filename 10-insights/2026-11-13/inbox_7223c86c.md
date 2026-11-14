---
id: inbox_7223c86c
date: 2026-11-13
source_ref: "[[00-inbox/2026-11-13/0146-tomasz-tunguz-no-shirt-no-shoes-no-service-for-bots-11eb]]"
title: "No Shirt, No Shoes, No Service for Bots"
url: https://tomtunguz.com/no-shirt-no-shoes-no-service-for-bots/
source: tomasz-tunguz
published_at: 2026-11-13T00:00:00+00:00
fetched_at: 2026-11-14T01:53:19.588139+00:00
model: claude-sonnet-5-5
tokens_in: 0
tokens_out: 0
summary_zh: "大型電商與航空把 AI 代理擋在門外，因為代理不會買廣告位、升等與保固，而這些才是賺錢的部分。 **Why** 這些公司的基本商品只能打平，利潤來自廣告、加購與保固；AI 代理是「帶著任務的買家」，會跳過這些。 **How** Tunguz 用 10-K 數字拆解：Amazon 零售營業利益 $34.4b，而廣告約 $34.3b；United 的加購與聯名卡等收入超過其 $4.7b 營業利益；Dell 的服務毛利占其營業利益 127%。相對地，Shopify 靠 3.1% 的交易抽成，不論買家是人或代理都一樣，因此歡迎代理。 **What** United 本週修改條款，禁止 AI 代理訂票並保留取消權；Amazon 也封鎖第三方 AI 購物代理。Shopify 於 9 月把 WebMCP 擴展到結帳流程，自家測試 60 項結帳任務全數完成、耗時 10.3 秒，比瀏覽器自動化（56/60、27.4 秒）成本低 58%。文中指出商家需選擇調高基本價、收取代理結帳費，或設計誘因讓機器人願意追加銷售。"
key_points:
  - "Amazon 廣告收入約 $68.6b、約 50% 毛利，產生約 $34.3b，幾乎等於非 AWS 零售營業利益 $34.4b；United 的 $4.8b 座位/行李升等加 $3.2b 其他收入，合計超過其 $4.7b 營業利益"
  - "Dell 硬體毛利 13.7%，服務毛利 44.8%，服務毛利 $10.4b 占營業利益 $8.1b 的 127%"
  - "Shopify WebMCP 結帳測試：60/60 任務、10.3 秒，對比瀏覽器自動化 56/60、27.4 秒、成本低 58%；HUMAN Security 數據顯示 8 月到 10 月 AI 代理流量成長 8 倍"
tags: [ai-agents, agentic-commerce, webmcp, shopify, business-model]
topics: [agents.mcp, product_and_org.adoption]
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## No Shirt, No Shoes, No Service for Bots

大型電商與航空把 AI 代理擋在門外，因為代理不會買廣告位、升等與保固，而這些才是賺錢的部分。

**Why** 這些公司的基本商品只能打平，利潤來自廣告、加購與保固；AI 代理是「帶著任務的買家」，會跳過這些。

**How** Tunguz 用 10-K 數字拆解：Amazon 零售營業利益 $34.4b，而廣告約 $34.3b；United 的加購與聯名卡等收入超過其 $4.7b 營業利益；Dell 的服務毛利占其營業利益 127%。相對地，Shopify 靠 3.1% 的交易抽成，不論買家是人或代理都一樣，因此歡迎代理。

**What** United 本週修改條款，禁止 AI 代理訂票並保留取消權；Amazon 也封鎖第三方 AI 購物代理。Shopify 於 9 月把 WebMCP 擴展到結帳流程，自家測試 60 項結帳任務全數完成、耗時 10.3 秒，比瀏覽器自動化（56/60、27.4 秒）成本低 58%。文中指出商家需選擇調高基本價、收取代理結帳費，或設計誘因讓機器人願意追加銷售。

### 重點
- Amazon 廣告收入約 $68.6b、約 50% 毛利，產生約 $34.3b，幾乎等於非 AWS 零售營業利益 $34.4b；United 的 $4.8b 座位/行李升等加 $3.2b 其他收入，合計超過其 $4.7b 營業利益
- Dell 硬體毛利 13.7%，服務毛利 44.8%，服務毛利 $10.4b 占營業利益 $8.1b 的 127%
- Shopify WebMCP 結帳測試：60/60 任務、10.3 秒，對比瀏覽器自動化 56/60、27.4 秒、成本低 58%；HUMAN Security 數據顯示 8 月到 10 月 AI 代理流量成長 8 倍

**原文：** [tomasz-tunguz](https://tomtunguz.com/no-shirt-no-shoes-no-service-for-bots/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Read on tomtunguz.com → Bots passed 51% of global web traffic in 2024 & reached 54% in 2026, while monthly AI agent traffic jumped 8x in two months between August & October 2026. 1 
 

 Instead of welcoming those agentic buyers, the largest consumer storefronts are locking them out. 
 This week United Airlines updated its terms to ban AI agents from booking tickets, reserving the right to cancel any reservation bought by a bot. 2 Amazon has similarly blocked third-party AI shopping agents from its store. 3 
 Both companies cite security. The deeper reason sits on their income statements : in modern e-commerce, the base product merely breaks even ; ads, upgrades & warranties supply the profit. 
 

 Amazon collected $588b of retail revenue last year, but advertising is the only profit in it. The $68.6b of sponsored listings, at roughly a 50% margin, generate $34.3b : all of the $34.4b in retail operating income. 4 
 United runs the same playbook with fees instead of ads. Its $4.8b of seat & bag upgrades, $3.2b of credit card & loyalty fees & trip insurance commissions together top its entire $4.7b of operating income. 5 6 
 Dell’s computer business is a high-tech grocery store. Hardware sold at a 13.7% gross margin does not cover $14.6b of operating expenses ; ProSupport warranties & attached services at a 44.8% margin generate $10.4b of gross profit, or 127% of Dell’s $8.1b in operating income. 7 
 Each share tops 100% because the base product, priced near cost, loses money on its own. 
 Shopify runs the opposite model, which is why it welcomes agents. Shopify powers independent merchant websites & collects a 3.1% toll on every dollar processed, 78% of it from payment processing & merchant services. 8 Whether a human or an AI agent clicks buy, Shopify collects the same cut. In September, it opened checkout to browser agents across every eligible store. 
 An AI agent is a buyer on a mission. It skips the sponsored listings, declines Economy Plus unless explicitly instructed & unchecks the extended warranty on a Dell Latitude. 
 Merchants built on loss leaders now face a choice : raise base prices, charge an explicit agent checkout fee, or invent wholesale incentives that persuade bots to upsell. Until they re-price the funnel, the sign on the checkout window stays the same : no bots allowed. 
 
 
 
 
 Andreessen Horowitz (Olivia Moore & Justine Moore), Welcome to the B2A Economy , November 11, 2026 ; Imperva Bad Bot Report (2021 to 2026 automated traffic share rising from 42% in 2021 to 51% in 2024 & 54% in 2026) ; Cloudflare Radar (automated requests reaching 60.6% of web content HTML requests in August 2026) ; & HUMAN Security State of Agentic Traffic (November 9, 2026, showing monthly AI agent web requests rising 16.3x from February to October 2026 & 8.0x from August to October 2026, with Meta Muse at 59% & OpenAI agents at 30% of observed agent traffic). ↩︎ 
 
 
 United Airlines terms (revised November 11, 2026, Rules 1, 5.H & 6.J.6) & PhocusWire , November 11, 2026 : prohibits any automated artificial intelligence tool or agent from making, modifying or servicing a ticket or purchasing any service or product, & permits United to cancel tickets booked by an AI agent without notice, even if a human passenger supervised the transaction. ↩︎ 
 
 
 Amazon updated its robots.txt rules & sent formal cease-and-desist notices blocking third-party agentic browsers & shopping assistants (including Perplexity’s Comet & automated checkout agents) from executing purchases on amazon.com . ↩︎ 
 
 
 Amazon.com, Inc. Form 10-K for the fiscal year ended December 31, 2025 : consolidated net sales of $716.92b less AWS revenue of $128.73b equals $588.20b in non-AWS revenue. North America operating income ($29.62b) plus International operating income ($4.75b) equals $34.37b in non-AWS operating income. Advertising services revenue reached $68.64b in 2025 (up from $56.21b in 2024). ↩︎ 
 
 
 United Airlines Holdings, Inc. Form 10-K for the fiscal year ended December 31, 2025 : total operating revenue of $59.07b, operating income of $4.71b (8.0% operating margin) & net income of $3.40b. Disaggregated revenue Footnote 3 reports $4.80b in ancillary passenger fees (seat selection, Economy Plus & baggage) & $3.20b in other operating revenue (co-brand credit card marketing, Kinective Media advertising & lounge/partner fees), plus $3.41b in redeemed MileagePlus travel miles. ↩︎ 
 
 
 US Senate Permanent Subcommittee on Investigations airline ancillary fee report & travel insurance underwriting disclosures (Allianz Partners, AIG Travel Guard & Arch RoamRight) : airlines & online travel agencies retain 30% to 50% of gross written trip-insurance premiums as distribution commission at checkout. ↩︎ 
 
 
 Dell Technologies Inc. Form 10-K & Q4 FY26 earnings release for the fiscal year ended January 30, 2026 : total revenue of $113.54b & GAAP operating income of $8.15b ($22.71b total gross profit less $14.56b operating expenses). Products revenue was $90.41b with $78.06b cost of revenue ($12.35b gross profit, 13.7% gross margin) ; Services revenue (including ProSupport warranties, extended maintenance & deployment attach) was $23.13b with $12.77b cost of revenue ($10.36b gross profit, 44.8% gross margin, or 127.1% of GAAP operating income). ↩︎ 
 
 
 Shopify Inc. Q3 2026 earnings release, November 3, 2026 : GMV of $119.1b on revenue of $3.742b (subscription solutions $836m, merchant solutions $2,906m), gross profit of $1.78b at a 47.6% margin & operating income of $568m, so revenue equals about 3.1% of GMV, with 68% of GMV processed through Shopify Payments. Per the Form 10-Q, merchant solutions revenue is principally payment processing & currency conversion fees, with advertising on the Shopify App Store & Shop Campaigns included alongside lending, shipping labels & POS hardware in that $2,906m. TechCrunch , September 28, 2026 : Shopify extended WebMCP into checkout for all eligible merchants with no merchant configuration, letting browser agents read, update & submit a checkout once the buyer authorizes it, while Amazon & Adidas moved to block agents ; Shopify’s own test completed 60 of 60 checkout tasks in 10.3 seconds using WebMCP versus 56 of 60 in 27.4 seconds via browser automation, at 58% lower cost. ↩︎

</details>