---
title: "Getting Started"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

(NOTE: Cover how to organize directory at start of project.)

## Choose group to curate
Your group should be of a manageable size in terms of taxonomic breadth and total available sequences (e.g. a subset of Rhizaria or diatoms rather than the entire clade). It will be more useful for you and EukRef in general to finish curation of a smaller group. You can expand later.

(NOTE: Provide test files so instructors / maintainers can run through and test lesson.)


Step 1 - Generate a curated starting sequence set, alignment, and tree for your group
This initial sequence set will form the basis of your entire curation effort. Therefore it is critical that these sequences are well-curated, and you need an alignment of these sequences and a reliable phylogenetic tree built from them. There are multiple ways to get this initial sequence set, but in each case, you should ensure it meets the criteria below. Additionally, you need a file that contains diverse outgroups: 5-10 sequences from all of the neighboring clades (e.g., if you are working on ciliates you should include apicomplexa, dinoflagellates, and stramenopiles). This alignment MUST be untrimmed (e.g. contain all gaps) so that additional sequences can be added. The initial tree must be checked to make sure it covers the diversity of the group and reflects phylogenetic relationships expected based on current research/literature.  Any errant sequences need to be removed from the alignment.

Criteria for the initial set of sequences, alignment, and tree:

- The initial set of sequences should be small, ~200 sequences or fewer, so that you can easily check the resulting alignment and tree.
- Sequences should cover the breadth of the clade, including divergent groups.
- The alignment and tree should have outgroups included to detect sequences that branch outside of your clade.
- The alignment should be untrimmed
- The tree produced from this alignment should display expected relationships and problematic sequences should be removed.

Three possible ways to get your initial alignment:

1. You may already have a curated starting alignment and tree from previous work. In this case, you are ready to go after checking your tree and alignment. Proceed to Step 5.
1. Download sequences from GenBank based on taxonomy. This will target the sequences from cultured isolates or those that were identified in other ways (e.g. morphologically identified and picked). Proceed to Step 2.
1. Alternatively, you may wish to start with the SILVA or PR2 set of sequences for your group. You must ensure that these sequences meet the criteria above. Proceed to Step 2.

{% include links.md %}
