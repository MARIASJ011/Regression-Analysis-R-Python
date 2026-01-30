# Assignment 3 – Regression Analysis & Model Diagnostics

This assignment applies **linear regression techniques** to real-world datasets using **both R and Python**, with a focus on **model interpretation, multicollinearity diagnostics, and predictive analysis**. The work spans two applied contexts:  
(1) household consumption analysis using NSSO data, and  
(2) performance-based salary modeling in the Indian Premier League (IPL).

---

## Objective
- Apply **multiple linear regression** to real datasets
- Handle missing data using **mean imputation**
- Diagnose **multicollinearity** using Variance Inflation Factor (VIF)
- Interpret regression coefficients and model summaries
- Build simple **predictive models** and compare actual vs predicted values
- Implement regression workflows in **both R and Python**

---

## Datasets Used

### 1) NSSO 68th Round – Household Consumption
- Filtered for **Haryana (HR)**
- Variables include:
  - Food consumption quantity (`foodtotal_q`)
  - Monthly Per Capita Expenditure (`MPCE_MRP`, `MPCE_URP`)
  - Demographics (Age, Education)
  - Household characteristics (Meals at Home, Ration Card ownership)

### 2) IPL Ball-by-Ball & Salary Data
- IPL ball-by-ball data (2021–2024)
- IPL salary data (₹ lakhs)
- Focused analysis on **Shivam Dube**
- Performance metrics: runs scored, matches played

---

## Methodology

### Part A: Household Consumption Regression (NSSO – Haryana)

- Filtered dataset for **Haryana**
- Selected relevant economic and demographic variables
- Imputed missing values using **column means**
- Fitted multiple linear regression model:
- Evaluated model using:
- Regression summary
- **Variance Inflation Factor (VIF)** for multicollinearity
- Diagnostic plots (residuals, QQ plot, leverage)

Implemented in:
- **R** (lm, car::vif)
- **Python** (statsmodels OLS)

---

### Part B: Salary vs Performance Modeling (IPL – Shivam Dube)

- Filtered ball-by-ball data for **Shivam Dube** (2021–2024)
- Aggregated:
- Total runs per season
- Number of matches played
- Merged known salary data (₹ lakhs)
- Fitted regression model:
- Generated **predicted salaries**
- Visualized **actual vs predicted salary trends** over seasons

Implemented in:
- **R** (lm, ggplot2)
- **Python** (statsmodels, seaborn)

---

## Key Insights
- Household food consumption is significantly influenced by income and household characteristics
- VIF analysis helps identify and assess multicollinearity among predictors
- IPL salary shows limited explanatory power from runs and matches alone, highlighting the role of non-performance factors
- Regression workflows and results are consistent across **R and Python**, reinforcing tool-agnostic modeling skills

---

## Tools & Technologies
- **R**: lm, car, dplyr, ggplot2
- **Python**: pandas, statsmodels, seaborn, matplotlib
- **Statistical Methods**: Linear regression, VIF, residual diagnostics

---

## Project Structure
│── R/
│ ├── nsso_regression_haryana.R
│ └── ipl_salary_regression.R
│── Python/
│ ├── nsso_regression_haryana.py
│ └── ipl_salary_regression.py
│── README.md
---

## Notes
This assignment was completed as part of a **graduate-level analytics course** and emphasizes **regression modeling fundamentals, diagnostics, and interpretation** rather than production deployment. The techniques demonstrated here form the foundation for more advanced econometric and predictive modeling tasks.

---

**Author:** Maria  
**Coursework – Applied Regression & Analytics**
