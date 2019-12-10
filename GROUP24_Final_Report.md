# Final Report (//TODO)

## By Hanqing Zhao, Jianing Wang, Shihui Zhu

* [Overview](#overview)

* [k-Means Clustering](#k-means-clustering)

* [Global k-Means Clustering](#global-k-means-clustering)

* [Fuzzy c-Means Clustering](#fuzzy-c-means-clustering)

* [Mixture of Gaussian Clustering](#mixture-of-gaussian-clustering)

## Overview

Clustering is a really useful machine learning technique for analyzing all kinds of data. It can help us to group certain data points that have similar properties in a large dataset, in order to grab information from it. In biological research, we often obtain lots of data from the experiments. In order to shuffle the useful information from the sea of data, it is crucial for us to correctly interpret the patterns behind it using clustering. We can use clustering method in gene expression data obtained from RNA sequencing, to discover potential groups of genes and samples, and predict the unknown functions of genes.
In this report, we are going to expand on what we have learned about k-means clustering in the class, introduce global k-means, fuzzy c-means clustering, and Mixture of Gaussian clustering methods. Additionaly, we will discuss how they are different and useful in genomic data analysis.

## *K*-Means Clustering

K-means clustering is a clustering algorithm that essentially partitions all data points into k clusters with locally optimal within-cluster sum of squared Euclidean distances1. The standard algorithm starts with a given initial set of k cluster centers:  
Step 1: For each point, find its closest cluster center and assign it to the closest cluster.  
Step 2: Update the cluster centers to be the average of points contained within them.  
Step 3: Stop if the algorithm converges (that is, the cluster assignments no longer change). Otherwise, go to Step 1.

Here is a demo:

![k-means demo](http://shabal.in/visuals/kmeans/random.gif)

## Global *K*-Means Clustering

As mentioned, k-means clustering results are sensitive to the initial choice of clusters therefore they are only reliable for analyzing small sets of data. To improve it, auxiliary incremental approaches are recently introduced to k-clustering algorithm, which are known as the global k-means clustering.  

One traditional way is to start from one cluster (centroid), and continuously adding new clustering center as the iteration proceeds. 

Step 1: Given the finite data set $A$, $\{a_1, a_2, \dots, a_m\}$, consisting of m n-dimensional elements, compute A’s center, set this as the initial center.  
Step 2: Let the rest ($k$-1)-partition centroids be $x_1, x_2, \dots, x_{k-1}$, compute $\overline{f_k}(y)$, $y \in \R^n$by comparing the minimum square distance between each point and the closest cluster center from $x_1, x_2, \dots, x_{k-1}$ with the square distance of each pair of data. So the point with the minimum fk(y)value would be the new cluster center for the next iteration.  
Step 3: Select $\{x_1, x_2, \dots, x_{k-1},y\}$ as a new starting point, apply the k-means algorithm. Then use the result as the input, go back to step 2.  
Step 4: Stop iteration if $\overline{f_k}(y)$ is smaller than a given tolerance value

## Fuzzy c-Means Clustering

The fuzzy c-means clustering (FCM), also referred to as soft k-means clustering, is a clustering algorithm that partitions the data set into c clusters while each data point may potentially belong to multiple clusters. Compared to the well-known k-means clustering, FCM introduces a new attribute for each data point: **membership**. The membership function evaluates the similarity between a data point to each cluster center, and it ranges between 0 and 1, where memberships close to zero indicates little similarity between the point and the center, while memberships close to one indicates a high degree of similarity between the sample and the cluster. The algorithm starts with a given initial set of *c* cluster centers:  

Step 0: Determine all parameters needed for the algorithm, and initialize $U^{(0)}$ membership matrix randomly  

* $U^{(t)}$ = the fuzzy c-partition of all data points after $t^{th}$ iterations)
* $N$ = the number of data points
* $~c~$ = the number of cluster centers
* $d_{ij}$ = Euclidean distance between $i^{th}$ data point and $j^{th}$ cluster center
* $~v_i$ = the $i^{th}$ cluster center
* $~m$ = weighting component, *aka* the fuzzifier; $m \in (1,\infty)$
* $\mu_{ij}$ = membership of $i^{th}$ data point to $j^{th}$ cluster center
* $~y_k$ = the $k^{th}$ data point  

Step 1: Compute the fuzzy memberships for each data point  

$$ \mu_{ij} = \Big( \sum_{k=1}^c (d_{ij}/d_{ik})^{\frac{2}{m-1}} \Big)^{-1} $$

Step 2: Update the cluster centers according to the membership matrix

$$ v_i = \sum_{k=1}^N (u_{ik})^my_k \Big/ \sum_{k=1}^k (u_{ik})^m $$

Step 3: If $|| U^{(t+1)}-U^{(t+1)}|| < \epsilon$, that is, the change made by this iteration is less than some termination criteria, the algorithm stops. Otherwise, go to Step 1.

The result of clustering may look like this:

![FCM](images/fcm.png)

## Mixture of Gaussian Clustering



```html
<img src="http://shabal.in/visuals/kmeans/random.gif" width=500 height=300>
```

![MOG](https://media1.tenor.com/images/909622ac2e9ec02a97d4ce9489798b1d/tenor.gif?itemid=15288262)

$$ \mu_{ij} = \Big( \sum_{k=1}^c (d_{ij}/d_{ik})^{\frac{2}{m-1}} \Big)^{-1} $$

$$ v_i = \sum_{k=1}^N (u_{ik})^my_k \Big/ \sum_{k=1}^k (u_{ik})^m $$

$||U^{(t+1)}-U^{(t+1)}|| < \epsilon$

ee.<sup>superscript</sup> 



![global-kmeans](images/global-kmeans.png)


|      K-means          |  GMM |
|:------------------------|:----------------------------:|
|![K-Means](images/kmeans.png)  |  ![MOG](images/mog.png)|
| Fig. Comparison of clustering using k-means and Mixture of Gaussian. The plot |

| ![time](images/fcm_vs_km_time.png)|
|:--|
| Fig. Comparison of average time for k-Means and FCM. The table on the top shows the average executation time by k-Means and FCM. The plot at the bottom shows average runtime of k-Means and FCM.|
