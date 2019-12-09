
Brandon Lin, Jorge Gonzalez Abundis, David Tran

Group 28

10/29/19

# Overview
The advent of next generation sequencing and newer technology has greatly influenced the development of different alignment software. Original software aligners generally followed two different archetypes: programs that followed the seed-and-extend hash table based algorithm, like SOAP, MAQ and RMAP, or suffix/prefix trie and Burrow-Wheelers Transform based algorithms like BWA and Bowtie2 [here](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2943993/). Since the Bowtie was shown to be faster than traditional seed-and-extend algorithms in [this](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2690996/) study while maintaining accuracy and showing similar memory footprint, it and other Burrow-Wheelers Transform algorithms like Bowtie2 and BWA have emerged to be frontrunners in genomic alignment software. Newer advances in technology, like cloud computing and GPU Cuda integration, have also greatly decreased the speed and increased the efficiency of bioinformatics alignment software.

## BWA

 The Burrow-Wheelers Aligner(BWA) is separated into three programs: BWA-backtrack, BWA-MEM, and BWA-SW. BWA-backtrack supports reads up to 100bp, while BWA-SW, and the newer and faster BWA-MEM, can support up to reads ~1Mbp long. It uses the Burrow-Wheelers Transform algorithm to save memory while aligning reads. BWA supports both full-read alignment and chimeric alignment, and works optimally with reads with a sequencing error rate of ~2%, depending on the length of the alignment. It can work with genomes larger than 4GB, but cannot align chromosomes larger than 2GB. 
 
## Bowtie2

Bowtie2 is a tool used for aligning sequencing reads to long reference sequences. The tool usually aligns reads of about 50 to 100s characters long. Bowtie2 performs end-to-end or local read alignments. An alignment score displays how similar the read sequence is to the reference sequence. A high alignment score means there is a lot of similarity. End-to-end read alignments searches for alignments for all of the characters read, while local read alignment uses a trimmed version. It also indexes the genome with an FM index to keep a small memory footprint. For the human genome this footprint is typically around 3.2 GB.  


Sequence Aligners:
https://en.wikipedia.org/wiki/Sequence_alignment_software(under short-read sequence alignment)

## BBMap
BBMAP has a high mapping rate, high accuracy, and great speed. 

Drawback: has high memory usage

Performs affine-transform-optimized global alignment. It is slower, but more accurate than Smith-Waterman. Uses kmers to index the genome. There is no size or scaffold count limit. It has higher sensitivity and specificity that Burrows-Wheeler aligners. 

Testing against other alignment approaches:
ROC Testing Methodology
ROC curves generated files from files containing 1,000,000 reads containing a mix of mutation types
20% of the reads were perfect. Of the rest, the mutations rates varied:
85% SNP(randomly distributed)
50% Deletion
50% Insertion 
50% N(ambiguous)
30% Contiguous Substitution 
Rates are compounded 
(0.85)^2 of the reads have at least 2 SNPs, and .25 of the reads have both an insertion and a deletion.

SAM files contain a mapping quality field. The sam file is evaluated to calculate true and false positive rates 

BBMap is more accurate at all confidence levels



## GMAP - Genome Mapping and Alignment Program 

### Background 
This technique was developed in 2002, around the time when the draft human genome 
was first released. GMAP was designed to take advantage of newly available genomic 
sequence allowing users to align genes and expressed sequence tags (ESTs) rapidly to the 
Genome in order to reveal their intron-exon structure. The alignments also provide 
measurements of gene expression which are useful in identifying cancer specific genes 
and amplification of genomic regions in cancer. One of the most significant aspects of 
GMAP is that the program can handle transcripts that had up to 20-30% sequence 
deviation from the reference genome. In contrast, other programs for genomic locationation alignment, such as BLAT, generally had their alignment affected adversely by small amounts of deviation of only 1%. This relatively wide deviation allows for use of GMAP for cross species alignment. 

### Advantages of GMAP
Advantages of GMAP include: 
Map and align a single cDNA interactively against a large genome in about a second, without the startup time of several minutes typically needed by existing mapping programs.
Switch arbitrarily among different genomes without the need for a pre-loaded server dedicated to each genome. 
Run the program on computers with as little as 128 MB or RAM.
Perform high-throughput batch processing of cDNAs by using memory mapping and multithreading when appropriate memory and hardware are available. 
Generate accurate gen models, even in the presence of substantial polymorphisms and sequence errors.
Locate splice sites accurately without use of probabilistic splice site models.
Detect statistically significant microexons and incorporate them into the alignment 
Handle mapping and alignment tasks on genomes having alternative assemblies 

  Disadvantages of GMAP
Uses more memory compared to more recent programs such as Burrow-Wheelers Aligner (BWA). 
Less accurate than Bowtie2, BWA, and BBMap based on E. coli ROC Curves. 

  Computational Process 
GMAP takes a hierarchical approach that successively refines the alignment through a 
three stage process. The first stage looks at long oligomers (such as 24-mers or 30-mers) from both ends of the query sequence to identify candidate genomic regions that contain oligomers from both ends. The second stage attempts to align the read against each of the candidate regions found in Stage 1. The last stage fills in these gaps using a variety of dynamic programming algorithms at the nucleotide level 


## Cloudburst(BigBWA?)

How it works:
Cloudburst is based off the RMAP software implementation which:

Can map reads without sequence quality data

Supports paired-end reads

Supports bisulfite treated read mapping

Can map at a speed of ~8mbp/hr

Created 8/18/2009

Is a slower algorithm than state of the art burrow-wheeler transform algorithms like Bowtie2 and BWA

Is easily scalable with cloud computing to burrow-wheelers transform

Uses the Hadoop MapReduce implementation to allow cloud computing

Map phase: Extract K-mers(Seeds)

Reduce phase: Extend Seeds

Reduces the time to map reads linearly(~30X faster on 24 cores, and >~100 times faster on 96 cores)

Advantages:

Due to linear scaling, good for large datasets, or to just reduce the time needed to compute a normal dataset

Allows computation with shorter k-mers(which is more time consuming that using longer k-mers) due to parallel computing

Can be easily scaled due to the open source Hadoop MapReduce implementation

Computing costs are cheap(renting computational power is relatively cheap and faster than buying CPU’s for computational power)

