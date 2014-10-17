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

| There is a lot of criteria to find files
| We will see just few. For complete expression list: *man find*


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

-name
-iname

Find file matching date
=======================

-atime
-mtime
-atime
-newer

Find file belonging someone
===========================

-user
-uid

-group
-gid



