# Smart Delivery Delay Prediction

A machine learning project for predicting delivery delay risk using transaction and logistics data from the DataCo Supply Chain Dataset.

This project was developed as part of an Artificial Intelligence course project and demonstrates an end-to-end machine learning workflow, covering exploratory data analysis, data cleaning, feature engineering, preprocessing, classification modeling, model evaluation, visualization, and interpretation of delivery delay patterns.

---

## Project Overview

Delivery delays can affect customer satisfaction, logistics efficiency, and overall supply chain performance. This project analyzes transaction and logistics data to identify patterns associated with delivery delay risk and develops a machine learning classification model to predict the risk of delivery delays.

The dataset contains **180,519 observations and 53 variables**, with `Late_delivery_risk` used as the target variable.

### Target Variable

| Value | Description |
|---|---|
| `0` | No delivery delay risk |
| `1` | Delivery delay risk |

The project focuses on understanding the characteristics of delivery delays while applying machine learning techniques to a real-world supply chain problem.

---

## Objectives

- Understand the characteristics of supply chain and logistics data.
- Identify patterns associated with delivery delay risk.
- Perform data cleaning and preprocessing.
- Develop meaningful features for analysis and prediction.
- Build a machine learning classification model.
- Evaluate model performance using classification metrics.
- Analyze feature importance.
- Interpret delivery delay patterns from the data.
- Translate analytical results into meaningful logistics insights.

---

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

### Dataset Characteristics

| Item | Description |
|---|---|
| Observations | 180,519 |
| Variables | 53 |
| Target | `Late_delivery_risk` |
| Problem Type | Binary Classification |
| Data Domain | Supply Chain & Logistics |

The original dataset is **not included in this repository**.

---

# Methodology

The project follows an end-to-end machine learning workflow.

## 1. Exploratory Data Analysis

Exploratory Data Analysis (EDA) was performed to understand the structure, distribution, relationships, and patterns within the dataset.

The analysis included:

- Dataset structure and data types
- Missing value inspection
- Target variable distribution
- Shipping duration analysis
- Delivery delay risk by region
- Delivery delay risk by shipping mode
- Delivery delay risk by product category
- Route analysis
- Order hour analysis
- Day-of-week analysis
- Numerical correlation analysis
- Logistics feature correlation analysis
- Pair plot analysis

### Target Distribution

![Target Distribution](assets/target_distribution.png)

The target variable is relatively balanced:

- **45.17%** no delivery delay risk
- **54.83%** delivery delay risk

This indicates that there is no extreme class imbalance in the target variable.

---

## 2. Data Cleaning

The data cleaning process included:

- Checking missing values
- Removing duplicate records
- Removing columns containing sensitive customer information
- Removing observations with missing target values
- Filling missing numerical values using the median
- Filling missing categorical values with `unknown`

These steps were performed to improve data quality before feature engineering and model development.

---

## 3. Feature Engineering

Several additional features were created to support both analysis and prediction.

| Feature | Description |
|---|---|
| `Time_Difference` | Difference between actual and scheduled shipping duration |
| `Profit_Margin` | Profit-related feature derived from profit ratio and product price |
| `Region_Code` | Numerical representation of the order region |
| `Route` | Combination of order city and customer city |
| `Order_Hour` | Hour when the order was placed |
| `Order_DayOfWeek` | Day of the week when the order was placed |

Feature engineering was used to transform the original variables into features that could better represent logistics and temporal patterns.

---

## 4. Data Preprocessing

Numerical and categorical variables were processed using separate preprocessing pipelines.

### Numerical Features

- Median imputation
- Standardization using `StandardScaler`

### Categorical Features

- Most-frequent imputation
- One-hot encoding
- `handle_unknown="ignore"`

The preprocessing workflow was implemented using:

- `Pipeline`
- `ColumnTransformer`

This approach helps maintain a consistent preprocessing workflow between training and testing data.

---

## 5. Machine Learning Model

A **Random Forest Classifier** was used to classify delivery delay risk.

### Model Configuration

```text
n_estimators = 200
random_state = 42
