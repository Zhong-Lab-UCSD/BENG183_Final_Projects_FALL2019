**TODO: UPDATE FORMAT**

# BENG 183- Final Project Summary

## INTRO: 
Current methods such as ChIP-seq, Hi-C and bisulfite sequencing are ways to
epigenetically analyze specific modifications and their effects on the entire genome. However,
these methods require prior knowledge of the mechanisms and how they create these
modifications, limiting what potential mutations/changes can be fully investigated. One method
that overcomes this limitation is ATAC-seq which can analyze chromatin accessibility no matter
the mechanism.

## WHAT IT IS: 
ATAC-seq is an Assay for Transposase-Accessible Chromatin with high
throughput sequencing. It uses next generation sequencing to explore chromatin accessibility,
“the degree to which nuclear macromolecules can physically be in contact with chromatinized
DNA”, throughout the genome. Compared to other similar methods of analyzing chromatin,
ATAC-seq produces similar results with a lesser amount of cells and has a straightforward
protocol.

## HISTORY: 
ATACseq was created at Stanford University in Howard Chang’s and William
Greenleaf’s labs. Their goal was to develop a type of chromatin sequencing that would not need
as much time and resources as other chromatin sequencing methods. They used the Tn5
transposase because it was being used in other sequencing methods at the time and was very
successful at fragmenting and adding adapters at the same time. They thought that if they used
this method on open chromatin, they would be able to discover the chromatin accessibility.

## PROTOCOL: 
This protocol only needs around 50,000 cells and a couple hours to produce
results. There are two main steps of the protocol: Cell
Preparation and Transposition Reaction. In Cell
Preparation, cells are collected and counted. Counting the
cells is an extremely important step as the count can affect
transposition reaction and size distribution of the DNA
fragments. The cells are kept in a homogenous solution
and are treated with a nonionic detergent to extract the
nuclei. In Transposition Reaction, the open chromatin
found in the nuclei are tagged with sequencing adapters
using Tn5 transposase. After this, the DNA fragments are
amplified using PCR and then sequenced using next
generations sequencing. Some things to keep in mind are
to keep the cell counts from 25,000-75,000. Anything outside these bounds could lower the
quality of the data. Furthermore, cutting the chromatin usually results in a lesser quality of the
data. A simple protocol can be completed as follows:
1. Harvest Cells
2. Lyse cells
3. Introduce mutant Tn5 transposases, preloaded with DNA adapters for tagmentation and
fragmentation of DNA
4. Purify fragmented and tagged DNA
5. PCR amplify and purify this amplified DNA
6. Sequence and map reads to heterochromatin and euchromatin

## APPLICATIONS: 
ATAC-seq has a multitude of uses. It can be implemented for things such as
nucleosome mapping, transcription factor occupancy analysis, identifying new enhancers, and
investigating pathological conditions. It is often used as a way to screen for experiments where
researchers can focus follow-up experiments based on changes in chromatin accessibility noticed
between samples.

## ADVANTAGES/DISADVANTAGES:
The advantages of ATAC-seq are that it is an extremely
fast protocol with prep time taking around three hours and does not require many cells to run. It
also has a high signal-to-noise ratio compared to other sequencing methods of its type. Some
disadvantages of ATAC-seq are that sometimes chromatin that is bound may sometimes be
tagged and sequenced. Furthermore, only 50% of the fragments are tagged properly for the PCR
amplification step. Also, the fragments that do get tagged may not have enough space between
the adapters for PCR amplification step.
snATAC-seq: Methods like these tend to average the results from all cell types and therefore
single-cell methods are sometimes preferred for certain experiments. ATAC-seq can be modified
to include sequencing for single cells. When the chromatin is sheared and tagged with Tn5, each
fragment has a unique barcode which can be later on used to identify cell type. This enables
users to look at chromatin accessibility variations between cell types.

## FUTURE DEVELOPMENTS:
Future applications or optimizations of this protocol look to
apply ATAC-seq in a single cell analysis through microfluidics or combinatorial cellular
indexing. Also, due to its ease of use, ATAC-seq is likely to become commonly used in many
epigenomics workflows to analyze chromosome accessibility.

## References?
https://www.abcam.com/epigenetics/epigenetics-application-spotlight-atac-seq
https://www.activemotif.com/blog-atac-seq
https://www.illumina.com/science/sequencing-method-explorer/kits-and-arrays/atac-seq.html
https://www.nature.com/articles/s41576-018-0089-8
Buenrostro et al. (2015) Curr. Protoc. Mol. Biol. 109, 21.29.1-9.
