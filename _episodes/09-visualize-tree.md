---
title: "Visualize Your Tree and Remove Errant Sequences"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

Download your tree e.g. “RAxML_bestTree.clade”. Open tree in FigTree and annotate taxa with either “remove” for taxa you wish to remove, or you can modify/add to the existing name. You can only annotate taxa, NOT nodes or clades.  You can select entire clades to annotate all taxa at once. Annotated nodes cannot be collapsed (annotations within the collapsed node will not be reported). “Save as” the tree with annotations for example “RAxML_bestTree.clade_annotated.tre”, which is a nexus file.

(NOTE: Add screenshots illustrating how to do the above in FigTree)

Inputs:

-t RAxML_bestTree.clade_annotated.tre
-m metadata.txt

~~~
python eukref_treeparse.py -t RAxML_bestTree.clade_annotated.tre -m metadata.txt
~~~
{: .language-python}

Output:
metadata_out.txt

The “metadata_out.txt” will be your tab-delimited metadata file with “remove” in the last column for the sequences you want to remove.  You can sort your metadata_out.txt file in excel to get all of the accessions of sequences that should be removed from your tree. Save these accessions to be removed in a file called accessions_remove.txt.

Inputs:

-i current_DB.clustered.fasta
-s accessions_remove.txt

~~~
python eukref_filter_fasta.py -i current_DB.clustered.fasta -s accessions_remove.txt -o current_DB.cleaned.fasta
~~~
{: .language-python}

Output:

current_DB.cleaned.fasta

Go back to Step 7 to align and build a new tree, repeat until you are happy with your current set of sequences.


{% include links.md %}