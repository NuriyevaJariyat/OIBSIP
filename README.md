# Customer Segmentation Using RFM Analysis and K-Means

## Project Overview

This project focuses on customer segmentation using **RFM analysis** and **K-Means clustering**. The goal is to identify groups of customers with similar purchasing behaviour and provide marketing recommendations for each segment.

## Dataset

The dataset contains e-commerce transaction data with information such as:

* Invoice Number
* Stock Code
* Description
* Quantity
* Invoice Date
* Unit Price
* Customer ID
* Country

## Data Cleaning

The following steps were performed:

* Removed customers with missing `CustomerID`
* Checked and removed duplicate records
* Converted `InvoiceDate` to datetime format
* Calculated `TotalPrice`

## RFM Analysis

Three behavioural features were selected for customer segmentation:

* **Recency** – number of days since the customer's last purchase
* **Frequency** – number of unique purchases/orders
* **Monetary** – total amount spent by the customer

## Data Standardisation

`StandardScaler` was used to standardise the RFM features before applying K-Means clustering.

## K-Means Clustering

The **Elbow Method** was used to determine the optimal number of clusters.

The analysis resulted in **4 customer clusters**.

## Cluster Profiles

Based on the mean RFM values, the clusters were interpreted as:

* **Cluster 0 – Loyal / High-Value Customers:** active customers with frequent purchases and relatively high spending.
* **Cluster 1 – Inactive / At-Risk Customers:** customers who have not purchased for a long time and have low purchase frequency and spending.
* **Cluster 2 – VIP / Best Customers:** customers with the highest purchase frequency and monetary value.
* **Cluster 3 – Regular / Low-Value Customers:** the largest customer segment, with relatively low purchase frequency and spending.

## Visualisation

Customer clusters were visualised using:

* Recency vs Frequency scatter plot
* Frequency vs Monetary scatter plot
* Number of customers per cluster bar chart

## Marketing Recommendations

* **VIP customers:** provide exclusive offers and loyalty rewards to retain them.
* **Loyal customers:** use personalised offers and cross-selling to increase their value.
* **Regular customers:** use promotions and product recommendations to increase purchase frequency.
* **At-risk customers:** use reactivation campaigns and special discounts to encourage them to return.

## Tools & Technologies

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* Jupyter Notebook

## Key Outcome

The project demonstrates how **RFM analysis and K-Means clustering can be used to segment customers based on purchasing behaviour and support targeted marketing strategies.**
