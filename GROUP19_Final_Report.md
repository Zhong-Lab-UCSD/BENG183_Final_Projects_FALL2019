# Genome-Wide Association Studies

Authors: Yoon Kang, Sneha Lakshmanan, Jonathan Bui


# Introduction to Population Genetics


## What is population genetics?[^1][^2]

Population genetics is the study of genetic variations within populations. The genetic variations could include changes in the frequencies of genes and alleles in a population. The focus of population genetics is on the population of the species, not on the individual. The genes found within a population will be polymorphic, meaning that it will be in different forms or alleles. Each individual in a population receives its alleles from other members of the population (parents). As these alleles are passed down, variations of the alleles may occur. Population genetics is the study of these variations, how these variations change from one generation to the next, and the impact of these variations on the population overall. Variations within a population are caused by mutations, genetic drift, natural selection, environmental diversity, migration, and non-random mating patterns. 


## Why perform population genetics studies?

Studying population genetics allows us to predict the occurrence of different alleles in a population. It is useful in the study of microevolution, population dynamics, and conservation genetics. It can also help us understand genetic variation and how that causes complex diseases like cancer

# Full Genome Sequences and SNPs


## Methods for producing full genome sequences[^3]

The NCI (National Cancer Institute) defines whole-genome sequencing in humans as “a laboratory process that is used to determine nearly all of the approximately 3 billion nucleotides of an individual’s complete DNA sequence, including non-coding sequence.” Full-genome sequencing can be done by Sanger sequencing, but this method takes a very long time and is very expensive. For example, it took more than a decade and more than $1 billion to sequence the entire human genome. Sanger sequencing is done by a **clone-by-clone method**. A clone-by clone method is where a whole sequence is fragmented and each fragment is cloned in bacteria to produce multiple copies. Those fragments are broken down further and each of those smaller fragments is sequenced. Today, we have “next-generation sequencing” techniques to sequence full genomes more efficiently. In general, next-generation sequencing technologies break the whole sequence into fragments that are then individually sequenced and reassembled back into the whole sequence with the help of bioinformatics techniques. One method that was used for Sanger Sequencing but is better utilized in next-generation sequencing is **whole-shotgun sequencing**. In shotgun sequencing, the whole sequence is fragmented and then cloned in bacteria. But in this case, the fragments are random so they may overlap with other fragments, aiding the reassembly into the whole sequence. It also works better for shorter sequences. Because of these differences, whole-shotgun sequencing is best utilized with a reference genome. It also requires computational techniques for reassembly. 

After fragments are sequenced, they must be reassembled together to produce the whole genome sequence. There are multiple ways to do this as well. The two most common methods are **de novo assembly** and** assembly by reference matching**. De novo assembly assembles the genome by looking at overlapping sequences. It is done without a reference genome, and therefore is the only viable method to sequence new organisms. De novo assembly is challenging, but it presents less bias than mapping with a reference genome. Assembly by reference matching is easier but is only as good as the reference genome chosen. New or unexpected reads can be lost when using this method. However, this method presents the opportunity to identify single nucleotide polymorphisms (SNPs), which is useful for population genetics. 

Different biotechnology companies develop their own rapid sequencing technologies. Illumina’s HiSeq approach is rapid, high-throughput, and reasonably priced. It is an approach used by many research laboratories and clinics. Illumina also developed MiSeq, which can rapidly sequence a small portion in one day. They also offer other different methods of sequencing based on the sample that needs to be sequenced. Thermo Fisher Scientific designed a unique technique based on the detection of pH differences. Another company, Oxford Nanopore Technologies, introduced their MinION, which enables anyone to sequence on a desktop computer using a USB device. The DNA is passed through a protein nanopore membrane for sequencing and detection by creating an ionic current that varies based on the nucleotide. Next-generation sequencing relies heavily on technology and computational approaches, which can be modified based on the sample. 


## What are SNPs, distribution of SNPs in the population, and variation of SNPs in the population[^4][^5]

SNPs, or single nucleotide polymorphisms, are the most common genetic variation among populations. SNPs are caused when there is a change in a nucleotide in a DNA sequence. These are also known as mutations. There are different kinds of mutations that can occur, like base substitution, deletion, or insertion. SNPs are a normal event and occur frequently. Some SNPs are not harmful and do not alter gene function. However, some SNPs can alter gene regulation or function causing genetic diseases. SNPs may be unique to an individual or may occur in multiple individuals. Acting as biomarkers, SNPs can help scientists find dysregulated genes. SNPs can be used to analyze variations within a population and how those variations result in specific phenotypes. Many SNPs common in one population is present in other populations, but they may not be common in other populations. Additionally, SNPs common in more than one population can differ in frequency among the populations. 


