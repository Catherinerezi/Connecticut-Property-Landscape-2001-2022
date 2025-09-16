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
