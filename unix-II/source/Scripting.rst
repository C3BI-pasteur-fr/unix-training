.. _Scripting:


*********
Scripting
*********

make shortcut command
=====================

* We can create a short cut for a commande we repeat.
* A short cut for a command is an *alias*
* ``alias shortcut='command'`` 
  (no space surrounding the =)
* ``hgrep='history|grep'``

exercise:

* create a shortcut for command which extract the 
  bank:entryname from a blast report


make modification permanent
===========================

| Each time we modify the environment this modification
| is available only for the current terminal.
| To turn in permanent just put it in your .bashrc 

*.bashrc* is a file which is executed each time a terminal is created.

exercise 

#. make a copy of the *.bashrc* file
#. use vim to edit the *.bashrc* file and add the alias.


repeat an action
================

| Some times we need to repeat the same action *n* times with just a different details.
| for instance rename all files in a directory.
| for this we use a loop:

syntax: ::
 
   for var in list items
   do
      do something
   done

to be usefull we need :

* to set variable ``var=value`` (NO spaces surrounding =)
* to read variable ``$var``

example:
--------

remove '.fa' from all files terminating by 'fa.gde'
 
::
 
   for f in `ls il2*.fa.gde`
   do
      nam=`basename $f .fa.gde`
      mv $f $nam.gde
   done

exercise:
---------

#. copy the Proteique directory from the unix_training projets in central-bio in your local home
#. reformat all fasta file (*.fa* file) using squizz in *gde* format.
