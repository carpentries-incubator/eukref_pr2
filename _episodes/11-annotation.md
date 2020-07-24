---
title: "Annotation"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## Trim your metadata

Use the script eukref_metatrim.py Trim your metadata file to include only representative sequences of clusters – these are the sequences in your tree.

Inputs:

-i current_DB.cleaned.fasta is the fasta file with your clustered sequences containing only the sequences used in your reference tree.   -m metadata.txt is your metadata file from eukref_gbmetadata.py.

~~~
python eukref_metatrim.py -i current_DB.cleaned.fasta -m metadata.txt -o metadata_ref.txt
~~~
{: .language-python}


Outputs:

-o metadata_ref.txt, which only has the accessions in your reference tree. This will make annotating easier.

## Annotate classification

You need to annotate classification your metadata_ref.txt. Note that you should have GenBank taxonomy and SILVA taxonomy in your metadata_ref.txt file so you know the starting point. In many cases, it will be easiest to annotate clades directly on your reference tree. You can annotate the tree and then export annotations to your metadata_ref.txt file using the instructions below.

Download your reference tree e.g. “RAxML_bestTree.clade”. Open tree in FigTree and annotate taxa with the name of the taxon. You can only annotate the taxa, NOT nodes or clades.  You can select entire clades to annotate all taxa at once. Annotated nodes cannot be collapsed (annotations within the collapsed node will not be reported). “Save as” the tree with annotations for example “RAxML_bestTree.clade_annotated.tre”, which is a nexus file.

Run script eukref_treeparse.py to add annotations in your tree to your metadata_ref.txt file. 

Inputs:

-t RAxML_bestTree.clade_annotated.tre
-m metadata_ref.txt

~~~
python eukref_treeparse.py -t RAxML_bestTree.clade_annotated.tre -m metadata_ref.txt
~~~
{: .language-python}

Outputs:

The “metadata_ref_out.txt” will be your tab-delimited metadata file that includes the Accession Number of representative for your clusters and the annotations that you made on the tree in the last column.

## Expand your curation

Use the script eukref_metaexpand.py to expand your curation to all sequences within the clusters.

Inputs:

-i metadata.txt is the initial metadata file you got
-r metadata_ref_out.txt is the reference metadata you just added annotations to
-c current_DB.clusters.uc is the cluster file (.uc) from usearch. Use the most recent version if you clustered multiple times.

~~~
python eukref_metaexpand.py -i metadata.txt -r metadata_ref_out.txt -c current_DB.clusters.uc -o metadata_ref_expanded.txt
~~~
{: .language-python}

Outputs:

-o metadata_ref_expanded.txt is the expanded annotated metadata file

{% include links.md %}