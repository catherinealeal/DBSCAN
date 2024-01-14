# DBSCAN

## Goal 

DBSCAN creates clusters based on the density of the points in the vicinity of the data.

The goal of this project is to implement the DBSCAN algorithm via function generation and compares the results to sklearn's DBSCAN implementation. Also compare the results of the DBSCAN clustering to the clustering via sklearn's K-Means function. 

## Load data 

The data used here is a small, 2-D dataset curated to test clustering algorithms. 

[Dataset](https://gist.githubusercontent.com/yanyanzheng96/c4bf88d73e03305cc0e1abd0a8a8e185/raw/c15f0f59d06ccbe9e708eddaf361cc33c19b1ec6/data_dbscan.csv)

## K-Means clustering with sklean 

Using k = 2. 

<img width="502" alt="Screenshot 2024-01-14 at 12 58 24 PM" src="https://github.com/catherinealeal/DBSCAN/assets/100166102/e50d723f-b479-4cbc-8782-b58e22a5ecea">

K-means clustering uses centroids and a distance measure to cluster points, so clusters will take on a circular shape. In this case, the data is clustered in curved lines rather than circles, so the k-means algorithm is not ideal for this data and generates many misclassifications. 

## Function to implement range query 

This function takes in a dataframe containing all of the points in our data set (df_data), the point (Q) represented by it's index in the data frame (q_index), and a floating point value that indicates the radius from point Q to search for neighbors (eps). It will return the slice of df_data containing all the points within eps distance of Q, including Q. 

The distance measure used here will be set as Euclidean distance. 

<img width="478" alt="Screenshot 2024-01-14 at 12 59 02 PM" src="https://github.com/catherinealeal/DBSCAN/assets/100166102/0498dd01-4de1-422e-8b9e-7994ff3912e5">

## Function to implement DBSCAN 

This function accepts a dataframe of points to be clustered (df_data), a floating point that defines the radius of search (eps), and an integer that defines the minimum points required for a cluster (minPts). It returns a series of cluster assignments of the same length as df_data. 

If the data is classified as noise, the cluster assignment is 0, and all of the clusters will have a label of 1-k, were k is derived in the function and represents the total number of clusters found. 

The distance measure used will be set as Euclidean distance. 

Parameters: 
- eps = 0.23 
- minPts = 6

<img width="489" alt="Screenshot 2024-01-14 at 12 59 45 PM" src="https://github.com/catherinealeal/DBSCAN/assets/100166102/270f9bb9-1595-4628-b2ee-24f7373c436f">

## Compare results to sklearn

<img width="482" alt="Screenshot 2024-01-14 at 1 01 33 PM" src="https://github.com/catherinealeal/DBSCAN/assets/100166102/675ce657-e05a-47ab-a3d7-c2f3d09afc2f">

Both implementations produced the same results: 2 clusters and 3 noise points. Based on this, I would say the manual and automatic DBSCAN algorithms performed with equal efficacy.

## View full notebook [here](https://github.com/catherinealeal/DBSCAN/blob/5164ee5e68175649e7186b949ac86993ecfa9b57/DBSCAN.ipynb)
