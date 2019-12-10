# Different Clustering Algorithms in Biological Data Analysis

## By Hanqing Zhao, Jianing Wang, Shihui Zhu

* [Overview](#overview)

* [k-Means Clustering](#k-means-clustering)

* [Global k-Means Clustering](#global-k-means-clustering)

* [Fuzzy c-Means Clustering](#fuzzy-c-means-clustering)

* [Mixture of Gaussian Clustering](#mixture-of-gaussian-clustering)

* [Discussion](#discussion)  

* [Application in RNA-seq Data](#application-in-rna-seq-data)

* [Reference](#reference)

## Overview

Clustering is a really useful machine learning technique for analyzing all kinds of data. It can help us to group certain data points that have similar properties in a large dataset, in order to grab information from it. In biological research, we often obtain lots of data from the experiments. In order to shuffle the useful information from the sea of data, it is crucial for us to correctly interpret the patterns behind it using clustering. We can use clustering method in gene expression data obtained from RNA sequencing, to discover potential groups of genes and samples, and predict the unknown functions of genes.
In this report, we are going to expand on what we have learned about k-means clustering in the class, introduce global k-means, fuzzy c-means clustering, and Mixture of Gaussian clustering methods. Additionaly, we will discuss how they are different and useful in genomic data analysis.

## *K*-Means Clustering

K-means clustering is a clustering algorithm that essentially partitions all data points into k clusters with locally optimal within-cluster sum of squared Euclidean distances. The standard algorithm starts with a given initial set of k cluster centers [11]:

Step 1: For each point, find its closest cluster center and assign it to the closest cluster.  
Step 2: Update the cluster centers to be the average of points contained within them.  
Step 3: Stop if the algorithm converges (that is, the cluster assignments no longer change). Otherwise, go to Step 1.

Here is a GIF demo:

![k-means demo](https://shabal.in/visuals/kmeans/random.gif)

<img src="http://shabal.in/visuals/kmeans/random.gif" width=700 height=500>

## Global *K*-Means Clustering

As mentioned, k-means clustering results are sensitive to the initial choice of clusters therefore they are only reliable for analyzing small sets of data. To improve it, auxiliary incremental approaches are recently introduced to k-clustering algorithm, which are known as the global k-means clustering.  

One traditional way is to start from one cluster (centroid), and continuously adding new clustering center as the iteration proceeds. 

Step 1: Given the finite data set $A$, $\{a_1, a_2, \dots, a_m\}$, consisting of m n-dimensional elements, compute A’s center, set this as the initial center.  
Step 2: Let the rest ($k$-1)-partition centroids be $x_1, x_2, \dots, x_{k-1}$, compute $\overline{f_k}(y)$, $y \in \R^n$by comparing the minimum square distance between each point and the closest cluster center from $x_1, x_2, \dots, x_{k-1}$ with the square distance of each pair of data. So the point with the minimum $\overline{f_k}(y)$ value would be the new cluster center for the next iteration.  
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

The Mixture of Gaussian clustering method is a way to cluster data points not only by the means, but also by variance. Therefore, it can make the cluster more correctly in some circumstances. Gaussian Mixture Models (GMMs) assume that there are a certain number of Gaussian distributions, and each of these distributions represents a cluster. Hence, a Gaussian Mixture Model tends to group the data points belonging to a single distribution together.

GMM is a probabilistic model that uses soft clustering method to distribute the points in different clusters. Soft clustering, also known as fuzzy clustering or soft k-means, is a form of clustering method in which one data point can belong to more than one cluster. The GMM uses the probabilistic density function in a 3D gaussian distribution is given by:

$$ f(x|\mu, \Sigma)=\frac{1}{\sqrt{2\pi|\Sigma|}}e^{\frac{1}{2}(x-\mu)^t \Sigma^{-1}(x-\mu)}$$

* $x$ = the input vector. 
* $\mu$ = 2-D mean vector
* $\Sigma$ = 2 $\times$ 2 covariance matrix

Therefore, when we cluster the datasets in a 2 dimensional plot, we will define $k$ clusters, so we will have a mixture of $k$ Gaussian distributions, with each of them having a mean vector and a variance matrix.  

Since we do not know these mean and variance because we do not know which Gaussian generated which data point, these parameters are calculated by a process called Expectation-Maximization (EM), which involves two steps --- the E-step and the M-step. We also have a parameter called $\Pi$ which represent the density of the distribution.

During the E-step, we compute the responsibilities for each Gaussian for each datapoint. The responsibility is calculated by dividing the Probability of $X_i$ belongs to cluster $c$ by the Sum of probability $X_i$ belongs to $c_1,c_2,\dots,c_k$. This value will be big if the point is assigned to the correct clusterm and low otherwise.

During the M-step, we modify the parameters of each Gaussian to maximize the likelihood for the responsibility weighted data. The density $\Pi$, mean $\mu$ and the covariance matrix $\Sigma$ are updated until convergence. They are updated following the manner below:

$$ \Pi = \frac{\#points~assigned~to~cluster}{Total~\#points}$$  

$$ \mu = \frac{1}{\#points~assigned~to~cluster}\Sigma_ir_{ic}x_i$$  

$$ \Sigma_c = \frac{1}{\#points~assigned~to~cluster}\Sigma_ir_{ic}(x_i-\mu_c^T)(x_i-\mu_c)$$

Here is a GIF demo for the algorithm:

![MOG](https://media1.tenor.com/images/909622ac2e9ec02a97d4ce9489798b1d/tenor.gif?itemid=15288262)

## Discussion

### Limitations

Standard *k*-means clustering requires a careful selection of initial cluster centers. A different initialization may yield to a different number of iterations required for convergence, and a different clustering results. However, in some cases, the algorithm may not converge at all. In addition, the algorithm produces a clustering that attains local optimum, and more importantly, there may be different cluster assignments that have the same optimal scores [11]. Last but not least, the standard k-means clustering is vulnerable to the noise, thus its reliability is compromised provided the data is fuzzy.

### Comparions between *k*-means and FCM

Both k-means and FCM are partition-based clustering algorithm, and they work in a similar iterative fashion. The key difference between FCM and k-means is that using FCM, each data points may belong to multiple clusters based on the computed membership values. These fuzzy classification makes the clustering less vulnerable to noise if the input data is a bit fuzzy. For instance, when clustering of microarray data, k-means clustering may not work well because it does not provide information about the influence of a given gene for the overall shape of clusters. On the other hand, FCM is one fuzzy partitioning method and can attribute cluster memberships to genes [4].

However, as FCM is a bit more complex than k-means, it has a slower runtime compared to k-means clustering. As Velmurugan performed comparative analysis of k-means and FCM on telecommunication data [11], he pointed out that k-means runs significantly faster than FCM (Fig. X).

| ![time](images/fcm_vs_km_time.png)|
|:--|
| Fig. Comparison of average time for k-Means and FCM. The table on the top shows the average executation time by k-Means and FCM. The plot at the bottom shows average runtime of k-Means and FCM.|

### Comparison between *k*-means and global *k*-means

Because global *k*-means clustering involves a series of computation of the auxiliary function $\overline{f_k}(y)$, which produces an affinity matrix in every iteration, it requires longer runtime and greater computation power comparing with the standard *k*-means clustering. However, this gives a much better set of centroids for initial *k*-clusters because at each iteration the cluster centers can be refined according to the previous ones.

### Comparison between GMM and *k*-means

Although *k*-means clustering method is widely used in biological data analysis, it is also simple to understand and implement, it has certain drawbacks and limitations that we need to be aware of. Firstly of all, *k*-means is hard clustering, which means one data point can only belong to one specific cluster, so it sometimes cannot handle dataset with noise as well as soft clustering method such as fuzzy *c*-means and GMM. Secondly, comparing k-means and GMM, k-means uses distance based model while GMM uses distribution-based model. *K*-means will attempt to group the data points in a circular form because the means is calculated by Euclidean distance. Therefore, *k*-means fails to identify the correct cluster when the data points are not in circular fashion, which is shown in the picture below.

Here is an example of how k-means clustering does not perform as well as the mixture of Gaussian clustering method, because the dataset not only need to consider mean, but also need to consider variance.

| ![kmeans_vs_GMM](images/kmeans_vs_gmm.png)|
|:--|
| Fig X. Comparion of clustering results. (a) The clusters generated by *k*-means. (b)The clusters generated by GMM.|

### Real Case Analysis and Comparison of the Clustering methods

## Application in RNA-seq Data

```html
<img src="http://shabal.in/visuals/kmeans/random.gif" width=500 height=300>
```

## Reference

1. Andrews, Tallulah S., Hemberg, Martin. “Identifying cell populations with scRNASeq” vol. 59, *Molecular Aspect of Medicine*. Feb., 2018.

2. Adil M. Bagirov, Julien Ugon, Dean Webb. “Fast modiﬁed global k-means algorithm for incremental cluster construction.”

3. Bezdek, J., Ehrlich, R. & Full, W. FCM: The fuzzy c-means clustering algorithm. *Computers & Geosciences* 10, 191-203 (1984).

4. Dembele, D., and P. Kastner. "Fuzzy C-Means Method For Clustering Microarray Data". *Bioinformatics*, vol 19, no. 8, 2003, pp. 973-980. *Oxford University Press (OUP)*, doi:10.1093/bioinformatics/btg119.

5. Duo, Angelo., et., al. “ A systematic performance evaluation of clustering  methods for single-cell RNA-seq data.” NCBI., 11 Sep. 2018. 

6. Hartigan, J. A., and M. A. Wong. "Algorithm AS 136: A K-Means Clustering Algorithm". *Applied Statistics*
, vol 28, no. 1, 1979, p. 100. *JSTOR*, doi:10.2307/2346830.

7. Jiang, D., Tang, C. and Zhang, A. (2019)."Cluster Analysis For Gene Expression Data: A Survey - IEEE Journals & Magazine". *Ieeexplore.Ieee.Org*, 2019, https://ieeexplore.ieee.org/document/1339264.


8. Likas, Aristidis. et., al. “The global k-means clustering algorithm.” *Pattern Recognition*. 4 March 2002.

9. Liu, Zhe et al. "A New Clustering Method Of Gene Expression Data Based On Multivariate Gaussian Mixture Models". *Signal, Image And Video Processing*, vol 10, no. 2, 2015, pp. 359-368. *Springer Science And Business Media LLC*, doi:10.1007/s11760-015-0749-5.

10. Singh, Aishwarya. "What Are Gaussian Mixture Models? A Powerful Clustering Algorithm". *Analytics Vidhya*, 2019, https://www.analyticsvidhya.com/blog/2019/10/gaussian-mixture-models-clustering/.

11. Sheng Zhong. "Intro to Machine Learning". BENG 183.

12. T., Velmurugan. "Performance Based Analysis Between K-Means And Fuzzy C-Means Clustering Algorithms For Connection Oriented Telecommunication Data". *Applied Soft Computing*, vol 19, 2014, pp. 134-146. *Elsevier BV*, doi:10.1016/j.asoc.2014.02.011.

13. Warner, Jake. "Clustering Rnaseq Data Using K-means Clustering -2-Bitbio". *2-Bitbio.Com*, 2019, https://2-bitbio.com/2017/10/clustering-rnaseq-data-using-k-means.html.

14. Warner, Jake. "Clustering Rnaseq Data Using Fuzzy C-Means Clustering - 2-Bitbio". *2-Bitbio*, 2019, https://2-bitbio.com/post/clustering-rnaseq-data-using-fuzzy-c-means-clustering/.



![global-kmeans](images/global-kmeans.png)
