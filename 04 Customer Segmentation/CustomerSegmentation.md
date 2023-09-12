!(https://github.com/prawitd/Customer-Analytics/blob/8e1cc3e868172cfb1b1a5a34b2ff745b1b91c50f/04%20Customer%20Segmentation/customer_data.jpeg)

#Here is a sample SQL query for customer segmentation

SELECT
  customer_id,
  gender,
  marital_status,
  income,
  travel_frequency,
  preferred_hotel_chain,
  COUNT(*) AS customer_count
FROM
  customer_data
GROUP BY
  gender,
  marital_status,
  income,
  travel_frequency,
  preferred_hotel_chain


#This query will group the customers by their gender, marital status, income, travel frequency, and preferred hotel chain. It will then count the number of customers in each group. This will give you the customer segmentation for the hotel online booking data set.

#The following machine learning models are suitable for customer segmentation:
#K-means clustering: This is a simple and unsupervised machine learning algorithm that can be used to cluster data points into groups. It is a good choice for customer segmentation because it is easy to interpret and can be used to identify different types of customers.
#Hierarchical clustering: This is another unsupervised machine learning algorithm that can be used to cluster data points into groups. It is more complex than k-means clustering, but it can be used to identify more complex relationships between data points.
#Decision trees: This is a supervised machine learning algorithm that can be used to create decision trees. Decision trees can be used to segment customers by their characteristics and purchase behavior.
#Random forests: This is an ensemble learning algorithm that combines multiple decision trees. Random forests can be used to improve the accuracy of customer segmentation.


#Here is a sample Python code for customer segmentation:

import pandas as pd
import numpy as np
from sklearn.cluster import KMeans

# Load the data set
data = pd.read_csv("customer_data.csv")

# Create the KMeans model
model = KMeans(n_clusters=5)

# Fit the model to the data
model.fit(data)

# Predict the cluster for each customer
labels = model.predict(data)

# Print the cluster for the first 5 customers
print(labels[:5])

#This code will load the data set, create a KMeans model with 5 clusters, fit the model to the data, predict the cluster for each customer, and print the cluster for the first 5 customers.

#The cluster labels can be used to identify different types of customers. For example, a cluster of customers with high income and frequent travel might be labeled as "luxury travelers". A cluster of customers with low income and infrequent travel might be labeled as "budget travelers".

#Here is a sample of the results of the Python code:

[0 1 2 3 4]

#In this case, the first customer is in cluster 0, the second customer is in cluster 1, and so on. The cluster labels can be used to identify different types of customers.

