# Reverse engineering the dengue virus (under development 🚧)


<img src="https://user-images.githubusercontent.com/75043245/151876851-a653d8ab-d05e-42ac-958a-7ade33d03c2b.png" width="300" height="200">


<h2> What is dengue? </h2>

> Dengue is a viral infection transmitted to humans through the bite of infected mosquitoes. The primary vectors that transmit the disease are Aedes aegypti mosquitoes and, to a lesser extent, Ae. albopictus. The virus responsible for causing dengue, is called dengue virus (DENV). There are four DENV serotypes and it is possible to be infected four times. While many DENV infections produce only mild illness, DENV can cause an acute flu-like illness. Occasionally this develops into a potentially lethal complication, called severe dengue. There is no specific treatment for dengue/severe dengue. Early detection of disease progression associated with severe dengue, and access to proper medical care lowers fatality rates of severe dengue to below 1%.  Dengue is found in tropical and sub-tropical climates worldwide, mostly in urban and semi-urban areas. The global incidence of dengue has grown dramatically with about half of the world's population now at risk. Although an estimated 100-400 million infections occur each year, over 80% are generally mild and asymptomatic. - World Health Organization



<h2> What do I hope to achieve?</h2>

- Visualize data to discover patterns between viral families

- Determine the evolutionary behaviour of the virus

- To gauge the differences and similarities between viruses

<h2> Prerequisite understanding </h2>


- Each codon (triplet of nitrogenous base) is transcribed into an RNA sequence and is then translated into an amino acid
- Specific triplets have specific amino acids
- These translated amino acids perform specific functions ranging from protein synthesis to playing a role in immune response
- By manipulating the nitrogen bases (AGCT) of the DNA the code will be introducing mutations in the genetic code which will change the amino acid sequence and thus change the proteins involved in cellular or viral processes, such as the reverse transcription of retroviruses (After a virus eg. a retrovirus or a coronavirus enters a host cell, reverse transcriptase converts the viral RNA genome into double-stranded DNA. This viral DNA then migrates to the nucleus and becomes integrated into the host genome)
- The genome sequence I got from US DOHHS is the DNA sequence, and they used a reverse transcriptase to convert RNA to cDNA - likely! (RNA is converted to cDNA during library prep during sequencing. Then the output sequence is the DNA sequence. They basically generated a cDNA library and sequenced that (library is  population of DNA molecules containing all the necessary sequence information to allow DNA propagation in a cellular host) )



<h2> Code:</h2>

