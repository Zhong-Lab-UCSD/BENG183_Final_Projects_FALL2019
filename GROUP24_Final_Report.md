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

Step 1: Given the finite data set <img src="/tex/53d147e7f3fe6e47ee05b88b166bd3f6.svg?invert_in_darkmode&sanitize=true" align=middle width=12.32879834999999pt height=22.465723500000017pt/>, <img src="/tex/9233262f58a431ec864c8dc2308dad7b.svg?invert_in_darkmode&sanitize=true" align=middle width=113.57686394999999pt height=24.65753399999998pt/>, consisting of m n-dimensional elements, compute A’s center, set this as the initial center.  
Step 2: Let the rest (<img src="/tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/>-1)-partition centroids be <img src="/tex/7e721fe1c7f64784d20cd0f496e836db.svg?invert_in_darkmode&sanitize=true" align=middle width=110.8617807pt height=14.15524440000002pt/>, compute <img src="/tex/2bfa3db256fd1625d91ab9bc03acd9bc.svg?invert_in_darkmode&sanitize=true" align=middle width=37.57057094999999pt height=28.091038800000003pt/>, <img src="/tex/88b6fa172b4ea7646e022c6707d88558.svg?invert_in_darkmode&sanitize=true" align=middle width=32.30026799999999pt height=21.839370299999988pt/>by comparing the minimum square distance between each point and the closest cluster center from <img src="/tex/7e721fe1c7f64784d20cd0f496e836db.svg?invert_in_darkmode&sanitize=true" align=middle width=110.8617807pt height=14.15524440000002pt/> with the square distance of each pair of data. So the point with the minimum fk(y)value would be the new cluster center for the next iteration.  
Step 3: Select <img src="/tex/65cdf6ecba6cf2ad3ea727e92424763a.svg?invert_in_darkmode&sanitize=true" align=middle width=144.07717499999998pt height=24.65753399999998pt/> as a new starting point, apply the k-means algorithm. Then use the result as the input, go back to step 2.  
Step 4: Stop iteration if <img src="/tex/2bfa3db256fd1625d91ab9bc03acd9bc.svg?invert_in_darkmode&sanitize=true" align=middle width=37.57057094999999pt height=28.091038800000003pt/> is smaller than a given tolerance value

## Fuzzy c-Means Clustering

The fuzzy c-means clustering (FCM), also referred to as soft k-means clustering, is a clustering algorithm that partitions the data set into c clusters while each data point may potentially belong to multiple clusters. Compared to the well-known k-means clustering, FCM introduces a new attribute for each data point: **membership**. The membership function evaluates the similarity between a data point to each cluster center, and it ranges between 0 and 1, where memberships close to zero indicates little similarity between the point and the center, while memberships close to one indicates a high degree of similarity between the sample and the cluster. The algorithm starts with a given initial set of *c* cluster centers:  

Step 0: Determine all parameters needed for the algorithm, and initialize <img src="/tex/7f4a7f354755718b4f9f1d20ee6befdc.svg?invert_in_darkmode&sanitize=true" align=middle width=29.842518749999986pt height=29.190975000000005pt/> membership matrix randomly  

* <img src="/tex/edf4afd6c1c54a275a8eb945d2f18e47.svg?invert_in_darkmode&sanitize=true" align=middle width=28.25576324999999pt height=29.190975000000005pt/> = the fuzzy c-partition of all data points after <img src="/tex/f271d732e18c7d4b41283a542206f6ec.svg?invert_in_darkmode&sanitize=true" align=middle width=18.59791559999999pt height=27.91243950000002pt/> iterations)
* <img src="/tex/f9c4988898e7f532b9f826a75014ed3c.svg?invert_in_darkmode&sanitize=true" align=middle width=14.99998994999999pt height=22.465723500000017pt/> = the number of data points
* <img src="/tex/bb4927a015f350a51aa5add94cc4b125.svg?invert_in_darkmode&sanitize=true" align=middle width=7.113805050000002pt height=14.15524440000002pt/> = the number of cluster centers
* <img src="/tex/2ccee0b78bcd2047f49b3b53962d20a4.svg?invert_in_darkmode&sanitize=true" align=middle width=19.311372299999988pt height=22.831056599999986pt/> = Euclidean distance between <img src="/tex/3def24cf259215eefdd43e76525fb473.svg?invert_in_darkmode&sanitize=true" align=middle width=18.32504519999999pt height=27.91243950000002pt/> data point and <img src="/tex/95291b39ba5d9dba052b40bf07b12cd2.svg?invert_in_darkmode&sanitize=true" align=middle width=20.37223649999999pt height=27.91243950000002pt/> cluster center
* <img src="/tex/dfe1e706ec872f8f4e70b7fd7d0d1be5.svg?invert_in_darkmode&sanitize=true" align=middle width=12.6189657pt height=14.15524440000002pt/> = the <img src="/tex/3def24cf259215eefdd43e76525fb473.svg?invert_in_darkmode&sanitize=true" align=middle width=18.32504519999999pt height=27.91243950000002pt/> cluster center
* <img src="/tex/ca86770189c155d1bd7603cb0bda6c93.svg?invert_in_darkmode&sanitize=true" align=middle width=14.433101100000004pt height=14.15524440000002pt/> = weighting component, *aka* the fuzzifier; <img src="/tex/c89ebbe8796f8d733c509da65324e25d.svg?invert_in_darkmode&sanitize=true" align=middle width=79.2731676pt height=24.65753399999998pt/>
* <img src="/tex/e734211e84b9554fd8c03c3065a7703d.svg?invert_in_darkmode&sanitize=true" align=middle width=20.66033309999999pt height=14.15524440000002pt/> = membership of <img src="/tex/3def24cf259215eefdd43e76525fb473.svg?invert_in_darkmode&sanitize=true" align=middle width=18.32504519999999pt height=27.91243950000002pt/> data point to <img src="/tex/95291b39ba5d9dba052b40bf07b12cd2.svg?invert_in_darkmode&sanitize=true" align=middle width=20.37223649999999pt height=27.91243950000002pt/> cluster center
* <img src="/tex/9bff5b69509474d890ac3b247f6d5bf9.svg?invert_in_darkmode&sanitize=true" align=middle width=15.325460699999997pt height=14.15524440000002pt/> = the <img src="/tex/448aa5c656d95a0430b90ac5ded7840c.svg?invert_in_darkmode&sanitize=true" align=middle width=21.737180849999987pt height=27.91243950000002pt/> data point  

