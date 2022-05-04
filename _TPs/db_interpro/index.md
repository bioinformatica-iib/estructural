---
layout: page
title: TP N°1
subtitle: Protein Databases
data : false
menubar_toc: true
hero_height: is-small
toc_title: CONTENIDOS
construccion: false
---

<style>
details > summary:first-of-type {
   display: list-item;
}
details summary { 
  cursor: pointer;
}

details summary > * {
  display: inline;
}

</style>

{% if page.construccion %}

**Pagina en construccion**

{% else %}

## Recursos Online

* **UniProt:** [https://www.uniprot.org/](https://www.uniprot.org/)

* **InterPro**:** [http://www.ebi.ac.uk/interpro](http://www.ebi.ac.uk/interpro)
* **PFAM:** [http://pfam.xfam.org](http://pfam.xfam.org)
* **Protein Data Bank (PDB)**: [http://www.rcsb.org](http://www.rcsb.org) and [http://www.ebi.ac.uk/pdbe](http://www.ebi.ac.uk/pdbe)

## Objetivos
* Familiarizarse con el uso de UniProt
* Familiarizarse con el uso de **PFAM**


## UniProt

UniProt is probably the most comprehensive and up-to-date collection of protein sequence and annotation data. It should be the first stop for any researcher looking for the available information about a protein, as it is very comprehensive and saves the effort of integrating data from multiple sources.

### UniProtKb. The UniProt KnowledgeBase.

Uniprot's major database is **UniProtKB** (UniProt KnowledgeBase), that has two sections: the **TrEMBL** and **Swiss-Prot**  sections.

* **TrEMBL** is a compendium of automatically annotated information on proteins that were mostly, but not exclusively obtained from the translation of nucleotide coding sequences (CDS) available at *GenBank*.
* **Swiss-Prot:** is a manually annotated and reviewed protein resource where high-quality information can be found.

**TrEMBL** provides the raw data for **Swiss-Prot** curators to revise; therefore, while **TrEMBL** has more entries than **Swiss-Prot**, it lacks the expert manual annotation.

### Uniparc and Uniref

UniProt is also home of **UniParc** (the UniProt Archive), a non-redundant database of almost all publicly available protein sequences in the world. Currently **UniParc** contains protein sequences from more than 20 publicly available databases, such as:
* EMBL-Bank/DDBJ/GenBank nucleotide sequence databases
* Ensembl
* EnsemblGenomes
* Protein Data Bank (PDB)
* RefSeq
* Saccharomyces Genome database (SGD)
* TAIR Arabidopsis thaliana Information Resource
* UniProtKB/Swiss-Prot, UniProtKB/Swiss-Prot protein isoforms, UniProtKB/TrEMBL

**UniRef** (the UniProt Reference Clusters) are collections of UniProt sequences clustered at specific sequence similarity thresholds (such as 90% for UniRef90).

### The UniProt website

* The [UniProt website](https://www.uniprot.org/) allows browsing of its data sets by clicking the tiles on the homepage and through the links in the footer of every webpage.

<p style="text-align:center">
<img src="./images/uniprot_homepage.png" alt="UniProt Homepage" style="max-width:70%">
</p>

<figcaption align = "center">

**Fig 1.** The [UniProt](https://www.uniprot.org) homepage.

</figcaption>
<br>
<br>

<p style="text-align:center">
<img src="./images/uniprot_footer.png" alt="UniProt Footer" style="max-width:70%">
</p>

<figcaption align = "center">

**Fig 2.** This [UniProt](https://www.uniprot.org) footer appears on every webpage.

</figcaption>
<br>
<br>

* At the top of the page, there is a search bar and direct access to perform similarity searches on the UniProtKB database with BLAST and pairwise alignments with Clustal Omega.


<p style="text-align:center">
<img src="./images/uniprot_top.png" alt="UniProt Search Bar" style="max-width:70%">
</p>

<figcaption align = "center">

**Fig 3.** [UniProt](https://www.uniprot.org) top search bar.

</figcaption>

* The ‘Retrieve/ID mapping’ link at the homepage can be used to search for a list of protein identifiers and retrieve their individual UniProt entries at once. It also serves for converting the input identifiers to their equivalent in GenBank, PDB and many other external databases.

* Searches can be performed using the top search bar at the homepage, with a drop-down menu to select the target database and an *Advanced* option for further refinement.

<p style="text-align:center">
<img src="./images/uniprot_dropdown_menu.png" alt="UniProt Dropdown Menu" style="max-width:70%">
</p>

<figcaption align = "center">

**Fig 4.** [UniProt](https://www.uniprot.org) dropdown menu.

</figcaption>
<br>
<br>

* Searching UniProtKB leads to the results page where selected information about the retrieved sequences is presented in table format. A *Column* button (sharp as a pencil) on top allows customization of the different fields shown. The results can be limited to a certain database, organism, search term, etc. using the *Filter by* options on the left-hand bar. There is also a *View by* section to cluster the results by taxonomy, pathway or other criteria.

<p style="text-align:center">
<img src="./images/uniprot_results.png" alt="UniProt Results Page" style="max-width:70%">
</p>

<figcaption align = "center">

**Fig 5.** [UniProt](https://www.uniprot.org) results page.

</figcaption>
<br>

* By default, UniProt entries are displayed in the *Entry* view on the left-hand bar, with links to the different entry sections below. Click on the title of each section for more information. The *Feature viewer* is a useful alternative that provides an overview of all annotations along the protein’s sequence.

<p style="text-align:center">
<img src="./images/uniprot_entry_sections.png" alt="UniProt Entry Sections" style="max-width:70%">
</p>

<figcaption align = "center">

**Fig 6.** [UniProt](https://www.uniprot.org) entry sections.

</figcaption>
<br>

### Uniprot entries
Each UniProt entry can be referred to two unique identifiers:
* The **Accession number** is a sequence of 6 to 10 alphanumerical characters (e.g. P04637) that is kept in all updates and thus should be used in all publications. 
* The **Entry name** is a more readable ID often selected to reflect biological properties like the protein name or the organism (e.g. P53_HUMAN), which may change if more information about the entry or related sequences becomes available.

An UniProt entry can have both experimental and predicted data. Manual assertions, taken from published experiments, transferred from experiments in similar proteins or imported from other databases, are coloured in gold. Data retrieved by the automatic annotation process is coloured in blue.

The annotation content of an UniProt entry is ranked by a discrete 5-stars system. The score of each entry is computed from the presence or the number of annotation types. More stars reflect a more extensively annotated entry; however, the system does not represent annotation correctness.

UniProt is updated every four weeks. The latest data sets can be retrieved by following the ‘Download latest release’ link on the ‘UniProt data’ section of the homepage.

## Uniprot Exercises

### Exercise 1.
Do you have a protein you are working on? Try to access its UniProt entry by browsing or searching the database. You can use your protein to perform most of the following exercises too.

### Exercise 2.
Search for *CDC7*.
1. What is the name of this protein?
2. How many entries exist in different organisms, and how many in human?
3. How many of the human entries are high-quality entries?
4. When searching for CDC7, how many of the resulting entries are the product of the cdc7 gene? (Hint: use the filtering tools at the left-hand bar.) Why is Q8NEY8 among the results? What about B1AMW7?

### Exercise 3.
Lysine-specific demethylase 3B exists in human (Q7LBC6) and mice (Q6ZPY7). Although its function is known, it has been annotated from different sources in each organism. Can you identify these sources?

### Exercise 4.
Go to the UniProt entry for human Lysine-specific demethylase 3B. Inspect the different annotated features available (fields can be shown or hidden with the left-hand bar) and then answer the following:
1. What is the entry name?
2. Which UniProtKB database does this entry belong to?
3. Which are some of the molecular functions and biological activities associated with this protein?
4. Where is this protein located? Where does this information come from?
5. How many proteins are known to interact with it?
6. Does it have any protein interaction motif?
7. Is there any known structure of this protein? Does it comprise the whole sequence?
8. How many isoforms are annotated of this protein? How do they differ from the canonical sequence?
9. Can you find when was this entry created and when is the date of its last modification? How many times was it modified?
10. Find out which information is available for position 773 at the main ‘Entry’ page. Then, go to the ‘Feature viewer’ and inspect the same position. (Hint: the sliding semi-circles at the top can be used to focus the display on the desired region). You will probably find some extra information; what does it tell you about your protein? Now that you are aware of this information, can you find it in the main ‘Entry’ page too?

### Exercise 5.
The UniProt entry Q9UBU3 corresponds to GHSR, an appetite-regulating hormone. It is expressed as a preprotein that is later cleaved into ghrelin and obestatin. Can you locate the position of these mature proteins in the full-length preprotein? (Hint: the ‘Feature viewer’ can be helpful). Do they have any natural sequence variant? How many proteins share 90% identity with the full-length protein?

### Exercise 6.
Isoform 6 of Prelamin-A/C (P02545), also known as progerin, has a mutant variant associated with disease. What is the name of this syndrome? How does this variant differ from the canonical sequence?

### Exercise 7.
Lysine-specific demethylase 5C (P41229) is another human histone demethylase that specifically targets the lysine 4 of histone H3. Can you find the Kcat and Km of this reaction on its UniProt entry? 

### Exercise 8.
Can you download the sequence of the Lysine-specific demethylase 5C isoform 1 in FASTA format? 

<ul class="block-list has-radius is-primary">
   <li class="is-highlighted is-info has-icon" markdown="span">
    <span class="icon"><i class="far fa-lightbulb"></i></span>
        <b>FASTA Format</b><br>
        A <b>FASTA file</b> starts with the ">" (greater-than) symbol plus a brief description of the sequence, followed by the actual sequence in standard one-letter code in the second line.<br>
        <b>Multi-FASTA files</b> have many of these combinations, one after another and with an optional blank line after each sequence.
   </li>
</ul>

### Exercise 9.
UniProt entries have a specific section named ‘Family & Domains’. It describes the identity, position and length of domains that were annotated in the protein. A domain is defined as ‘a specific combination of secondary structures organized into a characteristic three-dimensional structure or fold.’ How many of these domains can you find in Lysine-specific demethylase 5C? Are there any other relevant regions of the proteins described? If so, can you find references to these domains cross-linked from other databases?


## PFAM

[Pfam](http://pfam.xfam.org) is a useful resource to identify conserved functional regions in proteins. **Pfam** helps finding regions of similarity between a query sequence and its database of annotated protein families, with the goal of gaining knowledge about the architecture, function and relationships of the protein of interest.

A **Pfam** entry is built from a multiple sequence alignment of a curated set of sequences known to belong to the family. This is the *seed* alignment that is used to train a *profile Hidden Markov Model* (or *profile HMM*) that provides an extended representation of the family. This probabilistic model reflects the variability in each position of the family and is used for an exhaustive search of a large database (such as UniProtKB) for all homologous sequences. Those retrieved sequences showing significant similarity to the profile HMM are aligned to this model, resulting in a more comprehensive *full alignment* of the family.

<ul class="block-list has-radius is-primary">
   <li class="is-highlighted is-info has-icon" markdown="span">
    <span class="icon"><i class="far fa-lightbulb"></i></span>
        <b>Before continue reading, think and discuss:</b><br>
        What is the definition of a Domain?
   </li>
</ul>

Although regions covered in **Pfam** are commonly called *domains*, a **Pfam** entry does not necessarily represent a stretch of sequence that folds into a discrete tertiary structure, but rather a conserved evolutionary unit. In fact, each entry in **Pfam** is classified in one of six categories according to the length and characteristics of it.

* A **Family** of related sequences can have one or many domains. 
* A **Domain** is a collection of related sequence regions that behave as a distinct structural unit.
* Sequences of a **Repeat** can only form stable structural unit when multiple copies are present.
* A **Motif** is a group of short sequences with a defined role, often in binding.
* **Coiled-coil** sequences adopt alpha-helical structures that coil together.
* **Disordered** regions show noticeable sequence similarity but do not adopt regular structures.

Large and divergent families may share significant sequence, structural of functional similarity with members of other families. Since these *superfamilies* are hard to represent by a unique alignment or profile HMM, **Pfam** provides a higher-level grouping of these families into **Clans**.

### Useful things to know about Pfam
* **Pfam** acts as a database of families that can be browsed and as a tool for similarity searching with the sequence of interest. Searches can also be made with the accession or name of the entry (e.g. VAV_HUMAN), or a **Pfam** family name (e.g. PF00571), or using related keywords.
* Any residue in any given sequence can only belong to one **Pfam** family.
* Data in **Pfam** is mostly taken from UniProt. Information is also linked from Wikipedia when available.
* Just like BLAST, **Pfam** provides an E-value that reflect the significance of a search hit.
* When **Pfam** builds a protein family, a ‘gathering threshold’ is set by hand for each family. This GA score determines the minimum score that any sequence should get in the profile HMM search to include this sequence in the full alignment.
* Profile HMMs are built and used using the widely used HMMER3 software package, available at http://hmmer.org
* It is possible to download the seed and full alignments and the profile HMM. 
* Sometimes it is useful to download large volumes of data in bulk. Although this is not straightforward to use, **Pfam** (like the NCBI and many others) provides access to its database via an FTP site and a RESTful interface.
* Although **Pfam** is highly relevant, it may be superseded by other, more integrative databases sometime soon. Keep an eye for updates! 

## Pfam Exercises
### Exercise 1.
Do you have a protein of interest? If so, try to find which **Pfam** domains it has and if it belongs to any **Pfam** clan. 

### Exercise 2.
Go to entry PF00571. Does it describe a protein, a domain, a family or a clan? How many sequences are linked with this entry?

### Exercise 3.
On the same **Pfam** entry PF00571, observe the tabs on the left-hand menu.
1. In the ‘Summary’ section, can you find the names of three proteins that carry this domain?
2. ‘Domain organisation’ lists the domain architectures (specific arrangements of certain domains) where this family is found. How many proteins have the ‘CBS x 2’ architecture? Notice the graphical and colourful representation of the annotated domains; you can hold the mouse over them for an extended description. Can you find a ‘disorder’ region in this architecture? Discuss: Would you call this disordered region a domain?
3. Another abundant architecture is ‘IMPDH, CBS x 2’. What do the little colour dots indicate? Where does this information come from?
4. Still in the ‘Domain organisation’ section, you’ll find on the bottom of the page the less populated architecture. Click on ‘Show’ to see all 70+ sequences with this architecture. Do they all look the same? Why are some colour blocks displayed with rugged edges?
5. In the ‘Alignments’ section the various formats in which the pre-calculated alignments for the family are presented. Try to download the ‘seed’ alignment in FASTA format, with sequences depicted in alphabetical order and showing gaps as dashes. 
6. The ‘HMM logo’ is a graphical summary of the profile HMM that provides a quick overview of its properties. For each position in the X-axis, a higher Y-axis value indications stronger conservation. Which is the most conserved position in this logo? 
7. **Pfam** provides evolutionary information about the proteins that belong to this family. Notice you can get a phylogenetic tree of the family in the ‘Trees’ section: which multiple sequence alignment was used to build this tree? There is also a menu option (‘Species’) for checking the distribution of this protein family across species. In which kingdom is this protein more abundant? How many eukaryotic species appear to have this protein?
8. The section ‘Interactions’ lists 15 interactions for domains in this family. Use the ‘More…’ link to display further information about the source of this data: is it determined experimentally or based on computational predictions?
9. In the ‘Interactions’ section, follow the link to the IMPDH family. What is the activity of this domain? Can you determine the structural fold of this family from the name of the clan it belongs to? (Notice that the ‘Clan’ section is active for this entry.)
10. The ‘Structures’ section links the regions of UniProt entries where the CBS domain was found with their identifiers the PDB database of known structures. By following the ‘PDB ID’ link you can inspect the tertiary structures in the PDB database. How many different structures of the first 60 residues of the domain can you find?

### Exercise  4.
‘Domain organisation’ lists the domain architectures (specific arrangements of certain domains) You may recall that UniProt has at least three domains (JmjN, ARID and then JmjC) annotated for the human Lysine-specific demethylase 5C. Search **Pfam** with its UniProt entry name KDM5C_HUMAN to see the corresponding entry of the protein. Notice that the links on the left-hand menu are different than those for **Pfam** families.
1. In the ‘Summary’ section, can you find any other domains and/or interesting regions? 
2. What does the ARID domain of this protein bind to? Can you find a PDB code of it?
3. Are the zinc fingers listed as domains in **Pfam**? Were they also annotated as domains in UniProt?
Additional Resources

## InterPro
[InterPro](http://www.ebi.ac.uk/interpro) is a natural extension to Pfam and other databases for protein classification. **InterPro** also predicts functional characteristics of proteins by assigning them to families and by recognizing protein domains and relevant sites. However, **InterPro** is a *meta-database*: it combines protein signatures from multiple, independent databases into a single resource for an integrative sequence classification.

In **InterPro**, a *protein signature* is just a computational model that reflect the site-specific amino acid conservation pattern of a multiple sequence alignment. It can take the form of a sequence pattern, a profile that describes a certain sequence motif or a sophisticated Hidden Markov Model (HMM) that contemplates insertions and deletions in protein families. Initial models are used for iterative searches of databases such as UniProtKB to collect remote homologues and increase the number of distant sequences that the model represents. The final protein signature is a very descriptive prediction model that can be used for protein sequence analysis.

Among the many member databases of **InterPro** are:
* Pfam.
* SMART: a database of protein domain architectures.
* Superfamily: an HMM-based database of functional and structural annotation in proteins.
* CATH/Gene3D: a database of domain superfamilies with known structure and their prediction in complete genomes.
* MobiDB: a central resource for annotation of protein intrinsic disorder in UniProt sequences.

Since the different databases would very likely have redundant information, a team of **InterPro** curators check and manually merge the signatures referring to the same family, domain or site into single **InterPro** entries. Therefore, each protein signature has as an **InterPro** accession code plus the corresponding code in the individual databases.

Notice that the strength of **InterPro** lies on the integration of multiple sources of information, each with its typical strengths, and not in the quantity of information extracted from them. By collecting multiples sources of annotation, **InterPro** serves as a powerful diagnostic tool. However, when signatures of interest are found, it is generally advisable to follow the links to the corresponding member databases for further information.

An **InterPro** entry can be of a few different types:
* **Domains** in **InterPro** are discrete units with distinct sequence, structure or function that can be find in different biological contexts.
* Members of a **Family’ of proteins**, while also sharing a common evolutionary origin, have similar sequences, structures and/or functions.
* **Homologous Superfamily** entries collect proteins with common ancestry. They normally have very low sequence conservation but a noticeable structural similarity.
* **Repeats** identify short sequences typically found many times in the same protein.
* A **Site** is also a short sequence but with one or more conserved residues that may have a defined function:
    - active site, a short sequence that contains one or more conserved residues, which allow the protein to bind to a ligand and carry out a catalytic activity.
    - binding site, a short sequence that contains one or more conserved residues, which form a protein interaction site.
    - post-translational modification sites (PTMs), a short sequence that contains one or more conserved residues some of which are the site of a Post-translational modification.
    - conserved site, a short sequence that contains one or more conserved residues.
* The **unintegrated** are signatures from member databases that are *unintegrated* in InterPro. These signatures might not yet be curated or might not reach InterPro's standards for integration. However, they can still provide important information about a protein of interest

### Useful things to know about InterPro:
* At the homepage, a box on the top right corner allows searching **InterPro** with distinct entry codes related with your protein of interest. You can use an **InterPro** accession code (consisting of ‘IPR’ plus a number), an identifier from UniProtKB or any of the member databases, etc. You can also search with keywords related with the function or activity of your protein (e.g. ‘isomerase’).
* Searches of the **InterPro** database with a sequence of interest can be made with *InterProScan*. It is automatically loaded when you click on the ‘Search’ tab but it is also available for download in the *Download* tab.

* Also, you can download all **InterPro** entries and all mappings of **InterPro** entries to UniProtKB proteins, among other data sets, from the ‘Download’ tab.

## Interpro Exercises
### Exercise 1.
Do you have a protein of interest? If so, try to find which **InterPro** signatures it matches. 

### Exercise 2.
Search **InterPro** with the Pfam identifier PF00571. What is its **InterPro** accession code? Does it describe a protein, a domain, a family or something else? Does it describe the same entity that Pfam does? Do they look similar or at least have things in common?

### Exercise3.
Looking at the same **InterPro** entry, can you tell which are the signatures from other databases that were merged with Pfam to create this **InterPro** entry? (If so, follow the links and check if these member databases provide new information on the protein.)

### Exercise 4.
How many proteins are matched by this entry? How many domain architectures? How many proteins have two repeated occurrences of this entry followed by a transporter-associated domain (IPR005170)?

### Exercise 5.
Search for the **InterPro** entry describing the protein Lysine-specific demethylase 5C (UniProtKB  entry P41229). The left-hand menu lets you filter out unwanted signatures, while the main section holds the prediction of signatures in the protein of interest.
1. Which signatures are recognized in this protein? What changes if you de-select the box ‘Domains’, on the ‘Entry type’ section at the left-hand menu?
2. Protein signatures are mapped to the query sequence in the main results. Look at the ‘Homologous superfamilies’ section. What is the architecture of this superfamily?
3. The most C-terminal signature found in this superfamily is a certain zinc finger. Which **InterPro** signatures describe this region? What type of signatures are these? Where does **InterPro** takes the information for this assignment? (Hint: inspect the ‘Detailed signature matches’ section.)
4. Among the matched signature is the IPR0001606 ‘domain’ entry. Which databases were processed to create this entry? Do they all map to the exact same region of the protein of interest? If not, why?
5. Can you identify any intrinsically disordered region in this protein? (Remember that ‘mobidb’ is a top resource for annotation of these regions.)
6. Follow the link on the top-left to Download the protein sequences of all 221 similar proteins in FASTA format. Open the file on your system to check consistency.

### Exercise 6.
Search for the **InterPro** entry describing the protein with the FASTA sequence copied at the bottom of the page. 
1. Does it belong to any protein family? Can you find the name of the PRINTS database entry used for building this **InterPro** family signature?
2. What is the difference between **InterPro** signatures IPR001767 and IPR003587?
3. Looking at the previous two signatures and IPR000320, can you describe the architecture of this protein? How does it differ from the architecture presented by the ‘Homologous superfamilies’ section at the top?
4. What is the biological role of this protein? (Hint: click on the name of the protein family.)
5. Does this protein have a signal peptide?
6. How could you know, at a glance, that this protein has a peptidase activity?

```
>squirrel_seq | example from EBI Train Online
MALPARLVPLCCLALLALPAQSCGPGRGPVGRRRYVRKQLVPLLYKQFVPSVPERTLGAS
GPAEGRVARGSERFRDLVPNYNPDIIFKDEENSGADRLMTERCKERVNALAIAVMNMWPG
VRLRVTEGWDEDGHHAQDSLHYEGRALDITTSDRDRNKYGLLARLAVEAGFDWVYYESRN
HVHVSVKAGTVGGGCFRETEAAQLWGDARGLRELHRAWVLAADAAGRVVPTPVLLFLDRD
LQRRASFVAVETERPPRKLLLTPWHLVFAARGPAPAPGDFAPVFARRLRAGDSVLAPGGD
ALRPARVARVAREEAVGVFAPLTAHGTLLVNDVLASCYAVLESHQWAHRAFAPLRLLHAL
GALLPGGAVQPTGMHWYSRFLYRLAEELLG
```

## Protein Data Bank (PDB)

The **Protein Data Bank** (PDB) is a collective repository of the atomic coordinates of proteins and other biological molecules. These have been determined experimentally by X-ray crystallography, NMR spectroscopy and, more recently, cryo-electron microscopy.

PDB files provide information on the tertiary structure of macromolecules, and at the same time, they allow users to inspect their secondary structures, domain arrangement and global folds. They can also be used as a high-confidence piece of evidence about interactions, from binding of small ligands to formation of oligomers and protein complexes. 

PDB mainly stores coordinate files, which list each atom in a structure and their three-dimensional position in space. (Besides the main molecule, it can also hold small molecules, ions, water and other ligands). These files also have a ‘header’ section with information about the protein, the experimental procedure, reference bibliography, etc. All data should be stored as a plain text file and respecting a certain layout to allow an easier identification of the different sections.

A single PDB archive is maintained by three independent distribution sites:
* The [RCSB](http://www.rcsb.org) PDB in USA.
* The [PDBe](http://www.ebi.ac.uk/pdbe) in Europe.
* The [PDBj](https://pdbj.org/) in Japan.

Although the main data and resources are shared, each site provides a set of exclusive services to users for the inspection of data. 

All PDB entries in these databases receive an identifier in the form of a four-character accession code. This should start with a number and be followed by any three alphanumeric characters, in upper or lowercase (e.g., 2c3v). 

Although PDB files can be inspected with a text editor (to review the header data, for example), it is usually better to use a dedicated visualization program. It will display the structure on a virtual 3D coordinate system, allowing the user to zoom, rotate and translate the structure, change its representation, display bonds and calculate distances, find structural features of interest, etc. These tools can be accessed online and are available at the PDB sites, but more powerful and versatile programs (like UCSF Chimera or PyMol) should be downloaded.

### Useful things to know about PDB:
* Most PDBs have a *chain ID* associated with its atoms. This is a unique identifier (usually a one-letter code starting on A) for all residues or nucleotides belonging to the same polypeptide or nucleotide chain, respectively. Thus, chain IDs help recognize the different molecules present in the file. 
* PDB files normally have one model for each molecule they contain. However, a PDB entry may carry one or multiple models of the same molecule. For example, due to the characteristics imposed by the technique itself, structures solved by NMR usually have 20 alternative models in the same file. 
* It is generally better to inspect first the ‘Biological assembly’ than the ‘Asymmetric Unit’ of an entry. The latter is useful for the crystallographer to refine the coordinates of the structure against experimental data. However, the biological assembly should reflect the functional form of the molecule.
* A central descriptor of the quality of the experimental data, and thus of the resulting PDB file, is its resolution. Expressed in Å (Ångstrom), low resolution values give more confidence on the location of atoms, while values exceeding 3 Å only allow a rough determination of the basic contours of the molecule.
* Many PDB entries have *missing residues*. These are portions that were not observed during the experimental determination of the structure, possibly due to an increased flexibility. These could range from short loops within globular domains to long disordered segments. 
* You should never assume blindly that a PDB file will follow the sequence of the corresponding UniProt entry. They may differ due to decision of the experimentalist or technical difficulties.
* Structure files must comply with the PDB format. Lately, PDB entries have been also made available in other interconvertible formats like mmCIF and XML, which are easier to understand by computers.

## PDB Exercises

### Exercise 1.
Do you have a protein of interest? Using RCSB PDB, can you find its structure? (You may not know if someone solved it yet, or at least the structure of a homologous protein. You may BLAST your sequence against the PDB database and inspect the results for these hits).

### Exercise 2.
In this tutorial we’ll work with the oxy-myoglobin of Physeter catodon (sperm whale). The PDB ID of this entry is 1A6M. Search for it using the top-right box.
1. Use the buttons on the top right to download a PDB file of the protein. 
2. Inspect the ‘Structure Summary’ section. When did this structure first appeared in the PDB? Is it a good quality structure? 
3. On the ‘Macromolecules’ section of the same page, you’ll find a mention to the Myoglobin entity. How many chains does it have? Can you find its UniProt accession?
4. Still there, the ‘Protein Feature View’ provides a site-specific mapping between UniProt and PDB, with many additional features from other databases. What kind of secondary structures does this protein adopt? Besides, can you find the iron binding sites? (Hint: use the zoom buttons on top).
5. Does this structure have a bound oxygen molecule?
6. Go to the ‘3D View’ tab, where you can play around with a three-dimensional representation of the protein structure. Hold the left button over the structure and move the mouse to rotate the structure. Use the right button to move it. Zoom in and out using the mouse wheel. 
7. Click over the structure to identify atoms. Can you find any of the iron binding sites you’ve seen before?
8. Now, on the ‘Display Options’ section on the right, use the ‘Interaction’ drop-down menu to focus the display on the interaction with the oxygen atom carried by the heme group. Move around the structure until you can identify the residue numbers. Are they the same as above? If not, why?
9. Set the ‘Interaction’ back to ‘None’. Now play around with the ‘Style’ and ‘Color’ drop-down options to change the representation of the protein. You can mark the ‘Spin’ checkbox on the ‘Viewer options’ menu to see the structure from different sides.
10. Check the ‘Experiment’ tab to see which pH was set on the crystallization experiments.
11. Inspect the information on the ‘Sequence Similarity’ tab to find out how many protein chains in other PDB entries are 100% identical to this protein.
12. Click on the number of chains in the 100% cluster and a table will load below showing the PDB entries of all these chains. Select 1A6M and any other structure solved at pH=4.0 (Hint: check the ‘Details’ column). Now, on the top of the list, select the ‘jFATCAT-rigid’ algorithm to perform a structural comparison of both structures. Wait until the superposition loads; Does the change in pH cause any significant difference between both structures?
13. A similar superposition can be obtained on the ‘Structure Similarity’ section. Here, the server proposes 3QM9 as structurally similar to 1A6M, even though they only share 40% sequence similarity. Select ‘jFATCAT-rigid’ on the lower right to compare them. Do you see more differences than in the previous comparison?
14. Without leaving these results, browse to the ‘Alignment Block(s)’ section below to see a structure-base sequence alignment of 1A6M and 3QM9.  Judging from the sequence similarity, the structural superposition and the conservation of residues, would you say 3QM9 could is also a myglobin?

<!--
## TMHMM
http://www.cbs.dtu.dk/services/TMHMM

TMHMM is a dedicated server for the prediction of transmembrane helices in proteins. Although it was first presented two decades ago, it has been updated and is still a reference for the task.
The program is based on the development of a Hidden Markov Model that served as a predictive tool. It was originally trained with a set of 160 membrane proteins. Its good performance was determined by a 10-fold cross validation and the comparison with a negative set of 645 non-membrane proteins from the PDB. 
The first output of TMHMM is a set of statistics and a list of the predicted transmembrane helices. This list is the most relevant part, as it maps the start and end of each predicted helix and loop region. The location of these loops, either ‘inside’ or ‘outside’ the cell, is also given. Therefore, the server makes it possible to trace the path of the protein from one side to the other of the membrane.
A posterior probability plot allows identification of strong transmembrane segments that made it to the final model and weak segments that were not considered good enough. The HMM calculates the total probability that a residue is part of a helix, an inside loop or an outside loop; then combines these assessments on the final model.
Some useful things to know about TMHMM:
    * The server does not accept sequences longer than 8,000 amino acids.
    * If the whole sequence is labeled as inside or outside it means that no membrane helices were predicted. 
    * Raw data can be downloaded from the link in the bottom of the results and used to create custom plots.

Exercises
    1. The interface to TMHMM Server 2.0 is quite simple. Use the search box on the homepage to run the prediction for bacteriorhodopsin, which sequence is pasted at the bottom of this page. Use the default output format (‘Extensive, with graphics’) to get more descriptive results.
    2. Inspect the results of the search. How many transmembrane helices did you find? 
    3. Among the statistics you’ll find the ‘Exp number of AAs in TMHs’. This is the expected number of amino acids in transmembrane helices according to this HMM prediction method. When this number exceeds 18, the protein is likely a transmembrane protein. Is bacteriorhodopsin a transmembrane protein?
    4. Another statistic is ‘Exp number, first 60 AAs’. This is the same as above but limited to the first 60 amino acids. If this number is not small, then a transmembrane helix that was predicted in the N-terminal region could be a signal peptide instead. (You could try some of the dedicated tools for prediction of signal peptides, such as SignalP).
    5. In the plot, red blocks correspond to transmembrane helices, blue lines indicate regions on the inside, and exterior segments are shown in purple. Could there be another transmembrane helix that the model is discarding? (Hint: look at the plot).

>AAA72184.1 bacteriorhodopsin
MQAQITGRPEWIWLALGTALMGLGTLYFLVKGMGVSDPDAKKFYAITTLVPAIAFTMYLSMLLGYGLTMVPFGGEQNPIYWARYADWLFTTPLLLLDLALLVDADQGTILALVGADGIMIGTGLVGALTKVYSYRFVWWAISTAAMLYILYVLFFGFTSKAESMRPEVASTFKVLRNVTVVLWSAYPVVWLIGSEGAGIVPLNIETLLFMVLDVSAKVGFGLILLRSRAIFGEAEAPEPSAGDGAAATS
-->


## Additional resources

### UniProt: Exploring protein sequence and functional information

[https://www.ebi.ac.uk/training/online/course/uniprot-exploring-protein-sequence-and-functional](https://www.ebi.ac.uk/training/online/course/uniprot-exploring-protein-sequence-and-functional)

### Pfam: Quick tour

[https://www.ebi.ac.uk/training/online/course/pfam-quick-tour](https://www.ebi.ac.uk/training/online/course/pfam-quick-tour)

### InterPro: Quick tour
[https://www.ebi.ac.uk/training/online/course/interpro-quick-tour](https://www.ebi.ac.uk/training/online/course/interpro-quick-tour)

### InterPro: Functional and structural analysis of protein sequences
[https://www.ebi.ac.uk/training/online/course/interpro-functional-and-structural-analysis-protei](https://www.ebi.ac.uk/training/online/course/interpro-functional-and-structural-analysis-protei)

### InterPro FAQS
[https://www.ebi.ac.uk/interpro/faqs.html](https://www.ebi.ac.uk/interpro/faqs.html)

### Protein classification: An introduction to EMBL-EBI resources
[https://www.ebi.ac.uk/training/online/course/protein-classification-introduction-embl-ebi-resou](https://www.ebi.ac.uk/training/online/course/protein-classification-introduction-embl-ebi-resou)

### PDBe: Quick tour
[https://www.ebi.ac.uk/training/online/course/pdbe-quick-tour](https://www.ebi.ac.uk/training/online/course/pdbe-quick-tour)

### PDBe: Exploring a Protein Data Bank (PDB) entry
[https://www.ebi.ac.uk/training/online/course/pdbe-exploring-protein-data-bank-pdb-entry](https://www.ebi.ac.uk/training/online/course/pdbe-exploring-protein-data-bank-pdb-entry)

### PDBe: Searching the Protein Data Bank
[https://www.ebi.ac.uk/training/online/course/pdbe-searching-protein-data-bank](https://www.ebi.ac.uk/training/online/course/pdbe-searching-protein-data-bank)

### PDBe: Searching for biological macromolecular structures
[https://www.ebi.ac.uk/training/online/course/pdbe-searching-biological-macromolecular-structure](https://www.ebi.ac.uk/training/online/course/pdbe-searching-biological-macromolecular-structure)


<!--
BLAST
http://blast.ncbi.nlm.nih.gov

BLAST (acronym of Basic Local Alignment Search Tool) is arguably the most important contribution of Bioinformatics to science. Over the last 20 years it has been the de facto tool for finding similar sequences to a protein or nucleotide sequence of interest, a useful first step towards its characterization.
As its name suggests, BLAST perform local alignments. Contrary to global approaches, which are designed to identify the overall similarity between two or more sequence from start to end, a local alignment can find segments of similarity even if they appear on different order in the compared sequences. Given that sequence conservation is a usual indicator of significant functional similarity, the locally aligned sequences may correspond to conserved motifs, domains or other biologically relevant regions. Local conservation that extends to full-length sequences may indicate homology (evolution from a common ancestor).
The success of BLAST lies in its algorithm. Briefly, it splits the input sequence in small fragments (or ‘words’) of defined size and scans a database of sequences to find all identical occurrences of each word. When a match is found, BLAST extends the comparison forwards and backwards, allowing gaps until the score falls below a certain threshold. (This score is computed from a substitution matrix, like BLOSUM62, penalizing inclusion of gaps.) All similar sequences are presented in the results by increasing ‘E-value’, an estimation of the number of times you may expect to find a similar or better alignment score just by chance.
The speed of the BLAST algorithm serves well for an efficient search within huge databases, such as those of all known proteins and nucleotides. The National Center for Biotechnology Information implements different versions of BLAST in its dedicated web server:
* BLASTN can be used to search nucleotide databases for similarity to a nucleotide query. It’s the only BLAST tool that aligns nucleotides to nucleotides.
* BLASTP can be used to search protein databases for similarity to a protein query.
It is also possible to use translated nucleotide sequences to look for potential coding regions with similarity:
* BLASTX takes a nucleotide query, translates it in the six possible frames and uses these to search protein databases.
* TBLASTN uses a protein query to search all possible translated sequences from a nucleotide database.
* TBLASTX translates a nucleotide query in all six frames and searches a translated nucleotide database.
The NCBI BLAST web server provides many databases to search for similarity, such as the (mostly) non-redundant and comprehensive ‘nr’ (protein) and ‘nt’ (nucleotide) databases; the ‘refseq’ data set of genomic, transcript and protein sequences; the ‘pdb’ database of protein sequences with known structure, and many organism-specific genomic databases.
Some useful things to know about BLAST:
* The protein you search with is referred to as the ‘query’. Every segment of similarity returned by the search is a ‘hit’, because you ‘hit’ this on a ‘subject’ sequence of the target database.
* BLAST is, above all, an algorithm for pairwise alignment of sequences. You can align two sequences of interest with the option ‘Align two or more sequences’ below the query input box in BLASTP.
* It is generally difficult to find remote homologues which may share low sequence similarity with the protein of interest. In these cases, PSI-BLAST (accessible from the ‘Program Selection’ section in BLASTP) can be used to perform a deep search by incorporating similar sequences in further search rounds.
* In the BLASTN tool you can opt for the MEGABLAST program to optimize the search for highly similar sequences. This can be useful, for example, when your goal is to identify an unknown transcript or genome.
Exercises
    1. Go to the NCBI BLAST homepage and select Protein BLAST. The search interface will load, with ‘blastp’ active on the top and several sections below (clic ‘Algorithm parameters’ to see more). 
    a. The main input box allows searching with a sequence, an ‘Accession.Version’ identifier (a stable code that increases the version number when the sequence is updated) or a ‘GI’ number (a numeric code that is replaced by a new GI when the sequence changes). Can you find this information in the FASTA sequence copied in the following page? (It corresponds to the green algae C. reinhardtii protein BLD10, involved in creating the centrosome/basal body complex.) You can also also upload the sequence as a file and limit the search to a part of it using the ‘From’ and ‘To’ boxes on the right.
    b. Which databases can you search? How many sequences does the ‘swissprot’ database have?
    c. Can you restrict your search to Eukaryota but removing Homo sapiens from the search?
    d. Increase the number of ‘Max target sequences’ and set a lower ‘Expectation threshold’ (e.g. 1e-4) so that you get many results while avoiding most of those hit sequences without statistical significance.
    e. The choice of substitution matrix (and gap costs) affect calculation of the similarity score between the ‘query’ and each ‘hit’. Higher PAM and lower BLOSUM matrices (e.g. PAM250, BLOSUM45) are better for identifying distant homologues. Which are the different matrices you can choose?
    f. Which would be the effect of activating the ‘Low complexity regions’ filter?
    g. Which options change if you opt for running PSI-BLAST instead?
    2. Search for similarity to C. reinhardtii BLD10 with BLASTP using default parameters (use the ‘Reset page’ top right button if you changed anything). You’ll get the BLAST output page, divided in four main sections.
        a. Job details are shown on the top. The ‘RID’ link can be used to retrieve the results from any computer until the expiration date. Also, ‘Search summary’ is useful for reviewing the parameters used for running BLAST. Which is the alternative name given here to the ‘Max target sequences’ input option?
        b. In the same section, use ‘Taxonomy reports’ to get an overview of the evolutionary extent of BLD10.
        c. For protein searches, the ‘Graphic Summary’ section maps superfamilies of conserved domains. Which domains are found in BLD10, and where?
        d. Also in the ‘Graphic Summary’ you get a graphical representation of the top scoring hits, coloured by score and mapped by their region of similarity with the query. Each block corresponds to an independent hit; blocks linked by thin grey lines are separate matches in the same subject protein.
        e. The ‘Descriptions’ section lists the sequences producing significant alignments. Can you recognize them all? Do they look like real homologues to BLD10?
        f. The results are first sorted from best to worse E-value, then by decreasing scores, etc. Reorder the list by decreasing query coverage. What does this field mean? What are the other fields in this list? 
        g. In this example, if you were interested in downloading five sequences of significant similarity to the query, would you download the top one? Use the check boxes to select five hits of high identity, from different organisms, and covering as much as possible of the query. Download these as a FASTA file. What is the difference between downloading ‘complete sequences’ and ‘aligned sequences’?
        h. In the ‘Alignments’ section you can find the alignments between the query and each hit. Individual hits of the same subject are listed together; this is the case of the BLD10 protein from Gonium pectorale. How long is this sequence? How long is the region of significant similarity with the query? How many of their residues are identical and how many are similar?
        i. Click the ‘Sequence ID’ link at the top of the G. pectoral BLD10 protein alignment (or to the right of the entry in the ‘Descriptions’ section) to get the GenPept entry of this protein, with information about it presented in a structured format usually known as ‘GenBank’. Can you find the region of the outer membrane channels? Use the drop-down menu on the top right to view this region only.
>gi|158280659|EDP06416.1|basal body protein [Chlamydomonas reinhardtii]
MAIDVDRTLAVLRRKLEALGYSDPLEPASLQLVQKLVEDLVHTTDSYTAVKQQCAKQAQEIAAFDTRLESVRQDSVRLQSENSQLHVLVMQHAERHEREAREHYTAVKRLEDTIAELSYWKHAAAEKLASADKENAGLRKRCEELAKLTDRLASGAATPQSVAPKISSRSPIRVAPPPSPPRPRQATVDVLQAANGRILSLQRQLADATAELQELRQRVAEDEDQIRRRDVEIDRLGTRAGTDTNVLALRARNEANESMILQLNGTVESLAARVRELEAVEVRCEELQGALRRAEMDRDQAEERYSRSARDHDALSREVLGLRRDLAALQDTNNRAAGLLAADAAGASTPDTTAGAPALRQRLADSRADVERLSGQLAAADMERRNLAQQLSALRSELDDTQFLLAEAQSRAAGLAAAQAVAESEARRLAGEAAAREGRLRELDSQLAVVLSDLEARQAGFAALEKDRAEANARAEELARRLDEVERSAASERAAAAAAQQSVSRLDSELRVVRGSAAALEAEAAALRQELQDVSVGKVRATSALSSTEDEAVRARQQAEALRMQLTAERRAAEELRAGHDTLQLEVDRLGGQLALQQQEAELLRQQLAAARGELAASEAAASGAEQKLSGLGALSQRLEEMGEQARRAQAATAEAEAEAVRLRAAVSEAKEGQARAERGLREARREVEGAREAEALVRAQLREVEAQAEGTSKALKAAEADRDRALMDARLAAGDLASLRDQLAAETSSAADAGSTARQMAARLSAAERAAAAAQEERERAAVAAEEAEAAAAAARGREEEARAQGREWAERARRAEALVAEYEADVAQLRAARDSDAAALRSLEDTVAAARRDLDARRSEVEQLTTLSLRGDATVQEYMANLKAMSTDLRAAEMRAADLAGEAAAAQDAAASWRSEAEQLRGLLRQMDADRDNLQHELDAKAERLVAQEQQLAGAQAAEQEAARLLALAEGRLALTDNRAREGEAEAAAVRAQLAAALDSVRALSGEGEALREELRAVSEDLEALVRENQVVGGELAAVAAQRDSAAEEARRLGGRRASAEQLLRAKEAEAEDLRRVYEALAAEHRRLQGGVGALEREGAMREAALQAKAAEVSSLAESQRAAQATINQYVMDLQAFERQVDSLSRQLSQAEADGEELVRQREALLEEIRAAQQVRLGLERHREELQRQVASLDSQVAIGRARLEDSNSEAASLNQRLAMERSRVAELEGLLAGMRAREFRSDFASDRAGGQLAVMVDRNRALEEQVASLQHQVGALQASREAQDRELSRLRGEALALAASTAASLEGRTAAAGGAAAGAAKDQAAALDRLTSERDAAQDEAARLRGALAAAEAAAASASTAAAVSIPAAGSGSEAAAVLRVRCSELERRNTELMQELRTLQDTCRQQESLLSAAQNELSALQAEHRRLVELVARLDQDKAAAAAEAAAARQQVATATRRVATAEQEAAAGAARLQSQLRDEQGRRRQAERDFLELLSSIEGAGGEAAAAAVAAAHGEGAAELASRRLRELQTQVDALEAEKAGLEEATQRTRATLGAMSGQMAAIQAEYDATNTALAGLAGAMAAGAQGQGQVQGPAGTAPAAAAGAPGPQPGQAQAGGFGGAHGGGSISLSGGPRR


Additional Resources

UniProt: Exploring protein sequence and functional information
https://www.ebi.ac.uk/training/online/course/uniprot-exploring-protein-sequence-and-functional
BLAST Help
https://blast.ncbi.nlm.nih.gov/blast/Blast.cgi?PAGE_TYPE=BlastDocs
BLAST homepage & selected search pages: How to BLAST
ftp://ftp.ncbi.nlm.nih.gov/pub/factsheets/HowTo_BLASTGuide.pdf
**Pfam**: Quick tour
https://www.ebi.ac.uk/training/online/course/pfam-quick-tour
-->

{% endif %}