## Definitions

Some frequently used words throughout the chapter are defined here:

**Haplotype **- group of alleles inherited from a single parent

**Genotype **- the genetic composition of a cell or individual

**Phenotype **- the physical composition of a cell or individual as a result of its genotype

**SNP **- single nucleotide polymorphism. Sometimes called SNV, or single-nucleotide variant.

**Allele **-  variant form of a given gene

**Quantitative **- relating to the quantity, numerics, something that can be counted

**Qualitative **- relating to qualitative data, descriptive, something that cannot be measured, but can be observed

**Mendelian trait **- traits passed down from dominant and recessive alleles of one gene

**P-value **- probability of obtaining the test results or more extreme results in statistical hypothesis testing. Usually we define any p-value under 0.05 as statistically significant test result; otherwise, the test results might have been by chance. However, in the context of GWAS, the p-value threshold for significant is usually 5 * 10^(-8) or lower[^6].


# Comparative Genomics and Building Associations between Traits and SNPs


## Types of GWAS Studies[^7]

Genome-wide association studies are performed to find correlations between phenotype and genotype. A GWAS can fall under one of two major study designs depending on the phenotype of interest. The first design is a case-control design where the phenotype of interest, most likely a disease, is either expressed in the subjects or not expressed. In this GWAS design, a group of subjects without the disease who form the control group are compared to a group of subjects with the disease who form the case group. For instance, a group of individuals who never had lung cancer could be compared to a group of individuals with lung cancer in this type of GWAS. The second design is a quantitative design where the phenotype of interest is not binary in nature. Every person expresses this phenotype to varying quantitative levels. For instance, this type of GWAS can be used to study the quantitative trait of height. 

The overall goal of performing a GWAS, regardless of its design, is to identify locations in the genome associated with these phenotypes of interest. 


## Mendelian vs Complex and Multifactorial Inheritance

A common factor of the phenotypes being studied in a GWAS is that they are complex traits. Complex traits (also known as polygenic traits) are those influenced by multiple genes in the genome unlike Mendelian traits which are influenced by a single gene.[^8] Examples of complex traits include cancer, Alzheimer’s Disease, diabetes, and schizophrenia. Complex traits can also be multifactorial, meaning that they are influenced by environmental factors in addition to gene activity.[^9] An example of a multifactorial trait is height.[^10] One’s height is determined by many genes as well as by factors like nutrition, exercise, and sleep. Polygenic and multifactorial traits are studied in a GWAS because they do not follow Mendelian inheritance patterns. 


## GWAS Steps[^11]

The goal of a GWAS is to find genome loci associated with the phenotype of interest. The main steps of a GWAS are as follows:



1. Identify a phenotype of interest
2. Find populations of subjects appropriate for the study
3. Collect DNA samples from adequately large cohorts of these populations
4. Genotype each sample with SNP arrays (SNP chips)
5. Test regions in the genome for association with the trait
6. Analyze and interpret the results


# Visualizing GWAS Data


## GWAS Workflow with Plink[^12]

Plink is a software commonly used when performing a GWAS. It can be used to perform quality control on the data, assess population stratification, and perform association tests. Quality control and association tests will be covered in more detail in the following subsections. It should be noted that Plink is not used for visualization which can be done using R or Python instead. 

