# Customer Segmentation
Step 1: Data Cleaning:
1. Perform a preliminary data inspection and data cleaning.
a. Check for missing data and formulate an apt strategy to treat them.
b. Remove duplicate data records.
c. Perform descriptive analytics on the given data.
- Calculating the missing value % Contribution in Dataset
- Dropping the missing values in the dataset
- Changing the datatype as per business understanding
Step 2: Data Preparation
We are going to analysis the Customers based on below 3 factors:
•	R (Recency): Number of days since last purchase
•	F (Frequency): Number of tracsactions
•	M (Monetary): Total amount of transactions (revenue contributed)
-	Create New Attribute : Monetary
-	Create New Attribute: Frequency
-	Merge merge dataset 
-	Create New Attribute : Recency
-	Convert datetime to proper datatype
-	Compute the last date to know the last transaction date
-	Compute the difference between max date and transaction date
-	Compute the last transaction date to get the recency of customers
-	Extract the exact days
-	Merge the datasets to get the final RFM model

There are 2 types of outliers and we will treat outliers as it can skew our dataset
1.	Statistical
2.	Domain specific

-	Outlier Analysis of amount, frequency and recency
-	Removing (Statistical) outliers for Amount
-	Removing (Statistical) outliers for Frequency
-	Removing (Statistical) outliers for Recency

Rescaling the attribute
It is extremely important to rescale the variable so that they have comparable scale. There are two common ways of rescaling:
1.	Min-Max Scaler
2.	Standardization (mean-0, sigma-1)
Here, we will use Standardisation

-	Rescaling the attributes, Instantiate Standard scaler and Fit-Transform


 
Step 4 : Building the Model
K-means Clustering
K-means is one of the simplest and popular unsupervised machine learning algorithms.
The algorightm works as follows:
•	first we initialise K points, called means, randomly.
•	We categorize each item to its closest mean and we update the mean's coordinates, which we are the averages of the items categorised in that mean so far.
•	We repeat the process for given number of iterations and at the end, we have our clusters
-	K-means with some arbitrary k value
-	Elbow Curve / SSD
Silhouette Analysis
silhouette score = (p−q)/(max(p,q))
p is the mean distance to the points in the nearest cluster that the data point is not a part of q is the mean intra-cluster distance to all the points in its own cluster.
•	The value of the silhouette score range lies between -1 to 1
•	A score closer to 1 indicates that the data point is very similar to other data points in the clusters
•	A score closer to -1 indicates that the data point is not similar to the data points in its cluster
Ans: For n_clusters = 2, the silhouette score is 0.541842117113117
For n_clusters = 3, the silhouette score is 0.5084896296141937
For n_clusters = 4, the silhouette score is 0.48175475872338963
For n_clusters = 5, the silhouette score is 0.4639646901931184
For n_clusters = 6, the silhouette score is 0.4173990086284566
For n_clusters = 7, the silhouette score is 0.416300170967371
For n_clusters = 8, the silhouette score is 0.4025418765314729
-	Final model with K=3
-	Create Boxplot to visualize ClusterId  Vs Frequency
-	Create Boxplot to visualise ClusterId Vs Frequency
-	Create Boxplot to visualise ClusterId Vs Recency
 
Hierarchical Clustering
Hierarchical Clustering involves creating have a predetermined ordering from top to bottom. For example, all files and folders on the harddisk are organized in a hierarchy. There are two types of hierarchical clustering:
1.	Divisive
2.	Agglomerative
Single linkage:
In Single linkage hierarchical clustering, the distance between the 2 clusters is defined as the shortest distance between two points in each cluster. For example, distance between clusters r and s to the left is equal to the length of the arrow between their two closest point
 
Complete Linkage
In complete linkage heirarchical clustering, the distance between two clusters is defined as the longest distance between two points in each cluster. for example, the distance between clusters r and s to the left is equal to the length of the arrow between their two furthest points.
 
 
Average Linkage:
In average linkage heirarchical clustering, the distance between two clusters is defined as the average distance between each point is one cluster to every point is the other cluster. For example, the distance between clusters r and s to the left is equal to the average length each arrow between connecting the points of one cluster to the other.
 

Step 5: Final Analysis
Inference:
K-means clustering with 3 cluster ids:
•	Customers with cluster id 2 are the customers with high amount of transactions as compared to other customers
•	Customers with cluster id 2 are the frequent buyes
•	Customers with cluster id 0 are not recent buyers and hence of least of importance from business point of view
Hiearchical Clustering with 3 Cluster Ids:
•	Customers with Cluster_labels 2 are the customers with high amount of transactions as compared to other customers
•	Customers with cluster_labels 2 are frequent buyers
•	Customers with cluster_labels 0 are not recent buyers and hence least of importance from business point of view
