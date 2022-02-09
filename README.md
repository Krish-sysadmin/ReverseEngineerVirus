# Reverse engineering the dengue virus (under development 🚧)



**WARNING!: This project is on temporary sabbatical! Reverse engineering a virus is fun, but it's very consuming (especially without really understanding a lot of the biology behind the scenes), and I can't dedicate time to it now due to other projects and commitments. There is enough code here to decode the dengue virus into its full protein sequences so now all that is left is - to determine differences in it compared to its predecessors, find its evolution patterns and discover more patterns! More coming soon!

**Current time on this project will be spent by the team in reading more around the virus and reading new research done about it.**


<img src="https://user-images.githubusercontent.com/75043245/151876851-a653d8ab-d05e-42ac-958a-7ade33d03c2b.png" width="300" height="200">


<h2> What is dengue? </h2>

> Dengue is a viral infection transmitted to humans through the bite of infected mosquitoes. The primary vectors that transmit the disease are Aedes aegypti mosquitoes and, to a lesser extent, Ae. albopictus. The virus responsible for causing dengue is called dengue virus (DENV). There are four DENV serotypes and it is possible to be infected four times. While many DENV infections produce only mild illness, DENV can cause an acute flu-like illness. Occasionally this develops into a potentially lethal complication, called severe dengue. There is no specific treatment for dengue/severe dengue. Early detection of disease progression associated with severe dengue and access to proper medical care lowers fatality rates of severe dengue to below 1%.  Dengue is found in tropical and sub-tropical climates worldwide, mostly in urban and semi-urban areas. The global incidence of dengue has grown dramatically with about half of the world's population now at risk. Although an estimated 100-400 million infections occur each year, over 80% are generally mild and asymptomatic. - World Health Organization



<h2> What do I hope to achieve?</h2>

I could lie and say that I am trying to:

- Discover patterns

- Behaviour in terms of evolution for predictions

- To gauge the similarities, similar characteristics compared to other viruses

and that might just be the by product. But what I am actually trying to do is PLAY WITH THE VIRUS and get my hands dirty with the genetic code of it. Through this repository you too can! :)

<h2> Prerequisite understanding </h2>


- The base sequence of a gene is transcribed onto an RNA sequence called mRNA. In the ribosomes of cells each triplet of nitrogenous bases found in the mRNA, called a codon, will be translated into one amino acid by the molecule tRNA.
- Specific combinations of triplets code for specific amino acids (eg AAC will code for one amino acid whilst CCG will code for another)
- These translated amino acids then link through peptide bonds to form polypeptides which can fold into proteins whose functions range from immune response to structure, transport and sensitivity.
- By manipulating the nitrogen bases (AGCT) mutations can be introduced into the genetic code which will change the amino acid sequence and thus change the proteins involved in cellular or viral processes, such as the reverse transcription of retroviruses (after a virus eg. a retrovirus or a coronavirus enters a host cell, reverse transcriptase converts the viral RNA genome into double-stranded DNA. This viral DNA then migrates to the nucleus and becomes integrated into the host genome).
- The genome sequence I obtained from US DOHHS is the DNA sequence, and they likely used a reverse transcriptase to convert RNA to cDNA. (RNA is converted to cDNA during library prep during sequencing. Then the output sequence is the DNA sequence. They basically generated a cDNA library and sequenced that. Note: A library is a population of DNA molecules containing all the necessary sequence information to allow DNA propagation in a cellular host)



<h2> Code:</h2>

