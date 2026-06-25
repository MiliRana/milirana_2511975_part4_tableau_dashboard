# Executive Sales Dashboard — Tableau Project

## Business Problem Summary

The retail leadership team requires a consolidated executive dashboard to monitor and evaluate:
- Overall sales trends and seasonality across 2024–2025
- Regional and state-level performance disparities
- Category and sub-category profitability
- Customer segment behaviour and revenue contribution
- Impact of discounting on profit margins
- Shipping mode effectiveness and delivery delays
- Product return patterns and associated risks
- Campaign channel effectiveness

The goal is to surface actionable insights that support pricing, logistics, inventory, and marketing decisions.

---

## Dataset Description

**File:** `data/dashboard_sales_data.xlsx`  
**Sheet:** `dashboard_sales_data`  
**Rows:** 4,200 orders  
**Period:** January 2024 – December 2025

| Field | Type | Description |
|---|---|---|
| order_id | Text | Unique order identifier |
| order_date | Date | Date order was placed |
| ship_date | Date | Date order was shipped |
| customer_id | Text | Unique customer identifier |
| customer_segment | Text | Consumer / Corporate / Home Office |
| region | Text | North / South / East / West |
| state | Text | Indian state |
| city | Text | City of delivery |
| category | Text | Furniture / Office Supplies / Technology |
| sub_category | Text | 13 sub-categories |
| product_name | Text | Product name |
| ship_mode | Text | Same Day / First Class / Second Class / Standard Class |
| sales | Number | Revenue in INR |
| quantity | Number | Units ordered |
| discount | Number | Discount rate (0 to 1) |
| profit | Number | Net profit in INR |
| return_flag | Binary | 1 = Returned, 0 = Not returned |
| delivery_days | Number | Days from order to delivery |
| customer_rating | Number | Rating out of 5 |
| campaign_channel | Text | Organic / Paid / Social / Email / Referral |

---

## Tableau Workbook Description

**File:** `tableau/executive_dashboard.twbx`

The packaged workbook contains:
- 7 individual analysis sheets (one per business question)
- 1 executive dashboard combining all key views
- Calculated fields, filters, and dashboard actions

### Sheets Included
1. **Sales Trend** — Monthly sales line chart (2024–2025)
2. **Regional Performance** — Map + bar chart of sales/profit by region and state
3. **Category Profitability** — Bar chart of category and sub-category profit margins
4. **Customer Segment View** — Segment comparison: sales, profit, order count
5. **Shipping Performance** — Avg delivery days and sales by ship mode
6. **Discount vs Profit** — Scatter plot of discount rate vs profit
7. **Return Analysis** — Return rate by category and segment

---

## Calculated Fields Created

| Field Name | Formula | Purpose |
|---|---|---|
| Profit Margin | `[Profit] / [Sales]` | Measures profitability as a percentage of sales |
| Cost | `[Sales] - [Profit]` | Derived cost of goods/operations |
| Average Order Value | `SUM([Sales]) / COUNT([Order ID])` | Average revenue per transaction |
| Return Rate | `SUM([Return Flag]) / COUNT([Order ID])` | Proportion of orders returned |
| Shipping Delay Bucket | `IF [Delivery Days] = 0 THEN "Same Day" ELSEIF [Delivery Days] <= 2 THEN "Fast (1-2 days)" ELSEIF [Delivery Days] <= 4 THEN "Normal (3-4 days)" ELSEIF [Delivery Days] <= 6 THEN "Slow (5-6 days)" ELSE "Very Slow (7+ days)" END` | Categorises delivery speed for analysis |
| Discount Tier | `IF [Discount] = 0 THEN "No Discount" ELSEIF [Discount] <= 0.10 THEN "Low (1-10%)" ELSEIF [Discount] <= 0.20 THEN "Medium (11-20%)" ELSEIF [Discount] <= 0.30 THEN "High (21-30%)" ELSE "Very High (>30%)" END` | Groups discounts for pattern analysis |
| Profitable Order | `IF [Profit] > 0 THEN "Profitable" ELSE "Loss-Making" END` | Flags individual orders for profitability analysis |

