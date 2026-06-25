# Chart Selection Justification — Executive Sales Dashboard

This document explains the rationale behind each chart type selected for the executive dashboard, covering the business question each chart addresses, design principles applied, and mistakes deliberately avoided.

---

## 1. Sales Trend View — Line Chart (Monthly)

**Business Question Answered:**  
How are total sales and profit changing month over month across 2024–2025? Are there seasonal patterns?

**Why This Chart Type:**  
A line chart is the most appropriate visualisation for continuous time-series data. It communicates directional trends, acceleration, deceleration, and seasonal cycles clearly. Lines connect data points in a way that implies continuity — appropriate here because sales are a continuous measure over time.

**Fields Used:**  
- X-axis: Order Date (aggregated to Month/Year)
- Y-axis (dual axis): SUM(Sales) and SUM(Profit)
- Color: Separate lines for Sales (blue) and Profit (orange) to distinguish the two measures
- Label: Year markers to separate 2024 and 2025 trends

**Design Principle Applied:**  
Dual-axis line chart with a shared X-axis. Both lines share the same time axis for direct temporal comparison. Gridlines are minimised to reduce clutter. Y-axis starts at zero to avoid misleading slope impressions.

**Mistake Avoided:**  
Avoided a bar chart for the trend view — while bars can show time-series data, they fragment visual continuity and make it harder to perceive trend direction. Avoided area charts which can overstate volume differences.

---

## 2. Regional Performance View — Map + Bar Chart

**Business Question Answered:**  
Which regions and states are generating the most sales and profit? Where are the geographic strengths and gaps?

**Why This Chart Type:**  
A filled map (choropleth) is the most intuitive chart for geographic data. Decision-makers immediately relate to spatial distribution — seeing which areas of India are dark (high) vs light (low) communicates regional performance at a glance. The supporting bar chart provides exact values that the map's colour gradient cannot convey precisely.

**Fields Used:**  
- Map: State field (geographic role), colour = SUM(Profit), size = SUM(Sales)
- Bar chart: Region on Y-axis, SUM(Sales) on X-axis, color = Profit Margin (calculated field)
- Tooltip: State, Sales, Profit, Margin on hover

**Design Principle Applied:**  
Sequential single-hue colour scale (light to dark) for the map — avoids misleading divergent colour schemes that imply positive/negative rather than high/low. Bar chart sorted descending by sales so the best-performing region is always at the top — enables fast scanning without reading labels.

**Mistake Avoided:**  
Avoided using a pie chart for regional breakdown — while intuitive for simple proportions, pie charts perform poorly with 4+ segments and cannot convey geographic meaning. Avoided using too many colours on the map (one colour family used, varying in intensity only).

---

## 3. Category Profitability View — Horizontal Bar Chart

**Business Question Answered:**  
Which categories and sub-categories are most profitable? Which are generating losses or thin margins?

**Why This Chart Type:**  
A horizontal bar chart is ideal for categorical comparison where labels (category/sub-category names) need to be readable. Horizontal orientation allows longer labels to sit naturally on the Y-axis without rotation. Sorting by profit margin immediately highlights the best and worst performers.

**Fields Used:**  
- Y-axis: Sub_Category (with Category as a grouping row)
- X-axis: Profit Margin (calculated field: SUM(Profit)/SUM(Sales))
- Color: Diverging colour scale — positive margin = green shades, negative margin = red
- Label: Profit Margin % displayed on each bar

**Design Principle Applied:**  
Diverging colour encoding is applied deliberately here — unlike the map (where all values are positive), profit margin can be negative for some sub-categories (Tables, Bookcases at high discounts). Red/green immediately draws the eye to loss-making areas without requiring the reader to read values. Bars are sorted within each category group by margin descending.

**Mistake Avoided:**  
Avoided a treemap — while treemaps show hierarchy well, they struggle to convey negative values and make direct size comparisons difficult. Avoided stacked bar charts which make it hard to compare sub-category values against a consistent baseline.

---

## 4. Customer Segment View — Grouped Bar Chart

**Business Question Answered:**  
How do the three customer segments (Consumer, Corporate, Home Office) compare on sales, profit, and order volume?

**Why This Chart Type:**  
A grouped bar chart allows direct side-by-side comparison of multiple measures across a small number of categories. With only three segments, the grouping is clean and readable. It enables leadership to compare segments on multiple dimensions without switching between charts.

**Fields Used:**  
- X-axis: Customer Segment
- Y-axis: SUM(Sales), SUM(Profit), and COUNT(Order ID) as separate bars per group
- Color: Distinct hues for each measure (Sales = blue, Profit = teal, Orders = grey)
- Label: Values displayed above each bar

**Design Principle Applied:**  
Consistent colour assignment across the dashboard — Sales is always the same blue regardless of which chart it appears in. This reduces cognitive load for the reader who learns the colour code once and applies it across all views.

**Mistake Avoided:**  
Avoided a pie chart or donut chart for segment breakdown — these are effective only for showing proportional shares, not for comparing absolute values or multiple measures simultaneously. Avoided stacking bars (which would obscure individual measure values).

