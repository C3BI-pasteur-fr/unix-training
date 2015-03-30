.. _Module:


******
Module
******


why module
==========

* The softwares evolve very quickly in bioinformatics.
* The new versions give not always the same results.
* We need to have several versions installed at the same time.

what is module
==============

* *module* allow to load dynamically a package with a specified version on demand.
* *module* modify the environment dynamically.


what is available
=================

To know what package are available:
   
* ``module av`` display all available packages.
* ``module av bla`` display all available packages **begining** by *bla*
   

do a program available
======================

* ``module load package/vers`` load the package. 
* ``module list`` list all packages loaded in the environment.
* ``module unload package/vers`` unload a package.
* ``module purge`` unload all loaded packages.

get help on a module
====================

* ``module help package/vers`` display help about the package.

your own modulefiles
====================

Why write your own modulefiles

* ``share controled environment`` among your workmates
* ``share coherent programs and alias`` among your workmates
* ``set up specific tools and pipelines`` with control

* see ``man modulefile`` for the syntax to use. 

use your own private modulefiles
================================

* place your modulefiles under ``~/privatemodules``
* ``module load use.own`` your modulefiles wil be available for all module commands


use shared private modulefiles
================================

* place the modulefile under a directory with ``read permissions`` for all users you want to share.
* tell users to isue the command ``module use`` the given directory, they will gain acces to your modulefiles.

where is hide my program?
=========================


* ``whatprovides program`` list all package that provides the program.

exercises
 
* what modules provides blastp?
* load the right module.



module documentation
====================

* https://projets.pasteur.fr/projects/modules/wiki
