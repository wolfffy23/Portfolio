# Customer Segmentation using K-Means Clustering

## Overview
This project segments 2,000 mall customers into distinct behavioral clusters using K-Means clustering. The goal is to identify groups of customers with similar spending patterns, income levels, and demographics — insights that can inform targeted marketing strategies.

## Dataset
- **Source:** Kaggle (Mall Customers Dataset)
- **Records:** 2,000 customers
- **Features:**
  - `CustomerID` — Unique identifier
  - `Gender` — Male / Female
  - `Age` — Customer age (18–70)
  - `Annual Income (k$)` — Yearly income in thousands
  - `Spending Score (1–100)` — Retail spending behavior score

## Approach

### 1. Exploratory Data Analysis (EDA)
- Checked for missing values across all features (none found)
- Plotted distributions for age, income, and spending score
- Analysed gender breakdown using pie chart and violin/swarm plots
- Computed correlation matrix across numerical features
- Visualised relationships between all variable pairs using regression plots and scatter plots segmented by gender

### 2. Feature Selection
Selected three features for clustering: `Age`, `Annual Income`, and `Spending Score`. These capture the core behavioral and demographic dimensions relevant to customer segmentation.

### 3. K-Means Clustering
- Used the **elbow method** to test cluster counts from 3 to 26, plotting inertia to identify the optimal number
- Selected **13 clusters** based on the elbow curve
- Applied K-Means with Lloyd's algorithm
- Visualised the resulting clusters and centroids in a **3D scatter plot**

### 4. Dimensionality Reduction & Validation
- Applied **PCA** (retaining 95% variance) to reduce the feature space and visualise cluster structure in 2D
- Applied **t-SNE** for non-linear dimensionality reduction to further validate that the clusters are well-separated in lower dimensions

## Key Findings
- Customers naturally segment into distinct groups based on the relationship between income and spending behavior
- High-income, high-spending clusters represent the most valuable customer segment
- Low-income, low-spending clusters require different engagement strategies than high-income, low-spending ones
- PCA and t-SNE both confirmed that the 13-cluster structure holds up beyond the original feature space

## Tech Stack
- **Python** — pandas, NumPy
- **Scikit-learn** — KMeans, PCA, TSNE
- **Visualisation** — Matplotlib, Seaborn

## How to Run
1. Clone the repository
2. Install dependencies: `pip install pandas numpy matplotlib seaborn scikit-learn`
3. Open `customer_segmentation_kmeans.ipynb` in Jupyter Notebook
4. Run all cells top to bottom
