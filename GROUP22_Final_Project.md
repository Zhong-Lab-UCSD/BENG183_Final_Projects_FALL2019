# Machine learning : Hidden Markov model (HMM) 

A Hidden Markov Model (HMM) was first introduced as a way to solve speech recognition problems in 1990s. Later, many HMM applications are brought into play in the field of bioinformatics. In this chapter, we will show the definitions for the Markov Chain and HMM, as well as bioinformatics problems using HMM and their algorithm implementations.

## Definitions and Preliminaries

### Markov Chain
**Markov Chain** is a stochastic process that 
(For simplicity purposes, we focus on discrete time and discrete state space here, to align with HMM applications we will introduction later.)
1. is discrete time
    * **discrete time**: $T=\{0,1,2,3,...\}$.
2. has discrete state space 
    * **discrete state space**: $S=\{s_1,s_2,s_3,...\}$.
    * **states**: random variables $\{x_t : t \in T\}$, which take value from $S$.
    * Note: the states $x_0,x_1,x_2,x_3,...$ are observable - what is different from HMM.
        * **initial distribution**: $\pi = ({\pi}_i)$, where each entry ${\pi}_i$ stands for the probability for the Markov Chain to start at $i \in S$.
3. satisfies the Markov property
    * **Markov property** (first-order MP): predicting the future depends solely on its present state, this prediction can be made just as well as knowing the full history. 
        * i.e. the probability of being at state $x_{t+1}$ at time $t+1$ depends only on the state $x_t$ at time $t$ but not $x_{t-1},...,x_1$.
        * Similarly, we have **$k^{th}$-order Markov property**. It states that predicting the future depends solely on its most recent k states, this prediction can be made just as well as knowing the full history. 
    
    * **transition matrix**: $A=(a_{ij})$, where each entry $a_{ij}$ represents the probability to get from $i$ $(\in S)$ to $j$ $(\in S)$ in one step. Here, we restrict the Markov Chain to be time invarient so that the transition matrix is always the same.

To define a Markov Chain, we need (1) the time index set $T=\{0,1,2,3,...\}$, (2) the state space $S=\{s_1,s_2,s_3,...\}$, (3) the transition matrix $A=(a_{ij})$, (and (4) the initial distribution $\pi = ({\pi}_i)$). 

#### Markov Chain Example
The following is an example of Markov Chain, known as reflected random walk,