---

## 5. Shipping Performance View — Bar Chart with Reference Line

**Business Question Answered:**  
Which shipping modes cause the most delays? How does shipping mode relate to total sales and customer satisfaction?

**Why This Chart Type:**  
A bar chart with a reference line is the clearest way to show performance against a benchmark for categorical groups. Showing average delivery days per shipping mode, with a reference line at the overall average (4.71 days), immediately communicates which modes are above or below the business norm.

**Fields Used:**  
- Y-axis: Ship Mode
- X-axis: AVG(Delivery Days) — primary measure; SUM(Sales) — secondary bar (dual axis)
- Color: Ship Mode (distinct colors per mode)
- Reference Line: Overall average delivery days
- Label: Average days displayed on bar ends

**Design Principle Applied:**  
Sorting is critical here — bars are sorted from fastest (Same Day) to slowest (Standard Class), which naturally guides the reader from best to worst performance. The dual-axis presentation allows comparison of speed vs volume without switching views.

**Mistake Avoided:**  
Avoided a scatter plot for this view — while a scatter (delivery days vs sales) could show correlation, it requires cognitive effort and is less readable for an executive audience. Avoided a line chart which implies continuity between shipping modes — they are discrete categories.

---

## 6. Discount vs Profit View — Bar Chart (Discount Tier)

**Business Question Answered:**  
What is the relationship between discount level and average profit? At what point does discounting become loss-making?

**Why This Chart Type:**  
A bar chart using the Discount Tier calculated field shows average profit per discount band clearly. This is preferable to a scatter plot for an executive dashboard because it aggregates the relationship into digestible categories rather than showing thousands of individual data points. The pattern (decreasing bars across tiers) tells the story immediately.

**Fields Used:**  
- X-axis: Discount Tier (calculated field: No Discount, Low, Medium, High, Very High)
- Y-axis: AVG(Profit)
- Color: Diverging scale — green for profitable tiers, red for loss-making tier (>30% discount)
- Label: Average profit value and order count displayed inside/above each bar
- Reference Line: Zero profit line to clearly demarcate profitable vs loss-making zones

**Design Principle Applied:**  
The zero reference line is the most important design choice here — it transforms a simple bar chart into a decision-support tool. Leaders immediately see which discount tiers cross into negative territory. Sorting is fixed from No Discount to Very High (left to right) to reinforce the directional narrative.

**Mistake Avoided:**  
Avoided a scatter plot (Discount % vs Profit for individual orders) — while statistically rigorous, 4,200 individual points would create overplotting and make the pattern harder to read for a non-technical audience. Avoided a line chart which would imply that discount tiers are continuous rather than categorical buckets.

---

## 7. Return Analysis View — Bar Chart (Return Rate)

**Business Question Answered:**  
Which categories and customer segments have the highest return rates? Where is return risk concentrated?

**Why This Chart Type:**  
A horizontal bar chart showing return rate (%) by category and then by segment is the clearest way to compare discrete groups on a rate metric. The percentage framing (rather than absolute return count) is essential for fair comparison across categories of different sizes.

**Fields Used:**  
- Y-axis: Category (primary view), Customer Segment (secondary view)
- X-axis: Return Rate (calculated field: SUM([Return Flag]) / COUNT([Order ID]))
- Color: Single color with intensity encoding (darker = higher return rate) — avoids distracting multi-color schemes for a single measure
- Label: Return rate percentage and absolute return count displayed on bars
- Reference Line: Overall return rate (4.5%) for benchmark comparison

**Design Principle Applied:**  
The reference line at the overall return rate is critical context. Without it, a 7.7% Furniture return rate is just a number. With the 4.5% overall average as reference, it becomes immediately visible that Furniture is 71% above the business average — a quantified risk signal. Bars sorted descending by return rate (highest risk at top).

**Mistake Avoided:**  
Avoided showing absolute return counts without normalising to rate — Furniture has fewer total orders than Office Supplies, so raw counts would be misleading. Avoided a pie chart which cannot show rates clearly and struggles with reference lines.

---

## General Dashboard Design Principles Applied

### Color Consistency
Each measure has a fixed color across all charts (Sales = blue, Profit = teal/green, Returns = red-orange). This reduces the cognitive effort required to read multiple charts on the same dashboard.

### Minimal Clutter
Gridlines are set to light grey and used sparingly. Background is white/light grey. Chart borders are removed. Axis titles are concise. Tooltips provide additional detail on hover rather than cluttering the chart face.

### Sorting
All bar charts are sorted by the primary measure (descending) unless a specific ordering tells a better story (e.g., Discount Tier sorted by tier level, not by profit value).

### Titles and Labels
Every chart has a clear, action-oriented title (e.g., "Furniture Margin Drags Portfolio Performance" rather than "Category Profitability"). KPI cards display large, bold numbers with a descriptive subtitle.

### Interactivity
Dashboard filters (Region, Category, Segment, Date, Ship Mode) apply to all sheets simultaneously. A filter action is set so clicking a region on the map filters all other charts — enabling drill-down exploration without leaving the dashboard.
