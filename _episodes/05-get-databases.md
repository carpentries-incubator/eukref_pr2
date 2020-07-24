---
title: "Download Databases"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## Download and unpack databases

~~~
tar -xvf databases.tar.gz
~~~
{: .language-bash}

Inside the unpacked “databases” directory you will find three files: Reference_DB.fas and gb203_pr2_all_10_28_97p_noorg.fasta, and tax_d.bin.  These files are used for filtering results within eukref_gbretrieve.py. All three files must be in the current working directory where you run the eukref_gbrtrieve.py script in Step 6.


## Get GenBank nt database

Locate a copy of GenBank nt database in use at your institution or on your server. 
At the EukRef workshop there is a copy on the Amazon server. GenBank NT should ideally be downloaded to a server. There will be more than 40 files totaling more than 30 GB. Downloading can take several hours. You may wish to install and use a tool like wget.  In a workshop setting download one time and allow access for all participants.

Make a new folder called DATABASEFOLDER. From ftp://ftp.ncbi.nlm.nih.gov/blast/db/ download taxdb.tar.gz and all nt.tar.gz files. Also, download all nt_.tar.gz.md5 files.

Unpack with the following command:

~~~
for i in nt*; do tar -xvf $i ; done
~~~
{: .language-bash}

Run md5 checksum to ensure all files are fully downloaded.

(NOTE: Add explanation of what checksums are and instructions on how to run.)

## Export database

Before running the pipeline run the following commands

~~~
export BLASTDB=/path/to/DATABASE_FOLDER
~~~
{: .language-bash}

(you can also add BLASTDB to your PATH permanently)

(NOTE - Add instructions on how to modify PATH.)

{% include links.md %}