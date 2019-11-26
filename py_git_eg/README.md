# README

Markdown contains example scripts from the tutorial, and my code and explainations (second half of document - denoted by ######)

This markdown contains the example scripts to accompany the manuscript.

[version]: https://www.authorea.com/users/5990/articles/17489/_show_article#article-paragraph-version__minus__your__minus__code__dot__tex-landing-welcome

## process.sh

`process.sh` downloads the ENCODE CTCF ChIP-seq data from multiple types of kidney samples and calls peaks.
The downloaded BAM files and [MACS2][] output are saved in tissue-specific subdirectories in `../data/`.
Run it as follows:

```bash
bash process.sh
```

You will need to have Python 2.7 installed because it is a [prerequisite][] for the peak caller [MACS2][].
To install MACS2, run:

```bash
pip install macs2
```

[prerequisite]: https://github.com/taoliu/MACS/blob/master/INSTALL.rst#prerequisites
[MACS2]: https://github.com/taoliu/MACS

## clean.py

`clean.py` filters peaks with a fold change cutoff and merges peaks from the different kidney samples.
It creates the file `../data/sites-union.bed`.
Run it as follows:

```bash
python clean.py
```

It can be run with either Python2 or Python3.
You will first need to install [bedtools][] and [pybedtools][].
See their documentation for instructions, but as an example, this can be accomplished on Ubuntu with the following:

```bash
apt-get install bedtools
pip install pybedtools
```

[bedtools]: http://bedtools.readthedocs.org/en/latest/content/installation.html
[pybedtools]: http://pythonhosted.org/pybedtools/main.html

## analyze.R

`analyze.R` creates diagnostic plots on the length of the peaks and their distribution across the genome.
It creates the file `../data/sites-union.pdf`.
Run it as follows:

```bash
Rscript analyze.R
```


######### Commands_Ass7_11004894_MG ####################

#All code in one block


```bash

#first configure git

git config --global user.name "HaplessHacker"
git config --global user.email "martingordon808@gmail.com" 

git init #ran in thesis directory to initialise git

git add py_git_eg/clean.py
git add py_git_eg/analyze.R
git add py_git_eg/process.sh #added the three files

git commit -m "Add initial version of thesis code."

git status

git log

nano clean.py , change fc_cutoff=10 to fc_cuttoff=20

git status 

git log 

git commit -m "Edited version of clean.py"

git push -u origin master #enter github username and password when requested

```


######## git log output ##########

(base) Martins-MacBook:py_git_eg martin$ git log
commit c5a8ca80a6a2e3c92ca4696529414c0a7b925169 (HEAD -> master)
Author: HaplessHacker <martingordon808@gmail.com>
Date:   Tue Nov 26 14:59:07 2019 +0000

    Edited version of clean.py

commit 9dd9d9d720ba488b7d5a9cf5e4b577194110f7f6 (origin/master)
Author: M. Gordon <martingordon808@gmail.com>
Date:   Tue Nov 26 11:54:46 2019 +0000

    Add initial version of thesis code

######### git diff output #####################

(base) Martins-MacBook:py_git_eg martin$ git diff
diff --git a/py_git_eg/clean.py b/py_git_eg/clean.py
index 9f76681..7f7ccf1 100644
--- a/py_git_eg/clean.py
+++ b/py_git_eg/clean.py
@@ -28,7 +28,7 @@ def filter_fold_change(feature, fc = 1):
         return False
 
 # Filter based on fold-change over control sample
-fc_cutoff = 10
+fc_cutoff = 20
 epithelial = epithelial.filter(filter_fold_change, fc = fc_cutoff).saveas()
 proximal_tube = proximal_tube.filter(filter_fold_change, fc = fc_cutoff).saveas()
 kidney = kidney.filter(filter_fold_change, fc = fc_cutoff).saveas()



############# github weblink ################

https://github.com/HaplessHacker/thesis/tree/master/py_git_eg
