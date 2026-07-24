# Fraud Detection

Fraud Detection for E-commerce and Credit Card Transactions using Machine Learning.

## Objectives

- Data preprocessing
- Feature Engineering
- Fraud Detection
- Explainable AI using SHAP

## Dataset

- Fraud_Data.csv
- creditcard.csv
- IpAddress_to_Country.csv

## Interim 1 - Data Understanding and Preprocessing

### Data Cleaning

- Checked missing values.
- Removed duplicate transactions.
- Converted timestamp columns into datetime format.

### Exploratory Data Analysis

Performed:

- Numerical feature distributions.
- Fraud class distribution analysis.
- Fraud rate analysis across categorical variables.
- Country-based fraud analysis.

### Geolocation Feature Engineering

- Converted IP addresses into integer format.
- Used pandas merge_asof for range-based IP lookup.
- Added country information.
- Unmatched IP addresses were assigned "Unknown".

### Feature Engineering

Created:

- hour_of_day
- day_of_week
- purchase_month
- is_weekend
- time_since_signup_hours
- user_transaction_count
- device_transaction_count

### Data Transformation

- One-hot encoded categorical variables.
- Standardized numerical variables using StandardScaler.

### Class Imbalance

Fraud data was highly imbalanced.

SMOTE will be applied only after train-test splitting during model development to avoid data leakage.

## Interim 2 - Model Building

### Train/Test Split

The dataset was divided using stratified train-test splitting:

- Training set: 80%
- Testing set: 20%

Stratification was used to preserve the fraud ratio.

---

### Handling Class Imbalance

The dataset contained significantly fewer fraud transactions.

SMOTE was applied only to the training dataset to create synthetic fraud samples.

This prevents:

- Model bias toward legitimate transactions
- Data leakage into evaluation data

---

### Models Developed

Two classification models were trained:

### 1. Logistic Regression

Used as an interpretable baseline model.

Advantages:

- Simple interpretation
- Provides probability estimates
- Useful benchmark

---

### 2. Random Forest

Used as the ensemble model.

Advantages:

- Captures nonlinear fraud patterns
- Handles complex feature interactions
- Provides feature importance

Hyperparameters were tuned using GridSearchCV:

- Number of trees
- Maximum tree depth

---

### Evaluation Metrics

Because fraud detection is highly imbalanced, accuracy was not used.

Models were evaluated using:

- F1 Score
- AUC-PR
- Confusion Matrix

---

### Model Selection

The Random Forest model was selected as the final model because it achieved better performance on fraud detection metrics while maintaining strong interpretability through feature importance analysis.
