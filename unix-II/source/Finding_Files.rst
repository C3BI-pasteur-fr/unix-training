.. _Finding_Files:


*************
Finding files
*************

Find a file on the file system
==============================

**find** - search for files in a directory hierarch

* **find [paths]  EXPRESSIONS**
* **paths** = directories which are searched
* **paths** must precede expression

.. warning:: NEVER perform a find starting at / on the central storage.

| There are lots of criteria to find files.
| We will see just a few. 
| For a more complete expressions list: *man find*


Find a file or a directory
==========================

* **-type** restricts the search on the type of entries.
   * **f** regular file  
   * **d** directory
   * **l** symbolic link

::

   find . -type f


Find files by name
==================

* **-name pattern** Base of file name (the path with the leading directories removed) matches shell pattern pattern.  
* The metacharacters (``*``, ``?``, and ``[]``) are supported.

.. role:: red

:red:`Don't forget to enclose the pattern in quotes in order to protect it from expansion by the shell.`

* **-iname**  Like -name, but the match is case insensitive.

::
   
   find . -name '*.fasta'
   
   
Find files by date
==================

* **-atime n** File was last accessed n*24 hours ago.
  When find figures out how many 24-hour periods ago the file was last accessed, 
  any fractional part is ignored, so to match -atime +1, a file has to have been
  accessed at least two days ago.
* **-ctime n** File was created n*24 hours ago.  
* **-mtime n** File was last modified n*24 hours ago
* **-newer file_b** File was last modified more recently than file_b.

::

   #find every files which was read at most 3 days ago or  
   find . -atime 2
   #find every files created today
   find . -ctime 0
   
   
Find files by owner
===================

* **-user uname** File is owned by user uname (numeric user ID allowed)
* **-uid n** File's numeric user ID is n.

* **-group gname** File belongs to group gname (numeric group ID allowed).
* **-gid n** File's numeric group ID is n.


Find files and execute a command on the result
==============================================

* **-exec** specifies that the following command template should be executed
  for each matching file.

* **{}** is replaced by the current file name

* **\;** ends the command to execute

::
   
   #find each fasta file in my DataBio directory 
   #containing the string 'ABCD'
   find ~/DataBio -name '*.fasta' -exec grep -H ABCD {} \;

Exercises
=========

#. on your virtual machine, find all the files created on tuesday in your
   home directory.
#. on your virtual machine, find all the files containing IL2 sequences
   (rely on the header) and move them to a new directory: use **-exec**.
#. connect to central-bio and find all the files that are owned by one of
   your unit members in your unit directory.   
#. find file begining with il2 or IL2 but without extensions
   (HINT: **!** negates an expression for instance ``find . ! -type f`` match all link and dir)

Find files on a file system
===========================

.. warning::

   NEVER perform a find starting at / on the central storage.
