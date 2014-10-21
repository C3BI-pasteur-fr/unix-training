.. _Backgrounding_tasks:


*******************
Backgrounding tasks
*******************

Job control
===========
* so far, all the tools we have used run interactively in your
  terminal: that means that while this tool runs, you cannot 
  use the terminal for anything else.
* task running in the terminal: **foreground job**.
* other tasks: **background jobs**.

Job control commands
====================
* start a task as a background job: 

::

   sleep 30 &

* stop the foreground job and return to the shell: [CTRL]+Z

* list the jobs attached to your terminal session

::

   jobs

Job control commands, continued
===============================

* run a backgrounded job

::

   bg %1

* bring a backgrounded job to the foreground

::

   fg %1

Job control
===========

* These commands are not meant for heavy load works. If you need to
  run and manage multiple heavy tasks, it's better to rely e.g. on a DRM.
