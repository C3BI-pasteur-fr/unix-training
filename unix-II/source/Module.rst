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

where is hide my program?
=========================


* ``whatprovides program`` list all package that provides the program.

exercises
 
* what modules provides blastp?
* load the right module.



module documentation
====================

* https://projets.pasteur.fr/projects/modules/wiki