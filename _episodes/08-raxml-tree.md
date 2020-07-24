---
title: "Build RaxML Trees and Clean Up"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## Build a phylogenetic tree using RAxML

> ## Warning: Threads
> Do not use more threads (-T option) than available processors. Typically no more than 4 
> on a laptop and potentially many more on a cluster. NOTE: you can add a backbone 
> constraint tree with the option -g.  This should be done if clades within your group are 
> always monophyletic in the literature (e.g. in phylogenomic or multigene analyses), but 
> are not monophyletic in 18S trees. The sequences (tips) in this constraint tree must be 
> in your alignment (they should be a subset of your sequences), and the names must match 
> exactly.
{: .alert}

~~~
raxmlHPC-PTHREADS-SSE3 -T 4 -m GTRCAT -c 25 -p 31415 -x 20398 -d -f a -N 100 -n NAME -s current_DB.trim.fasta –w /full/path/to/output_directory
~~~
{: .language-bash}

> ## Alternative: Build tree using FastTree
> FastTree is very easy to install and gives you “quick and dirty” tree, in case you don’t 
> want to or can’t 
> wait for RAxML tree or in cases when the number of taxa is too high (more than several
> thousand).
> 
> ~~~
> fasttreeMP -gtr -nt current_DB.trim.fasta > NAME_fasttree.tre
> ~~~
> {: .language-bash}
{.callout}

{% include links.md %}