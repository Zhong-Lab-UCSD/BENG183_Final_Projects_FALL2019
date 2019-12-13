<img src="https://i.imgur.com/UHs2ojK.png" width=300px/>

## Overview
In examining the diversity of life, we're often directed to the sequence of an organism's DNA as the source of variation. Differences in these genomes are directly correlated with changes in genetic products, regulatory effects, and molecular interactions--all of which contribute to the great phenotypic variation observed in our world.

However, in this paper, we wish to look beyond the genome. Instead, we introduce the topic of epigenomics, the analysis of gene expression that is not attributable to mutations to the DNA sequence of a genome. Rather, epigenetic expression alteration is caused by biochemical interactions with various proteins and other compounds.

We will briefly describe the biology of the two most well-known epigenomic modifications: [DNA Methylation](#Biology-DNA-Methylation) and [Histone Modifications](#Biology-Histone-Modifications). Then, we will describe in detail the analytical techniques and technologies used to quantify each epigenomic modification.

## Biology: DNA Methylation
### Introduction
The first epigenomic modification discovered was DNA methylation. Uncovered as early as when Rollin Hotchkiss formalized the notion of DNA being the genetic material (1984), DNA methylation remains one of the most influential epigenomic modifications today.<sup>13</sup>

On the surface, it appears to be a simplistic process. DNA methyltransferases (DNMTs) transfer methyl groups from S-adenosyl methionine (SAM) to the fifth carbon of cytosine residues to form 5-methylcytosine (5mC), thereby directly methylating DNA.<sup>3</sup> As we'll see, this simple change can have an astronomic effect. First, some basics.

### I. CpG Islands
As mentioned above, it is cytosine bases that are methylated. Not all cytosines, however, are equally prone to methylation; the majority of methylation happens on cytosines that precede a guanine nucleotide, a motif called a CpG site.<sup>3</sup> CpG sites are often grouped in close proximity, which forms a CpG island. The overall methylation of CpG islands is the primary driver of methylation changing gene expression.<sup>3</sup>

For a region to be considered a CpG island, it must have:
1. A sequence length longer than 200bp
2. A GC content of more than 50%
3. A statistical ratio of observed/expected CpG (cytosine followed by guanine) greater than 0.6

In the human genome, there are around 25,000 such CpG islands, about half of which contain transcription start sites.<sup>3</sup> Such CpG islands can directly influence expression levels, which we'll explore next.

### II. Repression Mechanism
In fact, there are two ways in which the methylation of a CpG island near a transcription start site may inhibit gene expression: Steric Bulk and Protein Binding.

#### Steric Bulk
The addition of a methyl group to cytosines increases the steric bulk of the molecule. Specifically, the addition of a CH<sub>3</sub> group adds a physical barrier that functions as a guard for the grooves in the double-helical structure of the DNA.<sup>13</sup> 

Because these grooves are critical for protein specificity recognition, the bulk created by the methyl group inhibits the binding of transcription factors and, therefore, downstream gene expression.

<img src="https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/Steric_Bulk.png" height=300px/>
<i><b>Figure 1</b> Overview of steric hinderance caused by methylation of DNA, resulting in transcriptional repression.</i>

#### Protein Binding
There exist proteins that bind to CpG motifs if and only if they are methylated. These proteins are denoted “Methyl-CpG-binding domain proteins” (MBDs).<sup>3</sup> MBD binding innately amplifies the steric hinderance mentioned above.

Their main repressional mechanism, however, is not steric. Rather, MDBs recruit histone deacetylases, proteins that remove acetyl groups from histones. (As we’ll see below, acetyl groups binding to histones relaxes chromatin condensation, making DNA more accessible for transcription factors.) In turn, chromatin condenses and transcription is significantly repressed. 

### III. Case Study: DNA Methylation + Cancer
To underscore the importance of DNA methylation on a broader scale, we mention its application with respect to cancer.<sup>11</sup> Specifically, DNA hypermethylation of CpG islands near tumor suppressor genes has been observed in cancerous cells. At the same time, oncogenes are often found with abnormally low DNA methylation levels, leading to their overexpression. As these improper methylation patterns proliferate through cell division, a tumor can form.

An upside for this correlation, however, is that observing this pattern in tumor cells has opened the door for epigenetic treatment. There are currently drugs available that specifically target demethylation of tumor suppressor gene hypermethylation, and more are in development.

<img src="https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/Methylation_Cancer.png" width=450px/>
<i><b>Figure 2</b> Example of hyper/hypomethylation in a tumor cell.</i>

## Biology: Histone Modifications
### Introduction
Histones are proteins found in eukaryotic cell nuclei that order DNA into nucleosomes. These components of chromatin are subject to post-translational modifications including methylation, acetylation, phosphorylation, and others still being researched. The histone code hypothesis suggests that these modifications, along with epigenetic markers, influence the recruitment of proteins responsible for regulating gene expression. Multiple modifications work together simultaneously to regulate and change chromatin state and gene expression.<sup>10</sup> Let's explore some of these modifications. 

<img src="https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/Histone_Background.png" width=450px/>
<i><b>Figure 3</b> General structure of a DNA-histone complex. The two most common modifications (acetylation) and (methylation) are shown.</i>

### I. Histone Acetylation/Deacetylation
Acetylation connects a negative charge acetyl group to lysine residues of the N-terminal histone tails (specifically H3 and H4) by histone acetyltransferase (HAT).<sup>10</sup> By doing so, negatively charged DNA is repelled, causing the chromatin to relax into euchromatin, allowing for transcription factors to bind and increase gene expression. Opposingly, deacetylation by histone deacetylase (HDAC) condenses chromatin into heterochromatin, therefore deactivating gene activity.<sup>7</sup>

<br />

<img src="https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/Histone_Acetylation.png" width=450px/>
<i><b>Figure 4</b> Acetylation of histones, leading to relaxation of DNA into euchromatin. Note the larger regions of exposed DNA open for transcription after acetylation.</i>

### II. Histone Methylation/Demethylation
Unlike histone acetylation, methylation is a post-translational epigenetic modification that does not directly change histone charge or histone-DNA interactions. Instead, a methyl group is added to lysine or arginine residues of histone tails, each impacting transcription differently. More specifically, arginine methylation activates transcription and transcriptional activities while lysine methylation effects depend on the methylation site and length.<sup>10</sup> 

Methylation at different sites result in either activation or deactivation. Some common methylation sites are<sup>7</sup>: 

1. H3K4, K36, and K79 which result in transcriptional activation
2. H3K9, K27, and H4K20 while silence gene activity/expression

<img src="https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/Histone_Methylation.png" width=450px/>
<i><b>Figure 5</b> Histone methylations at various locations. Notice both activation and repression is possible depending on methylation type.</i>

### III. Histone Phosphorylation
Unique from both histone methylation and acetylation, histone phosphorylation employs interactions between other histone modifications and binding proteins. Chromatin remodeling happens when a phosphoryl group attaches to the histone tail. This can occur on all histone core proteins, each having distinct effects. This process plays a primary role in cell division, transcriptional regulation, and DNA damage repair.<sup>10</sup>

<img src="https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/Histone_Phosphorylation.png" width=450px/>
<i><b>Figure 6</b> One example of histone phosphorylation. Various possible signals caused by this particular phosphorylation are described.</i>

## Analysis Techniques: DNA Methylation
### Background
The goal of DNA Methylation analysis is fairly obvious: we wish to detect what parts of the genome are methylated to identify, confirm, or analyze downregulated regions.

Let's take an example: We have two bacterial samples that should both be expressing a gene that turns them blue. However, one culture appears blue while the other appears white. Given what we've learned, we may hypothesize that, for some reason, the white colony of bacteria has methylated the region containing the gene, thus downregulating it. How can we test this hypothesis?

Indeed, genetic sequencing shows the DNA sequence of both bacteria to be identical, yet the white colony shows little to no transcription of this gene. What we've just mentioned sets the context for DNA methylation analysis: **genetic sequencing is unable to distinguish methylated and non-methylated cytosine**.<sup>5</sup> Therefore, we require other analysis techniques, one that allows us to differentiate between these two:

### I. Bisulfite Sequencing
#### Overview
Bisulfite sequencing is the most widely-used and popular DNA Methylation analysis technique.<sup>1</sup> The core idea is to convert non-methylated cytosine into uracil, but keep methylated cytosine unchanged. Then, run a sequencing analysis. The converted cytosine (now uracil) will be detected during sequencing as thymine, so every detected cytosine will be a methylated cytosine, giving a clear indication of which regions are methylated.<sup>1</sup>

![Bisulfite Conversion](https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/Bisulfite_Conversion.png)  
<i><b>Figure 7</b> The conversion of non-methylated cytosines into uracils, which are read as thymines by sequencing technology. Notice that methylated cytosines are unchanged and remain sequenced as cytosines.</i>

#### Lab Technique
The first milestone in a bisulfite sequencing analysis is the treatment of DNA with [bisulfite](https://en.wikipedia.org/wiki/Bisulfite). There are three major steps<sup>1</sup> in this protocol:

1. Denaturation of DNA into single strands
2. Incubation with bisulfite solution at high temperature
3. Cleaning of DNA; removal of bisulfite and residues

The product of this will be DNA with non-methylated cytosine converted into uracil. Although [whole-genome bisulfite sequencing](https://en.wikipedia.org/wiki/Whole_genome_bisulfite_sequencing) (WGBS) is becoming increasingly viable, it is not yet a common method. Thus, we will only describe the lab technique for region-specific analysis. However, we will mention one WGBS analysis method [below](#Bonus---Whole-Genome-Bisulfite-Sequencing-Analysis).

Having used bisulfite to convert all non-methylated cytosine to uracil, the next step is to use a [Polymerase Chain Reaction](https://en.wikipedia.org/wiki/Polymerase_chain_reaction) (PCR) to amplify the region of interest. Traditionally, primers must be selected carefully (such as selecting for low cytosine or non-CpG island rich areas) so potentially converted cytosine do not inhibit PCR amplification. Additionally, in parallel, a PCR for the same region is run on DNA that has *not* been treated with bisulfite.

Both PCR products (bisulfite-treated and native DNA) are cleaned and sequenced using any modern sequencing technique. This yields two digital sequence files:
1. A bisulfite-treated sequence where each cytosine is a methylated cytosine.
2. A native DNA sequence that is true to the original sequence. 

We now move to computational analyses conducted on these data files.

#### Computational Analysis
The simplest analysis possible with these two files is aligning the two sequences, and identifying where there is a C-T mismatch. For example, take the two sequences below:
```
Bisulfite:  GTATCTAT
Native:     GCATCTAC
```

We see the bisulfite sequence identifies the cytosines at positions 2 and 9 as thymines, but the cytosine at position 5 remains a cytosine. We would conclude that the cytosines at positions 2 and 9 were not methylated, while the cytosine at position 2 was.

A related but more interesting analysis than a base-by-base comparison is one that answers, "What areas of this region of interest are methylation-rich?" Tools such as [MethylCoder](https://github.com/brentp/methylcode)<sup>8</sup> provide the answer by aggregating the results of the base-by-base comparison, determining locales with high aggregate values, and reporting the raw and aggregated results.

#### Bonus - Whole Genome Bisulfite Sequencing Analysis
The quintessential question asked of WGBS is, "What regions of the whole genome are methylation-rich?"<sup>5</sup> Here, the data required for analysis are slightly different than before:

1. Bisulfite sequencing data (FASTQ)
2. Reference genome of interest (FASTA)

Recently developed [EPIC TABSAT](https://tabsat.ait.ac.at/)<sup>4</sup> is one excellent tool for such an analysis. Given these inputs, the following general analysis steps are performed:

1. Quality assessment of raw data
2. Read alignment to reference genome
3. Methylation site analysis and grouping

The tool will then output information about methylation-rich sites, relative methylation level, and more (shown below).

<img src="https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/WGBS.jpg"/>
<i><b>Figure 8</b> Summary of various data outputs by EPIC TABSAT (click above for clearer image). Note in particular 1) the lollipop plot that shows % methylation arranged according to samples' accurate chromosomal coordinates and 2) the patternmap showing methylation significance by sample.</i>

### II. HELP Assay
#### Overview
The HpaII tiny fragment Enrichment by Ligation-mediated PCR (HELP) Assay leverages restriction enzyme digestion analysis to determine DNA methylation patterns.<sup>5</sup>

Two restriction enzymes are used:
1. HpaII, which cuts DNA at `CCGA` sites where the inner cytosine is *not* methylated
2. MspI, which cuts DNA at `CCGA` sites regardless of cytosine methylation

This results in MspI cutting DNA into some number of additional fragments compared to HpaII, and calculating the magnitude of this difference provides a relative measurement of DNA methylation.

<img src="https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/HELP_Overview.png" width=450px/>
<i><b>Figure 9</b> Overview of two (similar) variations of the HELP assay. Our focus is on the left protocol</i>

#### Lab Technique
Two DNA samples are isolated and, in parallel, subject to either HpaII or MspI digestion.<sup>6</sup> We assume the HpaII sample has been digested at only `CCGA` sites where the inner cytosine is *not* methylated, resulting in some number of fragments. Additionally, we assume the MspI sample has been digested at all of the sites that HpaII was, but additionally at `CCGA` sites where the inner cytosine *is* methylated.

Each sample is then subjected to ligation-mediated PCR (LM-PCR).<sup>6</sup> This protocol first adds linker sequences to every fragment. These sequences are complementary to fluorescently labeled PCR primers, so each fragment is amplified without the worry of complementarity/primer specificity. This yields a fluorescently detectable pool of DNA that has a quantity relative to the initial number of fragments. Importantly, the HpaII and MspI PCR reactions use different fluorescent labels.

<img src="https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/Label_PCR.jpg" width=450px/>
<i><b>Figure 10</b> Simplified idea of LM-PCR. Note the linker binding, the primer complementarity, and fluorescent label.</i>

Next, a microarray is set up such that it contains binding sites for expected `CCGA` site cuts (determined using reference sequence analysis).<sup>6</sup> Equal amounts of each PCR product is added evenly across the microarray, creating a mosaic of MspI and HpaII bound sequences. The microarray is then scanned twice, once for each type of fluorescent label used. The difference in fluorescence between the two is representative of the methylation level.

#### Computational Analysis
One of the key benefits of this technique is that it's fairly light on dry-lab analysis. Though results are generally more qualitative and inexact, it is a far simpler and easier protocol than bisulfite sequencing.

However, there have been attempts to increase the quantitative power of the assay. A data analysis pipeline in R was developed to take signal intensity data of the microarrays and run various normalizations and to quantify the differences. This pipeline, however, is *not* packaged as a tool, but contains a series of computational steps in R that are beyond the scope of this introductory epigenomics lesson. The detailed paper, however, is linked [here](https://academic.oup.com/bioinformatics/article/24/9/1161/207143) for reference.

### Review of DNA Methylation Analysis Techniques
As mentioned before, bisulfite sequencing generally provides more quantifiably solid results than the HELP assay, but also requires greater wetlab and computational power.<sup>5</sup> Indeed, the computational tools for bisulfite sequencing are plentiful, and will generate robust analyses. However, the HELP assay provides a great low-effort alternative for determining DNA methylation levels in a generic context.

From a broader perspective, a recurring limitation of DNA methylation analysis is that any given result is only a snapshot of a single cell at a given point in time. This means repeating an experiment on the same organism may yield vastly different results given that a different cell in a different point in time is used. 

A better method would be one that uses continual measurement of methylation instead of endpoint analysis; this way, we may get a better glimpse into the dynamic mechanisms of true genomic methylation. Such tools and techniques are being developed and implemented today.

## Analysis Techniques: Histone Modifications
### Background
The goal of histone modification analysis is simply to identify the levels of modification or locate where on the genome these modifications are being made. 

In this section we will explore two popular techniques to do so: 

1. ChIP-seq, utilized in studying site-specific modifications
2. Mass Spectrometry (MS), used to precisely compare global levels of specific modifications among different samples 

### I. ChIP-Seq
#### Overview
Chromatin Immunoprecipitation (ChIP) is a powerful tool used to analyze protein interactions with DNA. Specific antibodies are utilized to isolate a specific protein or modification factor of interest. This is used to identify the location and abundance of the protein or modification is within the genome, giving us insight into chromatin structure and gene expression.<sup>7</sup>


<img src="https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/ChIP_Seq.png" width=450px/>
<i><b>Figure 11</b> Wetlab protocol for ChIP-Seq.</i>

Let’s take an example: We have two samples of DNA, one for clear cell renal carcinoma and one for regular kidney cells.<sup>12</sup> We want to find sites where expression is higher in the clear cell renal carcinoma sample in order to potential histone modification sites. For this example, we will be using H3K27ac, meaning that there is acetylation at histone 3, at location 27. Given what we’ve learned about histone acetylation and ChIP-seq, how do we find these modification sites?

We know that histone acetylation happens when acetyl group attaches to the histone tails of certain proteins by HAT. So by using ChIP, we can find which proteins on our DNA sequence these acetyl groups are using protein-specific antibodies. In our case, we will use anti-histone H3K27ac.

#### Lab Technique
Here is the basic protocol<sup>7</sup> for both samples:

1. Crosslink cells with formaldehyde 
2. Isolate and shear DNA into chromatin fragments 
3. Immunoprecipitate with protein-specific antibody 
4. Reverse-crosslinks and purify DNA for sequencing 

Next, we prepare the sequence libraries by attaching sequence adaptors to both ends of each fragment. We must then perform PCR to amplify the library and check its concentration. The next step is sequencing. Many sequencing techniques can be used in this step. 

We now move to computational analyses conducted on these data files.

#### Computational Analysis
Before jumping into the fun stuff we must also:

1. Clean the raw reads by removing adaptors and PCR duplicates
2. Computationally align fragments to the reference genome 

Next, we use peak-calling which utilizes different algorithms to identify regions where there are more reads than background. Popular software include: MACS, PeakSeq, SICER, CCAT, etc.<sup>2</sup> From here, we can visualize the data on a genome browser. 

<img src="https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/ChIP_Visualization.png" width=450px/>
<i><b>Figure 12</b> Visualization of peak-calling software output on a genome browser.</i>  

We can clearly see that the bottom two rows (clear cell renal carcinoma) have higher levels of binding than the top two rows (regular kidney cells). More specifically, this ChIP-seq shows an active ZNF395 super-enhancer only in the clear cell renal carcinoma cells. We  have found where on the genome and which specific gene is overexpressed.<sup>12</sup> 

### II. Mass Spectrometry
#### Overview
Mass Spectrometry (MS) gives us an unbiased quantitative analysis of post-translational histone modifications. Unlike ChIP-seq, MS is designed to output a large variety of histone modifications and their relative abundance within a single analysis. However, this method involves more wet-lab preparation. The bottoms-up method is the most popular method, in which intact proteins are digested into short peptides for nano-liquid chromatography and mass spectroscopy.<sup>9</sup>

Let’s take this example: We want to analyze histones from human embryonic stem cells (hESCs) with and without retinoic acid (important in cell growth, differentiation, and organogenesis). We want to figure out the relative abundance of histone modified peptides<sup>9</sup>. How can we utilize MS to figure this out?

#### Lab Technique
Because of the sophistication of the lab protocol, we will not be focusing on the biology of the lab technique.

<details>
  <summary>However, you may click here for a simplified step-by-step protocol<sup>9</sup></summary>

1. Harvest cells of interest and isolate the nuclei 
2. Perform histone purification 
3. Perform histone variant fractionation
4. Histone quantification
5. Histone derivatization using Lysine 
6. Histone digestion using Trypsin
7. Propionylation of Histone Peptides at N-termini
8. Stage-tip desalting 
  
</details>

We will now focus on the computational analyses conducted on these MS raw data files.

#### Computational Analysis
We will import these raw files into a software to perform peak area integration. Two popular softwares for this are [EpiProfile](https://github.com/zfyuan/EpiProfile2.0_Family) and [Skyline](https://skyline.ms/project/home/software/Skyline/begin.view). 

<img src="https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/Mass_Spec1.png" width=450px/>
<i><b>Figure 13</b> Visualization of peak area integration output.</i>

Using these ion chromatograms, we can find the area under the curve to estimate the abundance of each peptide. To find the relative abundance of a modification, we sum up all of the different modified forms of the peptide and divide by the total area for that peptide.  Using tools like Mascot, we can find the relative abundance of a specific peptide by dividing its area by the total area of all of the modifications.<sup>9</sup>

<img src="https://github.com/sabeelmansuri/Epigenomics/blob/master/assets/Mass_Spec2.png" width=450px/>
<i><b>Figure 12</b> Results of relative abundance analysis.</i>

In figure A, we can see the relative quantification of the histone H3 peptide KQLATKAAR (aa 18 - 26). 
In figure B, we can see the relative quantification of the histone H3 peptide KSTGGKAPR (aa 9 - 17). 
In figure C, we can see the relative abundance of detected peptides for histone H3 with and without cell treatment with retinoic acid.<sup>9</sup> 

We can see that hESCs had a reduction of acetylated peptides when stimulated for differentiation. 

This data only shows the 35 modified forms of histone H3 that were quantified.<sup>9</sup> However, MS has the power to more than 200 proteoforms, including all variants and low abundant modifications!

### Review of Histone Modification Analysis Techniques
The most popular method of analyzing histone methylation method is ChIP-seq. It is a very powerful tool to analyze protein interactions with DNA, and is perfectly applicable to find and quantify histone modifications. However, this technique has a low throughput and bias against hyper modified proteins. Alternatively, although more tedious mass spectrometry is more precise, returning the relative abundance of several histone variants on a global level in a single analysis.

The analysis of histone modifications is becoming increasingly prevalent in cancer, pathology, and developmental research as well as precision medicine. With the immergence of these new technologies and research, we can expect exciting innovative approaches to medicine and healthcare. 

## Concluding Remarks
We've scratched the surface of major epigenomic modifications and some analysis techniques used to quantify them. Yet, the opportunity for exploration and development is vast.

We hope to have, at the very least, demonstrated the importance of these epigenomic modifications, and inspired further research into their future applications.

## Citations
1. [Darst, Russell P et al. “Bisulfite sequencing of DNA.” Current protocols in molecular biology vol. Chapter 7 (2010): Unit 7.9.1-17. doi:10.1002/0471142727.mb0709s91.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3214597/#S2title)  
2. [Diaz, Aaron et al. “Normalization, bias correction, and peak calling for ChIP-seq.” Statistical applications in genetics and molecular biology vol. 11,3 Article 9. 31 Mar. 2012, doi:10.1515/1544-6115.1750](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3342857/)
3. [Gardiner-Garden M, Frommer M. "CpG islands in vertebrate genomes". Journal of Molecular Biology. 196 (2): 261–82. July 1987. doi:10.1016/0022-2836(87)90689-9.](https://www.sciencedirect.com/science/article/pii/0022283687906899?via%3Dihub)
4. [Krainer, Julie, et al. “EPIC-TABSAT: Analysis Tool for Targeted Bisulfite Sequencing Experiments and Array-Based Methylation Studies.” Nucleic Acids Research, vol. 47, no. W1, 2019, doi:10.1093/nar/gkz398.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6602470/)
5. [Kurdyukov, Sergey, and Martyn Bullock. “DNA Methylation Analysis: Choosing the Right Method.” Biology vol. 5,1 3. 6 Jan. 2016, doi:10.3390/biology5010003.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4810160/)
6. [Oda, Mayumi, and John M. Greally. “The Help Assay.” Methods in Molecular Biology DNA Methylation, 2009, pp. 77–87., doi:10.1007/978-1-59745-522-0_7.](https://link.springer.com/10.1007/978-1-59745-522-0_7)
7. [O'Geen, Henriette et al. “Using ChIP-seq technology to generate high-resolution profiles of histone modifications.” Methods in molecular biology (Clifton, N.J.) vol. 791 (2011): 265-86. doi:10.1007/978-1-61779-316-5_20](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4151291/)
8. [Pedersen, B., et al. “MethylCoder: Software Pipeline for Bisulfite-Treated Sequences.” Bioinformatics, vol. 27, no. 17, 2011, pp. 2435–2436., doi:10.1093/bioinformatics/btr394.](https://www.ncbi.nlm.nih.gov/pubmed/21724594)
9. [Sidoli, Simone et al. “Complete Workflow for Analysis of Histone Post-translational Modifications Using Bottom-up Mass Spectrometry: From Histone Extraction to Data Analysis.” Journal of visualized experiments : JoVE ,111 54112. 17 May. 2016, doi:10.3791/54112](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4927705/)
10. [Strahl, B., Allis, C. The language of covalent histone modifications. Nature 403, 41–45 (2000) doi:10.1038/47412](https://www.nature.com/articles/47412)
11. [Thompson, Reid F., et al. “An Analytical Pipeline for Genomic Representations Used for Cytosine Methylation Studies.” Bioinformatics, vol. 24, no. 9, 2008, pp. 1161–1167., doi:10.1093/bioinformatics/btn096.](https://www.ncbi.nlm.nih.gov/pubmed/18353789)
12. [Yao et al. (2017). VHL Deficiency Drives Enhancer Activation of Oncogenes in Clear Cell Renal Cell Carcinoma. Cancer Discovery. 7. CD-17. 10.1158/2159-8290.CD-17-0375.](https://www.ncbi.nlm.nih.gov/pubmed/28893800)
13. [Moore, Lisa D et al. “DNA methylation and its basic function.” Neuropsychopharmacology : official publication of the American College of Neuropsychopharmacology vol. 38,1 (2013): 23-38. doi:10.1038/npp.2012.112](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3521964/)
