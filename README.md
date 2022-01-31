# Reverse engineering the dengue virus (under development 🚧)

What is dengue?

> Dengue is a viral infection transmitted to humans through the bite of infected mosquitoes. The primary vectors that transmit the disease are Aedes aegypti mosquitoes and, to a lesser extent, Ae. albopictus. The virus responsible for causing dengue, is called dengue virus (DENV). There are four DENV serotypes and it is possible to be infected four times. While many DENV infections produce only mild illness, DENV can cause an acute flu-like illness. Occasionally this develops into a potentially lethal complication, called severe dengue. There is no specific treatment for dengue/severe dengue. Early detection of disease progression associated with severe dengue, and access to proper medical care lowers fatality rates of severe dengue to below 1%.  Dengue is found in tropical and sub-tropical climates worldwide, mostly in urban and semi-urban areas. The global incidence of dengue has grown dramatically with about half of the world's population now at risk. Although an estimated 100-400 million infections occur each year, over 80% are generally mild and asymptomatic. - World Health Organization



What do I hope to achieve?
- Discover patterns
- Behaviour in terms of evolution for predictions
- To gauge the similarities, similar characteristics compared to other viruses

The essence of how this works?
- Each codon (triplet of nitrogenous base) is transcribed into an RNA sequence and is then translated into an amino acid
- Specific triplets have specific amino acids
- These translated amino acids perform specific functions ranging from protein synthesis to playing a role in immune response
- By manipulating the nitrogen bases (AGCT) the code will be introducing mutations in the genetic code which will change the amino acid sequence and thus change the proteins involved in cellular or viral processes

<img src="https://user-images.githubusercontent.com/75043245/151876851-a653d8ab-d05e-42ac-958a-7ade33d03c2b.png" width="300" height="200">

<h2> Code:</h2>

