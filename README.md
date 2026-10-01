# Smart Delivery Delay Prediction

A machine learning project for predicting delivery delay risk using transaction and logistics data from the DataCo Supply Chain Dataset.

This project was developed as part of an Artificial Intelligence course project and focuses on exploratory data analysis, data preprocessing, feature engineering, machine learning, model evaluation, and interpretation of delivery delay patterns.

## Project Overview

Delivery delays can affect customer satisfaction, logistics efficiency, and overall supply chain performance. This project analyzes transaction and logistics data to identify patterns associated with delivery delay risk and build a classification model.

The dataset contains **180,519 observations and 53 variables**, with `Late_delivery_risk` used as the target variable.

- `0` → No delivery delay risk
- `1` → Delivery delay risk

## Objectives

- Understand the characteristics of supply chain and logistics data.
- Identify patterns associated with delivery delay risk.
- Perform data cleaning and preprocessing.
- Develop meaningful features for analysis and prediction.
- Build a machine learning classification model.
- Evaluate model performance using classification metrics.
- Interpret important features and delivery delay patterns.

## Dataset

The project uses the **DataCo Supply Chain Dataset** from Kaggle.

The dataset contains information related to:

- Transactions
- Customers
- Products
- Orders
- Shipping
- Regions
- Delivery performance

### Target Variable

| Variable | Description |
|---|---|
| `Late_delivery_risk` | Indicator of delivery delay risk (0 = no delay risk, 1 = delivery delay risk) |

The original dataset is not included in this repository.

## Methodology

### 1. Exploratory Data Analysis

The dataset was explored to understand its structure, distributions, relationships, and delivery delay patterns.

The analysis included:

- Dataset structure and data types
- Missing value inspection
- Target distribution
- Shipping duration analysis
- Delivery delay risk by region
- Delivery delay risk by shipping mode
- Delivery delay risk by product category
- Route analysis
- Order hour analysis
- Day-of-week analysis
- Correlation analysis

### 2. Data Cleaning

The data cleaning process included:

- Checking missing values
- Removing duplicate records
- Removing columns containing sensitive customer information
- Removing observations with missing target values
- Filling missing numerical values using the median
- Filling missing categorical values with `unknown`

### 3. Feature Engineering

Several features were created to support the analysis:

| Feature | Description |
|---|---|
| `Time_Difference` | Difference between actual and scheduled shipping duration |
| `Profit_Margin` | Profit-related feature derived from profit ratio and product price |
| `Region_Code` | Numerical representation of order region |
| `Route` | Combination of order city and customer city |
| `Order_Hour` | Hour when the order was placed |
| `Order_DayOfWeek` | Day of the week when the order was placed |

### 4. Data Preprocessing

Numerical features were processed using:

- Median imputation
- `StandardScaler`

Categorical features were processed using:

- Most-frequent imputation
- One-hot encoding
- `handle_unknown="ignore"`

The preprocessing workflow was implemented using `Pipeline` and `ColumnTransformer`.

### 5. Machine Learning Model

A **Random Forest Classifier** was used for delivery delay risk classification.

Model configuration:

```text
n_estimators = 200
random_state = 42