![](https://i.imgur.com/RW0evNh.png)

where time index set is $T=\{0,1,2,3,...\}$, the state space is $S=\{0,1,2,...\}$ and transition matrix is
 $$A=\begin{pmatrix} p & 1-p & 0 & 0 & ... \\ 0 & p & 1-p &  0 & ...\\ 0 & 0 & p & 1-p & ... \\ 0 & 0 & 0 & p & ... \\ \vdots & \vdots & \vdots & \vdots & \ddots \end{pmatrix}.$$
 
And here is a simple example of a symmetric (p = $\frac{1}{2}$) reflected random walk plot (State vs Time).

![](https://i.imgur.com/WRfYpxo.png)


### Hidden Markov Model
**Hidden Markov model** is derived from Markov Chain, but
1. the states in the Markov Chain are NOT observable, although they DO exist as part of the model
    * **hidden state space** is $S=\{s_1,...,s_N\}$ and **hidden states** are $x_0,x_1,x_2,x_3,... \in S$
    * **transition matrix**: $A=(a_{ij})$
    * **initial distribution**: $\pi = ({\pi}_i)$

2. On the other hand, the additional observations are known.
    * **observed state space** is $V=\{v_1,...,v_M\}$ and **observations** are $o_0,o_1,o_2,o_3,... \in V$
    * **emission matrix**: $B=(b_i(k))$, where each entry $b_i(k)$ represents the probability to observing $o_k$ when the Markov Chain is at $i \in S$

To define a Hidden Markov Model, we need (1) the time index set $T=\{0,1,2,3,...\}$, (2) the hidden state space $S=\{s_1,...,s_N\}$, (3) the observed state space $V=\{v_1,...,v_M\}$, (4) the initial distribution $\pi = ({\pi}_i)$, (5) the transition matrix $A=(a_{ij})$, and (6) the emission matrix $B=(b_i(k))$. 

#### Hidden Markov Model Example

The following is a simple example problem using Hidden Markov Model. Suppose that I have two coins, one of which is biased. Based on the observed outcomes of heads or tails, can you figure out the pattern how I changes between the two coins? 

![](https://i.imgur.com/MbeCpWt.png)


## HMM in Bioinformatics and Dynamic programming Algorithms

### Three Types of HMM Questions
1. Evaluation / Probability Evaluation (Forward procedures)
    * Given $(a_{ij}),(b_i(k)),({\pi}_i)$, observations $(o_0,o_1,...,o_T)$
    * Compute the likelihood of observation sequence with given model
2. Decoding / Optimal State Sequence (Viterbi algorithm)
    * Given $(a_{ij}),(b_i(k)),({\pi}_i)$, observations $(o_0,o_1,...,o_T)$
    * Identify the hidden state sequence $(x_0,x_1,...,x_T)$ that generates best observation sequence
3. Recognition / Learning (Baum-Welch (EM) Algorithm)
    * Given observation $(o_0,o_1,...,o_T)$
    * Identify hidden Markov Model with parameters $((a_{ij}),(b_i(k)),({\pi}_i))$ that best generates the observation sequence

### Gene Finding Problems and Dynamic programming Algorithms

We will discuss about algorithms to solve the above three types of HMM model problems. Specifically, we will do this in the context of gene finding problems.

#### 1. Evaluation

* **Question:**  
    During the training process of a hidden markov model, we have to evaluate how well the current model perform after each update of transition and emission matrix, and update the matrix again based on the result. So here comes our first question: Based on the current Markov model, what is the probability of getting a specific observed DNA sequence?
    
* **Problem Specification**:
    * If we have the DNA Sequence (e.g. ATTG...), we would like our observation to be $o_i \in \{A,C,T,G\}$ ($o_1=A, o_2=T, o_3=T, o_4=G, ...$)
    * The hidden states are the desired features. For example, they can be "exons" or "introns", or they can be "deletion", "duplication" or "insertion".

    Solution is the probability of getting each observation under each given hidden states
        
* **Evaluation Process - Forward algorithm**:
    We will simply the question for demonstration where we restrict the observation to be A or G only. Given the observation is seq(“A”, “G”, “A”) and the HMM (picture below) that has two states of S1 (as exon) and S2 (as intron), what is the probability that this sequence is generated by the current model?
    The following diagram shows the all transition probabilities and emission probabilities of all possible observation at each state in a pre-trained HMM.
    ![](https://i.imgur.com/hJ45ICA.png)

    

    Based on the observations(“A”, “G”, “A”) and the Forward Algorithm, we can fill out the evaluation process diagram showing below. 
    ![](https://i.imgur.com/Z5MGsFn.png)


#### 2. Decoding
* **Question**:
    
    Similar to the Evaluation problem, we also want to find which hidden states sequence that shows the best probability to generate the observed sequence, based on the current Markov model. One of the problems that we are trying to solve with HMM is to recognize exons and introns in an open reading frame. The input we usually have will be a DNA sequence, while the bases in the sequence are the emitted symbols of an HMM. On the other hand, what we want to find out is which state actually emits the corresponding symbol and those states are unobservable for the observers. We figure this out through picking the hidden state sequence that has the highest probability of doing so.
* **Problem Specification**:
    The parameters will be very similar to the Evaluation problem.            
    * If we have the DNA Sequence (e.g. ATTG...), we would like our observation to be $o_i \in \{A,C,T,G\}$ ($o_1=A, o_2=T, o_3=T, o_4=G, ...$)
    * The hidden states are the desired features. Here, they can be "exons" or "introns".
    
    Solution is the hidden state sequence that shows from which state that each observation nucleotide is generated. 
            
* **Decoding Process - Viterbi algorithm**:
    We could do something similar as the Evaluation problem just talked about and use the idea introduced below. But, here we are introducing a more advanced but more commonly used gene finding Viterbi algorithm.
    ![](https://i.imgur.com/T2HL8aF.png)
    In this algorithm,
    $V_i(t)$: the probability of the HMM stay in state i after generating $y_t$(observation at time step “t”), following the most probable path in the model.
    $a_{ji}$: the probability of state j transit to state i in the model
    $b_{ji}(y)$: the probability of observing ytwhen the HMM is at state i (after the transition from state j to state i).
    $S_I$:the initial state.
    
    ![](https://i.imgur.com/EnE5sEY.png)
    Based on the observations(“A”, “G”, “A”) and the Viterbi Algorithm, we can fill out the decoding process diagram showing below. 
    ![](https://i.imgur.com/cWZL4lw.png)
    Then for each observation, we select the state with the highest probability of generating current observation to be the result for current step.
    ![](https://i.imgur.com/txY3NIb.png)
As the result shown above, (S1,S1,S1) will be the best hidden state sequence that generates the observation(A,G,A)
  
#### 3. Recognition/Training
* **Question**: 
    In gene finding, the common problems that we are trying to solve are identifying protein-coding genes and random ORFs(open reading frames) in prokaryotic DNA sequences or recognizing exons, introns, intergenic regions or promoters etc. from eukaryotic genes. Therefore, in real-life cases, we are trying to build and train a hidden markov model with a set of sequence contains the desired features within them. Therefore, we have the question of how to build up the model.
    
* **Problem Specification**:
    Again, the parameters will be very similar to the Evaluation problem.            
    * If we have the DNA Sequence (e.g. ATTG...), we would like our observation to be $o_i \in \{A,C,T,G\}$ ($o_1=A, o_2=T, o_3=T, o_4=G, ...$)
    * The hidden states are the desired features. For example, they can be "exons" or "introns", or they can be "deletion", "duplication" or "insertion".

    Solution is the trained hidden Markov model that maximize the probability of predicting given features on a DNA sequence.

* #### Training Process - Baum–Welch algorithm
    The following is a commonly used gene finding Baum–Welch algorithm.
    * **Step1:**  
    Deciding the number of desired features and initialize the transition matrix and emission probabilities of each possible observation for each hidden state.
    * **Step2:** Update transition matrix
    For example, we have two hidden states S1 and S2. Then we will have four possible transitions: S1 to S2, S1 to S1, S2 to S1, and S2 to S2. For each possible transition, we separate the observation sequence into 2-mers (e.g. ATGCGAT -> (AT,TG,GC,...,AT)) and we assume that the transition happens within each 2-mers is the transition we currently look at. Based on that, we calculate the probability of getting the 2-mer under provided transition (called P1) and the highest probability of observing that 2-mer (called P2). When we did it for each 2-mer, we sum up the all P1 and P2. The ratio sum(P1)/sum(P2) will be the new probability for that transition. Then we normalize the results to make each category has values that sum up to one.
    * **Step3:** Update emission matrix 
    Similar procedure with last step. Under the condition that a certain possible observation is generated by a certain state, we calculate the probability of getting the current training sequence with the restrictions for all training data(called P1). And then we calculate the highest probability of getting a sequence through the HMM for each training sequence(called P2). The ratio sum(P1)/sum(P2) will be the new emission probability of a certain possible observation within a certain state. We did the same for all possible combinations of observation and hidden state. Then we normalize the results to make each category has values that sum up to one.
    * **Step4:** Update the initial vector
    For each hidden state, we assume that the sequence start with that and we calculate the probability of getting the sequence based on that. Then we normalize the vector to make it sum up to one.
    * **Step5:** Repeat the 2-4 steps until we have the probability results converge satisfactorily.


    

## Discussions

### Some vailable HMM Tools in bioinformatics
* HMMER Program: A useful program for searching sequence databases for sequence homologs, and for making sequence alignments. The basic methods used in implementing HMMER is profile HMMs
    * Compared to BLAST, and other sequence alignment and database search tools based on older scoring methodology, HMMER aims to be significantly more accurate and more able to detect remote homologs, because of the strength of its underlying probability models.

* UPP: a method for ultra-large multiple sequence alignment
    * Up to 1,000,000 sequences
    * Robust to fragmentary sequences
* PFAM: a large collection of protein families, each represented by multiple sequence alignments and hidden Markov models (HMMs).
    * Using HMM to recognizing membership in protein families

### Advantages of HMM
1. Efficient learning algorithms-learning directly derived from the raw sequence data
Allow consistent treatment in the form of locally learnable
2. Can handle inputs of variable length - allow flexible generalization
3. In generating alignments part, the best path found by the Viterbi algorithm identifies a state for each position, and that in turn can specify the column. Different from alignments which each column can only be used once, HMM is more powerful for the same state can be used repeatedly in a path.
4. HMMs also allow variant structures to be modeled directly, not just as inserts and deletes to a consensus sequence. 
5. The state diagram offers a complete description of the system
6. It is possible to reconstruct lost data


### Disadvantages of HMM
1. They cannot express dependencies between hidden states
2. First order HMMs are limited by their first-order Markov Property
3. Only a small fraction of distributions over the space of possible sequences can be represented by a reasonably constrained HMM
4. HMM is expensive in both memory and running time: Time: O(K^2N) Space: O(KN)
5. The Baum-Welch algorithm: Not guaranteed to find globally best parameters: converges to local optimum, depending on initial conditions
6. Too many parameters/ too large model (over-fitting): Only as good as training set; More training is not always good.
7. HMM is only dependent on every state and its corresponding observed object:
    -The sequence labeling, in addition to having a relationship with individual words, also relates to such aspects as the observed sequence length.
    -The target function and the predicted target function do not match: HMM acquires the joint distribution P(Y, X) of the state and the observed sequence, while in the estimation issue, we need a conditional probability P(Y|X).




## References
1. Bishop, Martin J.; Thompson, Elizabeth A. (20 July 1986). "Maximum likelihood alignment of DNA sequences". Journal of Molecular Biology. 190 (2): 159–65. doi:10.1016/0022-2836(86)90289-5

2. Krishnadev, O., Srinivasan, N. AlignHUSH: Alignment of HMMs using structure and hydrophobicity information. BMC Bioinformatics 12, 275 (2011) doi:10.1186/1471-2105-12-275

3. L.R. Rabiner, "A tutorial on hidden Markov models and selected applications in speech recognition", Proc. IEEE, vol. 77, pp. 257-286, 1989.

4. Using hidden Markov models to align multiple sequences. David W. Mount. Cold Spring Harb Protoc. 2009 Jul; 2009(7): pdb.top41. doi: 10.1101/pdb.top41

5. Viterbi AJ (April 1967). "Error bounds for convolutional codes and an asymptotically optimum decoding algorithm". IEEE Transactions on Information Theory. 13 (2): 260–269. doi:10.1109/TIT.1967.1054010