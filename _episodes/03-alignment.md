---
title: "Building Initial Alignment"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## Assemble a set of close outgroup sequences

Outgroup sequences must be full-length. You should include outgroups from all of the clades that are neighbors to your group of interest, 5-10 sequences per group. These should be chosen based on your knowledge (ask for help if needed). You can get outgroup sequences from GenBank, SILVA or PR2. See step 2 for details. Add your outgroup sequences to clustered starting sequences (NAME.clustered.fasta file)

## Align using MAFFT.
Use the default MAFFT algorithm (command below) unless there is a specific reason to use a different algorithm or approach. (Experience users can use different preferred alignment program)

~~~
mafft --reorder --auto NAME.clustered.fasta > NAME_aligned.fasta
~~~
{: .language-bash}


> ## Alternative: Align using INFERNAL
>
> ~~~
> cmalign --outformat AFA -o NAME_aligned_infernal.fasta SSUref.cmm NAME.clustered.fasta
> sed 's/\./-/g' NAME_aligned_infernal.fasta > NAME_aligned.fasta
> ~~~
>{: .langauge-bash}
{: .callout}

> ## Alternative: Align using SINA*
> ~~~
> ./sina -i NAME.clustered.fasta -o NAME_aligned.fasta --outtype fasta --ptdb REFERENCE_ALN.ARB
> ~~~
> {: .language-bash}
> 
> If you choose to use SINA alignment, that you have to provide a reference
> alignment in ARB format. Easiest way to get one is to downloaded from 
> [SILVA's ARB database page](https://www.arb-silva.de/download/arb-files/).
{: .callout}


## Trim the alignment using trimal.

~~~
trimal -in NAME_aligned.fasta -out NAME.trimal.fasta -gt 0.3 -st 0.001
~~~
{: .language-bash}

{% include links.md %}