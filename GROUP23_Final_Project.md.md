# Protein Structure Prediction
By Yuishean Chen, Joseph Mattingly, and Ishan Ranjan

#### Table of Contents
* [Introduction](#introduction)
    + [Why Predict Protein Structure?](#why-predict-protein-structure-)
  * [Review of Protein Structure](#review-of-protein-structure)
    + [Primary Structure](#primary-structure)
    + [Secondary Structure](#secondary-structure)
    + [Tertiary Structure](#tertiary-structure)
    + [Quaternary Structure](#quaternary-structure)
  * [Sequence Determines Structure](#sequence-determines-structure)
    + [The Anfinsen Dogma](#the-anfinsen-dogma)
    + [Levinthal's Paradox](#levinthal-s-paradox)
  * [Homology models](#homology-models)
  * [Fold Recognition](#fold-recognition)
    + [Background & Essential Principles](#background-and-essential-principles)
    + [Threading](#threading)
      - [Overview](#overview)
      - [General Pipeline](#general-pipeline)
      - [Limitations](#limitations)
  * [Ab Initio Prediction](#ab-initio-prediction)
    + [Background and Essential Principles](#background-and-essential-principles)
    + [Energy Functions](#energy-functions)
      - [Physics-based energy functions](#physics-based-energy-functions)
      - [Knowledge-based energy functions](#knowledge-based-energy-functions)
      - [Energy Landscapes](#energy-landscapes)
    + [Conformational Search](#conformational-search)
      - [Molecular Dynamics](#molecular-dynamics)
      - [Monte Carlo](#monte-carlo)
    + [Model Selection](#model-selection)
    + [Conclusions on Ab Initio](#conclusions-on-ab-initio)
  * [Sources](#sources)

## Introduction
In the world of today’s biological and medicinal advances, the influence of proteins is almost omnipresent. As you may remember from introductory level biology classes, proteins, in their most basic form, are polymer amino acid sequences, or polypeptides, whose structure is dependent on the folding of the polypeptide chain and other factors such as disulfide bonding. This section of the textbook is designed to give an overview of protein structure and the importance of predicting it, examine the tertiary level of structure in more detail, explore its effects on function, and review some of the main methods for predicting protein structure by using software.

### Why Predict Protein Structure?
Prediction of a protein’s 3D structure is highly relevant in the fields of medicine and biotechnology as knowledge of structure can help in fields such as drug and enzyme design, respectively. The field of **Structural Genomics** seeks to describe this 3-D structure of proteins given a genome, leading to the potential for personalized and precision medicine and therapies, furthering the two aforementioned fields of drug and enzyme design.

## Review of Protein Structure

### Primary Structure
The **primary structure** of a protein is simply the sequence of amino acids that make up a polypeptide chain. This sequence is determined by the DNA that the protein’s mRNA was described from and can vary in length and diversity of amino acids used.

### Secondary Structure
A protein’s **secondary structure** consists of local folded structures on the chain that occur due to interactions between atoms on the backbone. The ɑ helix and the β pleated sheet are two of the most common types of secondary structure, with each being held together with hydrogen bonds.

### Tertiary Structure
A protein's **tertiary structure** is the overall three-dimensional structure of the protein and is the main target of protein structure prediction. The structure forms mainly out of amino acid R-group interactions, ranging from dipole-dipole to London dispersion forces. Hydrophobic R groups also tend to cluster inside of a protein, leaving the hydrophilic groups to interact with the outside environment. Disulfide bonds, or a Sulfur-Sulfur bond between two sulfur-containing R-groups of cysteine, are important to note when considering tertiary structure.

### Quaternary Structure
**Quaternary Structure** occurs when a protein is made up of more than one polypeptide chain. One of the most prominent examples is Hemoglobin, which is made up of four subunits.


## Sequence Determines Structure

### The Anfinsen Dogma
#### *A brief history & definition*
In 1961, Christian Anfinsen showed that a protein, ribonuclease A, could be refolded after denaturation and regain its function. This discovery gave rise to the Anfinsen Dogma (also known as the thermodynamic hypothesis) which postulated that a protein’s tertiary structure is determined solely by the protein’s amino acid sequence, or primary structure. Anfinsen recognized that the native or natural conformation of a protein was the configuration with minimum free energy, maximum stability, and reasonable kinetical accessibility (Anfinsen 1973). This ideal 3D conformation must have no comparative conformations that rival it in minimum free energy, hence granting the protein maximum stability and preventing spontaneous transitions between different conformations. Kinetical accessibility refers to the ease in which a protein can achieve this conformation without expending an unrealistic amount of activation energy.


### Levinthal's Paradox
#### *A brief history & definition*
Achieving these three conditions is relatively challenging to compute. Even calculating the structure of even small proteins require vast computational resources, as such algorithms would need to account for all possible interactions amongst the protein's residues. However, despite all these possible conformations, these proteins fold very quickly in nature. This is known as **Levinthal's paradox**, stating that proteins fold rapidly despite the large degrees of freedom its unfolded form possesses. Levinthal concluded that if a protein were to sample a possible conformation every picosecond, the time it would take to find its native structure would be longer than our universe has existed.

#### *Implications for structure prediction*
Of course, this does not bode well for protein structure prediction. However, Levinthal discovered that "protein folding is sped up and guided by the rapid formation of local interactions which then determine the further folding of the peptide" (Levinthal 1969). It stands to reason that a brute force approach, like testing every possible conformation is not computationally efficient. Instead, many prediction methods today utilize Levinthal's principles and others to find the native structure more methodically.


## Homology models
**Homology modeling** seeks to determine the 3D structure of a protein from its amino acid sequence and a homologous protein of known structure. Of the many methods used to predict protein structure, homology modeling remains the most reliable (Moult 2011).

The protein of interest is called the **target protein** in which only the sequence is known. A **template protein** is a protein of known sequence and structure which has been previously determined and exists in a protein database. The target protein must have > 30% sequence identity to the template protein to be considered homologous (Pearson 2013). Once homology has been determined, the template can be used to begin the construction of the target model. Homology modeling can be summarized in these steps:

### 1. Template recognition and initial alignment
The first step in homology modeling is template recognition. **Template recognition and alignment** is the process of finding a template protein within the PDB. This can be completed using a search algorithm tool such as BLAST. BLAST uses a scoring matrix to and gives penalties for openings and extensions of gaps between residues. It also gives lower scores to unlikely residue exchanges. The template with the highest score is chosen.


### 2. Alignment correction
**Conservative replacement** is an amino acid replacement in a protein that changes a given amino acid to a different amino acid with similar biochemical properties. If two amino acids have similar biochemical properties, a replacement of one for the other within a protein sequence will have little effect on the protein's structure.

**Alignment correction** fine-tunes the alignment made by BLAST. **Multiple sequence alignment programs (MSA)** are used to identify conserved and functionally important residues are aligned (Gromiha 2019).

Manual adjustments may be made to the alignment in order to improve its quality.

### 3. Backbone modeling
**Backbone modeling** is the generation of the protein models backbone. This can be done using modeling software such as *Modeller*. The model is produced by transferring coordinates of template residues that are present in the alignment (Via 2016). Side-chains may be added for any amino acid in the target that has an alignment with the template. Conserved residues may be added for the initial guess, but their side chains will not be automatically added and will be determined later. Since the model is produced from the template alignments, the quality of these alignments greatly affects the accuracy of the model.


### 4. Loop modeling
**Loop modeling** is the process of filling in gaps that exist in the backbone. The presence of gaps in the backbone originates from the target residues that did not align with the template. Deletions or insertions that occur during the alignment stage will result in conformational changes to the backbone. These conformational changes do not happen at the secondary structural elements 𝛂-helices and 𝝱-sheets. Therefore, residues that are inserted into the gaps may only be placed in loops and strands. This is a particularly challenging step in homology modeling because loop structures are the least conserved structure in a protein, thus tough to predict. There are two main approaches to loop modeling.

#### Strategies:
1. **Knowledge-based**: This is done by using the amino acids on each endpoint of the template where gaps exist. The PDB can be searched for known loops structures that are able to fill a particular gap.

2. **Energy Based**: An energy function is used to determine the quality of the loop. The function is minimized by using **molecular dynamics** or **Monte Carlo**, which are detailed later in this chapter.
    

### 5. Side-chain modeling
**Side-chain modeling** is the process by which missing side chains are added to residues in the model. Since rotamers tend to be conserved in homologous proteins, the prediction is made by copying the torsion angles between 𝛂-carbon and 𝝱-carbon to the target. Libraries of common rotamers are searched for all favorable side-chain torsion angles from known structures. Another method is to search every possible conformation for every torsion angle and to find the lowest energy interaction with neighboring atoms.

### 6. Model optimization
Once side-chain modeling is completed, the newly inserted residues may affect the predicted backbone causing it to become unstable. **Model optimization** is the process of making changes to the predicted side-chains and backbone in order to reduce the overall energy of the structure.

#### Strategies
1. **Iterative modeling** is done by remodeling the backbone after the predicted rotamers have been added. After remodeling the side backbone is complete, the rotamers are then refitted. This process is repeated until the model of lowest energy is constructed.

2. **Molecular Dynamic Simulation** is done by placing the protein in a forcefield and allows for observations of each molecule in the structure at a specific time. The goal is to find the structure with the lowest energy possible. MD simulation is explained in more depth later in this chapter.

### 7. Model validation
Even after energy minimization, a model with the lowest free energy may still be incorrectly folded. Two factors may cause errors to arise: 1) low sequence identity between the template and model-sequence, and 2) the presence of errors in the template. Such errors can come in the form of incorrect bumps, bond angles, torsion angles, and bond lengths in the model structure. One commonly used method to address invalid torsion angles is generating a **Ramachandran plot**, or a plot of a structure’s torsional angles - phi (φ)and psi (ψ). By generating this plot, researchers can visualize which torsion angles are permitted and not possible due to steric hindrance.

In terms of error tolerance, an error that occurs far from an active site is considered acceptable. However, if an error occurs in the active site, it is possible that the alignment with the template is less than optimal, and it becomes crucial a new template with stronger similarity be identified.

![https://i.imgur.com/ynZ1P19.jpg](https://i.imgur.com/ynZ1P19.jpg)

## Fold Recognition
### Background & Essential Principles 
As we have seen with homology modeling, given a target protein sequence with an unknown structure, if we can find proteins with similar sequences and known template structures, it is possible to predict the structure of the target with confidence using homology approaches (Gitter 2017). If no obvious homologs arise (sequence identity of <30%) when searching for sequence similarity, the task of structure prediction is substantially harder. Fold recognition methods may be used to predict the structure in such cases. This collection of methods is based on the observation that proteins of very different sequences, without any recognizable sequence similarities, can have the same folds (Feenstra 2018). Fold Recognition methods allow for a more accurate prediction of the target sequence’s structure even when the template is a remote homolog of the target.

### Threading 
#### Overview
Optimal Sequence Threading, or “threading”, methods are a specific class of fold-recognition methods. The main idea of threading revolves around going through a protein sequence and evaluating each part of the sequence with the intention of finding a known template model with a similar fold. The comparison for similarity is made through the application of a scoring scheme on the sequence-fold pair in question. As each part of the protein sequence is explored from start to end, the method gained its namesake of "threading", since the method "threads" through each part of the protein looking for matches to specific folds.

#### General Pipeline
The following four steps make up the general pipeline for threading methods ("Threading (protein sequence)"): selection of a template database, the selection of a scoring function, alignment, and prediction.

##### 1. Establishment of a Template Database
The first step in the general pipeline for protein threading is the selection of a database of structural templates. Templates can be selected from many protein databases ranging from general databases such as PDB, FSSP, or SCOP to species-specific databases such as the E-Coli strain K12-centered "THE-DB" (Diamond 2018). The selection of structures is usually made after filtering and removing proteins with high sequence similarity.

##### 2. Selection/Design of a Scoring Function/Scheme
A scoring function/scheme for threading is imperative in predicting a more accurate model. The best scoring schemes have the qualities of mutation, environment fitness, and pairwise potential (potential is the chance that any of these will occur in the sequence) as well as secondary structure compatibility and gap penalties (Bienkowska 2005). 

###### Consideration of Amino Acid Conservation Rates
It is important to consider that amino acid conservation rates may strongly differ between structural environments. As the structural environment of the residues for the potential template is already known, this can be used to give a score for an alignment between the target and potential template sequence. One such program/method that uses this method is FUGUE, which scores alignments using structural environment-specific substitution matrices structure-dependent gap-penalties (Feenstra 2018).

##### 3. Alignment
The target sequence is aligned with the candidate template structures, and is then the desired part of the sequence is evaluated using the selected scoring scheme. One of the most common ways that this is done is through the use of standard dynamic programming algorithms, which take the aforementioned amino acid conservation rates into account and, creates **P**osition **S**pecific **S**coring **M**atrix (PSSM) profiles of template structures (Holder 2013, Gitter 2017). Dynamic Programming algorithms can be classified further into either 1D, 1D/2D, and 2D algorithms. 1D algorithms use basic sequence-sequence alignment algorithms and are usually the fastest. 1D/2D algorithms look for an "approximately optimal score" (Bienkowska 2005) rather than a "global optimum" and take into account both the 1D amino acid alignment scores as well as 2D pairwise scores, with one notable example being David T. Jones' GenThreader (Jones 1999). The alignments are corrected with programs such as BLAST as mentioned in the homology modeling section.

##### 4. Prediction
After the scoring and alignment steps are complete, a model can be selected from the desired database that fits the target sequence best/has the most statistically significant score (Bienkowska 2005).

#### Limitations
Alignments produced using threading methods are often of poor quality due to the difficult task of detecting and aligning queries to remotely related templates. As dynamic algorithms assume that the target is threaded over a rigid backbone, this also limits accuracy. This leads to the need for manual inspection and modification using comparative modeling approaches to generate a good structure model using threading alignments, with the process being similar to that of homology modeling.

## Ab Initio Prediction
### Background and Essential Principles 
In the worst-case scenario, no structural homologs for an unknown protein exist. In this case, one must rely on modeling *ab initio*, or Latin for "from the beginning". With no homolog structure to draw influence, computationally determining the protein's structure is substantially more difficult. As of 2017, "the accuracy of ab initio modeling is low, and the success is generally limited to small proteins (<120 residues)" (Lee 2017). Expectedly, there is a race to construct a successful ab initio modeling procedure. These algorithms differ in many ways. Still, they share three common factors: 1) an accurate energy function that can locate the most thermodynamically stable state of a protein’s native structure 2) an efficient search method of identifying the most viable low-energy state through conformational search, and finally 3) the ability to select native-like models amongst incorrect ones.

### Energy Functions 
More simply put, properly designed energy functions help distinguish potential native protein conformations from thermodynamically unstable decoys. These energy functions can be categorized into two groups: 1) physics-based energy functions and 2) knowledge-based energy functions.

#### Physics-based energy functions
A strict physics-based energy function accommodates for interactions between atoms based on quantum mechanics and Coulomb potential; however, "the computational resources required for such calculations are far beyond what is available now" (Lee 2017). Instead, a more probable method is to treat atoms like point particles, each with their own unique potential value determined by torsion angles, van der Waals, and electrostatic interactions. Many successful molecular simulation programs utilize these "force fields", such as the molecular dynamics & analysis program CHARMM.

#### Knowledge-based energy functions
Statistical models, or knowledge-based energy functions, differ from physics-based force fields as they do not attempt to model actual inter-atom forces. Instead, knowledge-based energy functions are based on statistics of known protein structures' properties in the Protein Data Bank (PDB).

#### Energy Landscapes
These energy functions are then used to construct an *energy landscape*, or a visual mapping of all possible conformations of a protein sequence and their corresponding free energy levels. It is believed that protein folding follows the *folding funnel hypothesis*, which assumes all non-native conformations rest higher in the "funnel", and naturally, a protein will "fall" towards the bottom of the funnel and achieve a conformation with an unrivaled free energy minimum.

![Image result for energy landscape protein structure](https://www.researchgate.net/profile/Yann_Fichou/publication/282863427/figure/fig1/AS:614110089715725@1523426663988/Energy-landscape-of-globular-proteins-The-protein-energy-landscape-is-represented-by.png)

### Conformational Search 
The goal of conformational search is to efficiently find a protein's native structure in its rough energy landscape. The two most popular methods to identify the global minimum energy conformation are molecular dynamics simulations and Monte Carlo simulations.

#### Molecular Dynamics
For structure prediction, atomic force fields are combined with molecular dynamics (MD) simulations. The process of an MD simulation is as follows: a) obtain a model of the molecular system via NMR or crystallography, b) forces acting on each atom is then estimated c) move each atom accordingly to these forces based on Newton's laws of motion, d) advance simulation time by 1-2 femtoseconds (1 quadrillionth of a second) and calculate the next atomic movements. This process is typically repeated millions of times, but even then, it makes little progress towards finding a protein sequence's native structure. Even "a one-microsecond simulation of a relatively small system (approximately 25,000 atoms) running on 24 processors takes several months to complete" (Durrant 2011). If a protein takes several microseconds to fold, this method would be far too inefficient.

![figure2](https://media.springernature.com/lw685/springer-static/image/art%3A10.1186%2F1741-7007-9-71/MediaObjects/12915_2011_Article_495_Fig2_HTML.jpg)

#### Monte Carlo
Monte Carlo methods are a category of computational algorithms that depend on repeated random sampling to obtain the desired results. In structure prediction, Monte Carlo search is commonly comprised of rotating critical molecular bonds in random amounts to generate a new structure that minimizes free energy. This process is repeated until a native-like structure is found. The ROSETTA software suite, built upon "one of the best-known ideas for *ab initio*" (Lee 2017), relies on a more efficient variation of Monte Carlo search. The program performs profile-profile alignments on the target sequence and clusters short PDB fragments based on sequence similarity. These similar fragments then undergo Monte Carlo assembly, essentially constructing an initial assembly of fragments and replacing each fragment with another from the same cluster (fragments grouped by structural similarity) until several conformations are generated that are located at a minimum in the energy landscape.

### Model Selection 

During conformational search, many "decoys" or non-native structures are generated alongside the most native-like structures. There are several methods to select the correct conformations: 1) physics-based energy functions, 2) knowledge-based energy functions, and 3) clustering of decoy structures. As we have previously discussed the former two, let's focus on the latter.

In 2004, Zhang and Skolnick created an iterative structure clustering method called SPICKER. After clustering postulated protein structures by similarity, the structures in each cluster were used to generate an averaged centroid structure. They found that the centroid structures of "the most populated clusters tend to be closer to the native conformation than the lowest energy structures" (Zhang 2004). This contradicts the general assumption: the structure with the minimum free energy is the most native-like conformation. However, Zhang and Skolnick concluded that "the highest density cluster is in the top 14.9% of all decoy structures, while the lowest energy state is in top 43.1% of decoys".

### Conclusions on Ab Initio
Though often limited by the available computational resources, ab initio still remains key to predicting the structure of proteins with little sequence identity to other proteins in the PDB. In addition, it can also help predict a novel protein's distant homologous structures that may be low in sequence identity but high in structural similarity. So despite its drawbacks, ab initio modeling remains critical in the field of structure prediction.
## Sources
Abeln, Sanne, et al. “Protein Three-Dimensional Structure Prediction.” Encyclopedia of Bioinformatics and Computational Biology, 2019, pp. 497–511., doi:10.1016/b978-0-12-809633-8.20505-0.

Al-Karadaghi, Salam. “Introduction to Protein Homology / Comparative Modeling, Modeling Servers.” Protein Structures, https://proteinstructures.com/Modeling/Modeling/homology-modeling.html

Anfinsen, B. “Principles That Govern the Folding of Protein Chains.”  _Science_, 						American Association for the Advancement of Science, 20 July 1973,  	[https://science.sciencemag.org/content/181/4096/223](https://science.sciencemag.org/content/181/4096/223).

Bienkowska, Jadwiga, and Rick Lathrop. “Threading Algorithms.” Encyclopedia of Genetics, Genomics, Proteomics and Bioinformatics, by Lynn B. Jorde, Wiley, 2005. Diamond, Justin S, and Yang Zhang. “THE-DB: a threading model database for comparative protein structure analysis of the E. coli K12 and human proteomes.” Database : the journal of biological databases and curation vol. 2018 bay090. 1 Jan. 2018, doi:10.1093/database/bay090

Feenstra, K. Anton & Abeln, Sanne. (2018). Preface to Introduction to Structural Bioinformatics.

Gitter, Anthony. “Protein Threading.” 2017.

Gromiha, M. Michael, et al. “Protein Structural Bioinformatics: An Overview.” Encyclopedia of Bioinformatics and Computational Biology, 2019, pp. 445–459., doi:10.1016/b978-0-12-809633-8.20278-1.

Holder, Allen et al. “Dynamic programming used to align protein structures with a spectrum is robust.” Biology vol. 2,4 1296-310. 20 Nov. 2013, doi:10.3390/biology2041296

Jones, David T. “GenTHREADER: an Efficient and Reliable Protein Fold Recognition Method for Genomic Sequences.” Journal of Molecular Biology, vol. 287, no. 4, 1999, pp.797–815., doi:10.1006/jmbi.1999.2583.

Krieger, Elmar, et al. “Homology Modeling.” Structural Bioinformatics Methods of Biochemical Analysis, 2005, pp. 509–523., doi:10.1002/0471721204.ch25.

Krissinel, E. “On the Relationship between Sequence and Structure Similarities in Proteomics.” Bioinformatics, vol. 23, no. 6, 2007, pp. 717–723., doi:10.1093/bioinformatics/btm006.

Levinthal, Cyrus (1969).  [“How to Fold Graciously”](https://web.archive.org/web/20101007174851/http://www-miller.ch.cam.ac.uk/levinthal/levinthal.html).  _Mossbauer Spectroscopy in Biological Systems: Proceedings of a meeting held at Allerton House, Monticello, Illinois_: 22–24. Archived from the original on 2010-10-07.

Lee et al., 2009 J. Lee, S. Wu, Y. Zhang Ab initio protein structure prediction D.J. Rigden (Ed.), From Protein Structure to Function with Bioinformatics, Springer (2009), pp. 3-25

Moult, John, et al. “Critical Assessment of Methods of Protein Structure Prediction (CASP) - Round x.” Proteins: Structure, Function, and Bioinformatics, vol. 82, 2013, pp. 1–6., doi:10.1002/prot.24452.

Pearson, William R. “An Introduction to Sequence Similarity (‘Homology’) Searching.” Current Protocols in Bioinformatics, vol. 42, no. 1, 2013, doi:10.1002/0471250953.bi0301s42.

“Orders of Protein Structure.” Khan Academy, Khan Academy, [www.khanacademy.org/science/biology/macromolecules/proteins-and-amino-acids/a/orders-of-protein-structure](http://www.khanacademy.org/science/biology/macromolecules/proteins-and-amino-acids/a/orders-of-protein-structure).**

“Predict the Structure of Protein-Homology Modeling.” Virtual Amrita Laboratories Universalizing Education, Virtual Labs Ministry of Human Resource Developement , https://vlab.amrita.edu/?sub=3&brch=277&sim=1492&cnt=1.

“Threading (Protein Sequence).” Wikipedia, Wikimedia Foundation, 28 Nov. 2018, en.wikipedia.org/wiki/Threading_(protein_sequence).

Via, Allegra. “Homology Modelling.” Http://Aidanbudd.github.io/Ppisnd/TrainingMaterial/AllegraVia/PPI/tutorial_on_homology_modelling.Html, Universitas Budapestinensis De Rolando Eotvos Nominata, 4 June 2016, [http://aidanbudd.github.io/ppisnd/trainingMaterial/allegraVia/PPI/tutorial_on_homology_modelling.html](http://aidanbudd.github.io/ppisnd/trainingMaterial/allegraVia/PPI/tutorial_on_homology_modelling.html).


