# 📡 Telecom Customer Churn Prediction

**Client:** No-Churn Telecom | **Project Ref:** PM-PR-0017 | **Date:** December 2025  

---

## 🧩 Business Problem

No-Churn Telecom is an established European telecom operator facing intense competition from new market entrants. Despite initiatives such as tariff reductions and promotional campaigns, the company's **churn rate remained above 10%**, directly impacting revenue and market share.

The goal of this project was to leverage Machine Learning to **proactively identify customers at risk of churning**, enabling targeted retention campaigns before customers leave.

---

## 🎯 Project Goals

| # | Goal |
|---|------|
| 1 | Identify the key variables driving customer migration to competitors |
| 2 | Generate **Churn Risk Scores** (0–1 probability) to power retention campaigns |
| 3 | Introduce a new binary variable **`CHURN-FLAG`** (YES / NO) for priority customer handling |

> **Additional Use Case:** Auto-prioritize support tickets, ensure faster request fulfillment, and enable proactive outreach for all `CHURN-FLAG = YES` customers.

---

## 📦 Dataset

| Attribute | Details |
|-----------|---------|
| Source | SQL Database (`project_telecom`) |
| Table | `telecom_churn_data` |
| Total Records | 4,617 |
| Target Variable | `Churn` (Yes / No) |

### Features

The dataset contains 21 columns covering customer account and usage information:

| Category | Features |
|----------|----------|
| Account Info | State, Account Length, Area Code, Phone |
| Plan Info | International Plan, VMail Plan, VMail Message |
| Day Usage | Day Mins, Day Calls, Day Charge |
| Evening Usage | Eve Mins, Eve Calls, Eve Charge |
| Night Usage | Night Mins, Night Calls, Night Charge |
| International Usage | International Mins, International Calls, International Charge |
| Support | CustServ Calls |
| Target | Churn (Yes / No) |

---

## 🔧 Tech Stack

```
Python 3.13
├── Data            : pandas, numpy, pymysql
├── Visualization   : matplotlib, seaborn
├── Preprocessing   : scikit-learn (LabelEncoder, train_test_split)
├── Imbalance       : imbalanced-learn (SMOTE)
└── Modeling        : scikit-learn (RandomForestClassifier, GridSearchCV)
```

---

## 🔬 Methodology

### 1. Data Extraction
- Connected to a remote MySQL database and loaded the full `telecom_churn_data` table using `pymysql` and `pandas.read_sql`.

### 2. Exploratory Data Analysis (EDA)
- Inspected data shape, dtypes, null values, and descriptive statistics.
- Plotted distribution histograms and boxplots for all numeric columns to understand feature spread and detect outliers.
- Analyzed churn vs. non-churn distributions across key variables.

### 3. Data Preprocessing
- Renamed all 21 columns to clean, readable labels.
- Applied **Label Encoding** to categorical variables (`International Plan`, `VMail Plan`, `Churn`).
- Dropped non-predictive identifier columns (`Phone`, `State`, `Area Code`).

### 4. Handling Class Imbalance
- The dataset had a significant class imbalance (churn minority class).
- Applied **SMOTE (Synthetic Minority Over-sampling Technique)** on the training set to balance classes before model training.

### 5. Model Training & Tuning
- Split data into **80% train / 20% test**.
- Trained a **Random Forest Classifier** as the base model.
- Used **GridSearchCV** with cross-validation to tune hyperparameters:
  - `n_estimators`, `max_depth`, `min_samples_split`, `min_samples_leaf`

### 6. Prediction & Output Generation
- Generated `CHURN_RISK_SCORE` — a continuous probability score between 0 and 1 for every customer.
- Generated `CHURN-FLAG` — a binary YES/NO flag based on the model's classification threshold.
- Exported the **Top 100 High-Risk Customers** sorted by descending risk score.

---

## 📊 Model Performance

| Metric | Value |
|--------|-------|
| Final Model | Random Forest + SMOTE + GridSearchCV |
| ROC-AUC Score | **0.904** |
| Churn Recall | **74%** |

The model achieves strong discriminative ability (AUC = 0.904) with a recall of 74% on the churn class — meaning it successfully identifies nearly 3 out of 4 customers who will churn, while remaining production-ready and avoiding excessive false positives.

---

## 📤 Deliverables

| Deliverable | Status | Output |
|-------------|--------|--------|
| Churn Drivers Analysis | ✅ Completed | EDA + Feature Importance plots |
| Churn Risk Score | ✅ Completed | `CHURN_RISK_SCORE` column (0–1) |
| Predictive CHURN-FLAG | ✅ Completed | `CHURN-FLAG` column (YES / NO) |
| Top 100 High-Risk Customers | ✅ Completed | Exported CSV |

---

## 💼 Business Impact

- **30–50% expected reduction** in customer churn through targeted retention
- Enables campaigns focused on the **top 100–500 highest-risk customers**
- Significant **cost savings** on customer acquisition by retaining existing customers
- Supports **priority support routing** for high-risk customers (`CHURN-FLAG = YES`)

---

## 🚀 How to Run

1. **Clone the repository**
   ```bash
   git clone <repo-url>
   cd telecom-churn-prediction
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy pymysql matplotlib seaborn scikit-learn imbalanced-learn
   ```

3. **Open the notebook**
   ```bash
   jupyter notebook Telecom_ChurnRateMl.ipynb
   ```

4. **Run all cells** — the notebook will connect to the database, run EDA, train the model, and output risk scores and churn flags.

---

## 📁 Project Structure

```
telecom-churn-prediction/
│
├── Telecom_ChurnRateMl.ipynb    # Main project notebook
├── README.md                    # Project documentation
└── high_risk_customers.csv      # Top 100 high-risk customer export
```

---