See here: [notebook](https://github.com/Krish-sysadmin/ReverseEngineerVirus/blob/main/dengue-virus.ipynb)

<h2> 🧬 Biology background info </h2>


- RNA and DNA are both nucleic acids, meaning they are made of repeating subunits called nucleotides. These nucleotides are made of a pentose sugar covalently bonded to a phosphate group and a nitrogenous base. RNA is a single stranded molecule meaning it has one long chain of nucleotides bonded by covalent bonds and has bases A, U, C and G. Also RNA has ribose as the pentose sugar
- mRNA is used in transcription where the genes of the DNA molecule are replicated onto an RNA molecule (but changing the base T in DNA for U in RNA) which then travels through the cytoplasm of the cell. In the ribosomes the tRNA basically gets groups of 3 bases where each three bases code for one amino acid and so a long chain of amino acids (protein) is made from one gene.
- DNA is double stranded, has deoxyribose sugar and has a double helix shape. In DNA the 2 strands are held together by hydrogen bonds between the complementary bases on the 2 strands (A from one strand pairs with T from another strand and C from one strand pairs with G from another strand). They always pair up in this way. 2 hydrogen bonds are formed between A and T and 3 hydrogen bonds are formed between C and G and that’s what basically holds the double helix together.

Remember: T in DNA  and U in RNA

<img src="https://user-images.githubusercontent.com/75043245/151867982-4b25dfa5-143e-496f-93b0-ed641fc0bf5c.png" width="200" height="200">

1. So you have 4 bases
2. A and T pair up (In each strand) Of DNA
3. C and G pair up (In each strand) Of DNA
4. But in RNA U pairs up with A instead of T
5. Genome sequence in link is DNA code which is a template 
6. The two strands of DNA separate. And mRNA bases attach to one of the DNA strands which is opposite to the one it wants to replicate. So if you wanna replicate A then mRNA will attach to T (so the mRNA base is T). They keep doing that until the desired code is replicated and they have a strand of RNA which goes to the ribosome and in ribosome. 3 bases are read at the same time. Those are the triplet codons. And an amino acid matching those is brought to them. Multiple amino acids together are bound by peptide bonds and that makes a protein

Codon table to see the code and see what amino acid that codes for: (DNA)

<img src="https://user-images.githubusercontent.com/75043245/151868401-8dd9c1f1-9858-4977-99f9-0163114c4fdb.png" width="200" height="200">


Note:
- Multiple amino acids together are bound by peptide bonds and that makes a protein


Basically:
- DNA is the template that stays inside the nucleus
- And RNA is the single strand that travels out of the nucleus into the ribosome to code for proteins
- RNA is a copy of DNA but a single strand
- Essentially DNA codes for RNA and RNA codes for proteins. But instead of T as a base RNA has U
- Codon table - multiple triplet codons code for 1 amino acid (eg AAT and AAC both code for leucine) to decrease the likelihood of mutations cos even if a base gets replaced (eg T by C) the same amino acid will be synthesized
- There MANY types of RNA , theres mRNA, tRNA, snRNA , rRNA etc etc. but, when you’re picturing a strand similar to the dna one you r about mRNA. With mRNA you need to know that basically it derives from the actual dna strand with all the information , but there’s a little complication here. DNA consists of two strands, the coding strand with a 5’-3’ direction which actually contains all the information of the genome as it is, and then its complementary strand, the non-coding strand with a 3-5 direction. Now, the mrna is created FROM the non coding dna strand, that’s why it has the SAME bases (except T, it’s replaced by U) , SAME direction with the coding strand. ( as they are both complementary to the non coding strand ). After all, that’s why they called it ‘coding strand’ of DNA. It’s because it has the same base sequence with the mRNA molecule, which is the one that travels to the ribosomes and helps with protein synthesis etc etc. DNA is ‘transcribed’ into mRNA with a process called ‘transcription’. And badically what happens during this process is some enzymes line up nitrogenous bases of RNA ( adenine, guanine, cytosine and uracyl -remember in place of thymine) opposite the complementary bases of the non-coding dna strand ( the complementary strand of mRNA) . A-T and G-C are complementary. The mRNA is single stranded.
- Gene sequence of the DNA, there are some regions between the sequences of the actual genes that are not going to be translated to proteins afterwards that are responsible for functions of the DNA , not for protein synthesis. After mRNA is transcribed, it also contains those regions that need to be cut off during a process called mRNA splicing. Enzymes inside the nucleus of the cell cut off those parts that ‘do not talk about proteins’ from the mRNA molecule, ( the introns ) and leave the exons, which are the actual genes. (The non-translating regions are the introns.)
- The mRNA molecule leaves the cell, travels to the ribosomes and then the translation begins. 
- Each amino acid refers to a codon ( let me explain )
- A codon is a sequence of 3 bases ( for example AUG- which codes for the amino acid methionin)
- A gene on the mRNA might have 50 codons or 50 codons ( thus 50x3=150 bases ) . The mrna binds to the ribosome and another molecule , the tRNA , reads the codons, and brings the amino acid needed, and thus the polypeptide chain ( the protein) is created
-  What tf stop means, UAG, UGA and UAA are ‘stop codons’ which code for no amino acid but they ‘inform’ the ribosomes when the polypeptide chain is done and the translation is complete

The DNA is basically untouched ( not to worry about it,only  unzips for transcription) . It stays there only opens up to be replicated but that’s it. DNA to RNA is transcription because then translation is when RNA codes for amino acids
You don’t make DNA out of RNA cos the DNA always stays in the nucleus and it’s been there since the cell formed

![image](https://user-images.githubusercontent.com/75043245/151870117-f037363b-e2a3-4097-943b-66747bcd8eba.png)


**Codon table**


![image](https://user-images.githubusercontent.com/75043245/151872198-90c1c385-167d-40eb-a748-90e7ae260cdd.png)


(That is RNA,  is what ultimately codes for the amino acid) 


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

Books (dengue related, bioinformatics, vaccines, genome studies, creation of DNA molecules (synthesis), textbooks) and courses:
- 
