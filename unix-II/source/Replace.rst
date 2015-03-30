.. _Replace:


***************
replace pattern
***************

.. role:: red

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
* print lines

remove lines
------------

* **sed '#pattern#d'** 
* remove lines where pattern is present (*like grep -v*)

replace pattern
---------------

* **sed 'sSEPpatternSEPreplace' file**
* ``sed 's/chromosome/chr/' arrayAnnot.txt``
  replaces **only the 1st** occurence of *chromosome* by 'chr' in :red:`each line` of *arrayAnnot.txt*
* ``sed 's#chromosome#chr#' arrayAnnot.txt``
  does the same.
* ``sed 's/chromosome/chr/g' arrayAnnot.txt``
  replaces all occurences of *chromosome* by 'chr' in *arrayAnnot.txt*
* add the **-r** option to use extended regular expressions in the script
  (sometimes you should find -E)

expression
----------

* ``\w``  match word (alphanumeric and _) 
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
---------------------

#. use golden to get the sequences
#. transform each sequence in fasta format and concatenate them in one file 
#. run clustalw (``clustalw -align -infile=filename``)


print lines
-----------

* **sed '#pattern#p'** 
* print (duplicate) lines where pattern is present 

usually used in combination with *-n* option 

The "-n" option will not print anything unless an explicit request to print is found

**sed -n -e'#pattern#p'** will print only line containing pattern

Addresses
---------

Sed  commands  can  be  given with no addresses, 
in which case the command will be executed for all input lines
otherwise command will only be executed for input lines which match that address.


* **number** Match  only  the specified line number.
* **first~step** Match every step'th line starting with line first
* **$**  Match the last line.
* **/regexp/** Match lines matching the regular expression regexp.
 


Adresses examples
-----------------
  
* **sed '2p'** will duplicate the second line
* **sed -n '1~2p'** will print all the odd-numbered lines  
* **sed -n '2~5p'** will match every fifth line, starting with the second
* **sed -n '$p'** will print only the last line
* **sed -n '4,$p'** will print from the 4th to the last line (included)
* **sed '3,5s/t/T/g'** replace every t by T from the 3rd  to the fifth line
* **sed '/motif/s/line/sentence/'** => ??
* **sed '1!s/l/L/g'** => ??

:download:`sed_play.txt <_static/sed_play.txt>` .

Exercises
---------

Transform *brca.example.illumina.0.1.fastq* *fastaq* file in *fasta* 
(try your sed expression on *test.fastaq* before to use it on the real file)

step by step

#. print only header line (every 4th lines starting at the first line)
#. replace @ by > at the begining of every header
#. print every 4th lines starting at the second line

#. How to show second read in brca.example.illumina.0.1.fastq?

| http://www.grymoire.com/Unix/Sed.html
| `sed in bioinfo <https://emb.carnegiescience.edu/sites/emb.carnegiescience.edu/files/140602-sedawkbash.key_.pdf>`_ 