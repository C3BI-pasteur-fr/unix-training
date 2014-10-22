.. _Finding_In_Files:


**********************************
Finding inside files and filtering
**********************************

===============
Finding in file
===============

grep
====

**print lines matching a pattern**

* **-i** (--ignore-case) Ignore case distinctions in both the PATTERN and the input files.
* **-v** (--invert-match) Invert the sense of matching, to select non-matching lines. 
* **-r** (--recursive) Read all files under each directory, recursively, following symbolic links only if they are on the command line.

* **-n** (--line-number) Prefix each line of output with the 1-based line number within its input file.

Exercises
=========

* count the number of sequences in the file 'abcd.fa' (a multiple fasta file)
* can we have the same approach with a fastq file?

grep with Regular Expressions
=============================

* **grep -E** or **egrep**
* Regular Expressions: sequences of characters to express a pattern
* useful metacharacters:

  * **.** any character
  * **[]** bracket expressions
  * **^** start of the string
  * **$** end of the string
  * **\*** match 0 to *n* times the preceding element
  * **{m,n}** match *m* to *n* times the preceding element


=========================
Filtering/sorting results
=========================
 

cut
===

* **cut** - remove sections from each line of files
* ``cut OPTION... [FILE]``

* **-d DELIM**   use DELIM instead of TAB for field delimiter
* **-f** select only these fields

::

   who | cut -d ' ' -f 1 
   find . -atime 0 | cut -d '/' -f 2,3
   
sort
====

* **sort** - sort lines of text files
* ``sort [OPTION]... [FILE]``

* **-k** --key=KEYDEF sort via a key, KEYDEF gives location and **type**.
* **-n** (--numeric-sort) compare according to string numerical value (OBSOLETE).
* **-r** (--reverse) reverse the result of comparisons.

::
   swho | cut -d ' ' -f 1 | sort | uniq -c | sort -k 1n,2
   
exercise
--------

We ran a blast with -m8 output. So the following fields are displayed

| id, percent identity, alignment length, number of mismatches, 
| number of gap openings, query start, query end,
| subject start, subject end, 
| Expect value, HSP bit score

separated by ``tab``.

#. copy the file *blast2_m8.txt* in the project of the course in your home.
#. sort the output folowing the % of identity (the highest identity to the top)
#. display only columns id of hit, percent identity, Expect value, HSP bit score
#. store the results in a new file.


uniq
====

report or omit repeated lines (Filter :red:`adjacent` matching lines)

* **uniq [OPTION] INPUT**
* **-c** prefix lines by the number of occurrences.

exercise
--------

| from the same blast output than previous exercise. 
| display all sequences id that match with the query.

usefull commands
================

xargs
-----
 
build and execute command lines from standard input
xargs reads items from the standard input, delimited by blanks
or newlines, and executes the command with any initial-arguments 
followed by items read from standard input.

-I

tee
---

* tee copies its input stream to the standard output and the files
  specified in argument
