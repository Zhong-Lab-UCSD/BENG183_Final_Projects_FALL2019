#Variant Calling Using Deep Variant: A Deep Learning Approach

Zoe Li, Tianyi Zhang, Ningxin Kang
Dec 9 2019

###Abstract
We are unique genetically because we have variations in our DNA. Genetic variants can be grouped into three categories by size: single nucleotide variant (SNV), insertion and deletion (indel), and structural variant (SV, including copy number variation, duplication, translocation, etc.). With the advancement of NGS(Next-generation Sequencing), tons of genetic data is produced for analysis. To identify mutation, the first important step is to detect candidate variants. Currently, we have a few tools available for variant calling: Deep Variant, GATK, and SpeedSeq. We will briefly introduce all three of these tools and then compare them in terms of their performance, runtime, device requirement, and potential possibilities in the following chapter. Among these three tools, Deep Variant is one of the newest TensorFlow based deep learning variant caller, which was first published in 2017 by winning the PrecisionFDA Truth Challenge. We will include a deeper explanation and analysis of how DeepVariant works with a step by step tutorial.


###Introduction

####GATK Methods:
The variant call software in GATK is called HaplotypeCaller. It can call SNPs and indel. The procedure generally contains following steps:
1. Define active regions 
Basically in this step the software finds the region where it needs to work on (Where there are differences) and ignore the parts that match perfectly.
2. Determine haplotypes by assembly of the active region
The program generates a De Brujin graph based on the alignment. From that, it predicts possible haplotypes from the data. A haplotype is a set of k-mers that represent possible sequences. Then the program redo a local alignment using the Smith-Waterman algorithm to identify possible sites of variant.
3. Determine likelihoods of the haplotypes given the read data 
Using PairHMM algorithm, the program aligns each possible haplotype(different k-mers) with the reference. The result is recorded in a matrix form where each element represents possibility where a certain haplotype is the true form. Then the matrix is marginalized, producing the probability each allele.
4. Assign sample genotypes 
Bayes' rule is used to calculate the possibility of genotypes per sample using the results generated from the last step. Finally the program pick the highest possible genotype.

####SpeedSeq Methods:
####Deep Variant Methods:
###**Compartion of three methods**

###**Walkthrough of DeepVariant**

###**Reference**
