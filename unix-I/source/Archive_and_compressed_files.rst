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

* **unzip -l** zipfile list archive files.
* **unzip -t** zipfile test archive files. 
  This option extracts each specified file in memory and it's integrity.
* **unzip** zipfile 
* **unzip -d dir** zipfile specify a directory to which to extract files.
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

* **bzip2** is like gzip but with an other algorithm of compression.
* **bunzip2** is like gunzip

create archive
==============

GNU ‘tar’ saves many files together into a single tape or disk archive.

* as we work on file (not tape) all commands we use have file (-f) option
* -c to create an archive 
* **tar -cf archive.tar foo bar** 
  Create archive.tar from files foo and bar. ::
   
   tar -cf foo Nucleique/3_seq.*
   
* usually we add .tar extension to the archive name.

.. warning:: This archive is not compress

create archive
==============

* **-C** allow to change to directory DIR

exercise:

* go in Sequence directory and compare
   #. tar -cf archive Nucleique/3_seq.*
   #. tar -cf archive-C_option -C Nucleique 3_seq.*


create and compress an archive
==============================

* after creating an archive we can compress it with **gzip**
* but we can do this 2 operation with tar 
   
* use option -z or -j for compress with gzip or bzip2 respectively. ::
 
   tar -czf  my_seq.tar.gz Nucleique/*
   tar -cjf  my_seq.tar.bz2 Nucleique/*
   
* usually we use double extension *tar.gz* or *tar.bz2* .
* sometimes we use *.tgz* or *.tbz*

create and compress an archive
==============================
exercise:

* use gzip to compress *archive* and *archive-C_option*
* use the right options to do this in one operation (beware to the archive names).

list the content of an archive
==============================

To know what an archive contains use the **-t** option. ::

   tar -tzf archive.tar.gz
   tar -tjf archive.tar.bz2

   tar -tzf toto.tar.gz 
   Nucleique/
   Nucleique/qn1.gb
   Nucleique/qr.fasta
   Nucleique/collection_of_colstridium_genomesFASTA.txt
   ...

uncompress and restore an archive
=================================
 
To extract an archive use the **-x** option. 
To uncompress an archive use -z or -j option for gzip or bzip2 respectively. ::

   tar -xzf archive.tar.gz 
   tar -xjf archive.tar.bz2 
   
by default the extract is been wher the command is run
we can change this using **-C dir** option. ::

   tar -xjf archive.tar.bz2 -C Foobar

.. warning:: the dir must exists  


send an archive by mail
=======================

**F\*EX** is the dl service at pasteur

* **fexsend** is the command

#. register **fexsend -I** ::

      fexsend -I
      F*EX server URL: http://dl.pasteur.fr/
      proxy address (hostname:port or empty if none): 
      Your e-mail address as registered at http://dl.pasteur.fr/: nimort.naoik@pasteur.fr
      Your auth-ID for nimort.naoik@pasteur.fr at http://dl.pasteur.fr/: pick_an_id
      data written to /pasteur/homes/nnaoik/.fex/id
   
#. fexsend file recipient@domain.fr

send an archive by mail
=======================

exercise:

#. for those who have not a fex account go on http://dl.pasteur.fr/
   and request an account

#. log on central-bio.pasteur.fr
#. send you one of the archive you did using F\*EX

(documentaion: https://projets.pasteur.fr/projects/fex/wiki)

   
   