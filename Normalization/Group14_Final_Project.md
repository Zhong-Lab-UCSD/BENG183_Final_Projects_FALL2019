# RNA-Sequencing Analysis Normalization Techniques

By Daniella Vo, Nidhi Bangari, Priya Jindal

1. [Introduction](#1)
2. [Normalization Techniques](#2)<br>
    2.1. [RPKM](#21)<br>
    2.2. [FPKM](#22)<br>
    2.3. [TPM](#23)<br>
    2.4. [SCBN](#24)<br>
    2.5. [SCnorm](#25)<br>
    2.6. [TMM](#26)
3. [Comparisons](#3)
4. [Summary](#4)
5. [References](#5)

## 1. Introduction<a name="1"></a> 

   The difference between two individuals is not only limited to genomic differences in DNA. An individual with the same genome in all of their cells will still have different cells behaving differently due to differing levels of gene expression<sup>[1]</sup>. Gene expression is regulated at many levels, one of which is the transcriptional level; a variety of transcription factors determine which genes will be transcribed and in what amounts at any time. The expression of genes in a cell can vary with environment, situations of stress, disease, etc. and understanding gene expression levels is key for a lot of research. For example, we can use gene expression levels to identify differentially expressed genes in cancer patients, and use this information to diagnose cancer early. 
   
   Thus, RNA-sequencing is used to determine gene expression levels, which allow researchers to identify differentially expressed genes, discover new RNA isoforms, and find genomic mutations. RNA-seq analysis takes raw reads as input, and outputs differentially expressed genes, which are genes that are expressed in different levels for different samples. The pipeline for RNA-seq analysis is shown in Figure 1 below:

<p align="center">
  <img src="https://github.com/nbangari/BENG183_Final_Projects_FALL2019/blob/master/Normalization/img/image6.png">
</p>
<p align="center">
    <em>Figure 1: RNA-seq analysis pipeline </em>
</p>

  The first step is to check the quality of the reads produced by the RNA-sequencing. One tool that can be used for this is FastQC, which gives various measurements of read quality that can be analyzed by the researchers. If the quality is good enough, the next step is to map the reads to the genome. This step takes all the fragments that were sequenced and maps them to their corresponding genes (or other areas of the genome). 
  
  The third step in the RNA-seq data analysis workflow is expression quantification. During this step, we are able to measure the expression level of a gene as a measure of the number of RNA reads that were aligned to it. The mapped reads to the genome are counted using tools such as featureCounts which determine the raw mapped read counts for sections of the genome. However, we cannot make any conclusions on gene expression solely based on these raw mapped read counts, and therefore we need to perform normalization.
  
  In this paper, we will be discussing the importance of normalization and going into detail to explore various normalization strategies or techniques that are commonly used. Each technique has its own pros and cons and we will be comparing the techniques to one another to see how they perform with respect to each other. 
  
  Normalization is important because if we simply measure the expression level of a gene as the raw number of RNA reads that were aligned to it, we will get an inaccurate picture. A very long gene is expected to have more reads that align to different parts of the gene than a short gene with the same expression level. For example, if we sequenced in reads of ~100 bp, and exactly 4 copies of a long gene and 4 copies of a short gene were sequenced, but the short gene was ~100 bp long and the long gene was ~1000 bp long, then we would have ~40 reads map to the long gene and ~4 reads map to the short gene, although their expression levels were the same. In addition, if many copies of reads were made in the PCR step and we had a very large total read library size, then many more reads would align to a single gene than if we have a small total read library size. Therefore we need to adjust for gene length and library size in order to get an accurate picture of expression levels. Without normalization, it will be difficult to compare between and within different samples.
  
  There are various approaches to normalization. In this paper we will look at several different algorithms used for normalization and how they compare to one another by looking at their techniques, their ideal use cases, and their applications in existing studies. 
  
## 2. Normalization Techniques<a name="2"></a>
The following are some different techniques in place to normalize RNA-seq data:
* *RPKM*
* *FPKM*
* *TPM*
* *SCBN*
* *SCnorm*
* *TMM*

### 2.1 RPKM<a name="21"></a>
RPKM stands for Reads Per Kilobase of transcript per Million
  
Steps for RPKM:
  1. The numerator is the read counts aligned to a single gene.
  2. The total reads in a sample divided by 1,000,000 is our “per million” scaling factor. Multiply this by the length of the gene in kilobases. This is our denominator.
  3. Numerator / denominator = RPKM value
  
  Dividing the number in Step 1 by the number in Step 2 gives you reads per million (RPM) and normalizes for sequencing depth. Dividing by the RPM values by the length of the gene in kilobases gives reads per kilobase of transcript per million (RPKM), and additionally normalizes for gene length<sup>[1]</sup>. 
  
<p align="center">
  <img src="https://github.com/nbangari/BENG183_Final_Projects_FALL2019/blob/master/Normalization/img/image5.png" width="600">
</p>
<p align="center">
    <em>Figure 2: RPKM calculation </em>
</p>
  
### 2.1 FPKM<a name="22"></a>
  FPKM stands for Fragments Per Kilobase of transcript per Million and is nearly identical in procedure to RPKM. The only difference is that RPKM is designed for single-end read analysis, while FPKM was designed for paired-end reads. RPKM relies on the assumption that every read is associated with a single fragment that was sequenced. However, in paired-end sequencing, usually two reads (a “pair”) correspond to a single fragment, unless one read did not map for some reason. In FPKM, if two paired-end reads map to one fragment, they are counted as one instance of a read mapping to a fragment, rather than two. 

<p align="center">
  <img src="https://github.com/nbangari/BENG183_Final_Projects_FALL2019/blob/master/Normalization/img/image9.png" width="500">
</p>
<p align="center">
    <em>Figure 3: Illustration comparing the FPKM and RPKM normalization techniques in single vs paired-end reads </em>
</p>

### 2.3 TPM<a name="23"></a>
TPM stands for Transcripts per million and normalizes for library size by measuring the number of reads that align to a particular gene as the proportion of total reads in the library. This means every sample has the same total TPM, so TPM can be compared both between and within samples, unlike RPKM/FPKM which cannot be compared between samples<sup>[2]</sup>.

### 2.4 SCBN<a name="24"></a>
SCBN stands for scale based normalization, and is a newly proposed method which aims to more accurately identify genes with differential expression between different species. This is normally a challenging task due to variations between species, as not only gene lengths and read counts need to be considered, but also the different gene numbers and gene lengths across species. SCBN handles this by using knowledge about orthologous genes that are conserved in both species. 

<p align="center">
  <img src="https://github.com/nbangari/BENG183_Final_Projects_FALL2019/blob/master/Normalization/img/image4.png" width="600">
</p>
<p align="center">
    <em>Figure 4: Displaying the difference between comparing the same genes within a single species, and comparing orthologous genes across different species <sup>[3]</sup> </em>
</p>

SCBN builds off another normalization method known as HTN, which is based on the hypothesis testing framework. HTN uses available knowledge of housekeeping genes, to calculate an optimal scaling factor. Using the same principles, SCBN utilizes the available knowledge of conserved orthologous genes for different species to derive the normalization scaling factor. SCBN assumes that a set of conserved orthologous genes between species is known in advance, and calculates the optimal scaling factor by minimizing the deviation between the empirical and nominal type I errors.

Tools to implement SCBN include an R package named “SCBN”, which is freely available at http://www.bioconductor.org/packages/devel/bioc/html/SCBN.html <sup>[3]</sup>.

### 2.5 SCnorm<a name="25"></a>
SCnorm is a method of normalization that uses quantile regression to estimate the dependence of transcript expression on sequencing depth for every gene. Quantile regression is similar to linear regression, but instead of finding the slope of all the data points, quantile regression breaks up the data points into x quantiles and determines the slope of the data points in each of these quartiles<sup>[4]</sup>.
 
    Workflow:
        1. Starting K = 1, where K represents the number of clusters. The equation is shown below: 

<p align="center">
  <img src="https://github.com/nbangari/BENG183_Final_Projects_FALL2019/blob/master/Normalization/img/image8.png" width="400">
</p>

       τ represents the quantiles; d represents the degrees; Yg,j denote the log non-zero 
       expression count for gene g in cell j for g = 1,…,m and j = 1,…,n; Xj denote log 
       sequencing depth for cell j; gene-specific relationship between log unnormalized 
       expression and log sequencing depth is represented by βg,1

       2. This calculation is repeated by increasing K if the modes of the slopes within each of 10 
        equally sized gene groups (where a gene’s group membership is determined by its median 
        expression among non-zero un-normalized measurements) are all less than 0.

       3. Normalized counts Y’g,j are given by
        
 <p align="center">
    <img src="https://github.com/nbangari/BENG183_Final_Projects_FALL2019/blob/master/Normalization/img/equation2.png" width="50">
 </p>
        
        where SF is the scale factor. The estimated scale factors are used to perform within-group 
        adjustment for sequencing depth to provide normalizes estimates of expression.

        4. When multiple biological conditions are present, SCnorm is applied within each condition 
        and the normalized counts are then re-scaled across conditions.
 
### 2.6 TMM<a name="26"></a>
TMM stands for trimmed means of M-values. 

  TMM is a method of normalization that estimates the relative RNA production level from RNA-seq data by estimating scale factors         between samples. TMM is calculated by dividing raw counts by the library size times a normalization factor. The library size is used     to account for the size of the library since a larger library can lead to more reads aligned but not necessarily more gene               expression. The normalization factor is used to account for “compositional biases” for example when certain genes are very highly       expressed to too low, these may be outliers<sup>[6]</sup> . TMM takes out these high and low expression outliers and only takes the mean of the         remaining values to calculate the trimmed mean. These normalization factors are calculated for each sample based on the weighted mean of log ratios between the sample's expression and the trimmed mean value. TMM works under the assumption that the majority of genes are not differentially expressed. The main difference       between TMM and other normalization strategies is the TMM does not account for the length of the gene or transcript<sup>[7]</sup>. 
   
    WorkFlow : 
    This briefly explains what occurs when we use TMM in R, since it is implemented in the 
    edgeR Bioconductor package:           
      1. Use the calcNormFactors function in the package to calculate normalization factors
          - Internally these normalization factors account library size
          - And determine a scaling factor based on the binomial distribution of data input since we 
          are only using the mean or trimmed values and are removing outlier values. 
      2. Then the raw gene counts are rescaled by dividing each gene count by the scaling factor 
         for each run. 
      3. TMM is the sum of rescaled gene counts of all runs.


## 3. Comparisons<a name="3"></a>

| Normalization Method | Within-sample or between-sample? | Pros | Cons |
|:---:|:---:|:---:|:----------:|
|RPKM    | Within-sample       | Straightforward   | Only for single-end reads, Cannot be compared between samples |
|FPKM    | Within-sample       | Works for paired-end reads | Cannot be compared between samples |
|TPM    | Between-sample       | Can be compared between samples   | Not as good when systematic variation exists between transcript specific expression and sequencing depth (e.g. seen in scRNA), Works best for a single species  |
|SCBM    | Between-sample       | Can be used to compare differential gene expression across different species | Requires a set of conserved orthologous genes between the species being compared to be known in advance  |
|SCnorm    | Between-sample       | Uses single scale factor instead of global scale factor (as global scale factors compromise performance in single-cell settings), Good for scRNA (small conditional RNA) data unlike other methods | Only focuses on between sample comparisons (need to use R/SCnorm to adjust for gene-specific features) |
|TMM    | Within-sample       | The data themselves do not need to be modified, unlike other normalization strategies. In TMM the estimated normalization factors are used directly in the statistical model used to test for DE, while preserving the data to be used elsewhere.    | Can only be used when looking for differences between the same gene in different samples, not different genes.   |
  
####  Comparing RPKM and SCBN  
A method previously used by Brawand et. al to normalize data across different species is to identify the most conserved genes, calculate the median expression levels in each species among the genes with expression values in the interquartile range for different species, derive scaling factors to adjust those median values to a common value, and then use RPKM to normalize the data. This method, called the “median” method, was compared for accuracy with SCBN<sup>[4]</sup> , and SCBN was found to have a lower error rate, as seen in the figure 5 below.

<p align="center">
  <img src="https://github.com/nbangari/BENG183_Final_Projects_FALL2019/blob/master/Normalization/img/image3.png" width="400">
</p>
<p align="center">
    <em>Figure 5:The false discovery number of differentially expressed genes is lower in SCBN across different numbers of conserved genes and varying noise levels </em>
</p>

 It was also shown that a larger percentage of the genes identified as differentially expressed by SCBN were associated with evolution or illness, thereby indicating that the genes identified by SCBN had greater functional importance than those found by the median method. 
 
####  Comparing SCnorm and TPM 
An experiment to test SCnorm was designed to sequence cells at very different depths. Prior to normalization, counts in the second group will appear four times higher on average given the increased sequencing depth. If normalization for depth is effective, fold-change estimates should be near one. After using the various normalization techniques on the data, SCnorm provides normalized data that results in fold-change estimates near one, whereas other methods show biased estimates, as seen in figure 6 below<sup>[5]</sup>.

<p align="center">
  <img src="https://github.com/nbangari/BENG183_Final_Projects_FALL2019/blob/master/Normalization/img/image2.png" width="300">
</p>
<p align="center">
    <em>Figure 6: For each gene, the fold-change of non-zero counts between two groups was computed for data following normalization via SCnorm, MR, TPM, scran, SCDE, and BASiCS. Box-plots of gene-specific fold-changes are shown in the panel for data normalized by each method <sup>[5]</sup>.</em>
</p>

#### Comparing TMM against other methods
In one study, researchers compared TMM to several other normalization strategies and noticed that for accessions with read lengths of 35 nucleotides, RPKM was able to get much higher correlation values, which means it had more accurate gene expression values, than TMM<sup>[7]</sup>. This they believed illustrated that the consideration of the transcript length in normalization is quite effective and can have a major impact on the gene expression analysis.

## 4. Summary<a name="4"></a>
Normalization is an important step in RNA-seq analysis because it allows you to compare within and between samples. This step is done after you have the raw counts for each gene and sample, before starting the differential gene analysis. There are numerous methods of normalization because there are different factors that need to be optimized when performing RNA-seq analysis, and which normalization method is needed depends on the type of RNA-seq analysis being done.


## 5. References<a name="5"></a>

[1] Alberts, B., Johnson, A., Lewis, J., Raff, M., Roberts, K., & Walter, P. (2002). Molecular Biology of the Cell 4th edn (New York: Garland Science). Ann Bot, 91, 401.

[2] Mortazavi, A., Williams, B. A., McCue, K., Schaeffer, L., & Wold, B. (2008). Mapping and quantifying mammalian transcriptomes by RNA-Seq. Nature Methods, 5(7), 621.

[3] Wagner, G. P., Kin, K., & Lynch, V. J. (2012). Measurement of mRNA abundance using RNA-seq data: RPKM measure is inconsistent among samples. Theory in Biosciences, 131(4), 281-285.

[4] Zhou, Y., Zhu, J., Tong, T., Wang, J., Lin, B., & Zhang, J. (2019). A statistical normalization method and differential expression analysis for RNA-seq data between different species. BMC Bioinformatics, 20(1), 163.

[5] Bacher, R., Chu, L. F., Leng, N., Gasch, A. P., Thomson, J. A., Stewart, R. M., … Kendziorski, C. (2017). SCnorm: robust normalization of single-cell RNA-seq data. Nature Methods, 14(6), 584–586. doi:10.1038/nmeth.4263

[6] Robinson, M. D., & Oshlack, A. (2010). A scaling normalization method for differential expression analysis of RNA-seq data. Genome Biology, 11(3), R25.

[7] Li, P., Piao, Y., Shon, H. S., & Ryu, K. H. (2015). Comparing the normalization methods for the differential analysis of Illumina high-throughput RNA-Seq data. BMC Bioinformatics, 16, 347. doi:10.1186/s12859-015-0778-7

[8] Zhong, S. BENG 183 Lecture Slides: https://sites.google.com/eng.ucsd.edu/beng183-fa19/schedule
