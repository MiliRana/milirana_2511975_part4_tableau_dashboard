# Dashboard Story — Retail Executive Performance Review
### For Leadership Audience | 2024–2025 Full Period Analysis

---

## Executive Summary

Over the two-year period from January 2024 to December 2025, the business generated **₹217M in total revenue** with **₹33.3M in total profit**, yielding an overall margin of **15.3%**. The portfolio is anchored by a high-performing Technology category and a strong South region. However, two critical risks demand leadership attention: **aggressive discounting is systematically destroying margins** across categories, and **the Furniture category is a compound risk zone** combining low margins, high returns, and frequent loss-making orders.

The dashboard tells a story of a business that is growing in revenue but could be significantly more profitable with targeted operational discipline in pricing and category management.

---

## What Is Performing Well

### Technology Is the Engine Room

Technology accounts for ₹153.9M in revenue — nearly 71% of total sales — and delivers the strongest margin at 18.2%. Sub-categories like Copiers, Accessories, and Phones consistently generate high-value, profitable orders. The average order value in Technology is significantly higher than other categories, and the return rate is the lowest in the portfolio at 3.0%.

### South Region Leads the Business

The South region (Telangana, Karnataka, Andhra Pradesh, Kerala, Tamil Nadu) is the top-performing geography, generating ₹64.7M in sales and ₹10.0M in profit. Key cities like Hyderabad, Bengaluru, and Chennai are driving volume and value. The South's performance suggests strong market penetration, favourable customer mix, and effective regional sales execution.

### Customer Segments Are Balanced and Healthy

All three segments — Consumer, Corporate, and Home Office — generate broadly similar sales and profit. Consumer segment achieves the highest average profit per order (₹8,141), indicating strong individual purchase intent without excessive discounting. This balance reduces concentration risk and provides a stable base for cross-segment marketing.

### Organic Channel Drives the Most Value

Orders acquired through the Organic channel represent a significant proportion of high-value, low-discount transactions. This indicates strong brand awareness and word-of-mouth referrals that are translating into quality orders without acquisition cost.

---

## What Is Underperforming

### Furniture Is a Consistent Underperformer

At a 6.9% margin, Furniture is contributing far less profit relative to its revenue share (23.8% of revenue, ~10.7% of profit). Tables and Bookcases are the main drag — these sub-categories regularly produce loss-making orders when discounts are applied. The situation is compounded by the highest return rate in the portfolio (7.7%), which further erodes already thin Furniture margins.

### West Region Trails on Margin

Despite similar order volumes to the East region, the West (Maharashtra, Madhya Pradesh, Rajasthan, Gujarat, Goa) consistently delivers the lowest margin (15.1%) and lowest absolute profit (₹7.4M). A closer look at West's product mix and discount patterns suggests that the region may be over-reliant on discounting to close deals.

### Corporate Segment Yields Lowest Per-Order Profit

Although Corporate has the highest order count (1,399 orders), it delivers the lowest average profit per order. Bulk corporate deals appear to come with deeper discounts that compress margins below what Consumer and Home Office segments tolerate.

---

## What Risks Are Visible

### Risk 1: Discount Discipline Is Broken

The data is unambiguous. Every incremental discount tier produces lower average profits, and orders at >30% discount are loss-making (-₹1,601 average profit). With 1,086 orders in the 21–30% bracket and 64 orders above 30% discount, there is clear evidence of unchecked discounting across the sales team. This is the highest-urgency risk on the dashboard.

### Risk 2: Furniture Is a Compound Liability

Low margin + high return rate + loss-making at standard discounts = a category that is destroying value. Without structural changes to Furniture pricing and discount policy, the category will continue to drag down overall portfolio performance. The risk is amplified by the fact that Furniture items typically involve higher logistics and handling costs, further compressing realised margins.

### Risk 3: Standard Class Delivery Risk

56.6% of all orders are shipped via Standard Class, with an average delivery time of 4.71 days. In an environment where customer expectations are shifting toward 2–3 day delivery as a baseline, this creates a growing churn and satisfaction risk. The elevated Furniture return rate may partially stem from longer shipping times causing damage or customer impatience.