---

## Dashboard Components

### KPI Cards (Top Row)
- Total Sales (INR)
- Total Profit (INR)
- Overall Profit Margin (%)
- Return Rate (%)
- Average Order Value (INR)

### Charts
1. Monthly Sales & Profit Trend (line chart)
2. Sales by Region (map + bar)
3. Category Profitability (horizontal bar)
4. Segment Comparison (grouped bar)
5. Discount vs Profit Impact (bar/table)
6. Shipping Mode Performance (bar)
7. Return Rate by Category (bar)

---

## Filters and Interactions

### Global Filters Applied to Dashboard
- **Region** — Filter all views by region
- **Category** — Filter all views by product category
- **Customer Segment** — Filter by Consumer / Corporate / Home Office
- **Order Date Range** — Filter by date range (2024–2025)
- **Ship Mode** — Filter by shipping method
- **Campaign Channel** — Filter by acquisition source

### Dashboard Actions
- **Filter Action:** Clicking a region on the map filters all other charts to that region
- **Highlight Action:** Hovering over a category highlights corresponding bars in the profitability view
- **URL Action:** Order ID can be used to open order detail (configurable)

---

## Key Business Insights

1. **Technology drives 70.9% of total revenue** (₹1.54B) with the highest margin at 18.2%, making it the most profitable category.
2. **Furniture has the lowest margin at 6.9%**, and sub-categories like Tables and Bookcases frequently generate losses when discounted above 20%.
3. **South region leads in both sales (₹646M) and profit (₹99.9M)**, making it the highest-performing region.
4. **Discounts above 30% consistently generate negative profit** — the average profit for orders with >30% discount is -₹1,601.
5. **Standard Class shipping accounts for 56.6% of orders** but has the longest average delivery time of 4.71 days, risking customer satisfaction.
6. **Furniture has the highest return rate at 7.7%**, compared to Technology (3.0%) and Office Supplies (3.7%).
7. **Home Office segment generates the highest profit** (₹11.6M) despite similar order volumes to Corporate and Consumer.
8. **No-discount orders yield average profits 8x higher** than heavily discounted orders (₹13,203 vs ₹-1,601 at >30% discount).

---

## Dashboard Story Summary

The business is performing strongly in Technology and South region, but faces margin pressure in Furniture due to aggressive discounting. Discount discipline is the single highest-leverage action leadership can take — orders with zero discounts outperform heavily-discounted orders by 8x in profit. Shipping delays in Standard Class and elevated return rates in Furniture are additional risk factors requiring operational attention. Full story: `outputs/dashboard_story.md`.

---

## Assumptions and Limitations

- `order_date` and `ship_date` were stored as Excel serial numbers; converted to date format in Tableau.
- `campaign_channel` contains some null values (~2% of rows); these are excluded from channel-level analysis.
- `delivery_days` is calculated as ship_date minus order_date (not actual delivery confirmation date).
- Same Day deliveries show 0 delivery days, which is expected and treated separately.
- Profit figures are taken as-is from the dataset; cost structure assumptions are not verified against external data.
- The dataset covers India-based operations; regional labels (North/South/East/West) refer to Indian geography.
- Screenshots in the `screenshots/` folder represent the Tableau dashboard views and were captured after building the workbook.

---

## Screenshots Included

| File | Description |
|---|---|
| `screenshots/full_dashboard.png` | Complete executive dashboard with all components |
| `screenshots/sales_trend_view.png` | Monthly sales trend chart (2024–2025) |
| `screenshots/regional_performance_view.png` | Regional and state-level sales/profit map |
| `screenshots/category_profitability_view.png` | Category and sub-category profit margin bars |
| `screenshots/filter_interaction_view.png` | Dashboard with filters applied showing interaction |
