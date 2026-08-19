# E-Commerce Order Data: Cleaning & Exploratory Data Analysis

## Overview

An end-to-end data analytics project using a 1,200-record e-commerce order dataset, covering data cleaning, validation, and exploratory data analysis (EDA).

The objective was not simply to process the dataset, but to interrogate the data, validate assumptions before drawing conclusions, and distinguish genuine analytical findings from statistical or structural artifacts.

---

## How to Use This Repository

Open `Ecommerce_Data_Cleaning_and_EDA.xlsx` — the **Change Log** tab contains the full audit trail for data cleaning decisions, and the **EDA** tabs contain the analysis behind each finding below.

---

## Business Questions

- What does a typical order look like, and is the mean a reliable representation of order value?
- Does order value differ meaningfully across Product, Payment Method, or Order Status?
- Is there a genuine trend in revenue and order volume over time?
- Are high-value outliers data errors or legitimate transactions?
- Is there a relationship between purchase Quantity and Unit Price?
- Does the structure of the dataset resemble realistic customer behavior?

---

## Tools & Techniques

**Tools:** Microsoft Excel

**Techniques:**
- Excel Tables
- Go To Special
- Conditional Formatting
- PivotTables
- AVERAGE / MEDIAN
- QUARTILE
- CORREL
- Custom number formatting
- ISO 8601 date standardization
- Scatter charts
- Line charts
- Descriptive statistics
- IQR-based outlier detection

---

## Part 1 — Data Cleaning & Preparation

### Data Quality Audit

- Audited **1,200 records** for duplicates, missing values, formatting inconsistencies, and categorical inconsistencies.
- Identified **309 blank Coupon Code values (26%)** and imputed them as **"No Coupon"** rather than deleting affected records.
- Verified **0 duplicate Order IDs**.
- Verified **0 duplicate full rows**.
- Standardized Date values to **ISO 8601 (YYYY-MM-DD)** while retaining native Excel date values to preserve sorting and date-based analysis.
- Standardized price fields to **2 decimal places**.
- Audited Product, Payment Method, Order Status, and Referral Source for casing, whitespace, and categorical inconsistencies; no anomalies were identified.
- Maintained a complete **before/after Change Log** to provide audit traceability for all data preparation decisions.

---

## Part 2 — Exploratory Data Analysis

### Key Findings

#### 1. Order value is positively skewed

Mean order value was **1,053.97**, approximately **28% higher than the median of 823.62**.

This indicates that a smaller number of high-value orders pull the mean upward. Therefore, the **median provides a more representative measure of a typical order** than the mean in this dataset.

Quantity and Items in Cart showed substantially less divergence between their mean and median values.

---

#### 2. Customer transaction categories have limited explanatory power for spend

Average order value varied by **less than 16%** across Product, Payment Method, and Order Status.

The variation within individual categories was substantially greater than the variation between categories, suggesting that these fields provide **limited explanatory power for order value** within this dataset.

![Average Order Value by Category](screenshots/category%20breakdown.png)

---

#### 3. The apparent 2025 revenue decline is a time-window artifact

Raw revenue decreased from **552,643.24 in 2023** to **231,882.85 in 2025**.

However, 2025 contains only **6 months of observations**, compared with **12 months in 2023**.

After normalizing for the observation period, monthly revenue in 2024 and 2025 was broadly comparable at approximately **38K–40K per month**. Therefore, the raw annual totals should not be interpreted as evidence of a comparable year-over-year decline without accounting for the different observation windows.

![Revenue and Order Volume Over Time](screenshots/time%20trend.png)

---

#### 4. High-value outliers appear explainable rather than erroneous

**8 orders** exceeded the IQR-based upper bound of **3,330.41**.

Each outlier combined relatively high **Quantity** with relatively high **Unit Price**. No common Product, Payment Method, or Date pattern was identified among the flagged transactions.

Based on the available evidence, the outliers were **retained rather than treated as data errors**.

---

#### 5. Quantity and Unit Price show virtually no linear relationship

The correlation between Quantity and Unit Price was approximately **0.01**, indicating essentially no linear relationship between the two variables in this dataset.

In practical terms, higher-priced products were not systematically associated with lower purchase quantities.

![Quantity vs Unit Price Scatter](screenshots/scatter%20-%20quantity%20vs%20price.png)

---

#### 6. Dataset structure suggests synthetic or highly controlled data generation

Categorical variables were distributed unusually close to uniform, with category distributions remaining within approximately **16% of their respective averages**.

Additionally, the 30-month dataset showed **no meaningful seasonal pattern** in order volume.

These characteristics suggest that the dataset may have been synthetically generated or highly controlled. Consequently, the findings should be interpreted as **analytical demonstrations rather than evidence of general real-world customer behavior**.

---

## Recommended Next Steps

If additional customer-level data were available, the next analysis would focus on:

- **Customer segmentation:** distinguish repeat purchasers from one-time customers and assess their contribution to revenue.
- **Referral performance:** test whether Cancelled or Returned orders vary meaningfully by Referral Source.
- **Customer lifetime behavior:** analyze repeat purchase frequency and customer-level revenue.
- **External validation:** compare these patterns against a real transactional dataset before applying conclusions to operational decisions.

---

## Project Deliverables

| Deliverable | Description |
|---|---|
| Cleaned Dataset | Validated and standardized 1,200-record dataset |
| Data Cleaning Log | Documented changes, rationale, and impact |
| EDA Workbook | Descriptive statistics, trends, outliers, relationships, and distribution analysis |
| Visualizations | Charts supporting the analytical findings |

---

## Repository Structure

```text
ecommerce-data-cleaning-eda/
│
├── Ecommerce_Data_Cleaning_and_EDA.xlsx
├── screenshots/
│   ├── scatter - quantity vs price.png
│   ├── time trend.png
│   └── category breakdown.png
│
└── README.md
```

---

## Author

Muhammed Ayodeji Suleiman
Quantity Surveying | Data Analytics
[http://linkedin.com/in/muhammed-suleiman-95bb6433b](#)
