# 💳 Bank Customer Monthly Spending Prediction

A machine learning regression project that forecasts individual bank customers' total monthly card spending using 3 years of transaction history — enabling better financial planning and budget support for customers.

> **Role:** This was a group project (Group 34, UTS). My individual contribution was the **regression use case: Predicting Monthly Spending Amount**.

---

## 📌 Project Overview

A bank had been collecting transactional data from ~983 customers over three years but lacked the expertise to extract value from it. This project addressed that gap by building machine learning models to predict each customer's next month's spending — giving the bank a tool to help customers manage budgets, reduce financial stress, and improve financial health.

**Dataset:** 132 transaction files + 1 customer file → merged into a single dataset  
**Records:** 4,260,904 transactions across 3 years  
**Tech stack:** Python, scikit-learn, Pandas, Matplotlib, Seaborn

---

## 🎯 Business Question

> *"Can we predict a customer's total spending for next month using their past transaction behaviour?"*

Accurate monthly spending forecasts allow the bank to:
- Help customers proactively budget their finances
- Reduce financial stress by anticipating upcoming expenses
- Enable personalised financial advice based on individual spending patterns

---

## 🔧 Pipeline Steps

### 1. Data Loading & Merging
- Merged 132 transaction CSV files with a customer demographic file on `cc_num`
- Final merged dataset: **23 columns, 4.26 million records**
- Converted `unix_time` to datetime, calculated `age_at_transaction` from date of birth

### 2. Exploratory Data Analysis
- Analysed spending trends from 2019–2022, with a notable spike in late 2022
- Explored spending by gender, category, and month
- Built a **geographic heatmap** of purchases across the US — highest density in Northeast, West Coast, Texas, and Florida
- Key demographic: customers aged 25–40 accounted for the majority of transactions

### 3. Feature Engineering
Six behaviour-based features were created from transaction history:

| Feature | Description |
|---|---|
| `monthly_spending` | Target variable — total spend per customer per month |
| `rolling_avg_spending` | 3-month rolling average of spending |
| `monthly_transactions` | Count of transactions per month per account |
| `unique_merchants` | Number of distinct merchants per month |
| `average_transaction` | Mean transaction amount |
| `max_transaction` / `min_transaction` | Spending range per period |

### 4. Data Preparation
- Dropped identifier columns (cc_num, SSN, names) and redundant columns
- Applied **StandardScaler** to normalise features
- Used a 1% sample of the dataset due to computational constraints
- Split: **80% train / 10% validation / 10% test** (index-based to avoid memory overhead)

### 5. Modelling — 3 Regression Models Compared

**Baseline:** Mean as predictor → R²: -0.000083, RMSE: 86.00

| Model | MSE | RMSE | R² |
|---|---|---|---|
| Linear Regression | 2,682.50 | 51.79 | 0.868 |
| Gradient Boosting | 2,409.71 | 49.09 | 0.893 |
| **Random Forest** ✅ | **1,885.22** | **43.42** | **0.935** |

---

## 🏆 Results

**Random Forest Regressor** was selected as the final model with:
- **R² of 0.935** — explains 93.5% of variance in monthly spending
- **RMSE of 43.42** — average prediction error of ~$43 per month
- **~75% reduction in prediction error** vs. the simple mean baseline (RMSE: 86.00 → 43.42)

The model significantly outperformed both baseline and simpler models, providing the bank with reliable, customer-level spending forecasts.

---

## 💡 Business Impact

- Customers can receive **personalised monthly budget alerts** based on predicted spend
- The bank can proactively offer **budget support tools** to customers likely to overspend
- Accurate forecasts improve **customer retention** by reducing financial stress
- Provides a foundation for **personalised financial product recommendations**

---

## 📁 Repository Structure

```
├── 36106-AT3-MLGR_34-24627453.ipynb   # Shivansh's regression notebook
└── README.md
```

---

## 🚀 How to Run

```bash
# Install dependencies
pip install pandas numpy scikit-learn matplotlib seaborn dataprep

# Launch notebook
jupyter notebook 36106-AT3-MLGR_34-24627453.ipynb
```

> **Note:** The dataset is not included in this repo as it was provided by UTS. Update `folder_path` in the notebook to point to your local data directory.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core language |
| scikit-learn | Linear Regression, Random Forest, Gradient Boosting, StandardScaler |
| Pandas / NumPy | Data manipulation and feature engineering |
| Matplotlib / Seaborn | Visualisations |
| dataprep | EDA plotting |

---

## 👤 Author

**Shivansh Pandey**  
Master of Data Science and Innovation — University of Technology Sydney  
[LinkedIn](https://linkedin.com/in/your-link) | [GitHub](https://github.com/shivanshweb)
