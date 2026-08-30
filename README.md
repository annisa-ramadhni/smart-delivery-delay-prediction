# Smart Delivery Delay Prediction

A machine learning project for predicting delivery delay risk using transaction and logistics data from the DataCo Supply Chain Dataset.

## Project Overview

This project analyzes delivery delay risk using transaction, logistics, customer, product, regional, and order-time information.

The dataset contains 180,519 observations and 53 variables. The analysis covers exploratory data analysis, data cleaning, feature engineering, data preprocessing, machine learning modeling, model evaluation, and interpretation of the results.

The target variable is `Late_delivery_risk`, where 0 represents no delivery delay risk and 1 represents delivery delay risk.

## Objectives

- Understand the characteristics of transaction and logistics data.
- Identify patterns related to delivery delay risk.
- Perform data cleaning and preprocessing.
- Create additional features that support the analysis.
- Build a machine learning model to predict delivery delay risk.
- Evaluate model performance using classification metrics.
- Generate insights from factors related to delivery delays.

## Dataset

The project uses the **DataCo Supply Chain Dataset** from Kaggle.

The dataset contains information related to transactions, customers, products, orders, shipping, regions, and delivery performance.

### Target Variable

| Variable | Description |
|---|---|
| `Late_delivery_risk` | Indicator of delivery delay risk (0 = no delay risk, 1 = delay risk) |

### Selected Variables

| Variable | Description |
|---|---|
| `Days for shipping (real)` | Actual shipping duration |
| `Days for shipment (scheduled)` | Scheduled shipping duration |
| `Benefit per order` | Benefit generated per order |
| `Sales per customer` | Sales value per customer |
| `Order Item Quantity` | Quantity of products in an order |
| `Order Item Discount` | Discount amount |
| `Order Item Discount Rate` | Discount rate |
| `Order Item Product Price` | Product price |
| `Order Item Profit Ratio` | Product profit ratio |
| `Customer City` | Customer city |
| `Customer Country` | Customer country |
| `Order Region` | Order destination region |
| `Order State` | Order destination state |
| `Order Status` | Order status |

## Methodology

The analysis was conducted through several stages.

### 1. Data Collection

The DataCo Supply Chain Dataset was loaded into Google Colab using Python and Pandas.

### 2. Exploratory Data Analysis

Exploratory data analysis was performed to understand the structure and characteristics of the dataset. The analysis included:

- Dataset structure and data types.
- Missing value inspection.
- Target variable distribution.
- Distribution of actual and scheduled shipping duration.
- Shipping duration based on delivery delay risk.
- Difference between actual and scheduled shipping duration.
- Delivery delay risk by region.
- Delivery delay risk by route.
- Customer city analysis.
- Product category analysis.
- Correlation analysis of numerical variables.
- Logistics feature correlation.
- Pair plot analysis.

### 3. Data Cleaning

The data cleaning process included:

- Checking missing values.
- Removing duplicate records.
- Removing columns containing sensitive customer information.
- Removing observations with missing target values.
- Filling missing numerical values using the median.
- Filling missing categorical values with `unknown`.

### 4. Feature Engineering

Several additional features were created to support the analysis:

- `Time_Difference` to measure the difference between actual and scheduled shipping duration.
- `Profit_Margin` to represent profit based on profit ratio and product price.
- `Region_Code` as a numerical representation of the order region.
- `Route` by combining the order city and customer city.
- `Order_Hour` to represent the hour when an order was placed.
- `Order_DayOfWeek` to represent the day of the week when an order was placed.

### 5. Data Preprocessing

Numerical features were processed using median imputation and `StandardScaler`.

Categorical features were processed using:

- Most-frequent imputation.
- One-hot encoding.
- `handle_unknown="ignore"` to handle unseen categories during prediction.

The preprocessing steps were implemented using `Pipeline` and `ColumnTransformer`.

### 6. Model Development

A **Random Forest Classifier** was used to predict delivery delay risk.

The model configuration included:

- `n_estimators = 200`
- `random_state = 42`

The dataset was divided into training and testing sets using an 80:20 split with stratification.

### 7. Model Evaluation

The model was evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

## Results

The Random Forest model achieved an accuracy of **1.00** on the test set used in the project.

The classification report produced precision, recall, and F1-score values of **1.00** for both target classes.

A confusion matrix was also used to examine the model's predictions against the actual target classes.

The very high evaluation result should be considered together with the selected features, especially variables that are closely related to delivery delay information.

## Insights

The analysis produced several insights related to delivery delay patterns.

### Insight 1 — Time Difference

`Time_Difference` measures the difference between actual shipping duration and scheduled shipping duration. This feature helps describe whether an order was delivered faster or took longer than the scheduled duration.

### Insight 2 — Delivery Delay Risk by Region

Delivery delay risk was analyzed across different `Order Region` values to identify regional differences in delivery risk.

### Insight 3 — Delivery Delay Risk by Shipping Mode

Different shipping modes were compared to examine variations in delivery delay risk.

### Insight 4 — Delivery Delay Risk by Product Category

Product categories were compared based on their average `Late_delivery_risk` to identify categories with higher delivery delay risk.

### Insight 5 — Delivery Delay Risk by Route

Routes were created by combining the order city and customer city. The analysis was used to identify routes associated with higher delivery delay risk.

### Insight 6 — Order Hour

Order time was analyzed to examine delivery delay risk across different order hours.

### Insight 7 — Day of the Week

Order days were analyzed to observe delivery delay risk across different days of the week.

## My Contributions

My contributions to this group project included:

- Developing the problem statement, objectives, and project benefits.
- Managing Google Drive mounting and dataset access in Google Colab.
- Conducting exploratory data analysis on the dataset structure.
- Performing correlation analysis using numerical heatmaps, logistics feature heatmaps, and pair plots.
- Conducting the data cleaning process, including missing value inspection, duplicate removal, sensitive column removal, and numerical and categorical missing value handling.
- Developing and explaining Insights 5–7 covering delivery routes, order hours, and days of the week.
- Creating the code and visualizations used for Insights 5–7.
- Contributing to the interpretation of the analysis results.

## Tools and Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Google Colab

## Project Structure

```text
smart-delivery-delay-prediction/
│
├── README.md
├── smart_delivery_delay_prediction.ipynb
└── .gitignore
