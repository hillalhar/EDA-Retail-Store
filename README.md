# Retail Sales Forecasting

This project involves analyzing and forecasting weekly sales for various departments across multiple retail stores. Using historical sales data that includes store information, promotional markdowns, and holiday events, a machine learning model is developed to predict future sales accurately.

## 📌 Project Summary

The goal of this project is to build a predictive model for a large retailer to forecast their weekly sales. Accurate sales forecasting is essential for various business operations, including inventory management, staffing, and marketing campaign planning. This project explores a dataset that combines sales figures with external factors like economic indicators and holiday schedules. A Random Forest Regressor is trained to capture the complex interactions between these features and predict weekly sales.

## 💾 Dataset

The project utilizes three separate datasets that are merged for a comprehensive analysis:

1.  **`sales.csv`**: Contains historical sales data for each department within each store.
    - `Store`: The store number.
    - `Dept`: The department number.
    - `Date`: The week of the sales record.
    - `Weekly_Sales`: The total sales for the given department in the given store for that week (the target variable).
    - `IsHoliday`: A boolean indicating if the week is a special holiday week.

2.  **`stores.csv`**: Contains supplementary information about each store.
    - `Store`: The store number.
    - `Type`: The type of store (A, B, or C).
    - `Size`: The size of the store.

3.  **`features.csv`**: Contains additional external data for each store on a given date.
    - `Store`: The store number.
    - `Date`: The week.
    - `Temperature`: The average temperature in the region.
    - `Fuel_Price`: The cost of fuel in the region.
    - `MarkDown1-5`: Anonymized data related to promotional markdowns.
    - `CPI`: The Consumer Price Index.
    - `Unemployment`: The unemployment rate.
    - `IsHoliday`: A boolean indicating if the week is a holiday week.

## ⚙️ Methodology

The project follows a structured approach to build a robust forecasting model.

### 1. Data Loading and Merging
- The three data files (`sales.csv`, `stores.csv`, `features.csv`) are loaded into pandas DataFrames.
- These DataFrames are then merged into a single, unified dataset based on the `Store` and `Date` columns.

### 2. Data Preprocessing
- **Handling Missing Values**: The `MarkDown` columns contain a significant number of missing values. These `NaN`s are replaced with `0`, assuming that a missing markdown value means no promotion was active.
- **Date Conversion**: The `Date` column is converted from an object type to a datetime object to enable time-based feature extraction.

### 3. Exploratory Data Analysis (EDA)
- **Sales Distribution**: Analysis of the `Weekly_Sales` column reveals its distribution and identifies any outliers or unusual patterns.
- **Sales Over Time**: The overall weekly sales are plotted over time to visualize trends and seasonality.
- **Holiday Impact**: The analysis shows a significant spike in sales during the Christmas season and notable increases during other holiday weeks (like Thanksgiving).
- **Store and Department Performance**: Sales data is aggregated to compare performance across different store types, sizes, and departments.

### 4. Feature Engineering
To help the model better understand the time-based patterns, new features are extracted from the `Date` column:
- `Week`: The week number of the year.
- `Year`: The year of the sales record.

### 5. Model Development and Evaluation
- **Model Selection**: A **Random Forest Regressor** is chosen for its robustness, ability to handle complex interactions between features, and resistance to overfitting.
- **Feature Selection**: Relevant features are selected for training, and the target variable is defined as `Weekly_Sales`.
- **Data Splitting**: The dataset is split into training and testing sets to evaluate the model's performance on unseen data.
- **Evaluation Metric**: The model is evaluated using the **Weighted Mean Absolute Error (WMAE)**. This metric is particularly useful for retail forecasting as it allows for giving more weight to certain periods, such as holiday weeks. The WMAE is calculated as:
  $$ WMAE = \frac{1}{\sum w_i} \sum_{i=1}^{n} w_i |y_i - \hat{y}_i| $$
  where `w_i` is 5 for holiday weeks and 1 otherwise.

## 📊 Results

The Random Forest model was successfully trained and evaluated. The feature importance analysis from the model revealed that the most critical predictors of weekly sales were **department**, **store size**, **store type**, and the **week of the year**. The model achieved a competitive WMAE score on the test set, demonstrating its effectiveness in forecasting weekly retail sales based on the provided features.
- `scikit-learn`

You can install all necessary packages by creating a `requirements.txt` file and running `pip install -r requirements.txt`.
