.. _Archive_and_compressed_files:

**************************************
Archive, compress and uncompress files
**************************************

zip
===


``zip`` is a compression and file packaging utility 

* **zip zipfile file1 file2 ...** ::

   zip Nucleique.zip Nucleique/*
      adding: Nucleique/2Xseq.fasta (deflated 84%)
      adding: Nucleique/3_seq.fasta (deflated 57%)
      ...
      
.. warning:: zip dir.zip dir produce an empty zip file

exercice:

create a compress archive of all files in the Sequence/Proteique dir

unzip
=====

unzip - list, test and extract compressed files in a ZIP archive

* unzip -l zipfile list archive files.
* unzip -t zipfile test archive files. 
  This option extracts each specified file in memory and it's integrity.
* unzip zipfile 
* unzip -d dir zipfile specify a directory to which to extract files.
* ...

exercice:

list, test and uncompress the zip archive proteique.zip that you did.

gzip
====

.. role:: red

gzip compress files (:red:`does not make an archive!`)

exercise:

| execute *gzip Sequence/Proteique/* *
| what is the difference with zip ?

gunzip
======

* **gunzip  gzip_file** uncompress files (compress with gzip)
* **gunzip -c gzip_file** uncompress files, write output on standard output; keep original files unchanged. 

exercise:
   
uncompress the files in Sequence/Proteique/

bzip2
=====

* bzip2 is like gzip but with an other algorithm of compression.
* bunzip2 is like gunzip

create archive
==============

GNU ‘tar’ saves many files together into a single tape or disk archive.


tar -czf
tar -cjf

tar -tzf
tar -tjf

tar -xzf
tar -xjf

