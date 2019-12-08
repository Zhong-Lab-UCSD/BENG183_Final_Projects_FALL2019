# Machine Learning in Bioinformatics 

Justin Huynh 

Kevin Ramos 

Aaron Ho

University of California, San Diego

---

## Introduction

Machine learning has become an important topic of discussion in research because it can be used to analyze large datasets and discover specific patterns that are not immediately visible to the human eye. The field of Bioinformatics has increasingly begun to use machine learning methods to gain greater insight and make predictions about complex biological processes in organisms. Specifically, machine learning methods are being used in genomics to analyze DNA sequences in various ways including finding subclasses of diseases, determining ancestry of individuals, predicting transcription factor binding sites, and predicting cell cycle phases. In discussing machine learning methods, it is important to distinguish two different types of learning: *supervised and unsupervised learning*.

<img src="learning.png" height="250" width="250">

In **supervised learning**, the model is trained using a labeled dataset. In other words, the correct labels are known and act as a “teacher” that corrects the algorithm during its training. The algorithm iteratively makes predictions on the training dataset until it reaches an acceptable level of performance. Supervised learning problems can be fall under classification, in which the algorithm's output value is a category.

In **unsupervised learning**, the input data does not have corresponding labels. The goal of this type of learning is to model the distribution of the dataset in order to gain greater insight about the data. Unsupervised learning problems can fall under clustering, which is useful for uncovering groups within the data. 

## Clustering

Clustering is a useful technique that groups similar data points in such a way that similar points will be grouped closer to one another, thus forming a cluster. The two clustering techniques that we will discuss are hierarchical clustering and K-means clustering. 

---

### Hierarchical Clustering 

![2](2.png width="100" height="100")

In Hierarchical clustering, similarity (distance) between points is calculated to cluster the most similar points together. This process is repeated until only a single cluster is left. Essentially, the algorithm builds a hierarchy of clusters.  
The algorithm for Hierarchical Clustering is as follows:

1. Calculate the similarity (distance) between all possible combinations of two profiles.
2. Place each profile in a separate cluster.
3. Group the two most similar clusters into a new cluster.
4. Calculate the similarity (distance) between the new cluster and all remaining clusters.
5. Repeat steps 3 and 4 until all profiles are in one large cluster.

### K-means Clustering

![3](3.png =250x250)

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

### Finding Subclasses of Lung Cancer via Clustering of Gene Expression Profile

### Determining Ancestry of New Samples via Clustering (PCA) of Genome

### Transcription Binding Site Prediction using CNN on Binding Motifs

### Cell Cycle Phase Prediction using CNN on Images of Jurkat Cells

## Challenges of Machine Learning Approaches in Bioinformatics

### Consequences of Overfitting Given Insufficient Data

### The Black Box of The Predictive Model

### Reliance on Prior Knowledge, and Misapplication of Machine Learning

## References

[1] Kimes, P. K., Liu, Y., Neil Hayes, D., & Marron, J. S. (2017). Statistical significance for hierarchical clustering. Biometrics, 73(3), 811–821. doi:10.1111/biom.12647

[2] Bhattacharjee, Arindam, et al. "Classification of human lung carcinomas by mRNA expression profiling reveals distinct adenocarcinoma subclasses." Proceedings of the National Academy of Sciences 98.24 (2001): 13790-13795.

[3] Li, Jun Z., et al. "Worldwide human relationships inferred from genome-wide patterns of variation." science 319.5866 (2008): 1100-1104.

[4] Alipanahi, Babak, et al. "Predicting the sequence specificities of DNA-and RNA-binding proteins by deep learning." Nature biotechnology 33.8 (2015): 831.

[5] Eulenberg, Philipp, et al. "Reconstructing cell cycle and disease progression using deep learning." Nature communications 8.1 (2017): 463.

[6] Deep learning for genomics. Nat Genet 51, 1 (2019) doi:10.1038/s41588-018-0328-0

[7] Xu, C., & Jackson, S. A. (2019). Machine learning and complex biological data. Genome biology, 20(1), 76. doi:10.1186/s13059-019-1689-0

[8] Libbrecht, M. W., & Noble, W. S. (2015). Machine learning applications in genetics and genomics. Nature reviews. Genetics, 16(6), 321–332. doi:10.1038/nrg3920
