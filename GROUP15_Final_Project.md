<p align="center"> <img width="382" alt="Screen Shot 2019-12-09 at 9 29 26 PM" src="https://user-images.githubusercontent.com/50211392/70498376-07d05b00-1acb-11ea-8624-ef15ff7f5612.png">
</p>

### History of Vaccinology  
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
       One of the biggest advances ever made in medical history was the discovery and creation of vaccines. Although throughout history many countries have practiced immunization, in 1796 Edward Jenner was credited with the founding of vaccinology after he inoculated a 13-year-old boy with cowpox and then later demonstrated that he was immune to smallpox, an extremely deadly disease. Several centuries later, the World Health Organization went on to declare in 1980 that smallpox had been eradicated globally. Then in 1885, Louis Pasteur produced the first successful rabies vaccine. As bacteriology became increasingly popular, more vaccines were developed against anthrax, cholera, plague, tuberculosis, tetanus and more. During the 20th century, scientists have actively researched and developed vaccines for some of the most commonly known infectious diseases of our time, such as polio, measles, mumps, rubella, and varicella (chickenpox). To do this day, scientists continue to research how to develop vaccines for common infectious diseases such as influenza.    

### Infection and Immunology
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
    To first understand the process of vaccine development, the methods through which viruses infect our bodies and the process of achieving immunity through vaccines must first be understood. A virus is a pathogen that infects a host cell and can only replicate within the living cells of that host. Typically, the general life cycle of a virus consists of the following steps which are summarized in **Figure 1** below:   
    &nbsp;&nbsp;&nbsp;&nbsp;**1.** Attach to target host cell   
    &nbsp;&nbsp;&nbsp;&nbsp;**2.** Penetrate host cell   
    &nbsp;&nbsp;&nbsp;&nbsp;**3.** Use host cell machinery to make viral proteins then make copies of viral genome*   
    &nbsp;&nbsp;&nbsp;&nbsp;**4.** Assemble new virions   
    &nbsp;&nbsp;&nbsp;&nbsp;**5.** Escape from the host cell to infect new cells
    <p> * <i> Note, there are different kinds of viral genomes such as ssRNA, dsRNA, ssDNA, and dsDNA. </i></p>  
<p align="center"> <img width="578" alt="Screen Shot 2019-12-08 at 4 57 39 PM" src="https://user-images.githubusercontent.com/50211392/70399846-34f21000-19dc-11ea-9b18-eb9d557a6361.png"> </p>  

**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
       The infectious virus has ***antigens*** (toxin or other foreign substances) on its surface which triggers an immune response. The body will naturally respond to such a viral attack by releasing antibodies that are produced by specialized white blood cells called B lymphocytes. These antibodies are y-shaped proteins that bind to the ***epitope*** which is the part of the antigen where an antibody will attach itself. These major components are labeled in **Figure 2** below.  
       <p align ="center"> <img width="385" alt="Screen Shot 2019-12-08 at 4 57 51 PM" src="https://user-images.githubusercontent.com/50211392/70399855-3faca500-19dc-11ea-86d2-7ca49cf101d4.png"> </p>
       
### Types of Vaccines
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
    The key to developing vaccines is to inject the antigen into the body without causing illness but trigger an immune response so that the immune system can learn how to fight that pathogen should it attack in the future. Scientists have created several ways of doing this, therefore there are different types of vaccines.   

**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
    A ***Live Attenuated Vaccine*** is an attenuated form of the pathogen which is introduced into the body. Because it is attenuated, it will not replicate and cause illness, but it will teach the immune system to recognize its antigens and be fully prepared to fight the pathogen in the future. Examples of live attenuated vaccines are the vaccines for Chickenpox, Measles, Mumps, and Rubella.
    
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
    An ***Inactivated Vaccine*** contains dead versions of the pathogens (killed by heat or chemicals) that cause disease. These are introduced into the body, and the immune system can learn from the antigens on the pathogen to know how to fight it in the future. Examples of inactivated vaccines are the vaccines for Polio and Rabies. 
    
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
    A ***Subunit/Conjugate Vaccine*** contains a specific piece of the pathogen such as a protein, carbohydrate or capsid. These vaccines produce a very strong immune response that will target that specific part of the pathogen effectively training the immune system without provoking illness. Examples of subunit/conjugate vaccines are the vaccines for HPV, Hepatitis B, and Meningococcal.   

