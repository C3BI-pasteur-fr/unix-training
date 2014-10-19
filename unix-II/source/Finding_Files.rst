.. _Finding_Files:


*************
Finding files
*************

Find a file on file system
==========================

**find** - search for files in a directory hierarch

* **find [paths]  EXPRESSIONS**
* **paths** = directories which are searched
* **paths** must precede expression

.. warning:: NO FIND STARTING AT /

| There is a lot of criteria to find files.
| We will see just few. 
| For complete expression list: *man find*


find a file or dir
==================

* **-type** restrict the search on the type of entries.
   * **f** regular file  
   * **d** directory
   * **l** symbolic link

::

   find . -type f


Find file matching name
=======================

* **-name pattern** Base of file name (the path with the leading directories removed) matches shell pattern pattern.  
* The metacharacters (``*``, ``?``, and ``[]``) are supported.

.. role:: red

:red:`Don't forget to enclose the pattern in quotes in order to protect it from expansion by the shell.`

* **-iname**  Like -name, but the match is case insensitive.

::
   
   find . -name '*.fasta'
   
   
Find file matching date
=======================

* **-atime n** File was last accessed n*24 hours ago.  
  When find figures out how many 24-hour periods ago the file was last accessed, 
  any fractional part is ignored, so to match -atime +1, a file has to have been
  accessed at least two days ago.
* **-ctime n** File's data was created n*24 hours ago.  
* **-mtime n** File's data was last modified n*24 hours ago
* **-newer file** File was modified more recently than file.

::

   #find every files which was read at most 3 days ago or  
   find . -atime 2
   #find every files created today
   find . -ctime 0
   
   
Find file belonging someone
===========================

* **-user uname** File is owned by user uname (numeric user ID allowed)
* **-uid n** File's numeric user ID is n.

* **-group gname** File belongs to group gname (numeric group ID allowed).
* **-gid n** File's numeric group ID is n.


Find a file on file system
==========================

.. warning::

   NEVER perform a find starting at / on the central storage.