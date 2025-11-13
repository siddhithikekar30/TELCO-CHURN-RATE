# Customer Churn Prediction using Machine Learning

This project aims to predict **customer churn** using the Telco Customer Churn dataset. It involves **EDA, preprocessing, feature engineering, hyperparameter tuning (Optuna)**, and modeling with **Random Forest** and **XGBoost**, followed by **SHAP explainability** to interpret model predictions.

---

## Dataset

- **Source**: [Telco Customer Churn (Kaggle)](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- **Samples**: 7,043
- **Target Variable**: `Churn` (Yes/No)
- **Goal**: Predict if a customer is likely to churn based on usage and account features

---

## 🔍 Workflow Overview

1. **Exploratory Data Analysis (EDA)**  
   - Class imbalance (~26% churn)
   - Churn patterns across contract type, internet service, payment method, etc.

2. **Preprocessing**  
   - Handled missing values in `TotalCharges` (filled with 0 for tenure = 0)
   - Encoded categorical features using one-hot and binary encoding
   - Removed `customerID`
3. **Modeling**
   - Trained **Random Forest** and **XGBoost**
   - Tuned hyperparameters with **Optuna** (`n_trials=200`)
   - Used **Stratified K-Fold (5)** cross-validation


4. **Explainability**
   - Used **SHAP** to identify top features contributing to churn

---

## Model Performance

| Metric            | Random Forest (Tuned) | XGBoost (Tuned) |
|-------------------|------------------------|------------------|
| Accuracy          | 79.0%                 | 78.3%           |
| Precision (Churn) | 63.8%                 | 61.4%           |
| Recall (Churn)    | 62.1%                 | 66.9% ✅         |
| F1 Score (Churn)  | 63.6%                 | **63.6%** ✅     |
| ROC AUC           | 84.5%                 | **85.7%** ✅     |

> ✅ **XGBoost** performs slightly better in recall, F1, and ROC AUC, making it the preferred model.

---

## 🔍 Top 5 Churn Indicators (SHAP Summary)

1.  **Low tenure** – New customers churn more
2.  **Fiber optic internet** – More likely to churn than DSL users
3.  **Month-to-month contract** – Highest churn rate
4.  **High monthly charges** – Contributes to churn
5.  **Lack of tech support / security services** – Correlates with churn

SHAP helps interpret individual predictions by showing how each feature shifts the output from the average.


---

## 📁 Project Structure (Description)

- **`data/`**: Contains the raw and fully processed datasets.
- **`models/`**: Stores the final `.pkl` models for XGBoost and Random Forest.
- **`notebooks/`**: Includes separate notebooks for EDA, preprocessing, modeling, tuning, and SHAP analysis.
- **`README.md`**: This project overview and documentation.

---


## 🙋‍♂️ Author

Siddhi Thikekar  
Final Year Dual Degree, Metallurgical and Materials Engineering  
IIT Kharagpur