**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
    A ***Toxoid Vaccine*** contains inactivated toxins that are secreted by a specific pathogen. These toxins are deactivated using formaldehyde and water. Once these inactivated toxins are injected into the body, the immune system will learn how to fight it off if it ever encounters that living toxin. Examples of toxoid vaccines are the vaccines for Diphtheria and Tetanus.   

### Identifying the Best T-Cell Epitopes 
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
    Currently, bioinformatics approaches to vaccine development focus on creating epitope-based vaccines (subunit/conjugate vaccines).  As such, the main focus of these techniques is identifying the epitopes of the virus that are best able to elicit the appropriate immune response. When a virus attacks the body, it can elicit the response of both the CD8 + (cytotoxic/killer T-cells) and CD4+ (helper T-cells). The body may recognize the virus as foreign, engulf it, and present fragments of it on the surface of a specialized cell on MHC II (Major Histocompatibility Complex) proteins that will attract the help of CD4+ cells. Alternatively, if the virus manages to enter a healthy cell and begins to produce viral proteins, the cells may present those viral proteins on the surface of the cell on MHC I proteins to attract the help of CD8+ cells. An illustration of this process is seen in **Figure 3** below.   
<p align = "center"> <img width="505" alt="Screen Shot 2019-12-09 at 10 55 50 AM" src="https://user-images.githubusercontent.com/50211392/70463844-8b119280-1a72-11ea-9da8-a1c1163e7c49.png"> </p>

