# Exploratory Data Analysis of Retail Sales

This project performs a comprehensive Exploratory Data Analysis (EDA) on a historical dataset of weekly sales from a large retailer. The goal is to uncover insights, identify trends, and understand the key factors that influence sales across different stores and departments without building a predictive model.

## 📌 Project Overview

This notebook focuses on a deep-dive analysis of retail sales data. The objective is to understand the patterns and relationships between weekly sales and various internal and external factors, such as store type, holidays, and economic indicators. By visualizing and summarizing the data, this analysis provides crucial business insights and lays the groundwork for any future forecasting projects.

## 💾 Dataset

The project utilizes three separate datasets that are merged for a comprehensive analysis:

1.  **`sales.csv`**: Contains historical sales data for each department within each store.
    - `Store`, `Dept`, `Date`, `Weekly_Sales`, `IsHoliday`.

2.  **`stores.csv`**: Contains supplementary information about each store.
    - `Store`, `Type`, `Size`.

3.  **`features.csv`**: Contains additional external data for each store on a given date.
    - `Store`, `Date`, `Temperature`, `Fuel_Price`, `MarkDown1-5`, `CPI`, `Unemployment`, `IsHoliday`.

## ⚙️ Analysis Workflow

The project follows a structured approach to explore and understand the data.

### 1. Data Loading and Merging
- The three data files (`sales.csv`, `stores.csv`, `features.csv`) are loaded into pandas DataFrames.
- These DataFrames are then merged into a single, unified dataset based on the `Store` and `Date` columns.

### 2. Data Preprocessing
- **Handling Missing Values**: The `MarkDown` columns contain a significant number of missing values. These `NaN`s are replaced with `0`, assuming that a missing markdown value indicates no promotional activity.
- **Date Conversion**: The `Date` column is converted to a datetime object to enable time-based analysis.

### 3. Exploratory Data Analysis (EDA)
The core of the project is the detailed analysis and visualization of the data to extract insights:
- **Sales Distribution Analysis**: The distribution of the `Weekly_Sales` column is examined to understand the range and concentration of sales values.
- **Time Series Analysis**: Sales are plotted over time to identify overall trends, seasonality, and significant events.
- **Holiday Impact Analysis**: The effect of holiday weeks on sales is investigated, confirming that special holidays (especially the Christmas season) are major drivers of revenue.
- **Store and Department Performance**: Sales are aggregated by store `Type`, `Size`, and `Dept` to compare performance and identify top-performing categories.
- **Correlation with External Factors**: The relationships between `Weekly_Sales` and external economic indicators like `Unemployment`, `CPI`, and `Fuel_Price` are analyzed to see how they correlate with consumer spending.

## 📊 Key Findings

The analysis of the retail data revealed several key insights:
- **Strong Seasonality**: Sales show a clear seasonal pattern, with significant peaks during the Q4 holiday season (Thanksgiving and Christmas). The week of Christmas is consistently the highest-grossing period.
- **Impact of Store Type**: Store `Type 'A'` consistently generates the highest volume of sales compared to types 'B' and 'C'.
- **Markdown Influence**: Promotional markdowns have a visible impact on sales, though the effect varies depending on the type and timing of the promotion.
