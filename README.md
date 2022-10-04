# Introduction
In this repository, I implemented c-means algorithm from scratch.
C-means algorithm is a fuzzy clustering method. Its logic is almost the same as k-means algorithm, but its improvement is that points are not forced to belong only to one cluster. They can belong to different clusters by different probabilities.
Different steps of this project are explained below.

## Implementation
To impelemnt this algorithm, following steps were taken.
1. Define number of clusters
2. Create random centroids for clusters
3. Determine the cluster (or clusters) of each data
4. Update the clusters' centroids based on their new data.
5. Go back to step 3 until the stop condition becomes true.

The first two steps are not very hard, the important parts of this algorithm are steps 3 and 4. Now, I am going to explain these steps.

### Determine the cluster (or clusters) of each data
To determine that each data belongs to what cluster (or clusters) we should look at each cluster as a fuzzy set. So each data belongs to all the clusters, but with different probabilities. In order to determine the degree to which each data belongs to each cluster, I used the following formula.


[<img src="https://github.com/kian79/Implement-C-Means-Algorithm/blob/main/Images/amount_of_belonging.png">]([http://google.com.au/](https://github.com/kian79/Implement-C-Means-Algorithm/blob/main/Images/amount_of_belonging.png))

In this formula, xk is the kth data, c is number of the clusters, Vi is the centroid of the ith cluster, and m is a parameter greater then one that we should determine for the algorithm. The above formula, determine the degree to which data belongs to each cluster, based on its distance from the centroid of that cluster and comparing it with its distance from other centroids.

### Update the clusters
In order to update the centroids of each custer based on clusters' new members, we should calculate the mean of all the data that belongs to the cluster and consider the output as the new centroid. Since in this algorithm, each data belongs to all the clusters, to calculate the centroid we should use weighted mean. This way, the data that belongs to a cluster more than other data play more important role in defining the centroid. The formula for this section is as below.


[<img src="https://github.com/kian79/Implement-C-Means-Algorithm/blob/main/Images/weighted_average.png">]([http://google.com.au/](https://github.com/kian79/Implement-C-Means-Algorithm/blob/main/Images/weighted_average.png))

### Stop Condition
We can stop the algorithm after a specific number of iterations. For example, we can assume that our clusters are stable after 100 iterations and stop the algorithm at that time.

### Loss Function
To make the clusters stable, our algorithm is solving a optimization problem. It minimizes the distance of each data from its centroid by minimizing the below loss function.


[<img src="https://github.com/kian79/Implement-C-Means-Algorithm/blob/main/Images/loss_function.png">]([http://google.com.au/](https://github.com/kian79/Implement-C-Means-Algorithm/blob/main/Images/loss_function.png))

### Determine number of the Clusters
To decide which c is better for our algorithm, I used the elbow method. In this method, I plotted the loss function for different values of c and chose the c that the cost function doesn't change too much after that.
For example, in the following plot I understood that after c=3 the cost dosn't change a lot. So clustered this data with 3 clusters.

The elbow plot:


[<img src="https://github.com/kian79/Implement-C-Means-Algorithm/blob/main/Images/elbow_data1.png">]([http://google.com.au/](https://github.com/kian79/Implement-C-Means-Algorithm/blob/main/Images/elbow_data1.png))

After using 3 clusters the clustering was as below.


[<img src="https://github.com/kian79/Implement-C-Means-Algorithm/blob/main/Images/data1_c3_plot.png">]([http://google.com.au/](https://github.com/kian79/Implement-C-Means-Algorithm/blob/main/Images/data1_c3_plot.png))

