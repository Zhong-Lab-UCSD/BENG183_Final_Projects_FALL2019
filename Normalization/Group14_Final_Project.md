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
  


