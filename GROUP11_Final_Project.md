# Machine Learning in Bioinformatics 

Justin Huynh 

Kevin Ramos 

Aaron Ho

University of California, San Diego

---

## Introduction

Machine learning has become an important topic of discussion in research because it can be used to analyze large datasets and discover specific patterns that are not immediately visible to the human eye. The field of Bioinformatics has increasingly begun to use machine learning methods to gain greater insight and make predictions about complex biological processes in organisms. Specifically, machine learning methods are being used in genomics to analyze DNA sequences in various ways including finding subclasses of diseases, determining ancestry of individuals, predicting transcription factor binding sites, and predicting cell cycle phases. In discussing machine learning methods, it is important to distinguish two different types of learning: *supervised and unsupervised learning*.

In **supervised learning**, the model is trained using a labeled dataset. In other words, the correct labels are known and act as a “teacher” that corrects the algorithm during its training. The algorithm iteratively makes predictions on the training dataset until it reaches an acceptable level of performance. Supervised learning problems can be fall under classification, in which the algorithm's output value is a category.

In **unsupervised learning**, the input data does not have corresponding labels. The goal of this type of learning is to model the distribution of the dataset in order to gain greater insight about the data. Unsupervised learning problems can fall under clustering, which is useful for uncovering groups within the data. 

## Clustering

Clustering is a useful technique that groups similar data points in such a way that similar points will be grouped closer to one another, thus forming a cluster. The two clustering techniques that we will discuss are hierarchical clustering and K-means clustering. 

---

### Hierarchical Clustering 

In Hierarchical clustering, similarity (distance) between points is calculated to cluster the most similar points together. This process is repeated until only a single cluster is left. Essentially, the algorithm builds a hierarchy of clusters.  
The algorithm for Hierarchical Clustering is as follows:

1. Calculate the similarity (distance) between all possible combinations of two profiles.
2. Place each profile in a separate cluster.
3. Group the two most similar clusters into a new cluster.
4. Calculate the similarity (distance) between the new cluster and all remaining clusters.
5. Repeat steps 3 and 4 until all profiles are in one large cluster.

### K-means Clustering

In K-means clustering, we choose an arbitrary “K” value which represents the number of clusters. Then, K points are selected to serve as a mean for each of the K clusters. The algorithm iteratively reassigns points to new clusters with the goal of minimizing the point’s distance to the cluster’s mean. 

The algorithm for K-means clustering is as follows:
1. Select a value K which represents the number of clusters.
2. Select centroid points for the K clusters.
3. Assign all points to their closest cluster centroid.
4. Calculate the new centroids for the newly formed clusters using.
5. Repeat steps 3 and 4.

The K-means algorithm terminates under the following conditions:
1. The centroid of newly formed clusters does not change.
2. The points do not change clusters.
3. The maximum number of iterations has been achieved.

With K-means clustering, the results can vary based on the “K” value that is chosen as well as the initial points for the clusters. In contrast, Hierarchical clustering can produce more intuitive results because it simply relies on calculating similarity (distances) between points and does not require choosing an arbitrary “K”. [1]

## Applications of Machine Learning to Biological Big Data and Bioinformatics


## Challenges of Machine Learning Approaches in Bioinformatics


## References