![plinkworkflow](https://slideplayer.com/slide/3256187/11/images/4/PLINK+in+GWAS+workflow+Experimental+Design+%26+Sample+Collection.jpg)

**Figure 1.** A GWAS workflow starting from the top right corner with experimental design and sample collection. The steps using Plink are in a red box and they are performing quality control on the data, assessing population stratification, and performing association tests. 

Figure by Wu, Guodong. “BST 775 Lecture: PLINK — A Popular Toolset for GWAS.” BST 775, 24 Sept. 2013, University of Alabama at Birmingham. 


## Testing for Association[^12]

After genotyping each sample, association tests need to be performed to measure correlation. A common way to test correlations between genotype and phenotype is to perform a linear regression. More specifically, a linear regression with genotype as an independent variable (x) and phenotype as a dependent variable (y) can show how strongly correlated the allele frequencies found at each SNP are with the phenotypic outcome. Performing a linear regression can yield two insights on the correlations within the SNP data. Firstly, the effect size (the slope of the regression line) can be obtained after performing a regression to quantify the extent of the influence the genotype has on the phenotype. Secondly, a p-value can be used to evaluate the confidence for the quantified associations. It should be noted that linear regression is not the only method used to quantify association. Lastly, association tests do not have to be calculated by hand, and Plink is a popular tool that can perform these calculations. 


## QQ-Plots and Data Correction[^13]

Quantile-Quantile plots, or QQ-Plots, are a way to visualize the quality of the p-values in the GWAS. If we consider the case where the p-values from the association tests were generated at random for each SNP (the case where the null hypothesis is true) the p-values obtained would follow a uniform distribution because any random p-value is equally likely to occur. A uniform distribution would also be observed for p-values obtained in the case where no SNPs were associated with the phenotype of interest, or in other words, there is no signal, since any p-value can be obtained due to noise. If the p-values from these two cases were to be plotted where the random p-values went on the x-axis and p-values from SNPs with no association to the phenotype went on the y-axis, we would observe a line with a positive slope. 

Confounding factors like ancestry or sex might cause two groups of people to have different genotypes at SNP positions. Confounding factors pose a problem when analyzing GWAS data since it leads to many false positive p-values. These false positive p-values incorrectly flag a SNP as significantly associated with the trait when in reality, the differences in genotype are due to these confounding factors and aren’t actually associated with the trait. The effect of confounding factors can be visually detected through a QQ-plot. When the p-values prior to correcting for confounding factors are plotted against randomly generated p-values (p-values under the null), a diagonal line more elevated than the line seen when there is no signal is observed. Confounding factors can be corrected for in Plink by loading covariates. Plink also contains multiple testing corrections for the p-values. (Confounding factors will be covered in more depth in a later section). 

The ideal QQ-plot should show a curve where most of the points fall on the line for the null distribution except for a small group of points that are highly elevated. These points indicate a cluster of SNPs significantly associated with the trait. 

![qqplot](https://images.slideplayer.com/47/11710376/slides/slide_35.jpg)

**Figure 2.** Three QQ plots. The leftmost QQ plot indicates that there is no signal from the data. The middle QQ indicates that there is a SNP position associated with the trait and is the most ideal. The rightmost QQ plot indicates that there is p-value inflation and the data must be corrected. 

Figure by Bryan, Dennis. “Genome-Wide Association Studies (GWAS).” Slide presentation.


## Manhattan Plots[^13]

Manhattan Plots are generated to visualize associations between genotype and phenotype for each SNP. They are easily identifiable by their tall peaks which resemble skyscrapers of a city, hence the name “Manhattan” plots. The x-axis represents the SNP positions along the genome which is organized by chromosome. The y-axis represents the negative log base 10 of the p-value obtained from performing an association test (as described in the previous section). The negative log base 10 calculation is applied to every p-value in order to obtain a plottable y-coordinate since p-values tend to be very small numbers that can be hard to distinguish. Therefore each point on the plot represents how closely associated each SNP is with the trait.


## Identifying a Significant GWAS Hit

A threshold of significance is needed to determine which SNPs actually have statistically significant association with the trait. Generally, the threshold is set to be the value 5 * 10^(-8).[^14] Visually, this threshold of significance is a baseline p-value that is shown as a horizontal and sometimes dashed line on the plot. If a SNP has an association that is statistically significant, it will have a y-axis value greater than the threshold y-axis value which is seen as a point plotted above the dashed line, indicating a p-value less than the threshold p-value. These points would be valid GWAS hits, or in other words, valid locations along the genome correlated to the trait of interest and can be further studied. 

![manhattanplot](https://www.researchgate.net/profile/Michael_Zwick/publication/280032519/figure/fig1/AS:284511138009089@1444844149773/Manhattan-plot-of-SNP-association-p-values-result-for-CD-vs-controls-within-pediatric.png)

**Figure 3. **A Manhattan plot showing** **SNP positions along the genome organized by chromosome on the x-axis and the negative log base 10 of the p-values from association tests on the y-axis. The significance threshold is shown as a solid horizontal black line. Genes located at the significant GWAS hits are identified. 

Figure by Cutler, David J, et al. “Dissecting Allele Architecture of Early Onset IBD Using High-Density Genotyping.” _PloS One_, Public Library of Science, 22 June 2015, www.ncbi.nlm.nih.gov/pubmed/26098103.


## Linkage Disequilibrium 

During meiosis, independent assortment of alleles within each chromosome occurs. These alleles could be “linked” or located on the same chromosome. In the case where these linked alleles are located close to each other on the chromosome, there is less of a chance that recombination will occur between these alleles to separate them. As a result, these linked alleles are more likely to be passed down to the offspring together. This phenomenon is known as linkage disequilibrium.[^7] Linkage disequilibrium is visually reflected in the peaks of the Manhattan plots. Each significant hit is generally composed of a cluster of multiple points with significant p-values as opposed to a single significant point even though there is only one causal variant. Linkage disequilibrium can be useful when performing a GWAS because a region of the genome associated with the phenotype can still be detected without having to genotype all possible SNPs since regions nearby the causal variant will be reflected as a hit.[^15]

## Evaluating and Interpreting Results[^13]

Significant hits identified from a Manhattan plot reveals positions in the genome that could be associated with the trait of interest. Therefore it’s important to note that a GWAS does not explain causal factors or identify a single causal variant. This fact is especially important to note since the traits studied under a GWAS are complex and multifactorial, meaning that the trait can be influenced by multiple genes and environmental factors. Furthermore, genes identified through a GWAS can also be noncoding. Ultimately, a GWAS only reveals candidate loci that can be traced to genes of the genome that could cause the trait. Further analyses such as CHip-Seq or RNA-seq should be performed to gain further insight for the trait of interest. 


# Limitations of GWAS[^6]


## Correlation vs. Causation

A genome-wide association study identifies what genetic differences are shared within two groups from different populations, informing the direction of future research into the causal link of that genetic variant. Why can’t a GWAS immediately identify causal genetic factors of a phenotype? Simply put, as part of the experimental design, researchers manually classify study participants into two groups of differing phenotypes, and perform a GWAS to identify the common SNPs that differ. Critically, the study groups are classified based on phenotype-- and every biologist knows that phenotype is complex. Not every trait can be immediately assumed to be Melendian (i.e. one SNP = one phenotype), and thus SNPs identified as significant in a GWAS can only be said to be _significantly associated_ with a given phenotype, while implying nothing about the role of that SNP in causing a phenotype.


## GWAS are not very powerful

Genome-wide association studies crunch a lot of data-- an individual human genome is roughly 3.2 billion base-pairs long, and every person has a unique genome! However, large unique datasets are also noisy, requiring the application of multiple statistical tests to ensure that a given SNP is truly significant. A GWAS will typically set the genome-wide false-positive rate at 5%, assuming 1 million independent tests for genetic variation are performed. Ultimately, this means that a SNP must have a p-value < 5 * 10^(-8) to be considered statistically significant[^6]. As more genomic data is accumulated in the future, the p-value threshold will likely need to be even more lower to account for additional statistical tests.

There are two general methods to tease out more significant results from a GWAS: increase the sample size, or reduce the number of statistical tests performed[^6]. Depending on the circumstances, expanding the size of the study cohort (i.e. gathering more data) can be difficult. Reducing the number of statistical tests may be preferable; this is done by (for example) limiting the analysis region to only genomic regions of known biological interest, thus excluding background genomic variability across the study population (i.e. make the dataset smaller). In either case, the fundamental limitations of the data must be considered in downstream analyses when interpreting the significant results produced by a GWAS.


## SNP chip data and how they differ from full genomes[^16]

Since genome-wide association studies are intended to identify the nucleotide variants present across members of a population, one might expect that researchers compare the full genome sequences of all individuals participating in the study. However, whole-genome sequencing (as of 2019) is still not widely used for GWAS; instead, many studies are based on partial genetic data collected from SNP chips, called “genotyping.” Additionally, different studies use different SNP chips for genotyping, which generates slightly different datasets because the chosen marker SNPs are not the same. This prevents direct comparisons between published GWAS datasets. To work around this, missing data can be estimated via statistical imputation, a bioinformatic technique to generate a common set of SNPs.


### Imputation, and a warning[^6][^17][^18]

Imputation is the process of filling in missing data with estimated values. Imputation is necessary in order to make different datasets comparable, since comparisons can only be made between identical nucleotide variants at a specific location in the genome.

Imputation works because there are known shared haplotype frequencies in populations of shared ancestry, such as those identified from HapMap or the 1000 Genomes project. (A haplotype is a set of closely linked alleles, and usually inherited together). These reference population datasets are used to estimate the unobserved SNPs surrounding an observed SNP in the dataset[^16]. There are many published algorithms to perform imputation on partial genomic datasets, such as IMPUTE2, PBWT, and Minimac3. 

However, imputation must be performed carefully! The reference population (which the imputation is based on) must match the study population, because different populations share different haplotypes. For example, if only individuals of European descent are present in the reference dataset, but the study population concerned individuals of African descent, then imputation would work poorly. Additionally, any downstream analyses must account for the inherent uncertainty of the imputed data-- in the end, the imputed data is not real, observed data!


## Confounding Factors in a GWAS


### Phenotype is complex

Phenotype is complex and influenced by a combination of factors, such as age, sex, environment, and inherited genetic factors. Teasing out the purely genetic factors for a particular phenotype is a Herculean task that genome-wide association studies cannot fully address. In fact, GWAS so far can only explain a small fraction of heritable traits, with different genes possibly playing different roles depending on the environment. In simulations, up to 90,000 to 100,000 SNPs may be implicated in explaining about 80% of the heritability of height[^6]; given that there are roughly 20,000 genes in the human genome, GWAS results would likely not be useful in teasing out the genetic factors for complex traits.


### Different genotyping platforms[^16]

Genome-wide association studies depend on the availability of sequence data from a large population sample; as mentioned previously, whole-genome sequencing is not often used to generate these datasets. Different SNP chip (microarray-based) technologies/platforms genotype different parts of the genome and must be tailored to different populations. For example, genotyping individuals of African descent requires collecting SNP data with greater genomic coverage compared to the SNP data necessary for studies on individuals of European descent, because the African genome is more varied (thus requiring more data to be useful).


# Applications of GWAS


## Research applications

Genome-wide association studies are primarily used as a research tool to examine the genetic basis for phenotype, and in order to refine the direction of future research into interesting genetic variants. For certain heritable diseases such as Alzheimer’s, GWAS have been able to identify the genomic loci associated with risk of developing the disease[^19]. This is typical of how GWAS are used in research. Another well-known GWAS result is that the risk of developing breast cancer is increased if a person carries a particular version of the BRCA1 gene[^20]. GWAS are most useful in detecting single alleles of large significance, such as those that cause metabolic disorders or autoimmune diseases[^21]. 


## Clinical Applications

As mentioned in the section [Correlation vs. Causation](#Correlation-vs.-Causation) and [Confounding Factors in a GWAS](#confounding-factors-in-a-gwas), genome-wide association studies are not terribly useful for finding low-impact causal genetic mutations. Instead, genome-wide association studies are most powerful when used on a large sample size to identify a single SNP of large phenotypic effect (e.g. identifying the genes responsible for severe autoimmune diseases). This statistical power is useful in the aggregate; a doctor would not order a GWAS to diagnose a single patient. However, using the research findings gleaned from GWAS, a doctor may make more informed treatment decisions for a patient.

Direct-to-consumer genetic tests (such as those provided by 23andMe) or genetic screens ordered by a doctor, are generally not useful as a clinical diagnostic tool. Instead, genetic tests (backed by GWAS findings) are used to add context to the medical decisions a doctor might make in conjunction with a doctor’s clinical experience. GWAS findings and genetic tests do not, by themselves, conclusively identify a person’s susceptibility to disease or treatment[^22].


# Citations

[^1]:
     “Population Genetics.” _University of Leicester_, 1 Aug. 2017, www2.le.ac.uk/projects/vgec/highereducation/topics/population-genetics.

[^2]:
    Maia, Rafael Trindade, and Magnólia de Araújo Campos. “Introductory Chapter: Population Genetics - The Evolution Process as a Genetic Function.” _IntechOpen_, IntechOpen, 18 Feb. 2019, https://www.intechopen.com/books/integrated-view-of-population-genetics/introductory-chapter-population-genetics-the-evolution-process-as-a-genetic-function.

[^3]:
     “Whole-Genome Sequencing Methods.” _Healio_, https://www.healio.com/hematology-oncology/learn-genomics/whole-genome-sequencing/whole-genome-sequencing-methods.

[^4]:
     “What Are Single Nucleotide Polymorphisms (SNPs)? - Genetics Home Reference - NIH.” _U.S. National Library of Medicine_, National Institutes of Health, https://ghr.nlm.nih.gov/primer/genomicresearch/snp.

[^5]:
     Guthery, Stephen L., et al. “The Structure of Common Genetic Variation in United States Populations.” _The American Journal of Human Genetics_, Cell Press, 9 Jan. 2008, https://www.sciencedirect.com/science/article/pii/S0002929707637707.

[^6]:
     Tam, Vivian, et al. “Benefits and Limitations of Genome-Wide Association Studies.” _Nature Reviews Genetics_, vol. 20, no. 8, 2019, pp. 467–484., doi:10.1038/s41576-019-0127-1.

[^7]:
     Bush, William S, and Jason H Moore. “Chapter 11: Genome-Wide Association Studies.” _PLoS Computational Biology_, Public Library of Science, 2012, www.ncbi.nlm.nih.gov/pmc/articles/PMC3531285/.

[^8]:
     Singh, Abanish. “Complex Traits.” _SpringerLink_, Springer, New York, NY, 1 Jan. 1970, link.springer.com/referenceworkentry/10.1007%2F978-1-4419-1005-9_680.

[^9]:
     Korf, Bruce R. “Introduction to Human Genetics.” _Clinical and Translational Science (Second Edition)_, Academic Press, 2 Dec. 2016, www.sciencedirect.com/science/article/pii/B9780128021019000168#s0120.

[^10]:
     “Multifactorial Inheritance.” _Multifactorial Inheritance - Health Encyclopedia - University of Rochester Medical Center_, www.urmc.rochester.edu/encyclopedia/content.aspx?contenttypeid=85&contentid=p07268#:~:targetText=A%20combination%20of%20genes%20from,genes%20and%20shared%20environmental%20factors.&targetText=Diseases%20such%20as%20diabetes%2C%20high,pressure%2C%20or%20cancer%20are%20multifactorial.

[^11]:
     Tam, Vivian, et al. “Benefits and Limitations of Genome-Wide Association Studies.” _Nature News_, Nature Publishing Group, 8 May 2019, www.nature.com/articles/s41576-019-0127-1.

[^12]:
     Marees, Andries T, et al. “A Tutorial on Conducting Genome-Wide Association Studies: Quality Control and Statistical Analysis.” _International Journal of Methods in Psychiatric Research_, John Wiley and Sons Inc., June 2018, www.ncbi.nlm.nih.gov/pmc/articles/PMC6001694/.

[^13]:
     Ehret, Georg B. “Genome-Wide Association Studies: Contribution of Genomics to Understanding Blood Pressure and Essential Hypertension.” _Current Hypertension Reports_, U.S. National Library of Medicine, Feb. 2010, www.ncbi.nlm.nih.gov/pmc/articles/PMC2865585/.

[^14]:
     Fadista, João, et al. “The (in)Famous GWAS P -Value Threshold Revisited and Updated for Low-Frequency Variants.” _Nature News_, Nature Publishing Group, 6 Jan. 2016, www.nature.com/articles/ejhg2015269.

[^15]:
     Stankovich, Jim. _Statistical Analysis of Genome-Wide Association (GWAS) Data_. bioinformatics.org.au/ws09/presentations/Day3_JStankovich.pdf.

[^16]:
     Bush, William S., and Jason H. Moore. “Chapter 11: Genome-Wide Association Studies.” _PLoS Computational Biology_, vol. 8, no. 12, 2012, doi:10.1371/journal.pcbi.1002822.

[^17]:
     Schurz, Haiko, et al. “Evaluating the Accuracy of Imputation Methods in a Five-Way Admixed Population.” _Frontiers in Genetics_, vol. 10, 5 Feb. 2019, doi:10.3389/fgene.2019.00034.

[^18]:
     Li, Yun, et al. “Genotype Imputation.” _Annual Review of Genomics and Human Genetics_, vol. 10, no. 1, Sept. 2009, pp. 387–406., doi:10.1146/annurev.genom.9.081307.164242.

[^19]:
     Cruchaga, Carlos, et al. “GWAS of Cerebrospinal Fluid Tau Levels Identifies Risk Variants for Alzheimer’s Disease.” _Neuron_, vol. 78, no. 2, 24 Apr. 2013, pp. 256–268., doi:10.1016/j.neuron.2013.02.026.

[^20]:
     Kraft, Peter, and Christopher A Haiman. “GWAS Identifies a Common Breast Cancer Risk Allele among BRCA1 Carriers.” _Nature Genetics_, vol. 42, no. 10, 28 Sept. 2010, pp. 819–820., doi:10.1038/ng1010-819.

[^21]:
     Visscher, Peter M., et al. “Five Years of GWAS Discovery.” _The American Journal of Human Genetics_, vol. 90, no. 1, 13 Jan. 2012, pp. 7–24., doi:10.1016/j.ajhg.2011.11.029.

[^22]:
     “Direct-to-Consumer Genetic Tests.” _Consumer Information_, 13 Mar. 2018, www.consumer.ftc.gov/articles/0166-direct-consumer-genetic-tests.
