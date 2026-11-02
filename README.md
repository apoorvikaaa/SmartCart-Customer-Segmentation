🛒 SmartCart — Customer Segmentation Using Clustering

A customer segmentation project using K-Means and Agglomerative Hierarchical Clustering to identify groups of customers based on demographic information, purchasing behaviour, and shopping activity.

📌 Overview

SmartCart applies unsupervised machine learning to customer data to discover behavioural patterns and group similar customers together.

The project includes data cleaning, feature engineering, exploratory analysis, categorical encoding, feature scaling, dimensionality reduction with Principal Component Analysis (PCA), and clustering with K-Means and Agglomerative Clustering.

The resulting clusters can help explore differences in customer income, spending, and shopping behaviour. The project is exploratory: cluster labels represent groups found by the algorithms and do not have predefined meanings.

🎯 Objectives

Prepare customer data for unsupervised learning.

Engineer useful features such as customer age, tenure, total spending, and number of children.

Explore relationships and patterns in customer attributes.

Reduce feature dimensionality using PCA.

Determine a suitable K for K-Means using the elbow method and silhouette scores.

Compare K-Means and Agglomerative clustering results.

Characterize clusters using customer income and spending patterns.

✨ Project Workflow

Load and inspect data: Read the customer dataset and examine its dimensions, columns, and missing values.

Handle missing values: Fill missing Income values with the median.

Feature engineering:

Calculate Age from Year_Birth.

Calculate Customer_Tenure_Days from the customer joining date.

Create Total_Spending from product-category spending.

Create Total_Children from Kidhome and Teenhome.

Group education categories and marital status categories.

Clean features: Remove identifier, redundant, and original component columns after creating aggregated features.

Outlier handling: Filter records with Age below 90 and Income below 600,000.

Exploratory analysis: Inspect feature distributions, pairwise relationships, and a correlation heatmap.

Encode categorical data: Apply One-Hot Encoding to Education and Living_With.

Scale features: Apply StandardScaler.

Dimensionality reduction: Use PCA to transform the scaled data into three principal components and visualize it in 3D.

K-Means analysis: Calculate WCSS for a range of cluster counts, use KneeLocator to estimate the elbow, and calculate silhouette scores.

Clustering: Fit K-Means and Agglomerative Clustering with four clusters on the PCA-transformed data.

Cluster characterization: Examine cluster sizes and compare income and spending patterns.

🧰 Tech Stack

Technology

Purpose

Python

Programming language

Pandas

Data loading and manipulation

NumPy

Numerical operations

Matplotlib

Visualization

Seaborn

Statistical visualization

Scikit-learn

Scaling, PCA, clustering, and evaluation metrics

kneed

Elbow-point detection

Jupyter Notebook

Interactive development

📊 Dataset

The project uses smartcart_customers.csv, containing 2,240 customer records and 22 columns.

The dataset includes:

Feature

Description

ID

Customer identifier

Year_Birth

Customer birth year

Education

Education category

Marital_Status

Marital status

Income

Customer income

Kidhome

Number of children in the household

Teenhome

Number of teenagers in the household

Dt_Customer

Date the customer joined

Recency

Days since the customer's last purchase

MntWines

Spending on wines

MntFruits

Spending on fruits

MntMeatProducts

Spending on meat products

MntFishProducts

Spending on fish products

MntSweetProducts

Spending on sweet products

MntGoldProds

Spending on gold products

NumDealsPurchases

Number of purchases made with a discount

NumWebPurchases

Number of web purchases

NumCatalogPurchases

Number of catalog purchases

NumStorePurchases

Number of store purchases

NumWebVisitsMonth

Number of website visits in a month

Complain

Whether the customer complained

Response

Response to the campaign

🧪 Clustering Techniques

1. K-Means Clustering

K-Means partitions observations into a specified number of clusters by minimizing the within-cluster sum of squares (WCSS).

In this project:

WCSS is calculated for cluster counts from 1 to 10.

KneeLocator is used to estimate the elbow point.

Silhouette scores are calculated for cluster counts from 2 to 10.

A K-Means model with n_clusters=4 and random_state=42 is fitted to the three PCA components.

2. Agglomerative Hierarchical Clustering

Agglomerative Clustering is a bottom-up hierarchical clustering technique. It starts with individual observations and progressively merges clusters.

The notebook uses:

n_clusters=4

linkage="ward"

The model is fitted to the same three PCA components. Its cluster assignments are then used for the cluster-characterization section.

3. Principal Component Analysis (PCA)

PCA transforms the scaled feature set into three principal components. These components are used as the input to both clustering algorithms and to create 3D cluster visualizations.

📈 Cluster Analysis

The notebook explores the generated clusters through:

3D scatter plots of PCA components.

Cluster counts.

A cluster summary using feature means.

A scatter plot comparing Total_Spending and Income.

Cluster numbers are arbitrary identifiers; for example, Cluster 0 is not inherently better or more valuable than Cluster 1. Interpret each group by examining its feature profile.

🚀 Getting Started

Prerequisites

Python 3.10 or later

pip

Jupyter Notebook

1. Clone the repository

Replace <your-username> with your GitHub username:

git clone https://github.com/<your-username>/SmartCart-Customer-Segmentation.git
cd SmartCart-Customer-Segmentation

2. Create a virtual environment (recommended)

Windows:

python -m venv venv
venv\Scripts\activate

macOS / Linux:

python3 -m venv venv
source venv/bin/activate

3. Install dependencies

pip install -r requirements.txt

4. Run the notebook

Keep smartcart_customers.csv in the same directory as smartcart.ipynb, then run:

jupyter notebook

Open smartcart.ipynb and execute the cells in order.

📁 Repository Structure

SmartCart-Customer-Segmentation/
│
├── smartcart.ipynb
├── smartcart_customers.csv
├── requirements.txt
└── README.md

🔭 Possible Future Improvements

Compare the two clustering methods using additional internal validation metrics.

Tune the number of clusters rather than relying on a fixed value.

Explore alternative linkage methods for hierarchical clustering.

Use a dendrogram to visualize hierarchical cluster merging.

Profile clusters with clear business-oriented labels based on their measured characteristics.

Build customer personas and develop targeted marketing recommendations.

Use a reusable preprocessing pipeline to make the workflow easier to reproduce.

Investigate the effect of outliers and feature selection on cluster quality.

⚠️ Notes and Limitations

This is an exploratory unsupervised learning project; there is no predefined target label for the clusters.

Cluster assignments depend on the selected features, preprocessing, scaling, dimensionality reduction, and algorithm parameters.

The notebook estimates an elbow point and calculates silhouette scores, but the final K-Means and Agglomerative models are explicitly configured with four clusters.

Cluster numbers are not class labels and should be interpreted using the underlying customer characteristics.

The notebook uses 2026 - Year_Birth to calculate age. For reproducibility, consider using a fixed reference year or a date-based calculation.