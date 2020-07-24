---
title: "Retrieve All Sequences That Belong To Your Clade"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## Retrieve sequences from GenBank database

The `eukref_gbretrieve.py` script script will run in a loop until no new sequences are retrieved. This may take several hours for large groups.

Inputs:

-i Unaligned fasta file of your clustered starting set of sequences (the output of Step 2, NAME.clustered.fasta). Should be refined version, with any errant sequences detected in tree inspection during Step 4 removed. Should NOT include outgroups. Fasta headers must either be in standard GenBank format (>gi|ginumber|gb|accession| ), or have the accession number followed by a space (>accession )
-dbnt (/path/to/DATABASE_FOLDER/nt)GenBank NT file from Step 5c . -dbsi (Reference_DB.udb)PR2 SSU reference database plus representative bacteria, used for filtering results. Must be in current working directory.
-n Number of sequences retrieved from GenBank per blasted sequence. recommended: 100
-p Number of CPUs.
-g Name of the most inclusive group you are working with from PR2 taxonomy. Find in the PR2 taxonomy file (ReferenceDB.fas) by grep.
-m Blast method. recommended: megablast
-idsi PR2 Blast cut-off (nothing less than 70% similar will be retrieved).
-idnt GenBank Blast cut-off (average similarity to everything on the original database).

Example command, update with your information.

~~~
python eukref_gbretrieve.py -i current_DB.fasta -dbnt /scratch/NCBI_NT/nt -dbsi ../../Reference_DB.fas -n 100 -p 8 -g NAME -m megablast -idsi 75 -idnt 90 -td tax_d.bin
~~~
{: .language-python}


Outputs:

Reference set of sequences (current_DB.fas).
Reference sequences with only accessions in header for downstream use (current_DB_final.fas).
List of accession numbers (accessions_current_DB.txt).
A fasta file of short reads (<500 bp), and of chimeras will also be generated.


## Format sequences and metadata
Run the `eukref_gbmetadata.py` script to pull taxonomy and environmental information from GenBank records to 1) generate your initial reference database, and 2) reformat the fasta headers for easier annotation in a tree.

First, download the GenBank format for all sequences retrieved in step 6a from NCBI batch entrez. Upload accessions ( accessions_current_DB.txt).  Click the retrieve records link.  Click “send to” then download as GenBank(full) file (.gb extension).  This will download the gb file for all of your accessions. Save as gb_metadata.gb

Inputs:

-gb Genbank flat file
-i fasta file output from step 6a (current_DB_final.fasta)
–outgroup outgroup fasta file
-t reference taxonomy file (pr2_4.11_full.txt)


~~~
python eukref_gbmetadata.py -gb gb_metadata.gb -i current_DB_final.fasta -o annotated_DB_for_tree.fasta -m metadata.txt -t /path/to/pr2_4.11_full.txt --outgroup outgroup_filtered.fasta
~~~
{: .language-python}

Outputs:

metadata.txt: metadata file (tab delimited format) that includes taxonomy from GenBank, reference taxonomy, environmental data available in the GenBank record, and the publication associated with an accession.
annotated_DB_for_tree.fasta: fasta file with headers labeled for easier curation. We will use the PR2 taxonomic strings or alternatively the GenBank taxonomic string if the sequence is not in PR2. The outgroup_filtered.fasta will be added as well to this fasta file.



{% include links.md %}