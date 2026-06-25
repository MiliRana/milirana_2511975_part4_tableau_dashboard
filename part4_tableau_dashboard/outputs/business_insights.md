# Business Insights — Executive Sales Dashboard

## Overview

This document presents 8 key business insights derived from the Retail Executive Dashboard covering 4,200 orders from January 2024 to December 2025 across India.

---

## Calculated Fields Reference

Before the insights, the following calculated fields were used to derive these observations:

| Calculated Field | Formula | Purpose |
|---|---|---|
| Profit Margin | `[Profit] / [Sales]` | Measures profitability efficiency |
| Cost | `[Sales] - [Profit]` | Derived operational/goods cost |
| Average Order Value | `SUM([Sales]) / COUNT([Order ID])` | Measures transaction size |
| Return Rate | `SUM([Return Flag]) / COUNT([Order ID])` | Measures product/service failure rate |
| Shipping Delay Bucket | `IF [Delivery Days] = 0 THEN "Same Day" ELSEIF [Delivery Days] <= 2 THEN "Fast (1-2 days)" ELSEIF [Delivery Days] <= 4 THEN "Normal (3-4 days)" ELSEIF [Delivery Days] <= 6 THEN "Slow (5-6 days)" ELSE "Very Slow (7+ days)" END` | Categorises delivery performance |
| Discount Tier | `IF [Discount] = 0 THEN "No Discount" ELSEIF [Discount] <= 0.10 THEN "Low" ELSEIF [Discount] <= 0.20 THEN "Medium" ELSEIF [Discount] <= 0.30 THEN "High" ELSE "Very High" END` | Groups discounts for margin analysis |
| Profitable Order | `IF [Profit] > 0 THEN "Profitable" ELSE "Loss-Making" END` | Binary profitability classification |

---

## Insight 1: Sales Trend — Technology Dominates Annual Revenue

**Observation:**  
Technology sales far outpace other categories throughout the 2024–2025 period. The trend shows consistent month-over-month revenue generation with periodic spikes, likely tied to product launches or seasonal demand cycles.

**Data Evidence:**  
- Total Technology sales: ₹153.9M (70.9% of total revenue)
- Total Office Supplies: ₹11.5M (5.3%)
- Total Furniture: ₹51.6M (23.8%)

**Business Interpretation:**  
The business is heavily reliant on a single category for revenue. While Technology carries strong margins (18.2%), over-concentration creates risk if market conditions or supply chains in that category are disrupted.

**Recommended Action:**  
Diversify revenue mix by investing in Office Supplies marketing and expanding higher-margin Furniture sub-categories (Chairs, Furnishings). Set category revenue targets to reduce Technology dependency below 60% over 2 years.

---

## Insight 2: Regional Performance — South Region Leads, West Lags

**Observation:**  
The South region consistently records the highest sales and profit across both years. The West region underperforms relative to its order volume.

**Data Evidence:**  
- South: ₹64.7M sales, ₹10.0M profit (15.4% margin)
- North: ₹54.6M sales, ₹8.3M profit (15.2% margin)
- East: ₹48.9M sales, ₹7.6M profit (15.6% margin)
- West: ₹48.9M sales, ₹7.4M profit (15.1% margin)

**Business Interpretation:**  
South region (Telangana, Karnataka, Andhra Pradesh, Kerala, Tamil Nadu) drives the most value. West region, despite having similar order volumes to East, generates the lowest margin — suggesting potential issues with product mix, discount levels, or higher operating costs in states like Maharashtra and Madhya Pradesh.

**Recommended Action:**  
Conduct a West region audit: examine discount practices by sales reps, assess product mix, and identify whether specific states (e.g., Maharashtra) are pulling down overall margin. Consider replicating South region's go-to-market strategy in the West.

---

## Insight 3: Category and Sub-Category Profitability — Furniture Tables Generate Consistent Losses

**Observation:**  
Furniture as a category has the lowest profit margin at 6.9%. Within Furniture, the Tables sub-category regularly produces negative profit when discounts are applied, while Chairs and Furnishings are relatively healthier.

**Data Evidence:**  
- Furniture margin: 6.9%
- Office Supplies margin: 14.9%
- Technology margin: 18.2%
- Multiple Furniture orders (Tables, Bookcases) show negative profit values at 25–30% discount

**Business Interpretation:**  
The Furniture category — particularly Tables and Bookcases — is likely being used as a loss-leader or is suffering from uncontrolled discounting by the sales team. At current margins, any discount above ~15% on Furniture drives the order into loss territory.

**Recommended Action:**  
Enforce a hard discount ceiling of 15% for Furniture sub-categories. Review pricing strategy for Tables and Bookcases to ensure cost recovery. Consider whether loss-making Furniture orders are being used strategically to win large Technology or Office Supplies deals (bundling).

---

## Insight 4: Customer Segment Behaviour — Home Office Segment Delivers Best Returns

**Observation:**  
Home Office customers generate slightly higher total profit despite similar order counts to Corporate and Consumer segments.

**Data Evidence:**  
- Home Office: ₹74.5M sales, ₹11.6M profit, 1,446 orders → ₹7,989 avg profit/order
- Corporate: ₹70.6M sales, ₹10.7M profit, 1,399 orders → ₹7,663 avg profit/order
- Consumer: ₹71.9M sales, ₹11.0M profit, 1,355 orders → ₹8,141 avg profit/order

