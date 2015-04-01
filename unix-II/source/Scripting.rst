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

#. copy the Proteique directory from the unix_training projets in **central-bio** in your **local** home
#. reformat all fasta file (*.fa* file) using squizz in *gde* format.

scripts
-------

* scripts are executables text files that contains:
* the instruction to execute.
* the flow control instructions.
* a ``sheebang`` that describe the interpreter to use, eg: ``#! /bin/bash``. the ``sheebang`` must be the first line of the script.

scripts arguments
-----------------

* ``$0`` name of the script
* ``$1, $2 ... $n`` positional arguments received by the script
* ``$#`` number of positional arguments received
* ``$@`` list of arguments


tests
-----

you will find 2 syntax for the test

* ``[ expression ]``
* ``test expression``

expression evaluate in true (0) or false (1)

syntax: ::

    var="hello"
    [ $var = "hello" ]
    echo $? 

==> 0 means true

syntax: ::

    var=3
    [ $var -eq 2 ]
    echo $? 

==> 1 means false

put test at work
----------------

syntax: ::

    #! /bin/sh

    # check if we got arguments
    if [ $# -eq  0 ] 
      then 
        echo "no argument provided: exit"
        exit 1
    fi

    # check if file exists
    if [ -f $1 ]
      then
        echo "file $1 exists"
        ret=0
      else
        echo "file $1 does not exists"
        ret=1
    fi
    
    # exit with significative return value
    exit $ret

