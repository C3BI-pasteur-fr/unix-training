.. _File_System:

***********
File System
***********


File system
===========

* On unix there two important questions to ask before to do anything: 
   
   * who am I ?
   * where am I ?
   
.. rst-class:: build

   * who am I ? 
      * | We will see this later on this course.
        | For now you are the user "unix"
        
   * where am I ?

      * somewhere on the file system !
 

What is the file system
=======================

* Programs store data in files on disks.
* A file system is the way the files are stored on a disk.
* In Unix, the files are organized in a tree structure.

what is a "tree structure"?
===========================

do you already know a tree structure in biology?

.. rst-class:: build

   .. figure:: /_static/F1.large.jpg
      :class: align-center
      :width: 500px

file sytem tree structure
=========================

.. figure:: /_static/UnixDirectoryTree.png
      :class: align-center
      :width: 450px

.. ifnotslides::
   
   * file system is like a phylogenic tree: it's a hierarchical structure. 
   * ancestrors are replaced by directories and species by files.
   * so it contains directories that contains other directories and/or files.

* where am I?

.. rst-class:: build

      * in a directory.


what directory ?
================

* ``pwd`` (for **p**\ rint **w**\ orking **d**\ irectory)

.. rst-class:: build

   * /home/unix
   
   * This the coordinates of your current position.
   * But what does it mean?

   * To navigate, coordinates are not enough.
   * You need a map!


where am I on the map?
======================

This is my map!

.. figure:: /_static/local_file_system.png
      :class: align-center
      :width: 600px
      
* So now, I know where I'am.
* But know, I'd like to explore the map.


let's go for exploration
========================

* I need to know how to move.
* I need how to specify my destination.

* how to move?
    
    * ``cd``  (**c**\ hanging **d**\ irectory) 
    
* how to specify my destination?
   
   * two possibilities:
      
      * give absolute position of youre destination (same system of coordinates as pwd)
      * relative path
      
      
absolute path
=============

.. figure:: /_static/local_abs_path.png
   :class: align-center
   :width: 600px


File system on Pasteur server
=============================

.. figure:: /_static/home_abs_path.png
   :class: align-center
   :width: 600px
   
abolute path to home of user login_2 : /pasteur/homes/login_2
   