See here: [notebook](https://github.com/Krish-sysadmin/ReverseEngineerVirus/blob/main/dengue-virus.ipynb)

<h2> 🧬 Biology background info </h2>

The big ideas:

- DNA and RNA are nucleic acids, that is, they are polymers of repeating monomers called nucleotides. Each nucleotide consists of a pentose sugar covalently bonded to a phosphate group and a nitrogenous base.
- RNA is a single-stranded nucleic acid which consists of a long chain of nucleotides covalently bonded together by phosphodiester bonds. In RNA the pentose sugar is ribose and the bases are A (adenine), U (uracil), C (cytosine) and G (guanine). There MANY types of RNA , theres mRNA, tRNA, snRNA , rRNA which all carry out different tasks in a cell.
- DNA is a double-stranded nucleic acid with a double-helix structure. The two strands are also made of long chains of nucleotides covalently bonded by 3'-5' phosphodiester bonds, however, the nucleotides of DNA are made of deoxyribose sugar and the nitrogenous bases A, T (thymine), C and G. The two strands are linked together by hydrogen bonds formed between complementary base pairs on opposite strands. A forms 2 hydrogen bonds with T and C forms 3 hydrogen bonds with G. Hydrogen bonds basically hold the DNA molecule together. Note that the strands of DNA are anti-parallel, meaning they run in opposite directions.
- DNA consists of two strands, the coding strand with a 5’-3’ direction which actually contains all the information of the genome as it is, and then its complementary strand, the non-coding strand with a 3-5 direction. Now, the mrna is created FROM the non coding dna strand, that’s why it has the SAME bases (except T, it’s replaced by U) , SAME direction with the coding strand. ( as they are both complementary to the non coding strand ). After all, that’s why they called it ‘coding strand’ of DNA. It’s because it has the same base sequence with mRNA
- Transcription of DNA to mRNA: about mRNA. DNA is transformed into mRNA with a process called ‘transcription’. enzymes like RNA transcriptase II line up the nitrogenous bases of RNA (adenine, guanine, cytosine and uracil) opposite the complementary bases of the non-coding DNA strand (the complementary strand of mRNA).  The mRNA molecule formed is single stranded.
- In eukaryotes, after transcription, mRNA has to go through mRNA splicing in the cell's nucleus. There are some regions between the sequences of the actual genes, that are not going to be translated to proteins afterwards, that are responsible for other functions of the DNA , not for protein synthesis. After mRNA is transcribed, it also contains those regions that need to be cut off during mRNA splicing. Enzymes alongside snRNA inside the nucleus, cut off those parts that ‘do not refer to proteins’ from the mRNA molecule, (the introns) and leave the exons, which are the actual genes. (The non-translating regions are the introns.)
- Protein synthesis is the process by which proteins are made in a cell from genes. DNA is too large to move out of the nucleus through the nuclear pores, so it transcribes the base sequence of a gene onto an RNA molecule called messenger RNA (or mRNA). Note that the mRNA molecule is made of the complementary bases to the DNA molecule, where instead of Thymine, there is the RNA base Uracil which is complementary with Adenine (eg If a section of DNA has AATC then the mRNA has UUAG). The mRNA carries the transcribed gene onto a ribosome in the cytoplasm. In the ribosome, another type of RNA called tRNA (transfer RNA) groups bases of the mRNA molecule in triplets called codons. Each group of 3 bases (or codon) codes for one amino acid. As a gene has many bases the tRNA will code for many amino acids which will bond together by peptide bonds to form a large polypeptide (or protein). Each gene codes for specific polypeptides which then fold into proteins and have diverse functions.  
*DNA is basically untouched ( not to worry about it,only  unzips for transcription) . It stays there only opens up to be replicated but that’s it. DNA to RNA is transcription because then translation is when RNA codes for amino acids. 
You don’t make DNA out of RNA cos the DNA always stays in the nucleus and it’s been there since the cell formed


<details>
<summary>The fine details</summary>
<br>

 

<img src="https://user-images.githubusercontent.com/75043245/151867982-4b25dfa5-143e-496f-93b0-ed641fc0bf5c.png" width="200" height="200">

1. So you have 4 bases
2. A and T pair up (In each strand) Of DNA
3. C and G pair up (In each strand) Of DNA
4. But in RNA U pairs up with A instead of T
5. Genome sequence in link is DNA code which is a template  - Its the DNA sequence, and they used a reverse transcriptase to convert RNA to cDNA
6. The two strands of DNA separate. And mRNA bases attach to one of the DNA strands which is opposite to the one it wants to replicate. So if you wanna replicate A then mRNA will attach to T (so the mRNA base is T). They keep doing that until the desired code is replicated and they have a strand of RNA which goes to the ribosome and in ribosome. 3 bases are read at the same time. Those are the triplet codons. And an amino acid matching those is brought to them. Multiple amino acids together are bound by peptide bonds and that makes a protein

Codon table to see the code and see what amino acid that codes for: (DNA)

<img src="https://user-images.githubusercontent.com/75043245/151868401-8dd9c1f1-9858-4977-99f9-0163114c4fdb.png" width="200" height="200">


Note:
- Multiple amino acids together are bound by peptide bonds and that makes a protein




  



![image](https://user-images.githubusercontent.com/75043245/151870117-f037363b-e2a3-4097-943b-66747bcd8eba.png)


**Codon table**


![image](https://user-images.githubusercontent.com/75043245/151872198-90c1c385-167d-40eb-a748-90e7ae260cdd.png)


(That is RNA,  is what ultimately codes for the amino acid) 

  
</details>


<h2> Our progress  🌊 </h2>


<h2> Our todo list </h2>



<h2>  Unanswered Questions </h2>


<h2> Tests </h2>

None yet


<h2> Precautions and/or solutions </h2>

NOT MEDICAL ADVICE. I AM NOT A DOCTOR.



<h2>Resources to learn more about genomes, DNA, RNA, transcription and more: </h2> 

Websites 
- https://www.ncbi.nlm.nih.gov/nuccore/9626685
- https://en.wikipedia.org/wiki/Dengue_virus
- https://www.khanacademy.org/science/ap-biology/gene-expression-and-regulation/translation/a/the-genetic-code-discovery-and-properties
- https://www.who.int/news-room/fact-sheets/detail/dengue-and-severe-dengue
- https://people.cs.uchicago.edu/~fortnow/papers/kaikoura.pdf

Books (dengue related, bioinformatics, vaccines, genome studies, creation of DNA molecules (synthesis), textbooks) and courses:
- 
