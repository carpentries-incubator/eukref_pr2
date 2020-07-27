---
title: "Build an Initial Tree"
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

~~~
raxmlHPC-PTHREADS-SSE3 -T 4 -m GTRCAT -c 25 -e 0.001 -p 31415 -f a -N 100 -x 02938 -n NAME -s NAME.trimal.fasta -w /full/path/to/output_directory
~~~
{: .language-bash}

Constraint trees: You can use a constraint tree in RAxML (-g option), which will allow you to “dictate” how some part of the tree should look like based on previously published relationships for your clade, for example, based on morphology and/or multigene phylogeny. Constraint trees should be used with caution and should ONLY constrain robust relationships (those observed in multiple studies) since it is desirable to avoid fitting the tree into your personal favorite topology. All taxa in the constraint tree must be in the alignment and names in the alignment an in the constraint tree must match exactly. Moreover, constraint tree cannot contain taxa not present in the alignment. Constrained trees can be edited in Mesquite.

> ## Alternative: Build tree using FastTree
> FastTree is very easy to install and gives you “quick and dirty” tree, in case you don’t 
> want to or can’t 
> wait for RAxML tree or in cases when the number of taxa is too high (more than several
> thousand).
> 
> ~~~
> fasttreeMP -gtr -nt NAME.trimal.fasta > NAME.tre
> ~~~
> {: .language-bash}
{ .callout}

## Visualize tree using FigTree.

Identify errant sequences to be removed. Go back to step 3 to refine alignment, remove errant sequences and repeat as necessary until you have a high quality starting initial alignment and tree. If your tree does not reflect known relationships you may wish to use a constraint tree in step 4a.  Proceed to step 5 once you are happy with your tree/alignment. You will need the unaligned set of sequences (without outgroups) as input for step 5 (initial_DS.fas).


{% include links.md %}
