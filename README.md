# Decoding Connecticut’s Property Landscape: Trends, Segments, and Price Behaviors (2001–2022)
This is my personal project to learn how to build a customer segmentation. The main showcase of this project is an RFM segmentation that will change dynamically based on the selected transaction period towards trends, segments, and price behaviors for over a decade (2001-2022) in landscape of property. The data is aquired from [data.gov](https://catalog.data.gov/dataset/real-estate-sales-2001-2018). This dataset captures property sales across Connecticut from 2001 to 2022. Each record includes the sale price (Sale Amount), the tax assessment (Assessed Value), the town, property type, and the transaction date. A key derived measure is the Sales Ratio - sale price divided by assessed value, useful for comparing market prices with assessments and analyzing trends by time, town, and property category. 
![Preview](https://github.com/Catherinerezi/Connecticut-Property-Landscape-2001-2022/blob/main/assets/property_landscare_dasboard.png)

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
1. How is the distribution of properties based on RFM scores, and which segment most dominates the current property portfolio?

The line chart belows traces Connecticut’s property market from the early 2000s to 2022 and shows a long upward trajectory punctuated by short-lived dips, before culminating in a clear peak around 2021–2022. Over the full window, cumulative growth reaches +145.82%, consistent with a cycle propelled by ultra-low Federal Reserve rates and a work-from-home migration out of New York City that boosted suburban demand. The curve then bends downward after the peak, signalling that price momentum has eased and that the market has transitioned from rapid appreciation to consolidation.

<p align="center">
  <img src="assets/line%20chart.png" alt="How Property Sale Prices Have Evolved Over the Years" width="400">
</p>

**Current conditions (2025).** As borrowing costs have risen, affordability has tightened and both transaction volumes and price gains have cooled noticeably. The cooling is not uniform: higher-priced segments are typically more rate-sensitive, while mid-market family housing and rental-grade assets tend to adjust more gradually. Monitoring the **Sales Ratio** (sale amount / assessed value) alongside town and property-type splits helps distinguish cyclical softening from structural resilience.

**Strategic direction.** In a high interest rate era, prioritise the most resilient segments: towns with diversified employment bases, mid-price brackets with persistent user demand, and properties with defensible rental yields. Use RFM based portfolio segmentation to identify “champion” and “loyal” cohorts that continue to transact despite tighter credit, and track how their Sales Ratios evolve relative to assessments. Practical next steps include higher stress for testing prices under alternative rate scenarios, deepening the level of the city, drill downs to separate premium from value markets, and refreshing dashboards to highlight segments where liquidity and pricing remain robust.

2. How does the average property sale price evolve year on year, and are there patterns that could inform future investment or development decisions?
4. Which cities have the highest volumes of property transactions, and how does their distribution indicate market potential or dynamics?
5. How is the distribution of property prices in the most transaction-active cities, and which cities tend to have premium property markets or lower-middle-income markets?
6. Is there a strong relationship between sale price, assessed value, and the sales ratio that can be used as indicators for valuation or pricing strategy?
