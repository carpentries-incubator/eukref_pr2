---
title: "Build Reference Tree"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

Once you are happy with the set of sequences in your tree and your alignment you are ready to build your final reference tree. Your final, trimmed alignment is in input into RAxML. NOTE: you can add a backbone constraint tree with the option -g.  The sequences (tips) in this constraint tree must be in your alignment (they should be a subset of your sequences), and the names must match exactly.

~~~
raxmlHPC-PTHREADS-SSE3 -T 4 -m GTRCAT -c 25 -p 31415 -x 20398 -d -f a -N 100 -n NAME -s final_DB.trim
~~~
{: .language-bash}


{% include links.md %}