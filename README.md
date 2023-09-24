# RFM_Customer_Segmentation
----------------------------
This is a transnational data set which contains all the transactions occurring between 01/12/2010 and 09/12/2011 for a UK-based and registered non-store online retail. The company mainly sells unique all-occasion gifts. Many customers of the company are wholesalers.
Dataset source: http://archive.ics.uci.edu/dataset/352/online+retail

Feature Information:
InvoiceNo: Invoice number. Nominal, a 6-digit integral number uniquely assigned to each transaction. If this code starts with letter 'c', it indicates a cancellation.
StockCode: Product (item) code. Nominal, a 5-digit integral number uniquely assigned to each distinct product.
Description: Product (item) name. Nominal.
Quantity: The quantities of each product (item) per transaction. Numeric.
InvoiceDate: Invoice Date and time. Numeric, the day and time when each transaction was generated.
UnitPrice: Unit price. Numeric, Product price per unit in sterling.
CustomerID: Customer number. Nominal, a 5-digit integral number uniquely assigned to each customer.
Country: Country name. Nominal, the name of the country where each customer resides.

RFM Analysis
-------------
The RFM model is a marketing analysis framework used to segment and understand customer behavior based on three key factors: Recency, Frequency, and Monetary Value. It is commonly employed by businesses to categorize their customer base into distinct groups, which can then be used for targeted marketing strategies and personalized communication.

Recency – How recently did the customer purchase
Frequency – How often do they purchase
Monetary – How much do they spend?
Recency - In order to find the recency value of each customer, we need to determine the last invoice date as the current date and subtract the last purchasing date of each customer from this date.

Frequency - In order to find the frequency value of each customer, we need to determine how many times the customers make purchases.

Monetary - In order to find the monetary value of each customer, we need to determine how much do the customers spend on purchases.

By analyzing these three dimensions, businesses can segment their customer base into various groups. Here’s a general breakdown of how this segmentation might occur

K-Means Clustering
------------------
Clustering is an unsupervised machine learning technique used to uncover underlying groups within data. One common approach for this is the K-means clustering algorithm, which is frequently employed to identify distinct segments within a customer dataset.

Our dataset is large so Hierarchical clustering is not well suited for analysis.
During the process of building a KMeans model, it’s essential to specify the number of clusters beforehand. To determine the most appropriate number of clusters, various methods like silhouette analysis and the elbow method can be utilized. These techniques aid in selecting the optimal number of clusters that best represents the inherent structure of the data.

Elbow Method

One of the most common ways to choose a value for K is known as the elbow method, which involves creating a plot with the number of clusters on the x-axis and the total within sum of squares on the y-axis and then identifying where an “elbow” or bend appears in the plot.

The point on the x-axis where the “elbow” occurs tells us the optimal number of clusters to use in the k-means clustering algorithm.

![image](https://github.com/hemanthm01/RFM_Customer_Segmentation/assets/120650945/a7a93a8f-5c49-405e-aec7-743109fe9aa1)

Silhouette Analysis
-------------------
Silhouette Coefficient The overall silhouette score for a clustering can be computed by taking the
average silhouette coefficient across all data points. This score provides insight into how well the
data is clustered and whether the chosen number of clusters is appropriate. Higher silhouette scores
indicate better-defined clusters.

![image](https://github.com/hemanthm01/RFM_Customer_Segmentation/assets/120650945/52d2143a-2a4b-46f8-aaec-9716324e1a29)

Outcomes by Elbow method and Silhoutte score
----------------------------------------------

Based on the results obtained, selecting the highest silhouette score suggests that there could be two distinct clusters. On the other hand, choosing the lowest elbow squared error indicates that there might be around ten clusters.

As a result, in order to determine the most suitable number of clusters based on graphics, it is necessary to carefully consider the outcomes, and it appears that opting for a solution with four different cluster groups could be a balanced approach. K=4 have optimal score . Let’s visualize these clusters.

![image](https://github.com/hemanthm01/RFM_Customer_Segmentation/assets/120650945/0d528c08-7e39-4ce1-9a06-a8f6c3deffee)


DBSCAN (Density-Based Spatial Clustering of Applications with Noise) Clustering
--------------------------------------------------------------------------------
DBSCAN Clustering Algorithm K-Means and Hierarchical Clustering struggle with creating clusters of complex shapes and adapting to varying densities. In contrast, DBSCAN excels by grouping densely packed data points into clusters and effectively identifying clusters in large spatial datasets based on local density. The most exciting feature of DBSCAN clustering is that it is robust to outliers.

![image](https://github.com/hemanthm01/RFM_Customer_Segmentation/assets/120650945/92389154-7d4b-41eb-a0f8-edeedfbf6cbe)


