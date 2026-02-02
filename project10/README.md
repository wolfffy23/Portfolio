# Telecom Customer Churn Analysis

## Overview
An exploratory data analysis project investigating what drives customer churn in a telecom company. The goal is to identify key factors that distinguish churned customers from retained ones, providing actionable insights for retention strategies.

## Dataset
- **Source:** Kaggle (Telco Customer Churn)
- **Records:** 7,043 customers
- **Features:** 21 columns including demographics, service details, contract info, and billing
- **Target variable:** `Churn` (Yes/No) — 26.6% churn rate (1,869 churned vs 5,174 retained)

## Approach

### 1. Data Cleaning
- Identified that `TotalCharges` was incorrectly stored as a string — converted to numeric using `pd.to_numeric` with `errors='coerce'`
- This conversion revealed 11 hidden missing values (rows where TotalCharges was blank), which were dropped
- Standardised all column names to lowercase
- Final clean dataset: 7,032 records

### 2. Exploratory Data Analysis

#### Churn Distribution
- Visualised overall churn ratio — 26.6% of customers churned
- Plotted churners vs non-churners using bar and pie charts

#### Demographic Analysis
- **Gender:** Almost no difference in churn rate between male and female customers — gender is not a churn driver
- **Senior Citizens:** Senior citizens have a higher *proportion* of churners (~41.7%) compared to non-seniors (~23.7%), but non-seniors account for the majority of total churners (1,393 vs 476) due to their larger population share
- **Partner status:** Customers without a partner churn at ~33% vs ~19.7% for those with a partner — suggesting partnership correlates with retention
- **Dependents:** Similar pattern — customers without dependents churn at a higher rate

#### Service & Contract Analysis
- Analysed churn rates across all service features: PhoneService, MultipleLines, InternetService, OnlineSecurity, OnlineBackup, DeviceProtection, TechSupport, StreamingTV, StreamingMovies
- Generated grouped bar charts for all 16 categorical variables against churn
- Key finding: Fiber optic internet customers churn more than DSL or no-internet customers

#### Correlation Analysis
- One-hot encoded all categorical variables, expanding the dataset from 21 to 47 features
- Computed correlation of every feature against the churn target
- Plotted correlation bar chart and full heatmap to visualise relationships

#### Pairplot
- Generated a pairplot across numerical features (tenure, monthly charges, total charges) coloured by churn status to visualise cluster separation

### 3. Key Findings

**High churn drivers:**
- Month-to-month contracts — customers with no long-term commitment are free to leave
- No online security and no tech support — customers without these add-ons feel less invested
- Electronic check payment — the highest-churning payment method
- Fiber optic internet — associated with higher churn compared to DSL
- Low tenure — customers in their first year are most likely to churn

**Low churn indicators:**
- Long-term contracts (one year or two year)
- Customers with 5+ years of tenure
- Subscriptions without internet service (lower monthly costs)

**No significant impact:**
- Gender
- Phone service availability
- Number of lines

## Tech Stack
- **Python** — Pandas, NumPy
- **Visualisation** — Matplotlib, Seaborn
- **Data Processing** — One-hot encoding, correlation analysis

## How to Run
1. Clone the repository
2. Install dependencies: `pip install pandas numpy matplotlib seaborn`
3. Place `telco_cust_churn_data.csv` in the working directory
4. Open `Customer_churn_EDA.ipynb` in Jupyter Notebook
5. Run all cells top to bottom