See here: [notebook](https://github.com/Krish-sysadmin/ReverseEngineerVirus/blob/main/dengue-virus.ipynb)

To run the notebook: 

```

pip install notebook (or use anaconda)
cd ~/path/to/this/repo
jupyter notebook

```

<h2> 🧬 Biology background info </h2>

The big ideas:

- DNA and RNA are nucleic acids, that is, they are polymers of repeating monomers called nucleotides. Each nucleotide consists of a pentose sugar covalently bonded to a phosphate group and a nitrogenous base.
- RNA is a single-stranded nucleic acid which consists of a long chain of nucleotides covalently bonded together by phosphodiester bonds. In RNA the pentose sugar is ribose and the bases are A (adenine), U (uracil), C (cytosine) and G (guanine). There are many types of RNA , theres mRNA, tRNA, snRNA and rRNA which all carry out different tasks in a cell.
- DNA is a double-stranded nucleic acid with a double-helix structure. The two strands are also made of long chains of nucleotides covalently bonded by 3'-5' phosphodiester bonds, however, the nucleotides of DNA are made of deoxyribose sugar and the nitrogenous bases A, T (thymine), C and G. The two strands are linked together by hydrogen bonds formed between complementary base pairs on opposite strands. A forms 2 hydrogen bonds with T and C forms 3 hydrogen bonds with G. Hydrogen bonds basically hold the DNA molecule together. Note that the strands of DNA are anti-parallel, meaning they run in opposite directions.
- DNA consists of two strands, the coding strand with a 5’-3’ direction which actually contains all the information of the genome as it is, and then its complementary strand, the non-coding strand with a 3-5 direction. The mRNA is created from the non-coding DNA strand, that’s why it has the same bases (except T, it’s replaced by U) and same direction as the coding strand. After all, that’s why they called it ‘coding strand’ of DNA; it has the same base sequence with mRNA.
- Transcription of DNA to mRNA: DNA is copied into mRNA (single-stranded) by a process called ‘transcription’. Enzymes like RNA transcriptase II line up the nitrogenous bases of RNA (adenine, guanine, cytosine and uracil) opposite the complementary bases of the non-coding DNA strand. 
- In eukaryotes (such as plant and animal cells), after transcription, mRNA has to go through mRNA splicing in the cell's nucleus. There are some regions between the sequences of the actual genes that are not going to be translated to proteins afterwards and that are responsible for other functions of the DNA. After mRNA is transcribed, it also contains those regions that need to be cut off during mRNA splicing. Enzymes alongside snRNA inside the nucleus remove those parts that do not code for proteins from the mRNA molecule (the introns), and leave the exons which are the coding sections of the nucleic acid.
- Protein synthesis is the process by which proteins are made in a cell from genes. DNA is too large to move out of the nucleus through the nuclear pores, so it transcribes the base sequence of a gene onto an RNA molecule called messenger RNA (or mRNA). Note that the mRNA molecule is made of the complementary bases to the DNA molecule, where instead of Thymine, there is the RNA base Uracil which is complementary with Adenine (eg If a section of DNA has AATC then the mRNA has UUAG). The mRNA carries the transcribed gene onto a ribosome in the cytoplasm. In the ribosome, another type of RNA called tRNA (transfer RNA) groups bases of the mRNA molecule in triplets called codons. Each group of 3 bases (or codon) codes for one amino acid. As a gene has many bases the tRNA will code for many amino acids which will bond together by peptide bonds to form a large polypeptide (or protein). Each gene codes for specific polypeptides which then fold into proteins and have diverse functions.  
Note to reader: DNA remains basically untouched in the nucleus and only unzips for transcription and DNA replication. It is the transcribed mRNA molecule which moves out of the nucleus and codes for proteins.

<details>
<summary>The fine details</summary>
<br>

What is a polyprotein?
-  A bunch of protein strands helps together by covalent bonds
Usually a way viruses pack their proteins closer together


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
- https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4809784/
- https://pubmed.ncbi.nlm.nih.gov/26423934/
- https://a16z.com/2019/11/21/reverse-engineer-biology/
- https://en.wikipedia.org/wiki/Reading_frame
- https://www.yourgenome.org/facts/what-is-the-central-dogma#:~:text=The%20central%20dogma%20of%20molecular,this%20information%20to%20the%20ribosomes%3F.


Books (dengue related, bioinformatics, vaccines, genome studies, creation of DNA molecules (synthesis), textbooks) and courses:
- 
