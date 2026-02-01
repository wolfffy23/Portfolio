Customer Segmentation using K-Means Clustering

Project Overview
This project demonstrates an end-to-end customer segmentation analysis using the K-Means clustering algorithm. The dataset used is based on mall customer information, which is resampled and preprocessed before applying clustering techniques to identify distinct customer groups.

The notebook includes:

Data loading and preprocessing

Exploratory Data Analysis (EDA)

Feature engineering

K-Means clustering implementation

Visualization of customer segments

Dataset
The original dataset used is Mall_Customers.csv. A resampled version (Customer_Segmentation_Data.csv) containing 2000 customers is created for analysis. Key features include:

CustomerID – Unique identifier

Gender – Customer gender

Age – Customer age

Annual Income (k$) – Annual income in thousands

Spending Score (1-100) – Score assigned by the mall based on customer spending behavior

Key Steps
1. Data Preparation
Load and resample the dataset to 2000 records

Update CustomerID to a new range (2000–4000) and reformat it

Save the cleaned dataset as Customer_Segmentation_Data.csv

Standardize column names to lowercase with underscores

2. Exploratory Data Analysis (EDA)
Generate summary statistics

Check for missing values

Visualize gender distribution using a pie chart

Plot distributions of numerical features (Age, Annual Income, Spending Score) using Seaborn’s distplot

3. Data Preprocessing for Clustering
Select relevant numerical features for clustering

Normalize/scale features if necessary (implied, not shown in snippet)

Prepare data for K-Means algorithm

4. K-Means Clustering (to be implemented in subsequent cells)
Determine optimal number of clusters using the Elbow method

Apply K-Means algorithm

Assign cluster labels to customers

Analyze and profile each cluster

5. Visualization of Clusters
Plot clusters in 2D/3D space based on selected features

Interpret and label clusters (e.g., "High Income, Low Spenders", "Young, High Spenders")

Requirements
To run this notebook, ensure the following Python libraries are installed:

bash
pip install pandas numpy matplotlib seaborn scikit-learn
How to Run
Place Mall_Customers.csv in the same directory as the notebook.

Open customer_segmentation_kmeans.ipynb in Jupyter Notebook or Google Colab.

Run all cells sequentially.

The resampled dataset will be saved as Customer_Segmentation_Data.csv.

Proceed with clustering and visualization steps.

Expected Outcomes
Identification of distinct customer segments based on spending behavior, income, and age.

Insights that can be used for targeted marketing, personalized offers, and inventory planning.

Author
This project was developed as part of a data science portfolio to demonstrate unsupervised learning and customer segmentation techniques.

License
This project is for educational purposes. The dataset is publicly available and often used for learning clustering algorithms.


