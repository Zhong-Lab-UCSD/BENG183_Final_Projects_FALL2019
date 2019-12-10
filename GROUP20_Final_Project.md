
# Precision Medicine: Cancer
### by Alexander Chen, Jeffrey Yeung, and Jack Zhang

## Cancer and its current treatment

Today, treatment and selection of therapies follow a standard protocol: **when you are diagnosed with an ailment, you receive the same treatment as others who were diagnosed with the same affliction.**

With this paradigm, when one is diagnosed with cancer, he/she is simply given the same standard treatment as others who have the same type (origin) and stage of the cancer which is typically surgery, chemotherapy, radiotherapy, or a combination of the above.
 
 However discovery over the past years have been increasingly supportive of the conclusion that individual cancers often have variable responsive to these generic treatments, as a recent publication explains:

> Although combinations of cytotoxic chemotherapy are developed following rigorous evidence-based testing, a significant number of [cancer] patients may not benefit from the combination and develop side-effects due to the non-selective nature of the treatment.

**The hope of precision medicine is to challenge that - to use the genetic changes in a patient’s tumor to make a higher depth diagnosis and more targeted treatment.**


Prognosis begins with profiling the individual’s tumor. A sample of the tumor, along with normal DNA are both sequenced and then aligned to a reference genome. By comparing the alignments, mutation specific to the individual can be identified.