### Risk 4: Campaign Channel Visibility Gap

Approximately 2% of orders have no campaign channel recorded. While small, this data quality issue limits the ability to fully measure marketing ROI. If the volume of unattributed orders grows, the business loses the ability to optimise acquisition spend.

---

## What Opportunities Are Visible

### Opportunity 1: Discount Elimination in Technology

Technology already achieves an 18.2% margin. If discount practices in this category were tightened — particularly for high-value Copiers and Machines — the business could materially increase profit without any change in revenue volume. Even moving the average Technology discount from ~10% to 5% would add millions in incremental profit.

### Opportunity 2: Expand South Region Playbook to North

North region has the second-highest sales (₹54.6M) but is only marginally behind South. There is an opportunity to apply South's successful market strategy to accelerate North performance — particularly in states like Delhi, Uttar Pradesh, and Punjab, which show strong existing order volumes.

### Opportunity 3: Premium Shipping Upsell

First Class shipping customers likely have higher order values and urgency. Proactively offering First Class or Same Day as a premium option for Technology orders (where product condition and speed matter more) could increase perceived service value and reduce post-delivery issues.

### Opportunity 4: Return Reduction in Furniture

A targeted programme to reduce Furniture returns from 7.7% to 5% would directly improve category margins. This could involve better product descriptions, packaging standards, or pre-delivery customer communication.

---

## Recommended Business Actions

| Priority | Action | Owner | Timeline |
|---|---|---|---|
| 1 | Implement discount approval workflow for any discount >20% | Sales Director | 30 days |
| 2 | Cap maximum discount at 30% business-wide | CFO / Sales Director | 30 days |
| 3 | Conduct Furniture return root-cause analysis | Operations Manager | 60 days |
| 4 | Audit West region discount and product mix practices | Regional Sales Head | 60 days |
| 5 | Review Corporate segment pricing — enforce profitability floor | Pricing Team | 60 days |
| 6 | Evaluate Standard Class upgrade for high-value orders | Logistics Manager | 90 days |
| 7 | Fix campaign channel attribution gap (null values) | Marketing / Analytics | 30 days |
| 8 | Develop Furniture pricing refresh — eliminate loss-making SKUs | Category Manager | 90 days |

---

## Limitations of the Dashboard

1. **No cost-of-acquisition data.** Campaign channel analysis cannot calculate true ROI without customer acquisition cost (CAC) data.
2. **Profit figures are transaction-level only.** Overhead costs, returns-processing costs, and logistics exceptions are not captured in the profit field.
3. **Return reasons not available.** The `return_flag` field only indicates whether an order was returned, not the reason. Root-cause analysis requires an additional data source.
4. **Customer-level aggregation is limited.** The dataset does not cleanly link multiple orders to the same customer across time, preventing cohort or lifetime value analysis.
5. **Delivery days = ship lag, not actual delivery.** The `delivery_days` field captures order-to-ship date, not order-to-delivery confirmation. Actual customer-experienced delivery time may differ.
6. **Seasonal and promotional context is absent.** Sales spikes visible in the trend chart cannot be explained without a promotional calendar or event log.

---

## Suggested Next Analysis

1. **Customer Lifetime Value (CLV) Segmentation** — Link customers across orders to identify high-CLV segments and prioritise retention investment.
2. **Discount Elasticity Modelling** — Use the existing discount vs. sales data to build a model that identifies the optimal discount level per category that maximises profit (not just revenue).
3. **Return Reason Analysis** — Augment the dataset with return reason codes to identify whether returns are driven by product quality, delivery damage, or expectation mismatch.
4. **Campaign ROI Analysis** — Integrate acquisition cost data to calculate true marketing ROI by channel.
5. **State-Level Deep Dive** — Break the regional analysis down to state level to identify specific geographic pockets of underperformance or high growth potential.
6. **Profitability Cohort by Ship Mode** — Analyse whether customers who use First Class or Same Day shipping generate higher LTV and repeat purchase rates.
