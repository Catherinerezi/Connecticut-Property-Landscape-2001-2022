# Decoding Connecticut’s Property Landscape: Trends, Segments, and Price Behaviors (2001–2022)
This is my personal project to learn how to build a customer segmentation. The main showcase of this project is an RFM segmentation that will change dynamically based on the selected transaction period towards trends, segments, and price behaviors for over a decade (2001-2022) in landscape of property. The data is aquired from [data.gov](https://catalog.data.gov/dataset/real-estate-sales-2001-2018). This dataset captures property sales across Connecticut from 2001 to 2022. Each record includes the sale price (Sale Amount), the tax assessment (Assessed Value), the town, property type, and the transaction date. A key derived measure is the Sales Ratio - sale price divided by assessed value, useful for comparing market prices with assessments and analyzing trends by time, town, and property category. 

<p align="center">
  <img src="https://github.com/Catherinerezi/Connecticut-Property-Landscape-2001-2022/blob/main/assets/property_landscare_dasboard.png" alt="Dashboard preview" width="500">
</p>

# Attachments
- [Data processing (indonesian)](https://colab.research.google.com/drive/17JmBtTshNQwTCpHCfeGvTGX-6js-4aA7?usp=sharing)
- [Dashboard page](https://drive.google.com/file/d/1kqYnjQaiVn0FSfuC5GkQbQNClw3-B0PT/view?usp=share_link)

# Data Preprocessing
The following are steps I took to prepare the dataset before loading it into Power BI:

Data types & formatting:
- Cast numeric and date fields to proper types (e.g., Sale Amount, Assessed Value (numeric); Date Recorded (datetime); List Year (integer)).
- Standardize calculated fields (Sales Ratio, transaction_value) to a consistent numeric format.

Missing values:
- Drop columns with more than 20% missing values.
- Ensure completeness for essential fields only: sale amount, assessed value, transaction date, location (town), and property type.

Outlier assessment:
- Profile the distributions of Sale Amount and Assessed Value.
- Retain outliers since they represent <20% of observations and are considered contextually reasonable.

Property-level aggregation:
- Group records by Serial Number to eliminate duplicates.
- Compute aggregates: total sale amount, average sales ratio, sale frequency, and transaction time span (first/last dates).

External RFM merge
- Join RFM scoring results into the property summary (property_summary) on Serial Number.
- Preserve Serial Number as the stable key even when address-level rows are aggregated.

Finalization for visualization
- Output a clean, analysis-ready file: property_summary_clean.csv with structured columns.
- Remove duplicate column names and validate joins to support smooth, interactive exploration in Power BI.

# Explanatory Data Analysis Visualizations Carried Out

Visualization Type Purpose:
## 1. How does the average property sale price evolve year on year, and are there patterns that could inform future investment or development decisions?

The line chart belows traces Connecticut’s property market from the early 2000s to 2022 and shows a long upward trajectory punctuated by short-lived dips, before culminating in a clear peak around 2021–2022. Over the full window, cumulative growth reaches +145.82%, consistent with a cycle propelled by ultra-low Federal Reserve rates and a work-from-home migration out of New York City that boosted suburban demand. The curve then bends downward after the peak, signalling that price momentum has eased and that the market has transitioned from rapid appreciation to consolidation.

<p align="center">
  <img src="assets/line%20chart.png" alt="How Property Sale Prices Have Evolved Over the Years" width="400">
</p>

**Current conditions (2025).** As borrowing costs have risen, affordability has tightened and both transaction volumes and price gains have cooled noticeably. The cooling is not uniform: higher-priced segments are typically more rate-sensitive, while mid-market family housing and rental-grade assets tend to adjust more gradually. Monitoring the **Sales Ratio** (sale amount / assessed value) alongside town and property-type splits helps distinguish cyclical softening from structural resilience.

**Strategic direction.** In a high interest rate era, prioritise the most resilient segments: towns with diversified employment bases, mid-price brackets with persistent user demand, and properties with defensible rental yields. Use RFM based portfolio segmentation to identify “champion” and “loyal” cohorts that continue to transact despite tighter credit, and track how their Sales Ratios evolve relative to assessments. Practical next steps include higher stress for testing prices under alternative rate scenarios, deepening the level of the city, drill downs to separate premium from value markets, and refreshing dashboards to highlight segments where liquidity and pricing remain robust.

## 2. How is the distribution of properties based on RFM scores, and which segment most dominates the current property portfolio?

The pie chart below shows the portfolio’s unit distribution by RFM segment. While “Others” accounts for the largest share of properties by count, the “Best” and “Loyal” segments punch well above their weight, contributing a disproportionate share of total sales value thanks to higher average transaction amounts and healthier Sales Ratios. The “At Risk” cohort still represents a sizable block of inventory, indicating meaningful reactivation potential if pricing and outreach are tuned correctly.

<p align="center">
  <img src="https://github.com/Catherinerezi/Connecticut-Property-Landscape-2001-2022/blob/main/assets/pie_chart.png" alt="HHow is the distribution of properties based on RFM scores, and which segment most dominates the current property portfolio" width="300">
</p>

**Primary Target: $200k–$500k**. This bracket is the market’s sweet spot: it dominates both transaction volume and aggregate sales, offering strong liquidity with acceptable margins. Listings in this band tend to clear faster, attract broader buyer pools, and remain resilient as rates fluctuate.

**Strategic Recommendations:**
- Prioritize “Best” & “Loyal” in $200k–$500k: Concentrate inventory, marketing spend, and agent capacity here. Use targeted campaigns, faster underwriting/pre-approval flows, and tight SLA on showings and closings.
- Secondary Opportunity “At Risk”: Run re-engagement plays (time based bound incentives, payment plans, light CapEx refreshes) to convert dormant demand, while monitoring churn risk and Sales Ratio slippage.
- Don’t ignore “Others”: Nurture this pool with education, post sale service, and upgrade paths to graduate promising leads into the “Loyal” tier.
- Operational cadence: Track conversion rate, time on market, and 'Sales Ratio' by segment and price band making refresh RFM scores on a regular schedule is mandatory to keep targeting precise.
- Geo focus: Emphasize towns where $200k–$500k already concentrates transactions, and be selective in premium niches unless yield/absorption are clearly met.

## 3. Which cities have the highest volumes of property transactions, and how does their distribution indicate market potential or dynamics?

The visuals on below combine a pivot table of total sales by RFM segment and city with a bar chart of price category distribution for the top five towns. Together, they show where value is created and at what price bands transactions actually clear.

<p align="center">
  <img src="https://github.com/Catherinerezi/Connecticut-Property-Landscape-2001-2022/blob/main/assets/table.png" alt="Which cities have the highest volumes of property transactions, and how does their distribution indicate market potential or dynamics" width="400">
</p>

<p align="center">
  <img src="https://github.com/Catherinerezi/Connecticut-Property-Landscape-2001-2022/blob/main/assets/stacked_bar.png" alt="Which cities have the highest volumes of property transactions, and how does their distribution indicate market potential or dynamics" width="500">
</p>

**Market epicenters: Stamford & Norwalk.**
These two cities lead on total sales value and host a high concentration of “Best” and “Loyal” customers. Their mix skews more heavily toward the $500k–$1M+ tiers than peers, which lifts aggregate sales despite fewer units than "high volume" or "lower-priced" markets. Stamford, in particular, shows strength across segments, suggesting a broad based demand rather than single-price-point story.

**Volume anchors: Bridgeport & New Haven.**
These markets contribute substantial unit volume, with transactions concentrated in the sub-$500k bands. Liquidity is stronger here, which is useful for rapid turnover, entry level buyers friendly, and plays good for reactivation for the “At Risk” segment.

**Mid-market stability: Waterbury (and similar profiles).**
A pronounced concentration in the $200k–$500k range supports steady absorption and predictable Sales Ratios, making these towns reliable for sales pipeline health and inventory rotation.

**Development opportunities.**
- Primary priority: Double down on Stamford, allocate inventory and marketing to segments with proven conversion (especially “Best”/“Loyal”) across the $200k–$1M+ spectrum.
- Next wave: Expand selectively in Norwalk and scout adjacent towns exhibiting rising shares of “Best”/“Loyal” buyers and healthy Sales Ratios within $200k–$500k.
- Operational focus: Track segment mix, price absorption, real time market, and Sales Ratio by city to tune promotions, financing options, and agent capacity where they yield the highest ROI.

## 4. Is there a strong relationship between sale price, assessed value, and the sales ratio that can be used as indicators for valuation or pricing strategy?

The heatmap below summarizes the relationships among Sale Amount, Assessed Value, and the Sales Ratio (sale price ÷ assessed value). Overall, municipal tax assessments appear directionally aligned with market prices: where assessed values are higher, sale prices tend to be higher as well, indicating that the valuation framework broadly tracks underlying market conditions. The association is not uniform across all towns or property types, but it is sufficiently consistent to support comparative analysis and benchmarking.

At the same time, the chart highlights pockets of dispersion, locations, and sub segments where the Sales Ratio deviates materially from peers. These outliers signal opportunities for targeted reassessment to improve tax equity and valuation fidelity. Typical drivers include rapid micro market shifts, heterogeneous property features not fully captured in historical assessments, and cyclical effects in premium or very low price bands.

**What this means operationally:**
- Use the Sales Ratio distribution (by town and property type) to flag properties for review, e.g., ratios persistently > 1.3 or < 0.7, or clusters that diverge from local norms.
- Refit valuations with recent comparable sales, and supplement with features such as age, lot size, renovations, and amenity scores to reduce bias.
- Monitor correlation stability over time as a weakening link between assessed and transacted values in a locality is an early warning for drift.
- Report a concise dashboard: median Sales Ratio, interquartile range, and share of outliers, refreshed quarterly, to guide reassessment queues.

In short, tax valuations are generally accurate at a system level, but in data driven, locality specific review process, should be guided by the observed correlations, and the Sales Ratio would sharpen fairness and align assessments more closely with current market reality.

6. How is the distribution of property prices in the most transaction-active cities, and which cities tend to have premium property markets or lower-middle-income markets?
