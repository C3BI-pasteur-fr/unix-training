.. _Replace:


***************
replace pattern
***************

tr
==

* **tr**\ anslate
* replaces or removes characters (**NOT** strings) from its input dataset
  (standard input)

::

  tr 'a-z' 'A-Z' <allmysequences

* **-d** removes the characters

::

  tr -d '\r'

sed
===

* **s**\ tream **ed**\ itor for filtering and transforming text

sed read data (file or from pipe) and return the filtered data on the stdout.

the sed command is very versatile, so we just cover a few of its features.

The two commands to remember are: 

* remove lines
* replace patterns

remove lines
------------

* **sed '#pattern#d'** 
* remove lines where pattern is present (*like grep -v*)

replace pattern
---------------

* **sed 'sSEPpatternSEPreplaceSEP' file**
* ``sed 's/chromosome/chr/' arrayAnnot.txt``
  replaces **only the 1st** occurence of *chromosome* by 'chr' in *arrayAnnot.txt*
* ``sed 's#chromosome#chr#' arrayAnnot.txt``
  does the same.
* ``sed 's/chromosome/chr/g' arrayAnnot.txt``
  replaces all occurences of *chromosome* by 'chr' in *arrayAnnot.txt*
* add the **-r** option to use extended regular expressions in the script
  (sometimes you should find -E)

expression
----------

* ``\w``  match word (alphanumeric + _) 
* [0-9] digits


* keep only the field bank|accession number|entry_name (*sp|P80874|GS69_BACSU*)
* ``sed -r 's/.*\t(\w*\|\w*\|\w*).*/\1/g' blast2.txt`` 


Exercices
---------

#. Copy blast2_m8.txt from *projets* on central-bio in your local machine.
   Change the name of the bank *sp* into *uniprot*, in the *blast2_m8.t* file.
#. keep only the first field (like cut)
#. Clean the blast report to keep only the bank and the entry name like this:
   input:
   ``AK1BA_HUMAN sp|O08782|ALD2_CRIGR 83.23 316   53 0  1  316   1  316   0.0    537``
   output:
   ``sp:ALD2_CRIGR``

Exercises
---------

We want to create a file containing the sequences from the 10 most similar sequences to il2_human 
and align them (first step to modelize a sequence by homology).

#. get the il2_human sequence in fasta format
#. perform a blastp 
   (``blastall -p blastp -d uniprot_sprot -i the-input -m8``)
#. filter the output according the % of identity
#. keep the 10 best hit
#. reformat the line to keep only the bank and entry name in format (bk:entry_name)


Exercises (continued)
-----------------

#. use golden to get the sequences
#. transform each sequence in fasta format and concatenate them in one file 
#. run clustalw (``clustalw -align -infile=filename``)



