---
title: overview
date: 2023-12-05T00:00:00-06:00
draft: false
weight: -1
---

# Abstract
In unsupervised machine learning, models are trained using data that consists only of *feature* values without any known *labels*. The models determine relationships between the features of the observations in the training data.

# Clustering [[Reference](https://learn.microsoft.com/en-us/training/modules/fundamentals-machine-learning/7-clustering)]
- Identifies similarities between observations based on their features and groups them into discrete clusters.
- The label is the cluster to which the observation is assigned based only on its features.
- Examples:
  - Flowers based on their size, number of leaves, and number of petals.
  - Groups of similar customers based on demographic attributes and purchasing behavior.

Clustering is similar to multi-class classification except that the classes are unknown. In some cases, clustering is used to determine classes that are
then used for training a classification model.

# Training Clustering Models
## K-Means algorithm
K-Means clustering is achieved with these steps:
1. The feature ($x$) values are vectorized to define $n$-dimensional coordinates (where $n$ is the number of features).
   1. In the flower example, there are two features: number of leaves ($x_1$), and number of petals ($x_2$).
   2. The resulting feature vector is $[x_1,x_2]$
2. The number of clusters you decide to use is $k$. $k$ points are plotted at random coordinates. These points become the center of each cluster (called *centroids*).
3. Each data point is assigned to its nearest centroid.
4. Each centroid is moved to the center of the data points assigned to it based on the mean distance between those points.
5. After the centroid is moved, the data points may now be closer to a *different* centroid. Those data points are reassigned to clusters based on the new closest centroid.
6. Steps 4 and 5 are repeated until the clusters become stable, or a predetermined maximum number of iterations is reached.

# Cluster Model Evaluation 
Evaluation of a clustering model is based on how well the resulting clusters are separated from one another.

Metrics:
- *Average distance to cluster center* — how close, on average, each point in the cluster is to the centroid of that cluster.
- *Average distance to other center* — how close, on average, each point in the cluster is to the centroid of all other clusters.
- *Maximum distance to cluster center* — the furthest distance between a point in the cluster and its centroid.
- *Silhouette* — a value between -1 and 1 that summarizes the ratio of distance between points in the same cluster and points in different clusters (the closer to 1, the better the cluster separation).