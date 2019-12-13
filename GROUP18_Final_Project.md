# Applied Clustering and Classification: Bioinformatics
#### By Breenan Upton Sanderbeck, Tiffany Loo, and Sid Limaye

Contents:
- [K-means](#K-Means-Clustering)
- [Hierarchical Clustering](#Hierarchical-Clustering)
- [Support Vector Machines (SVM)](#SVM)
***


### The Use of Clustering Algorithms Within Biology
Even though clustering algorithms were initially made for generating predictions and decisions from data in the technological realm, the rise of big data in biology with growing fields like bioinformatics encouraged experts in the field to port such machine learning techniques to biology. People soon learned that gene expression data could be clustered to predict unknown genes’ functions, find subtypes of diseases, and shared regulatory DNA sequences. Genomics, proteomics, and systems biology are just some of the many fields in biology which have used these tools. The use of clustering and classification algorithms on biological data has aided to the growth of precision medicine by allowing predictions to be made about patient outcomes. 
#### K Means Clustering:
K Means clustering is a simple algorithm commonly used to cluster points into K distinct clusters. An important feature of K Means clustering to note is that the algorithm returns a specified number (K) of clusters. That means K Means clustering is primarily useful if you know exactly how many clusters your points fall into. Thus, for example,  K Means clustering might be useful for clustering cancer patients’ gene expression vectors into subtypes if you already know there are exactly K subtypes of this particular type of cancer but it would not be useful if you’re trying to discover how many different subtypes of a type of cancer exist. 

![](https://i.imgur.com/Es3oBZz.gif)


K Means clustering begins with an initialization of K centers for each of the K clusters. The initialization can be random, or some kind of a scheme can be used to pick the centers. For example, K of the points can be used, or the centers can be initialized to high data-density areas. After centers have been initialized, clusters are assigned to the points - each point is assigned to the cluster whose center is most similar to it. Deciding which center is most similar to a point can be done in a number of ways. The most common similarity measure is using the Euclidean distances between the point and the centers. Another method, Single linkage similarity measure, uses the Euclidean distance between the point and each cluster's closest data point to the point of interest. Correlation methods can also measure similarity between points. Next, the clusters’ centers are updated. Each cluster’s center is set to the mean of the points that fall in that cluster. Variants of the algorithm will sometimes use a different calculation, not the mean, for the centroid.
In this kind of clustering, the process of point reassignment and center calculation is iterated to find the clusters. Note that although sometimes the clusters stabilize, it is not guaranteed that this clustering will converge. The clusters "converge" when the points' memberships stop changing; in other words, when all of the points are reassigned to the same cluster (from the last iteration). Because sometimes the clusters will continue to change indefinitely, often times in bioinformatics applications the algorithm is stopped after a predetermined number of iterations, or the iteration is stopped when the mean inter-cluster distance falls below a given threshold.

Furthermore, k-means clustering is not stable with respect to the choice of initial points. This means that one particular initialization of the centers could give a different set of clusters than another. One approach used to tackle this problem is to try a set of different initializations, and see which clusterings these initializations approach, and select the clustering that was converged to the most often. The data density-dependent initialization mentioned above is another approach to combat this instability. [[6]](#Citations)

Pseudocode:
```
dataPoints = vector for each data point
centers = list of initial cluster centers
clusters = dictionary of points assigned to centers
While endCondition() is false: 
    For each point in dataPoints: 
        thisCenter = closestCenter(point, centers) 
        Update clusters so that point is assigned to thisCenter 
    For each center in centeters: 
        center = mean of all points in its cluster
```
##### Biological Application:
###### T-REKS: Identification of Tandem Repeats in Sequences with a K-Means Based Algorithm
Julien Jorda and Andrey V. Kajava developed a program that probes sequences for tandem repeats. In their program, the first step of their analysis is using K-Means algorithm to find most-likely lengths of the tandem repeats in a sequence. The lengths between identical neighbouring short strands are used as datapoints and K-Means algorithm was used to find potential lengths of tandem repeats. Hierarchical clustering (which is discussed in detail below) is used to initialize the cluster centers and Euclidean distance is used as the similarity measure. After the completion of the K-Means algorithm, each of the K clusters centers contain lengths between identical strands, the most frequent occuring length of that cluster is chosen as the Short string Main Length (SML) and used for later analysis. If a cluster has multiple most frequent lengths the shortest length is chosen.
By probing for repeats of length equal to a SML computed by the K-Means analysis, regions of tandem repeats can be identified. [[4]](#Citations)



---
#### Hierarchical Clustering:
Hierarchical clustering also utilizes similarity measures to find similarity between different ‘profiles’ of data such as through correlation calculations, cosine correlation, or euclidean distance. The profiles represent all separate clusters, then after the initial similarity calculations, the two most similar clusters are grouped together as a new cluster. Similarity will be calculated again by the same clustering method with the new cluster taken into account. These new similarity calculations are then used to find the next two most similar clusters which will be the next two grouped together as a new cluster. This method is repeated until all the initial profiles are in one cluster. In the end you will have a big dendrogram structure showing the connections between each profile. [[6]](#Citations)

Pseudocode:
```
n = number of profiles 
profiles = set of profiles
for i in 1 to n:
	ci = {profilesi}
clusters = {c1 … cn}
while clusters.size > 1:
	cmin1 and cmin2 = calculate minimum distance (ex. Euclidean distance)for all profiles within clusters
	Remove cmin1 and cmin2 from clusters since they represent the two most correlated profiles
	Add set {cmin1 and cmin2}  to clusters

```
The above method is just one way of implementing hierarchical clustering with code. This may not be optimal if you want to generate an actual dendrogram because it just shows the final clusters at the end of the program. However, if the distance that every merge of clusters occurs at is stored with the cluster, a dendrogram can easily be generated. 
Infographic:
![](https://i.imgur.com/UXvnMTr.gif)
##### Biological Application:
In lecture, we touched upon the usage of hierarchical clustering within the classification of human lung carcinoma using mRNA expression levels. The usage of hierarchical clustering in this paper by Bhattacharjee highlighted its ability in diagnosis of disease: the profiling done was able to differentiate between " primary lung adenocarcinomas from metastases of extra-pulmonary origin" [[1]](#Citations).  The results of the clustering were displayed  

![](https://www.pnas.org/content/pnas/98/24/13790/F1.large.jpg?width=800&height=600&carousel=1)

As seen from the above heat map, the clustering algorithm was able to successfully separate the samples into differing lung tumor classes (the classes circled at the top of the picture): "pulmonary carcinoid tumors, SCLC, squamous cell lung carcinomas, and adenocarcinomas". These classifications support the viability of such computational methods within the biological field as a medical tool.   

In an outside source, hierarchical clustering was utilized with a study on the immune response of lamprey (type of prehistoric jawless fish useful for studying developmental biology) larvae by clustering RNA-seq transcriptome data of larvae infected by Vibro splendidus, Aeromonas hydrophila and Saprolegnia parasitica parasites.  

![](https://ars.els-cdn.com/content/image/1-s2.0-S0161589019306777-gr3.jpg)

As seen in the heatmap marked by 'D', hierarchical clustering was used to compare the expression levels of the transcripts in three different infection types. The dendrogram results show that the Vibrospendidus and the Aeromonas hydrophila were both clustered with Sapralegnia parasitica parasite. Until this point, lamprey larvae were often dying from infection, thus this study promoted further understanding of the immune systems of such an important species and pushes for better lab cultures and artificial propagation of the larvae. [[2]](#Citations)

Although hierarchical clustering is an "out-dated" method because of its simplicity, it is still used in current day studies as seen from the lamprey paper published online just last month, November 2019. The algorithm is typically not the main finding of the paper, but is used instead for the grouping of data into an easily digestible heatmap for the readers. 

---

#### SVM:

The support vector machine learning technique is used for classifying data points into exactly two clusters. Thus SVM is most useful in creating a simple positive/negative test. SVM wouldn’t be used to cluster cancer patients to discover several subtypes of a cancer type. However, it would be used to train a model on data points of patients with and without cancer and then use that model to test whether or not a new patient has that cancer. Other examples of SVM being used in biology include “the prediction of protein secondary structure, multi-class protein fold recognition, and the prediction of human signal peptide cleavage sites” (7). 
It’s important to note that SVM is a supervised classification algorithm unlike Kmeans and hierarchical which are unsupervised clustering algorithms. This means, unlike the previously discussed ML algorithms, SVM requires training data to later make a decision about a new data point.  
The SVM algorithm’s output is a hyperplane that best separates the two classes of data. That hyperplane can then be used to classify a new data point by determining what side of the hyperplane the point falls on. The simplest example is in two dimensional which the below GIFs demonstrates.
Infographic:

![](https://i.imgur.com/Xdc1Iqv.gif)

The easy part of SVM is finding a hyperplane that separates the two classes-- the difficult part is finding the best hyperplane that separates the two classes. The quality of a hyperplane’s separation is measured by the distance from that hyperplane to the nearest points on each side.
The greater this margin, the better the hyperplane. Support vectors, which are data points that are closest to the hyperplane, also help determine the position and orientation of the hyperplane by continuing to maximize the margin around the hyperplane. The parameter to optimize is described by the following equation:

![](https://i.imgur.com/Y7adzCu.png)

The term being optimized represents the distance of a point to the hyperplane. An explanation of the term follows: ![](https://i.imgur.com/e2Mj1Ht.png)  is the projection of a data point xi onto the unit normal vector to the hyperplane, ![](https://i.imgur.com/lqITEtR.png) , and it gives the distance from that data point to a parallel hyperplane passing through the origin. The ![](https://i.imgur.com/83DK28k.png) term accounts for datasets where the hyperplane does not pass through the origin. The additional constraint below the equation ensures that the predictions, ![](https://i.imgur.com/T9MKhQg.png) have the same sign as the labels of the data points ![](https://i.imgur.com/cmRFQaJ.png).

However, this equation is nonlinear in two ways, making this a tough optimization problem to solve. By refactoring the equation in terms of a least squares problem, this parameter can be made into the following quadratic optimization problem, which is easier to approximate:

![](https://i.imgur.com/ZDsU3bA.png)

Observe that this approach only works when the data is separated by a boundary that is a line. In order to use this approach with datasets where the boundary may be nonlinear, it must be modified. This modification is called the "kernel" trick. In this situation, first a transform is applied to the data to make the separation boundary linear (in the new space), then the SVM is run, and finally the reverse transform is used on the learned boundary. The following image [[3]](#Citations) describes this process:

![](https://i.imgur.com/0Hasd9z.jpg)


##### Biological Application:

Huang et al. [[3]](#Citations) describe application of SVMs to cancer genomics. A couple of these applications involve using gene expression (mRNA counts) or gene regulation (methylation) as the feature data, with the subtype of cancer as the label. The trained model is then used to predict the cancer subtype for a new data point given the expression or methylation data. Another application described in the same review is known as SVM-RFE (**R**ecursive **F**eature **E**limination). It involves using an SVM to pick out what the "important" features in a dataset are - if a boundary is orthogonal to an axis (a feature), then the feature is probably important in the classification. It works by training the SVM, removing the least important features, then re-training the SVM. This is repeated to rank the importance of each of the input features. It's especially useful in non-linear contexts where approaches like PCA don't work.

Another paper [[5]](#Citations) describes the use of SVM to classify the attentiveness of people in two different tasks requiring attention or not requiring attention while wearing an EEG monitor. The data gained from the EEG was labelled either as "attention" or "relaxed" (people were either doing a puzzle or staring at a white screen) as attributes for plugging into their SVM model to build a classifier for patient attentiveness. Using their model, they tried classifying EEG data to test their accuracy for determining participant attention levels and achieved an average of around 84.80%. In this paper, SVM opens the door for classifying attention deficit disorders and biofeedback training.   

In modern bioinformatics, SVM is a relatively basic technique just like hierarchal clustering. As a result, it's often used as a technique to build off of, but (now) is rarely the focus of a paper or a result.

---

#### Summary

Using the above data science methods, precision medicine and bioinformatics is an exciting and growing field. Increasingly more machine learning tools and algorithms, initially used purely in the computational world, have been shown to also show viability within biology as seen in the above applications. This encourages "smarter" ways to diagnose, study, and develop treatments for diseases at a complexity before unthinkable due to less computational power and slower algorithms/methods. 

---

#### Citations:
[1] Bhattacharjee, Arindam, et al. "Classification of human lung carcinomas by mRNA expression profiling reveals distinct adenocarcinoma subclasses." Proceedings of the National Academy of Sciences 98.24 (2001): 13790-13795.
[2] Gou, Meng, et al. "Comparative transcriptomic analysis provides insights into immune responses of lamprey larvae under three pathogens infections." Molecular Immunology 117 (2020): 147-154.
[3] Huang, Shujun et al. “Applications of Support Vector Machine (SVM) Learning in Cancer Genomics.” Cancer genomics & proteomics vol. 15,1 (2018): 41-51. doi:10.21873/cgp.20063
[4] Julien Jorda, Andrey V. Kajava, T-REKS: identification of Tandem REpeats in sequences with a K-meanS based algorithm, Bioinformatics, Volume 25, Issue 20, 15 October 2009, Pages 2632–2638, https://doi.org/10.1093/bioinformatics/btp482
[5] Peng, Chia-Ju, et al. "An EEG-Based Attentiveness Recognition System Using Hilbert–Huang Transform and Support Vector Machine." Journal of Medical and Biological Engineering (2019): 1-9.
[6] Zhong, Sheng. "Intro to Machine Learning", BENG 183.
[7] https://jeremykun.com/2017/06/05/formulating-the-support-vector-machine-optimization-problem/
