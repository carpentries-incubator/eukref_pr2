---
title: "Retrieve an Initial Set of Sequences and Cluster"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

> ## Similarity Threshold
> Users can choose a different similarity threshold if desired. For example, you may wish to work at 99% identity for small clades. In this case, 
> replace 0.97 with 0.99 throughout.
{: .callout}

> ## Your Clade
> In all commands, you must substitute your clade name for “NAME”.
{: .callout}

## Retrieve initial sequences

We offer three ways of doing this - using GenBank, PR2 or SILVA. We recommend using SILVA or PR2 database. Use the grep command to pull out your 
sequences of interest. Note that clade names often differ in these different databases.

~~~
grep –A 1 -i “NAME” silva_reference_database.fasta > NAME.fasta
~~~
{: .language-bash)

OR

~~~
grep –A 1 -i “NAME” PR2_reference_database.fasta > NAME.fasta
~~~
{: .language-bash)

> ## Alternative - GenBank
> Use advanced search at NCBI, or add the text below to the NCBI query box. Replace XXXX with the Taxonomy ID. Find the Taxonomy ID by searching NCBI 
> taxonomy:
> 
> ~~~
> txidXXXXOrganism:exp NOT (mitochondrial OR mitochondria OR complete genome)
> ~~~
> {: .source}
> 
> This will target targeted cultured isolates or isolates that were morphologically identified
> After you have downloaded your sequences, clean fasta headers to contain the GenBank accession number only.
> 
> ~~~
> sed 's/gi\|[0-9]*\|gb\|//' NAMEgb.fasta | sed 's/\..*//' > NAME.fasta
> ~~~
> (: .language-bash)
{: .callout}

## Cluster your sequences
Clustering will allow you to produce a manageable number of sequences using usearch (two commands). Similarity threshold is set at 97% here but can be 
adjusted by changing the “-id” command.  These commands choose the longest sequence as the representative sequence for each cluster. We will use also 
this step to remove sequences shorter than 500 bp. You will use these representative sequences for your initial alignment/tree.

~~~
usearch -sortbylength NAME.fasta -fastaout NAME.sorted.fasta -minseqlength 500 -notrunclabels
usearch -cluster_smallmem NAME.sorted.fasta -id 0.97 -centroids NAME.clustered.fasta -uc NAME.cluste
~~~
{: .language-bash}

{% include links.md %}

