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

<img src="http://shabal.in/visuals/kmeans/random.gif" width=500 height=300>

## Global *K*-Means Clustering

As mentioned, k-means clustering results are sensitive to the initial choice of clusters therefore they are only reliable for analyzing small sets of data. To improve it, auxiliary incremental approaches are recently introduced to k-clustering algorithm, which are known as the global k-means clustering.  

One traditional way is to start from one cluster (centroid), and continuously adding new clustering center as the iteration proceeds. 

Step 1: Given the finite data set <img src="/tex/53d147e7f3fe6e47ee05b88b166bd3f6.svg?invert_in_darkmode&sanitize=true" align=middle width=12.32879834999999pt height=22.465723500000017pt/>, <img src="/tex/9233262f58a431ec864c8dc2308dad7b.svg?invert_in_darkmode&sanitize=true" align=middle width=113.57686394999999pt height=24.65753399999998pt/>, consisting of m n-dimensional elements, compute A’s center, set this as the initial center.  
Step 2: Let the rest (<img src="/tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/>-1)-partition centroids be <img src="/tex/7e721fe1c7f64784d20cd0f496e836db.svg?invert_in_darkmode&sanitize=true" align=middle width=110.8617807pt height=14.15524440000002pt/>, compute <img src="/tex/2bfa3db256fd1625d91ab9bc03acd9bc.svg?invert_in_darkmode&sanitize=true" align=middle width=37.57057094999999pt height=28.091038800000003pt/>, <img src="/tex/88b6fa172b4ea7646e022c6707d88558.svg?invert_in_darkmode&sanitize=true" align=middle width=32.30026799999999pt height=21.839370299999988pt/>by comparing the minimum square distance between each point and the closest cluster center from <img src="/tex/7e721fe1c7f64784d20cd0f496e836db.svg?invert_in_darkmode&sanitize=true" align=middle width=110.8617807pt height=14.15524440000002pt/> with the square distance of each pair of data. So the point with the minimum <img src="/tex/2bfa3db256fd1625d91ab9bc03acd9bc.svg?invert_in_darkmode&sanitize=true" align=middle width=37.57057094999999pt height=28.091038800000003pt/> value would be the new cluster center for the next iteration.  
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

The Mixture of Gaussian clustering method is a way to cluster data points not only by the means, but also by variance. Therefore, it can make the cluster more correctly in some circumstances. Gaussian Mixture Models (GMMs) assume that there are a certain number of Gaussian distributions, and each of these distributions represents a cluster. Hence, a Gaussian Mixture Model tends to group the data points belonging to a single distribution together.

GMM is a probabilistic model that uses soft clustering method to distribute the points in different clusters. Soft clustering, also known as fuzzy clustering or soft k-means, is a form of clustering method in which one data point can belong to more than one cluster. The GMM uses the probabilistic density function in a 3D gaussian distribution is given by:

<p align="center"><img src="/tex/fa2774981b934668dbf10d514931df16.svg?invert_in_darkmode&sanitize=true" align=middle width=266.47394234999996pt height=40.289634pt/></p>

* <img src="/tex/332cc365a4987aacce0ead01b8bdcc0b.svg?invert_in_darkmode&sanitize=true" align=middle width=9.39498779999999pt height=14.15524440000002pt/> = the input vector. 
* <img src="/tex/07617f9d8fe48b4a7b3f523d6730eef0.svg?invert_in_darkmode&sanitize=true" align=middle width=9.90492359999999pt height=14.15524440000002pt/> = 2-D mean vector
* <img src="/tex/813cd865c037c89fcdc609b25c465a05.svg?invert_in_darkmode&sanitize=true" align=middle width=11.87217899999999pt height=22.465723500000017pt/> = 2 <img src="/tex/bdbf342b57819773421273d508dba586.svg?invert_in_darkmode&sanitize=true" align=middle width=12.785434199999989pt height=19.1781018pt/> 2 covariance matrix

Therefore, when we cluster the datasets in a 2 dimensional plot, we will define <img src="/tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/> clusters, so we will have a mixture of <img src="/tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/> Gaussian distributions, with each of them having a mean vector and a variance matrix.  

Since we do not know these mean and variance because we do not know which Gaussian generated which data point, these parameters are calculated by a process called Expectation-Maximization (EM), which involves two steps --- the E-step and the M-step. We also have a parameter called <img src="/tex/0c4cdff2a5c675458f5a6629892c26d1.svg?invert_in_darkmode&sanitize=true" align=middle width=12.32879834999999pt height=22.465723500000017pt/> which represent the density of the distribution.

During the E-step, we compute the responsibilities for each Gaussian for each datapoint. The responsibility is calculated by dividing the Probability of <img src="/tex/1338d1e5163ba5bc872f1411dd30b36a.svg?invert_in_darkmode&sanitize=true" align=middle width=18.269651399999987pt height=22.465723500000017pt/> belongs to cluster <img src="/tex/3e18a4a28fdee1744e5e3f79d13b9ff6.svg?invert_in_darkmode&sanitize=true" align=middle width=7.11380504999999pt height=14.15524440000002pt/> by the Sum of probability <img src="/tex/1338d1e5163ba5bc872f1411dd30b36a.svg?invert_in_darkmode&sanitize=true" align=middle width=18.269651399999987pt height=22.465723500000017pt/> belongs to <img src="/tex/7a914c116509395f0acf452fc81725dc.svg?invert_in_darkmode&sanitize=true" align=middle width=87.19166114999999pt height=14.15524440000002pt/>. This value will be big if the point is assigned to the correct clusterm and low otherwise.

During the M-step, we modify the parameters of each Gaussian to maximize the likelihood for the responsibility weighted data. The density <img src="/tex/0c4cdff2a5c675458f5a6629892c26d1.svg?invert_in_darkmode&sanitize=true" align=middle width=12.32879834999999pt height=22.465723500000017pt/>, mean <img src="/tex/07617f9d8fe48b4a7b3f523d6730eef0.svg?invert_in_darkmode&sanitize=true" align=middle width=9.90492359999999pt height=14.15524440000002pt/> and the covariance matrix <img src="/tex/813cd865c037c89fcdc609b25c465a05.svg?invert_in_darkmode&sanitize=true" align=middle width=11.87217899999999pt height=22.465723500000017pt/> are updated until convergence. They are updated following the manner below:

<p align="center"><img src="/tex/b83ef5ac4168a2edc4ff1eaa3b195257.svg?invert_in_darkmode&sanitize=true" align=middle width=240.8622414pt height=37.0084374pt/></p>  

<p align="center"><img src="/tex/fa9be4c6dc2d2f0da575baddde7c95aa.svg?invert_in_darkmode&sanitize=true" align=middle width=290.56541745pt height=36.1865163pt/></p>  

<p align="center"><img src="/tex/64408a81a102eb5ac48414a9d142f0a3.svg?invert_in_darkmode&sanitize=true" align=middle width=417.53418135pt height=36.1865163pt/></p>

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

Because global *k*-means clustering involves a series of computation of the auxiliary function <img src="/tex/2bfa3db256fd1625d91ab9bc03acd9bc.svg?invert_in_darkmode&sanitize=true" align=middle width=37.57057094999999pt height=28.091038800000003pt/>, which produces an affinity matrix in every iteration, it requires longer runtime and greater computation power comparing with the standard *k*-means clustering. However, this gives a much better set of centroids for initial *k*-clusters because at each iteration the cluster centers can be refined according to the previous ones.

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