Step 1: Compute the fuzzy memberships for each data point  

<p align="center"><img src="/tex/7e7f5a756250695739067a267e57aeba.svg?invert_in_darkmode&sanitize=true" align=middle width=198.30180479999999pt height=45.2741091pt/></p>

Step 2: Update the cluster centers according to the membership matrix

<p align="center"><img src="/tex/a5db1d9a8cd6954654a6611206a242a3.svg?invert_in_darkmode&sanitize=true" align=middle width=209.41944045pt height=48.3106437pt/></p>

Step 3: If <img src="/tex/ae2d2999dad9c805927593c7eb415152.svg?invert_in_darkmode&sanitize=true" align=middle width=158.38923044999999pt height=29.190975000000005pt/>, that is, the change made by this iteration is less than some termination criteria, the algorithm stops. Otherwise, go to Step 1.

The result of clustering may look like this:

![FCM](images/fcm.png)

## Mixture of Gaussian Clustering



```html
<img src="http://shabal.in/visuals/kmeans/random.gif" width=500 height=300>
```

![MOG](https://media1.tenor.com/images/909622ac2e9ec02a97d4ce9489798b1d/tenor.gif?itemid=15288262)

<p align="center"><img src="/tex/7e7f5a756250695739067a267e57aeba.svg?invert_in_darkmode&sanitize=true" align=middle width=198.30180479999999pt height=45.2741091pt/></p>

<p align="center"><img src="/tex/a5db1d9a8cd6954654a6611206a242a3.svg?invert_in_darkmode&sanitize=true" align=middle width=209.41944045pt height=48.3106437pt/></p>

<img src="/tex/86148e50b9dc1d12bf05cb58feb530e5.svg?invert_in_darkmode&sanitize=true" align=middle width=158.38923044999999pt height=29.190975000000005pt/>

ee.<sup>superscript</sup> 



![global-kmeans](images/global-kmeans.png)


|      K-means          |  GMM |
|:------------------------|:----------------------------:|
|![K-Means](images/kmeans.png)  |  ![MOG](images/mog.png)|
| Fig. Comparison of clustering using k-means and Mixture of Gaussian. The plot |

| ![time](images/fcm_vs_km_time.png)|
|:--|
| Fig. Comparison of average time for k-Means and FCM. The table on the top shows the average executation time by k-Means and FCM. The plot at the bottom shows average runtime of k-Means and FCM.|
