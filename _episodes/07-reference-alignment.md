---
title: "Build an Alignment with the Reference Sequences"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## Cluster sequences using usearch

~~~
usearch -sortbylength annotated_DB_for_tree.fasta -fastaout current_DB.sorted.fasta -minseqlength 64 -notrunclabels
~~~
{: .language-bash}

If the FASTA file to be clustered contains long (e.g. genomic) sequences, it is likely that the clustering step will run out of memory. Check the screen output of this “usearch -sortbylength” step, which indicates the length of the longest sequence found within the file; this should not exceed 5,000 (the hard limit imposed in Step 5).[/su_note]

NOTE: you should choose the -id (similarity threshold for clustering) that is appropriate for your group.


~~~
usearch -cluster_smallmem current_DB.sorted.fasta -id 0.97 -centroids current_DB.clustered.fasta -uc current_DB.clusters.uc -notrunclabels
~~~
{: .language-bash}

## Align using MAFFT

If there is not a specific reason to use a different approach to use the default mafft algorithm.  See instructions below for alignments with groups known to be difficult.

~~~
mafft --reorder --auto current_DB.clustered.fasta > current_DB_aligned.fasta
~~~
{: .langauge-bash}


> ## Alternative: Align using INFERNAL
> 
> ~~~
> cmalign --outformat AFA -o current_DB_aligned_infernal.fasta SSUref.cmm current_DB.clustered.fasta
> sed 's/\./-/g' current_DB_aligned_infernal.fasta > current_DB_aligned.fasta
> ~~~
> {: .language-bash}
{: .callout}


> ## Alternative: Align using SINA*
>
> ~~~
> ./sina -i NAME.clustered.fasta -o NAME_aligned.fasta --outtype fasta --ptdb REFERENCE_ALN.ARB
> ~~~
> {: .language-bash}
> 
> If you choose to use SINA alignment, that you have to provide a reference
> alignment in ARB format. Easiest way to get one is to downloaded from 
> [SILVA's ARB database page](https://www.arb-silva.de/download/arb-files/).
{: .callout}

It is critical to open and check your alignment in Aliview software (or similar) to see if there are misaligned blocks or sequences. Make sure you look at the entire length of the alignment. If the alignment is not good you will not produce a good tree.  If you have a poor alignment you can 1) align according to a template (seed) alignment, the command below, or 2) modify your alignment by hand.

If you already have a curated alignment for your group you can use it as a template (seed) to align your new sequences with the following command.

~~~
mafft --reorder --genafpair --maxiterate 1000 --retree --anysymbol --seed template_curated_alignment.fasta current_DB.OUTGROUP.clustered.fasta > current_DB_aligned.fasta
~~~
{: .language-bash}

Remember to open your alignment file and check before proceeding.

## Trim the alignment using trimal

~~~
trimal -in current_DB_aligned.fasta -out current_DB_trim.fasta -gt 0.3 -st 0.001
~~~
{: .language-bash}

{% include links.md %}