**Business Interpretation:**  
All three segments are remarkably balanced in revenue and profit. Consumer segment achieves the highest average profit per order, suggesting higher-value or less-discounted individual purchases. Corporate segment, despite having the highest order count, has the lowest average profit per order — indicating potential over-discounting for bulk corporate deals.

**Recommended Action:**  
Review Corporate discount policies — ensure volume discounts are tied to minimum profitability thresholds. Invest in retention marketing for Consumer and Home Office segments, as they yield the best per-order returns.

---

## Insight 5: Discount Impact — Heavy Discounting Destroys Margins

**Observation:**  
There is a clear, negative linear relationship between discount level and profitability. Orders with no discount generate dramatically higher profits than discounted orders.

**Data Evidence:**  
- No Discount (0%): Average profit = ₹13,203 per order (1,024 orders)
- Low Discount (1–10%): Average profit = ₹10,010 per order (979 orders)
- Medium Discount (11–20%): Average profit = ₹6,336 per order (1,047 orders)
- High Discount (21–30%): Average profit = ₹3,181 per order (1,086 orders)
- Very High Discount (>30%): Average profit = **-₹1,601 per order** (64 orders — loss-making)

**Business Interpretation:**  
Discounting above 30% is categorically loss-making. The 1,086 orders in the 21–30% bracket are marginally profitable but represent a significant missed revenue opportunity. The business is leaving money on the table through over-discounting.

**Recommended Action:**  
Implement a discount approval workflow requiring manager sign-off for discounts above 20%. Cap maximum discount at 30% business-wide. Train sales team on value-selling to reduce discount dependence. Target reducing avg discount rate from current 13.7% to below 10% within 12 months.

---

## Insight 6: Shipping Performance — Standard Class Delays Risk Customer Satisfaction

**Observation:**  
Standard Class — the most-used shipping mode — has the longest average delivery time and accounts for the majority of revenue. Same Day shipping has near-zero delivery days but limited adoption.

**Data Evidence:**  
- Standard Class: 4.71 avg days, ₹122.8M revenue (56.6% of orders)
- Second Class: 2.68 avg days, ₹47.7M revenue
- First Class: 1.77 avg days, ₹31.9M revenue
- Same Day: 0.40 avg days, ₹14.6M revenue

**Business Interpretation:**  
The bulk of the business relies on the slowest standard shipping. Customers choosing Standard Class are experiencing nearly 5-day average delivery windows. In a competitive retail environment where 2-day delivery is becoming standard, this creates customer satisfaction and retention risk, particularly for repeat buyers.

**Recommended Action:**  
Survey Standard Class customers on delivery satisfaction. Evaluate cost-benefit of upgrading default shipping to Second Class (2.68 days) for orders above a certain value threshold. Promote First Class for Technology orders where speed and product condition are critical. Explore logistics partnerships to reduce Standard Class delivery time.

---

## Insight 7: Return Patterns — Furniture Returns Highest Risk

**Observation:**  
Furniture has a significantly higher return rate compared to the other two categories. Technology, despite being the highest revenue category, has the lowest return rate.

**Data Evidence:**  
- Furniture: 88 returns out of 1,147 orders = **7.7% return rate**
- Office Supplies: 61 returns out of 1,669 orders = 3.7% return rate
- Technology: 42 returns out of 1,384 orders = **3.0% return rate**
- Overall return rate: 4.5%

**Business Interpretation:**  
Furniture's 7.7% return rate is more than double that of Technology. High return rates in Furniture erode already thin margins further. Returns in this category likely stem from damage during shipping (large/fragile items), product-expectation mismatches, or quality issues.

**Recommended Action:**  
Investigate root causes of Furniture returns — run a return reason analysis. Improve product imagery and description quality online to manage expectations. Consider dedicated packaging standards for Tables and Bookcases. Set a KPI target of reducing Furniture return rate to below 5% within 6 months.

---

## Insight 8: Business Risk — Furniture Category is a Compound Risk Zone

**Observation:**  
Furniture simultaneously exhibits the lowest profit margin (6.9%), the highest return rate (7.7%), and the highest frequency of loss-making orders due to discounting. This makes Furniture the highest-risk category in the portfolio.

**Data Evidence:**  
- Furniture margin: 6.9% (vs 18.2% for Technology)
- Furniture return rate: 7.7% (vs 3.0% for Technology)
- Multiple Furniture sub-categories (Tables, Bookcases) generate losses at standard discount rates
- Furniture accounts for 23.8% of revenue but only ~10.7% of total profit

**Business Interpretation:**  
Furniture is consuming disproportionate operational resources (handling, returns, logistics) relative to the profit it generates. It is both a margin risk and a cash flow risk. Without intervention, Furniture will continue to drag down overall portfolio performance.

**Recommended Action:**  
Conduct a strategic review of the Furniture portfolio: (1) Identify which sub-categories and SKUs are consistently profitable and promote them, (2) Consider discontinuing or re-pricing loss-making SKUs, (3) Bundle Furniture with high-margin Office Supplies or Technology where possible, (4) Apply strict discount controls as outlined in Insight 5. Set a 12-month target to bring Furniture margin above 10%.
