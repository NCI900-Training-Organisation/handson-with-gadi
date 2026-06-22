Using Python on Gadi
==========================

.. admonition:: Overview
    :class: Overview

    **Tutorial:** 10 min

    **Objectives:**
    Understand how to build a Python virtual environment on Gadi.


To run Python programs on Gadi, we recommend using the **Python module** and **virtual environments** to manage dependencies. 

.. note::

   Python packages are not typically centrally managed on HPC systems in the same way as software 
   installed in `/apps`, because the Python ecosystem evolves quickly and often requires different, 
   and sometimes conflicting, package versions across users and projects. While `/apps` is well suited 
   to stable, shared applications, Python workflows are highly flexible and user-specific, making a 
   single system-wide installation impractical.

A Python virtual environment is an isolated workspace that allows you to manage project-specific dependencies without affecting the global Python installation or other projects. By creating a 
virtual environment, you can install and manage libraries and packages independently, ensuring that each project has its own set of dependencies and 
avoiding version conflicts. This isolation helps maintain consistent and reproducible development environments.

The following commands will guide you on how to create one if necessary.

Create a Python Virtual Environment on Gadi
********************************************

To get started with Python virtual environment load the Python module you want to use.

.. code-block:: shell

    module load python3/3.11.0

Create the Python virtual environment.

.. code-block:: shell

    python3 -m venv my_env

Activate the Python virtual environment.

.. code-block:: shell

    source my_env/bin/activate

Install all the required Python packages.

.. code-block:: shell

    python3 -m pip install python-papi numpy codetiming numba mpi4py

You can deactivate the virtual environment once you are done with it.

.. code-block:: shell

    deactivate
 