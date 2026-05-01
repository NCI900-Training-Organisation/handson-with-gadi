Modules
=======

.. admonition:: Overview
    :class: Overview

    **Tutorial:** 10 min

    **Objectives:**
    Learn how to find and load modules on Gadi.

Modules are how we manage software in most HPC machines. It provides a way to modify the user's environment to access required software packages. 

Gadi has a large array of software applications installed on its system. 
These are stored in ``/apps`` directory and can be accessed by loading the corresponding module. 


Module Commands
***************

We can see all the available modules using the command

.. code-block:: console
    
    module avail

To see all the versions of a module, we can use the command

.. code-block:: console

    module avail python3


If we want load a module *python3/3.11.0* we can use the command

.. code-block:: console

    module load python3/3.11.0

If we want to unload the same module use the command

.. code-block:: console
    
    module unload python3/3.11.0

We can unload all the modules using the command

.. code-block:: console
    
    module purge

Practice: Load the openmpi module
*********************************

To build and compile the program from our last practice (``hello_mpi.c``) into something that can run on Gadi, we need to use the module ``openmpi`` to help with the compilation.  

.. admonition:: Exercise
    :class: attention

    #. Check if the openmpi module is available, if so, which versions are available?
    #. Load the openmpi module verison ``4.1.5`` and check if it is loaded using the command ``module list``.
    #. Once successfully loaded, we can compile the program using the command 

    .. code-block:: console

        mpicc hello_mpi.c -o hello_mpi

    This will compile a binary file for you, named ``hello_mpi``. Check the binary file is created.
