Car Clustering using K-Means

Overview

This graded assessment is part of the Foundations of Machine Learning (C4M6 - K-Means Clustering) module of the Master’s in Machine Learning and AI program.

The objective of this notebook is to perform Unsupervised Learning using the K-Means clustering algorithm and identify natural groups of cars based on their characteristics.

The clustering is performed on four numerical features:

* Engine Size
* Horsepower
* City MPG
* Highway MPG

Since clustering is an unsupervised learning technique, there is no target variable. The algorithm discovers hidden structures in the data automatically.

⸻

Dataset

The dataset contains specifications of different cars.

Dataset Summary

Property	Value
Total Samples	205
Total Features	4
Target Variable	None
Learning Type	Unsupervised

Features Used

Feature	Description
enginesize	Engine size of the car
horsepower	Engine horsepower
citympg	Mileage in city driving
highwaympg	Mileage in highway driving

⸻

Feature Scaling

Since K-Means relies heavily on Euclidean distance, feature scaling is an essential preprocessing step.

The features were standardized using:

StandardScaler()

This transforms all features to have:

* Mean = 0
* Standard Deviation = 1

Scaling prevents features with larger magnitudes from dominating the clustering process.

⸻

K-Means Clustering

The clustering was performed using:

KMeans()

with the following parameters:

Parameter	Value
init	random
random_state	9001
n_init	20
K Values Tested	2, 3, 4, 5, 6

For each value of K, the following metrics were computed:

* Inertia (WCSS)
* Silhouette Score
* Cluster Counts

⸻

Results

K	Inertia (WCSS)	Silhouette Score
2	385.23	0.4708
3	234.45	0.4537
4	174.14	0.4337
5	133.71	0.4201
6	111.62	0.4148

⸻

Cluster Counts

K = 2

Cluster	Samples
0	85
1	120

⸻

K = 3

Cluster	Samples
0	61
1	98
2	46

⸻

K = 4

Cluster	Samples
0	15
1	41
2	88
3	61

⸻

K = 5

Cluster	Samples
0	15
1	52
2	41
3	80
4	17

⸻

K = 6

Cluster	Samples
0	15
1	46
2	63
3	17
4	33
5	31

⸻

Elbow Method

To identify the optimal number of clusters, the Elbow Method was applied.

Inertia Drops

Transition	Inertia Drop
2 → 3	150.78
3 → 4	60.31
4 → 5	40.43
5 → 6	22.09

The largest drop in inertia occurred between:

K = 2
and
K = 3

Therefore:

Optimal K = 2

according to the Elbow Method.

![alt text](image.png)

⸻

Silhouette Analysis

The Silhouette Score measures:

* Cluster compactness
* Separation between clusters

Higher values indicate better clustering.

The highest silhouette score obtained was:

0.4708
for
K = 2

This confirms that:

K = 2

produces the most compact and well-separated clusters among the tested values.

![alt text](image-1.png)

⸻

Interpretation

Both evaluation methods:

* Elbow Method
* Silhouette Score

suggest:

Optimal Number of Clusters
=
2

This indicates that the cars naturally divide into two major groups based on:

* Engine Size
* Horsepower
* City Mileage
* Highway Mileage

These clusters may roughly represent:

Economy Cars
and
Performance / Larger Cars

although K-Means itself does not assign semantic labels to clusters.

⸻

Key Learnings

This assessment demonstrates several important concepts in Unsupervised Learning:

K-Means Clustering

* Groups similar observations together
* Uses Euclidean distance
* Iteratively updates cluster centroids
* Minimizes Within Cluster Sum of Squares (WCSS)

Feature Scaling

* Essential before applying K-Means
* Prevents large-scale features from dominating distances

Elbow Method

* Helps determine an appropriate value of K
* Selects the point after which improvements become marginal

Silhouette Score

* Measures cluster quality
* Higher scores indicate better-defined clusters

⸻

Conclusion

K-Means clustering was successfully applied to the car dataset after feature scaling.

The analysis showed:

* Inertia decreases as K increases.
* Silhouette score decreases gradually after K = 2.
* Both Elbow Method and Silhouette Analysis identify:

Optimal K = 2

This assignment demonstrates how K-Means can uncover hidden structure in unlabeled datasets and highlights the importance of selecting an appropriate number of clusters using evaluation metrics.