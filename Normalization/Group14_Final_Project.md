# RNA-Sequencing Analysis Normalization Techniques

By Daniella Vo, Nidhi Bangari, Priya Jindal

## Introduction

  RNA-sequencing is used to determine the gene expression levels, which allows 
researchers to identify differentially expressed genes, discover new RNA isoforms,
and genomic mutations. The input for RNA-seq analysis is raw reads, and the output is differentially expressed genes, which are genes that are expressed differently for different cells. The pipeline for RNA-seq analysis is shown below:

<p align="center">
  <img src="https://github.com/nbangari/BENG183_Final_Projects_FALL2019/blob/master/Normalization/img/image6.png">
</p>

  The third step in the RNA-seq data analysis workflow is Expression quantification. During this step, we are able to measure the expression level of a gene as a measure of the number of RNA reads that were aligned to it. The difference between two individuals is not only limited to genomic differences in DNA. An individual with the same genome in all of their cells will still have different cells behaving differently due to differing levels of gene expression. Gene expression is regulated at many levels, one of which is the transcriptional level; a variety of transcription factors determine which genes will be transcribed and in what amounts at any time. The expression of genes in a cell can vary with environment, situations of stress, disease, etc. and understanding gene expression levels is key for a lot of research. For example, we can use gene expression levels to identify differentially expressed genes in cancer patients, and use this information to diagnose cancer early. 
  
  In the expression quantification step of RNA sequencing, the mapped reads to the genome are counted using tools such as featureCounts which determine the raw mapped read counts for sections of the genome. However, we cannot make any conclusions on gene expression solely based on these raw mapped read counts and therefore need to perform normalization.
  In this paper, we will be discussing the importance of normalization and going into detail to explore various normalization strategies or techniques that are commonly used. Each technique has its own pros and cons and we will be comparing the techniques to one another to see how they perform with respect to each other. Normalization is important because if we simply measure the expression level of a gene as the raw number of RNA reads that were aligned to it, we will get an inaccurate picture. A very long gene is expected to have more reads that align to different parts of the gene than a short gene with the same expression level. In addition, if many copies of reads were made in the PCR step and we had a very large total read library size, then many more reads would align to a single gene than if we have a small total read library size. Therefore we need to adjust for gene length and library size in order to get an accurate picture of expression levels. Without normalization, it will be difficult to compare between and within different samples.
  
  There are various approaches to normalization. In this paper we will look at the various algorithms used for normalization and how they compare to one another by looking at applications of these methods. 
  
## Normalization Techniques 
The following are some different techniques in place to normalize RNA-seq data:

* RPKM stands for Reads Per Kilobase of transcript per Million
  Steps for RPKM:
  1. The numerator is the read counts aligned to a single gene.
  2. The total reads in a sample divided by 1,000,000 is our “per million” scaling factor. Multiply this by the length of the gene in        kilobases. This is our denominator.
  3. Numerator / denominator = RPKM value
  
  Dividing the number in Step 1 by the number in Step 2 gives you reads per million (RPM) and normalizes for sequencing depth. Dividing   by the RPM values by the length of the gene in kilobases gives reads per kilobase of transcript per million (RPKM), and additionally     normalizes for gene length[1]. 
  ![RPKM](https://github.com/nbangari/BENG183_Final_Projects_FALL2019/blob/master/Normalization/img/image5.png)
  
* TMM stands for trimmed means of M-values. 

  TMM is a method of normalization that estimates the relative RNA production level from RNA-seq data by estimating scale factors         between samples. TMM is calculated by dividing raw counts by the library size times a normalization factor. The library size is used     to account for the size of the library since a larger library can lead to more reads aligned but not necessarily more gene               expression. The normalization factor is used to account for “compositional biases” for example when certain genes are very highly       expressed to too low these may be outliers, TMM takes out these high and low expression outliers and only takes the mean of the         remaining values. TMM works under the assumption that the majority of genes are not differentially expressed. The main difference       between TMM and other normalization strategies is the TMM does not account for the length of the gene or transcript.[5]
    
    - WorkFlow : This briefly explains what occurs when we use TMM in R, since it is implemented in the the edgeR Bioconductor package:           
       1. Use the calcNormFactors function in the package to calculate normalization factors
          * Internally these normalization factors account library size
          * And determine a scaling factor based on the binomial distribution of data input since we are only using the mean or trimmed             values and are removing outlier values. 
      2. Then the raw gene counts are rescaled by dividing each gene count by the scaling factor for each run. 
      3. TMM is the sum of rescaled gene counts of all runs.



 

  


