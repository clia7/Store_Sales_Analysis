# Store Sales – Time Series Forecasting

## Project Overview

This project explores the **Store Sales – Time Series Forecasting** Kaggle competition. The objective is to predict daily sales for different product families across multiple stores in Ecuador.

The project covers the complete data analysis and machine learning workflow, including:

- Exploratory Data Analysis (EDA)
- Data cleaning and preprocessing
- Data integration and feature engineering
- Time-based validation
- Machine learning model development
- Model evaluation and comparison
- Kaggle submission

The main focus was not only on building a predictive model, but also on understanding the underlying data, identifying meaningful patterns, and developing a structured analytical workflow.

## Competition

**Kaggle:** [Store Sales – Time Series Forecasting](https://www.kaggle.com/competitions/store-sales-time-series-forecasting)

The competition provides historical sales data, store information, oil prices, transactions, and holiday events to predict future sales.

**Prediction target:** `sales`

**Evaluation metric:** Root Mean Squared Logarithmic Error (RMSLE)

## Dataset

The project uses the following datasets:

| Dataset | Description |
|---|---|
| `train.csv` | Historical sales data |
| `test.csv` | Data for the prediction period |
| `stores.csv` | Store information and characteristics |
| `oil.csv` | Daily oil prices |
| `transactions.csv` | Daily transactions per store |
| `holidays_events.csv` | Holidays and special events |
| `sample_submission.csv` | Required submission format |

The training dataset contains approximately 3 million observations across 54 stores and multiple product families.

## Project Workflow

### 1. Exploratory Data Analysis (EDA)

The first stage focused on understanding the dataset and identifying patterns that could influence sales.

Topics investigated:

- Dataset dimensions and data types
- Missing values and duplicate records
- Sales distribution and descriptive statistics
- Sales development over time
- Sales patterns by store and product family
- Weekly and monthly seasonality
- Promotion effects
- Holiday and event information

**Key findings:**

- Sales show an overall upward trend over the observed years.
- Saturday and Sunday have the highest average sales, while Thursday has the lowest.
- Grocery and Beverages are among the strongest product families in terms of sales.
- Store-level sales differ considerably.
- Promotions are associated with substantially higher average sales.
- The sales distribution is strongly right-skewed, with many low or zero values and a small number of very high observations.

### 2. Data Preparation and Integration

Several datasets were combined to enrich the training and test data.

The following tables were integrated:

- Store information
- Oil prices
- Transaction data
- Holiday and event information

Merge operations were validated to prevent unintended row multiplication.

Holiday events required additional preprocessing because multiple events could occur on the same date. Events were aggregated by their geographical scope:

- National events
- Regional events
- Local events

Transferred holidays were excluded from the holiday feature aggregation.

### 3. Feature Engineering

Additional features were created to capture temporal patterns and relevant contextual information.

**Calendar features:**

- `year`
- `month`
- `day`
- `day_of_week`
- `week_of_year`
- `is_weekend`

**Store and product features:**

- `store_nbr`
- `family`
- `city`
- `state`
- `type`
- `cluster`

**Additional features:**

- `onpromotion`
- `dcoilwtico`
- `national_event_count`
- `national_holiday_count`
- `regional_event_count`
- `local_event_count`

Categorical variables were handled according to the requirements of the respective machine learning models.

### 4. Missing Value Handling

Missing values were investigated before model training.

Two relevant columns required special attention:

**