![Traditional Treatment model vs Precision & Pesonalized Medicine model for cancer prognosis.](https://imgur.com/c9pwOK4)

With this knowledge on hand, many routes for personalized treatment are opened. Immunotherapy drugs could be applied, motivating the patient’s immune system to better recognize and target cancer cells; Antibodies can be designed to seek specific antigens on malignant cells. All these treatments are better equipped to target the affected cells more accurately all while bypassing healthy cells, which relieves many of the negative side effects currently present in most cancer therapies.

By applying precision therapies along with traditional surgery, chemo, and radiation therapy. Treatments can be tailored to each person’s cancer.


## Integration of precision medicine into cancer treatment

The general procedure currently for analyzing cancer cells for targeted therapy involves sequencing reads, usually paired end reads using Illumina sequencing, followed by alignment of reads to a reference genome and de novo genome assembly using all reads. This genome is then compared with genome from a normal cell to detect somatic mutations using SNP calling. Finally RNA-seq is performed on the tumor sample to measure the gene expression and differential gene expression.

### Genome Alignment:
The reads are first generated through **next gen sequencing**. Sequencing by synthesis through either Illumina or Solexa is the most common way nowadays. The obtained paired end reads are in `FASTQ` format and often goes through a quality check to ensure good reads. Finally the reads are then aligned with a reference genome using `bwa mem` function. Output files are `SAM` for humans and `BAM` for binary computers. You can also view this alignment through online alignment browsers such as **IGV**.

### Genome Assembly:
The “shotgun” genome assembly method refers to the random fragmentation of the whole genome. Fragments of reads are assembled together using their average coverage or the number of reads covering a position in the genome. The more similarity there is between the end of one read and the beginning of another, the more likely they are to be from overlapping regions in the genome. To effectively assemble large numbers of short reads from Illumina, we need to break reads into kmers using de Bruijn Graph and adjust for errors within kmers. Finally the graph is cleaned and assembled through scaffolding and gap filling.

### RNA Sequencing:
Mapping reads to genome, transcriptome, and predicted exon junctions is important in determining the sample in functional studies and especially cancer genomics. First RNA from samples of interest is isolated and fragmented. Then it is sent to sequencing using next gen sequencing. Finally the reads are aligned to the appropriate reference using **STAR** and an index file for the reference. RNA seq can determine the activity level of various genes in the sample of interest. The output for STAR is an aligned BAM file.

### Quanitfying Gene Expression:
Normally after RNA-seq of the reads, the output BAM file needs to be analyzed for the gene expressions of the sample of interest. **RSEM** is used to quantify such gene expressions and takes in the aligned BAM file and outputs a gene level expression result file. Expression levels are normalized by measuring the FPKM.

### Differential Expression Analysis:
Differential expression analysis is needed to further analyze the various levels of gene expression in the sample of interest. In order to perform differential expression analysis, we need to first use **R** and its library **tximport** to import the output file from RSEM into **DESeq2** which is then used to perform the differential expression analysis.

## Precision oncology in context: SHIVA

In 2012, France’s Institut Curie began the **SHIVA01 trial**, a comprehensive Phase II trial aimed at determining the effectiveness of targeted precision medicine cancer therapies in comparison to traditional treatment methods. The trial enrolled 741 patients at 7 locations across France in the largest trial of its kind to date. 11 targeted therapies were employed to treat these patients, with each patient enrolled having been confirmed to have a cancer type with a molecular profile targeted by one of the 11 therapies.

The progression of the trial was accompanied by a high requirement for bioinformatic tools. The four V’s of modern data are all applicable in this setting: volume, variety, velocity, and veracity. Traditionally, this high bar for bioinformatics has constricted the ability of precision medicine to be effective, but modern technologies are becoming increasingly powerful. The SHIVA trial was groundbreaking in its ability to overcome the bioinformatics hurdles presented by precision medicine.

![enter image description here](https://i.imgur.com/tSCC9sE.png)

In a system that the trial named the Knowledge and Data Integration (KDI) system, platforms such as Ion Torrent PGM, AmpliSeq, and Affymetrix Cytoscan HD were used to gather and process data. Ultimately, these data were compiled into the patient’s molecular profile.

Thermo Fischer’s Ion Torrent PGM was the technique used in the SHIVA trial for DNA sequencing. This step was of vital importance, as it was the first step in determining a patient’s specific cancer’s molecular profile. The Ion Torrent PGM is an example of a ‘benchtop’ Next Generation Sequencing (NGS) setup that grants biologists a method of sequencing DNA with ease in any lab. Despite the advantages offered by the Ion Torrent PGM, Illumina’s MiSeq machine has begun to eclipse it in recent years. 

![](https://lh3.googleusercontent.com/NNxgjQ8c219_wwu8MJaRh566Z2QW7pI5FjAjshHia5BhRnxkUUiJ6q0zXr8fH8cLhJWREdyW2ejKJSKuc0ZzarXtZXvAmRphtvKAkyBGMZx_c1vT3DpU6bvrUVUEZ7jzUdAbX6-S)

The two platforms differ in the techniques they use for sequencing. The Ion Torrent uses a technique known as ion semiconductor sequencing. In this method, the machine takes advantage of the hydrogen ions that are released during DNA synthesis to determine the sequence of bases. The sequencer will add all four dNTP molecules into solution in rotation. If a dNTP is added into solution that results in the release of a hydrogen ion, the machine then knows that the added dNTP constitutes the next base in the DNA sequence.

![](https://lh6.googleusercontent.com/5f9t-0-Kwd3ICDwy7OgpE9u-IrXBHIqY-JZY7dqWCwx8HlT0u4qwWn7ncMrDRkCLsT9ZU_xACmnShfgVNq4vqoxoeZbh9TROoM5BjXFwc_9WtPaYBz8pvtBNdRHmrmBvaNv9TPlh)  
  
The Illumina MiSeq in contrast uses an optical system that detects dyes, known as dye sequencing. Similar to Ion Torrent, different dNTPs are added to a solution in rotation, but Illumina’s dNTPs are tagged with fluorescent dyes. The machine is then able to illuminate and detect these dyes to determine if a nucleotide has been added to a growing chain.

Both of these technologies represent breakthrough inventions that have paved the way for precision medicine and biological research. In practice, the differences between these two techniques result in considerable advantages and disadvantages. As of 2019, Illumina produces machines that are capable of outputs ranging from a few gigabases up to 6 terbases. This far outpaces Ion Torrent’s range of 30 megabases to 25 gigabases per chip. Ion torrent machines are capable of producing results far faster than Illumina machines generally, with most Ion Torrent platforms capable of returning up to 200 reads in an hour. Illumina sequencing on the MiSeq takes a minimum of 4 hours, and can take up to 55 hours, depending on the number of cycles used. Overall, the produced read qualities between the two machines are very similar, which is perhaps the most important metric. There are numerous other considerations when comparing these machines, but the consensus is that Illumina platforms are far more versatile than their Ion Torrent competitors, but Ion Torrents are advantageous for usage with smaller genomes, amlicons, and small genome regions.

In the context of the SHIVA study, the Ion Torrent technique performed very well; the full length of time between tumor biopsy and the corresponding bioinformatics report was 4 weeks. Although the Illumina platform would likely theoretically have been a preferable choice for the trial, there were almost definitely other factors that led to the usage of the Ion Torrent.
  
![](https://lh5.googleusercontent.com/-iiQq0eUK7e0BjN_LLQw8a2UgyFW5KNNNfwX5SoFznLd-3kFLHEozHoXOuWk_5hcHeOH_3-67CkYTmtUZv4eF9Hlz93JX1THL3QCRMqQNbA_mCVJ3qA1AUPQunF56fu8FQfRuYpl)

Ultimately, the SHIVA study failed to show significant improvement in progression-free survival (PFS) between the targeted and untargeted therapy groups. Perhaps of more note is that fact that the shortcomings of the trial have been identified and further trials are moving to fill in the gaps. The three molecular profiles targeted in SHIVA were the PI3K/AKT/mTOR pathway, the RTK/MAPK pathway, and the hormone receptor pathway. The majority of the patients in the trial were assigned to single agent therapies that targeted a single location in a single pathway, and of those therapies, many were aging molecules that have since been replaced by newer, more potent medications. Furthermore, the treatment paths for patients were determined algorithmically, with little or no input from physicians familiar with specific cases. In applied precision medicine, no case is typical, and no algorithm can yet come close to the intuition of a train oncologist.

In conclusion, the legacy of the SHIVA trial is still a bright one. The trial laid the groundwork for precision medicine in oncology, creating a path for other similar-minded trials to follow. One of the most significant contributions of the study was the data framework and bioinformatics pipeline used to screen hundreds of patients. The KDI can now be replicated, improved on, and implemented by other studies, forever opening the door for precision medicine in the future.

## References
-  Krzyszczyk, Paulina, et al. "The growing role of precision and personalized medicine for cancer treatment." _Technology_ 6.03n04 (2018): 79-100. [[PMC]](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6352312/)

- Burney IA & Lakhtakia R Precision medicine: Where have we reached and where are we headed?  Sultan Qaboos Univ. Med. J  17, e255–e258 (2017). [[PMC]](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5642353/)
- Bioinformatics for Cancer Genomics [[link]](https://bioinformatics.ca/workshops/2018-bioinformatics-for-cancer-genomics/)
- Marine, Rachel L., et al. "Comparison of Illumina MiSeq and the Ion Torrent PGM and S5 platforms for whole-genome sequencing of picornaviruses and caliciviruses." _BioRxiv_ (2019): 705632. [[PDF]](https://www.biorxiv.org/content/10.1101/705632v1.abstract)
- Servant, Nicolas, et al. "Bioinformatics for precision medicine in oncology: principles and application to the SHIVA clinical trial." _Frontiers in genetics_ 5 (2014): 152. [[link]](https://www.frontiersin.org/articles/10.3389/fgene.2014.00152/full)
- Salipante, Stephen J., et al. "Performance comparison of Illumina and ion torrent next-generation sequencing platforms for 16S rRNA-based bacterial community profiling." _Appl. Environ. Microbiol._ 80.24 (2014): 7583-7591. [[PDF]](https://aem.asm.org/content/aem/80/24/7583.full.pdf)
- Lahens, Nicholas F., et al. "A comparison of Illumina and Ion Torrent sequencing platforms in the context of differential gene expression." _BMC genomics_ 18.1 (2017): 602. [[PDF]](https://bmcgenomics.biomedcentral.com/track/pdf/10.1186/s12864-017-4011-0)
- Precision medicine: lesson learned from the SHIVA trial [[PDF]](https://www.thelancet.com/pdfs/journals/lanonc/PIIS1470-2045%2815%2900397-6.pdf)
- Subbiah, Vivek, and Razelle Kurzrock. "Debunking the delusion that precision oncology is an illusion." _The oncologist_ 22.8 (2017): 881-882. [[PDF]](http://theoncologist.alphamedpress.org/content/early/2017/05/05/theoncologist.2017-0040.long)
- SHIVA Trial: France's Big Shot at Precision Medicine for Cancer [[link]](https://www.labiotech.eu/features/shiva-trial-precision-medicine-cancer/)
- Le Tourneau, Christophe, Maud Kamal, and Ivan Bièche. "The SHIVA01 trial: what have we learned?." (2017): 831-834. [[PDF]](https://www.futuremedicine.com/doi/pdf/10.2217/pgs-2017-0062)

