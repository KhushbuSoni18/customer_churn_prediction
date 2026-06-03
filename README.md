# Customer Churn Prediction
### Predicting customer churn using machine learning to support proactive retention strategies

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## Table of Contents
- [Overview](#overview)
- [Problem Statement](#problem-statement)
- [Dataset](#dataset)
- [Project Workflow](#project-workflow)
- [Key Findings](#key-findings)
- [Model Performance](#model-performance)
- [Business Impact](#business-impact)
- [Project Structure](#project-structure)
- [How to Run](#how-to-run)
- [Tools & Libraries](#tools--libraries)

---

## Overview

Customer churn - when customers stop using a service - directly impacts business revenue and growth. This project builds a **Random Forest classification model** to predict which customers are likely to churn, enabling businesses to take proactive retention actions before customers leave.

The model was trained on a telecom dataset of **7,043 customers** and achieved **80% accuracy** on unseen test data.

---

## Problem Statement

> A telecom company is losing customers each month. The business needs a way to identify **which customers are at high risk of churning** so the retention team can intervene early with targeted offers or support.

**Goal:** Build a predictive model that flags high-risk customers based on their demographic profile and service usage patterns.

---

## Dataset

| Property | Details |
|---|---|
| Source | Telecom customer data |
| Records | 7,043 customers |
| Features | 21 columns (demographic + service data) |
| Target | `Churn` (Yes / No) |
| Class Balance | ~73% No Churn / ~27% Churn |

**Key features include:**
- **Demographics:** Gender, SeniorCitizen, Partner, Dependents
- **Services:** PhoneService, InternetService, OnlineSecurity, TechSupport, StreamingTV
- **Account info:** Contract type, PaymentMethod, PaperlessBilling
- **Financials:** MonthlyCharges, TotalCharges, Tenure

---

## Project Workflow

```
Raw Data --> EDA --> Data Cleaning --> Feature Engineering --> Model Training --> Evaluation --> Insights
```

### 1. Exploratory Data Analysis
- Examined distributions of numerical features (tenure, MonthlyCharges, TotalCharges)
- Analysed churn rate across contract types, payment methods, and service usage
- Identified class imbalance: ~27% of customers churned

### 2. Data Cleaning
- Converted `TotalCharges` from object to numeric (11 rows had blank values)
- Imputed missing values in `TotalCharges` using **median** to handle skew
- Removed duplicate records
- Dropped `customerID` (non-predictive identifier)

### 3. Feature Engineering
- Applied **one-hot encoding** to 17 categorical variables using `pd.get_dummies`
- Final feature set: 30+ encoded columns

### 4. Model Building
- **Algorithm:** Random Forest Classifier (`sklearn.ensemble`)
- **Split:** 80% train / 20% test with stratified sampling to preserve class balance
- **Scaling:** StandardScaler applied to all features

### 5. Evaluation
- Evaluated using accuracy, precision, recall, F1-score, and confusion matrix
- Plotted feature importance to understand top churn predictors

---

## Key Findings

| Finding | Detail |
|---|---|
| **Tenure is the #1 churn predictor** | Customers with < 12 months tenure churn at significantly higher rates |
| **Monthly charges matter** | High monthly charges (above ~$70) correlate strongly with churn |
| **Contract type is critical** | Month-to-month customers churn far more than 1-year or 2-year contract holders |
| **Fiber optic users churn more** | Likely due to higher monthly costs and competition |
| **Online security reduces churn** | Customers with OnlineSecurity or TechSupport are less likely to leave |

---

## Model Performance

| Metric | Score |
|---|---|
| **Accuracy** | **80%** |
| Precision (No Churn) | 83% |
| Recall (No Churn) | 92% |
| Precision (Churn) | 67% |
| Recall (Churn) | 47% |
| F1-Score (weighted avg) | 0.79 |

**Confusion Matrix summary (on 1,409 test records):**
- Correctly identified 952 / 1,035 non-churners 
- Correctly identified 176 / 374 churners 
- 198 churners were missed (false negatives) - room for improvement with class balancing techniques

> **Note:** The model is better at identifying loyal customers (92% recall) than churners (47% recall). This is a common trade-off with imbalanced datasets. Techniques like SMOTE or class_weight adjustment can improve churn recall.

---

## Business Impact

This model enables the retention team to:

- **Prioritise outreach** - focus limited retention budget on highest-risk customers instead of broad campaigns
- **Act early** - flag new customers with low tenure before they churn
- **Design better contracts** - data confirms month-to-month contracts are the biggest churn driver; incentivising longer contracts could directly reduce churn
- **Personalise offers** - customers without TechSupport or OnlineSecurity are higher risk; targeted upsell of these services may reduce churn while generating revenue

---

## Project Structure

```
customer_churn_prediction/
|
├── Customer_Churn_Prediction.ipynb
# Main notebook (EDA + Model)
├── Customer_data.csv
# Dataset (7,043 records)
├── feature_importance.png
  # Top 10 feature importance chart
└── README.md                         # Project documentation
```

---

## How to Run

**1. Clone the repository**
```bash
git clone https://github.com/KhushbuSoni18/customer_churn_prediction.git
cd customer_churn_prediction
```

**2. Install dependencies**
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

**3. Run the notebook**
```bash
jupyter notebook Customer_Churn_Prediction.ipynb
```

> Run all cells from top to bottom in sequence. The notebook contains all steps from data loading to model evaluation.

---

## Tools & Libraries

| Tool | Purpose |
|---|---|
| Python 3.8+ | Core language |
| pandas | Data manipulation and cleaning |
| numpy | Numerical operations |
| matplotlib / seaborn | Data visualisation |
| scikit-learn | ML model, scaling, evaluation |
| Jupyter Notebook | Interactive development environment |

---

## Author

**Khushbu Soni**
Aspiring Data Analyst | SQL · Python · Excel · Power BI

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://www.linkedin.com/in/khushbu-soni18/)
[![GitHub](https://img.shields.io/badge/GitHub-Profile-black?logo=github)](https://github.com/KhushbuSoni18)

---

*Part of a data analytics portfolio. Also see: [EV Analytics & Recommendation System](https://github.com/KhushbuSoni18/EV-Analytics-Recommendation-System) · [Retail Sales Analysis](https://github.com/KhushbuSoni18/Retail_Sales_Analysis) · [Support Ticket Dashboard](https://github.com/KhushbuSoni18/support-ticket-dashboard)*
