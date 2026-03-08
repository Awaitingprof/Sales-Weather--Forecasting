# Sales-Weather--Forecasting
Forecasting product sales based on weather conditions and historical demand using Decision Tree Regression in Python.

## Overview
This project tackles a real-world retail analytics problem:
How do weather conditions and past demand patterns impact sales performance?

By applying a regression model, the goal is to predict future sales, identify the most important drivers (weather variables, seasonality, past demand), and provide insights for better inventory planning, promotions, and business decisions.

## Dataset
The dataset contains store-level daily sales data enriched with weather information.

**Columns**
1. STORE_ID (string) : The Unique store identifier
2. STORE_NAME (string) : The Store name
3. CITY (string) : The City where the store is located
4. COUNTRY (string): The Country of the store
5. PRODUCT_ID (string): The Unique product identifier
6. PRODUCT_NAME (string): The Name of the product
7. CATEGORY (string): The Product category
8. SALES_DATE (datetime): The Date of the sales record
9. TOTAL_UNITS_SOLD (int): The number of units sold (Target variable)
10. TOTAL_REVENUE (float): The revenue generated
11. AVG_UNIT_PRICE (float): The average unit price of the product
12. AVG_TEMP (float): The average daily temperature
13. MAX_TEMP (float): The maximum daily temperature
14. MIN_TEMP (float): The minimum daily temperature
15. AVG_SUNSHINE (float): The average sunshine hours
16. AVG_WEATHER_CODE (int): The encoded weather condition

Engineered features: rolling averages, rolling sums, lagged sales, and seasonal encodings (month_sin, weekday_cos, etc.)

## Objectives
-Preprocess both categorical and numerical features for model training.
-Train a Decision Tree Regressor to predict TOTAL_UNITS_SOLD.
-Evaluate performance using metrics such as RMSE, MAE, and R².
-Identify key features (weather and historical demand) that most influence sales.
-Provide interpretable business insights on how weather impacts demand.

## ⚙️ Methods

1. **Data Pre-processing**
-Convert SALES_DATE to datetime and extract year, month, day, weekday.
-Encode seasonal patterns using sine/cosine transformations.
-Generate lag features (previous day/week sales) and rolling averages.
-Encode categorical variables (CITY, CATEGORY, etc.).
-Scale numeric features and handle missing values.

2. **Modelling**
-Decision Tree Regressor (scikit-learn) for faster training.
-Chronological train/test split (80% train, 20% test).
-Pipeline: preprocessing + model training.

3. **Evaluation**
-Metrics: RMSE, MAE, R²
-Plot: Actual vs Predicted sales curve
-Feature importance ranking

4. **Interpretation**
-Identify whether past demand or weather conditions are stronger predictors.
-Understand the role of seasonality (weekdays, months).
-Provide actionable business insights.

**Results**
-Evaluation Metrics:
RMSE: 1.63
MAE: 0.78
R²: 0.93

This means the model explains ~93% of the variance in sales and makes predictions with very low error.

## Top Feature Importances:
-Rolling average sales (past 7 days)
-Lagged sales (previous day, previous week)
-Average temperature and sunshine hours
-Weekday/month seasonality

### Business Insight:
-Sales are most strongly influenced by recent purchase patterns.
-Weather factors (temperature & sunshine) play a significant role in shaping demand.
-Seasonal trends (day of week, month) add extra predictive power.

### Technologies Used
-Python (pandas, numpy, scikit-learn, matplotlib, seaborn)
-Jupyter Notebook
-Joblib (for saving trained models)

### Responsible AI
-Predictions are only as good as the input data (e.g., unusual weather events may reduce accuracy).
-Model should not be used for financial/legal decisions without human oversight.
-Bias in weather or store data (e.g., limited to one country/region) may reduce generalization.

#### Intended for research, education, and retail analytics experiments only.


### License

This project is licensed under the MIT License.

#### References
-scikit-learn documentation
-Time Series Forecasting with Machine Learning
-Kaggle retail sales datasets
-Research on weather impact in retail analytics
