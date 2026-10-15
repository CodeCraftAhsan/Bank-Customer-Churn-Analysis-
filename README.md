# Bank Customer Churn Analysis | Python

**Exploring customer attrition through data quality checks, behavioral analysis, and feature engineering.**

![Python](https://img.shields.io/badge/Python-Data%20Analysis-3776AB?logo=python&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Cleaning-150458?logo=pandas&logoColor=white) ![Status](https://img.shields.io/badge/Status-EDA%20%26%20Feature%20Engineering-informational)

## Overview

Customer churn affects retention planning and the value banks can build from existing relationships. This project investigates the characteristics of customers who leave a bank, using Python to turn an intentionally messy, multi-sheet customer dataset into a cleaner foundation for analysis.

The notebook covers **data integration, quality assessment, cleaning, exploratory data analysis (EDA), visualization, and initial feature engineering**. A predictive classification model has **not yet been trained or evaluated** in the submitted notebook.

## Project snapshot

| Metric | Result |
|---|---:|
| Customers after deduplication | **10,000** |
| Customer churn rate | **20.37%** |
| Customers who exited | **2,037** |
| Customers retained | **7,963** |
| Geography coverage | **France, Germany, Spain** |
| Records after initial merge | **10,004** |
| Exact duplicate rows removed | **4** |

*Metrics are based on the outputs saved in the supplied Jupyter notebook.*

## Business questions

- What share of customers have exited the bank?
- How does churn vary by geography, gender, and activity status?
- What differences appear across age, balance, credit score, salary, tenure, and number of products?
- How can inconsistent customer records be standardized for reliable reporting?
- What additional features could be useful for a future churn model?

## Tools and skills

**Python · Pandas · NumPy · Matplotlib · Seaborn · Jupyter Notebook**

`Data merging` · `Duplicate detection` · `Missing-value imputation` · `Category standardization` · `Data type conversion` · `EDA` · `Automated plotting` · `One-hot encoding` · `Feature engineering`

## Workflow

### 01 — Integrate and assess data
- Loaded customer and account information from two Excel worksheets.
- Merged the tables on `CustomerId` with a left join.
- Removed the redundant tenure field introduced during the merge.
- Removed 4 exact duplicate records, leaving 10,000 customers.

### 02 — Clean and standardize
- Converted euro-formatted `EstimatedSalary` and `Balance` fields to numeric types.
- Filled missing surnames with a missing-value label and missing ages with the median age.
- Replaced invalid `-999999` salary entries with the salary median.
- Standardized `FRA`, `French`, and `France` into `France`.
- Verified the cleaned geographic distribution: France **5,014**, Germany **2,509**, Spain **2,477**.

### 03 — Explore churn behavior
- Visualized exited versus retained customers.
- Compared churn proportions across categorical customer attributes.
- Examined numeric distributions using histograms and box plots, including comparisons by churn status.
- Used loops to generate repeatable plots for multiple variables.

### 04 — Prepare modeling features
- Removed identifier/name fields from the proposed modeling dataset.
- Demonstrated one-hot encoding with `pd.get_dummies(..., drop_first=True)`.
- Created `Balance_vs_salary = Balance / EstimatedSalary` and explored its relationship to churn status.

## Key observations

**1. One in five customers had exited.** Of the 10,000 customers in the cleaned dataset, 2,037 were marked `Exited = 1` (20.37%). This gives a baseline for segment-level churn comparisons.

**2. Geographic labels needed standardization before analysis.** Three variants of France appeared in the raw data. Consolidating them prevented the same country from being reported as separate segments.

**3. Data-quality issues could distort customer insights.** Duplicate records, missing ages/names, euro symbols in numeric columns, and invalid salary placeholders were addressed before EDA.

**4. The balance-to-salary ratio offers a candidate analytical feature.** This derived measure was created and visualized, but its predictive value has not yet been tested.

> **Interpretation note:** Charts in the notebook explore potential associations. They do not establish why customers left or demonstrate causal effects.

## Repository contents

```text
bank-customer-churn-analysis/
├── Bank_Customer_Churn_analysis.ipynb  # Main analysis notebook
├── README.md                           # Project overview
└── data/                               # Add input workbook if sharing is permitted
```

## Run locally

1. Install Python and the packages used in the notebook:

   ```bash
   pip install pandas numpy matplotlib seaborn openpyxl notebook
   ```
2. Place the source Excel workbook (`Bank_Churn_Messy.xlsx`) in a local `data/` folder. **The source workbook is not included in the uploaded notebook.**
3. Update the two `pd.read_excel()` calls to use a portable path such as `data/Bank_Churn_Messy.xlsx`, specifying the relevant sheet where needed.
4. Open `Bank_Customer_Churn_analysis.ipynb` in Jupyter and run cells in order.

## Current limitations and next steps

- The notebook does **not** yet train, validate, or compare churn classification models.
- One-hot encoding is demonstrated but is not assigned back to the modeling dataset.
- A train/test split and metrics such as precision, recall, ROC-AUC, and confusion matrix are future work.
- Before modeling, check the engineered balance-to-salary ratio for zero denominators and assess any missing or extreme values.
- The analysis is descriptive; findings should not be treated as validated retention interventions.

## Business relevance

The analysis creates a reproducible starting point for customer segmentation and churn investigation. A bank's analytics team could build on it to compare churn across customer groups, validate risk indicators, and eventually evaluate targeted retention strategies.

---

**Portfolio project by Ahasan Hasan**  
*Data Analyst | Supply Chain & Finance Analytics*