**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
    The effectiveness of this response depends on several factors such as how well the viral peptides will be recognized by T-cells, how well they bind to different MHC’s and how likely these peptides are to be found in the virus among others. Therefore, when looking to develop vaccines that are composed of viral peptide fragments, it is crucial to look for which peptide sequences are highly conserved, which are good T-cell epitope candidates, and which have the ability to bind to a larger number of MHC’s[[1]](https://www.sciencedirect.com/science/article/pii/S1532046414002330?via%3Dihub).            
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
    Identifying which peptide sequences are highly conserved in a virus is a simple matter that can be done by analyzing the viral genome. Proteomics and transcriptomics can be used to assess the host of proteins that a virus can make. Thus, a great proportion of bioinformatics approaches to vaccine development revolves around identifying good candidates for T-cell epitopes that also have high MHC binding affinity, which is considered to be the most selective step in the process[[6]](https://www.ncbi.nlm.nih.gov/pubmed/28978689). Currently, there exist multiple bioinformatics tools that can determine which epitopes are best able to bind with MHC’s. These tools rely on the knowledge of the interactions between certain peptides and the side chains of MHC’s. Furthermore, these tools are able to take advantage of the fact that T-cell epitopes are usually linear and thus the tertiary and quaternary structure of the protein does not need to be taken into account. Some of these open server tools are shown in **Figure 5**.    

### Identifying the Best B-Cell Epitopes 
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
	B-cells are activated somewhat differently than T-cells. When a viral antigen binds to the surface protein of a B-cell, the B-cell is able to divide and proliferate, where all new cells made will be able to release antibodies that are specific to that viral antigen. The selective step, in this case, is detecting the viral antigens that are most likely to bind to B-cell surface cell receptors.  
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
	When discovering the epitopes of B-cells, a prediction based on linear strains of proteins no longer suffices. While generally successful for linear epitopes such as those reactive to MHC class proteins, the majority of B-cell epitopes are conformational epitopes, often grouped together with multiple proteins of varying natures and acting as a fully functional biological molecule in its own right.  
  
<p align="center"> <img width="554" alt="Screen Shot 2019-12-09 at 11 50 36 AM" src="https://user-images.githubusercontent.com/50211392/70467905-efd0eb00-1a7a-11ea-9975-c85542607d7a.png"> </p>
    
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
    As such, traditional protein sequencing methods used for linear protein structures fail. A successful, albeit pricey and slow method, is X-ray crystallography. However, this method is known to be expensive and inefficient. As such, new methods of computationally sequencing epitopes based on their 3D structure have been developed. An example of a prediction server built to handle such cases is **DiscoTope**, which functions as such[[3]](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1002829):  
       &nbsp;&nbsp;&nbsp;&nbsp;**1.** View the 3D structure of the epitope    
       &nbsp;&nbsp;&nbsp;&nbsp;**2.** Pass it along in a protein data bank file format (PDB, https://www.rcsb.org/)    
       &nbsp;&nbsp;&nbsp;&nbsp;**3.** Assign a log-odds ratio score (based on composition similarity to other epitopes in the        database) to each assumed amino acid (Gibbs sampling approach)    
       &nbsp;&nbsp;&nbsp;&nbsp;**4.** Build a score for each potential epitope by summing up the scores of nearby potentiates,                                          weighted by a function concurrently decreasing based off distance (spatial                                                    neighborhood)   
       &nbsp;&nbsp;&nbsp;&nbsp;**5.** Surface accessibility to portions of the protein are measured off of one or more surface                                          measures (ex. Half-sphere exposure) and scored   
       &nbsp;&nbsp;&nbsp;&nbsp;**6.** Combine all 3 scores to generate a final score for the epitope candidate to be reviewed                                           later    

**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
	As the current field of bioinformatics stands, 3D protein complexes are significantly more difficult to predict and sequence, with even some of the best tools only capable of reaching success rates in the high 60%s[[5]](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5348633/). However, as was shown with google’s DeepMind AlphaFold, many of these problems, when approached with machine learning and general engineering methods, have become significantly more manageable.

### Analyzing Various Bioinformatics Tools for Epitope Discovery
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
       As previously mentioned, there are several bioinformatics tools that exist for discovering the epitopes that would serve as the most ideal candidates for subunit/conjugate vaccines. These tools are usually designed for either assessing linear protein sequences or 3D protein sequences. Tools assessing linear protein sequences are often simpler and more reliable and are estimated to have reached an accuracy between 90-95%[[1]](https://www.sciencedirect.com/science/article/pii/S1532046414002330?via%3Dihub). These tools can be used for the binding predictions of MHCI’s. Some of these tools are shown in **Figure 5** below [[2]](https://www.hindawi.com/journals/bmri/2010/705821/). Some tools exist for assessing linear B-Cell epitopes such as **PREDITOP**, **PEOPLE**, and **BepiPred** (the default). However, since nearly 90% of B-cell epitopes are conformational epitopes and require 3D discovery techniques, these are limited in use so we will not discuss them[[4]](https://www.hindawi.com/journals/jir/2017/2680160/)[[5]](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5348633/). Therefore different tools are needed for non-linear B-cell epitopes. These are shown in **Figure 6**[[4]](https://www.hindawi.com/journals/jir/2017/2680160/).  
    
<p align="center"> <img width ="580" src="https://user-images.githubusercontent.com/50211392/70484153-d1c9b180-1a9f-11ea-8ab8-6aee1bc69feb.png"> </p>

**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
       Of the above tools, **NetMHC** performed best followed by **NetMHCPan**. Most of these tools can be found on the **IEDB** server. **IEDB** automatically recommends a mix of artificial neural networks, scoring matrices, and combinatorial libraries or when these are not able to be used, it recommends **NetMHC**[[4]](https://www.hindawi.com/journals/jir/2017/2680160/). Currently, in reverse vaccine development, a common workflow includes using **NetCTL** (a tool that looks at MHCI binding among other things such as proteasomal cleavage which is beyond the scope of this text) for T-cell epitope predictions which makes use of **NetMHC** for predicting binding[[5]](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5348633/).

<p align="center"> <img width = "580" src="https://user-images.githubusercontent.com/50211392/70484420-a72c2880-1aa0-11ea-9478-51f8d43df7d5.png"> </p>

**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
       Note that structure-based methods vary widely and are constantly and rapidly evolving based on the properties that scientists are discovering to be the most important for binding. A few examples include solvent accessibility (**CEP**), surface accessibility and propensity amino acid score (**DiscoTope**), geometrical properties (**ElliPro**, **PEPITO**, and **SEPPA**), physicochemical properties (**PEPITO** and **SEPPA**), and antibody-specific epitope propensity (**EPIPREAD**, **PEASE**)[[4]](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5348633/).  
       
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
       As many of the above tools rely on machine learning, they require a training data set. The data set used to train most of these methods is fairly small which limits how well we can train the algorithms[[1]](https://www.sciencedirect.com/science/article/pii/S1532046414002330?via%3Dihub). **IEDB** currently uses **DiscoTope** and **ElliPro** on its website for predicting B-cell epitopes. They tend to outperform other B-cell epitope prediction methods, with **ElliePro** having an AUC score of around 0.7.  **DiscoTope** is the method of choice for discontinuous epitopes and **ElliPro** for 3D Geometric epitopes[[5]](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5348633/). While the first two classes of tools require the input of the 3D structure of the epitope, algorithms such as Google’s AlphaFold have made predicting 3D structure from the linear sequence much simpler. Furthermore, every few years, there tends to come out with a new method for predicting discontinuous epitopes so we can hope for better performance in the near future.  
       
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
	Because the tools for T-cell and B-cell epitope prediction often require different input and output formats, it is difficult to definitively say which tools are better than others. Furthermore, there is generally a very limited dataset that we can use to evaluate the performances of the various methods[[1]](https://www.sciencedirect.com/science/article/pii/S1532046414002330?via%3Dihub). As such, despite the **IEDB** recommending certain tools, other tools are still in use and may come down to a judgement call on the researchers part as to which to use.

### Epitope/Vaccine Synthesis
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
       Knowing the general structure of epitopes for an infection, vaccine development becomes significantly more streamlined, hence the current shift in epitope-based vaccine development. Once an epitope’s structure has been determined, the synthesis of said epitope begins. Methods can range from building a sequence that would result in the desired protein and implanting said sequence as a plasmid into a cell for excretion, or a method known as Solid Phase Peptide Synthesis (**SPPS**). In **SPPS**, some insoluble material is chosen as an anchor to which the sequence will attach itself to. Amino acids, bound to resin beads, are added to the growing peptide sequence, protected by resin beads that prevent unwanted reactions. When an amino acid binds to the nascent peptide sequence, the resin prevents any other amino acids from binding. As the sequence is bound to the support, all the excess amino acids can be washed away, after which the resin at the end amino acid is removed and the next one is added, comparable to being the reverse of reverse Sanger sequencing by synthesis. At the very end, the crude peptide is cleaved from the support structure to give the desired peptide sequence using some form of acid, usually Trifluoroacetic Acid (**TFA**), but varies with the resin beads and anchor used. Such peptides are precipitated in ether, centrifuged, and isolated multiple times before being dried in nitrogen gas. All peptides are eluted with the use of TFA before being characterized with mass-spectroscopy, wherein expected peptide masses are identified. **Figure 7** below shows a visual representation of this peptide synthesis cycle.    

<p align = "center" > <img width="793" alt="Screen Shot 2019-12-09 at 12 20 04 PM" src="https://user-images.githubusercontent.com/50211392/70469835-ada9a880-1a7e-11ea-8070-cdba1026c254.png"> </p>

**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
    In the end, the desired epitope can be synthesized, alongside any other desired epitope as a single sequence if necessary, forming what is known as a chimeric protein. The benefits of synthesizing epitopes in a chimeric form are that, through the synthesis of only one peptide chain, multiple vaccines can be handled, either epitope varying within one strain of the disease to epitopes of multiple strains and diseases. As epitopes are stored in a desiccated form, before use and testing, it is necessary to resuspend the epitopes in a saline solution, the benefit being ease of preservation.
    
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
    Then begins the immunization trials, wherein live animals are treated with the epitope-based vaccines where, after the vaccination period has passed, cells are extracted and analysis on the vaccines’ impact begins. A variety of analysis methods are available, one being the use of **ELISPOT** kits, which are used for the detection of cytokine secreting cells and the secretion of one to two analytes, in this case being relevant antibodies to the epitope. Statistical analysis then begins to determine whether or not the epitope-based vaccine injected had any significant impact on antibody development. 
    
**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
    One major roadblock to epitope-based vaccine development is, ironically, the vast abundance of tools and databases available to the modern bioinformaticians. As even databases vary significantly in the statistical methodology used, even similar tools may yield different results. A unified pipeline for vaccine development has now become a major point of contention in the field.  

**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**
Below is a final summary of the workflow discussed in this chapter. 
<p align="center"> <img width="510" alt="Screen Shot 2019-12-09 at 4 14 09 PM" src="https://user-images.githubusercontent.com/50211392/70483928-f96c4a00-1a9e-11ea-93ad-8f51c465306e.png">
 </p>

*This chapter was written by Marehan Waly, Jelan Waly, and Spencer Liu for BENG 183 in Fall 2019.*  

**Sources:**   
**[1]** https://www.sciencedirect.com/science/article/pii/S1532046414002330?via%3Dihub        
**[2]** https://www.hindawi.com/journals/bmri/2010/705821/    
**[3]** https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1002829    
**[4]** https://www.hindawi.com/journals/jir/2017/2680160/     
**[5]** https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5348633/    
**[6]** https://www.ncbi.nlm.nih.gov/pubmed/28978689    
