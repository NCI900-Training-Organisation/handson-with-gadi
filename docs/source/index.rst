Handson with Gadi
===========================================

Overview
--------

This workshop provides an  introduction to basic command-line operations and guidelines for working 
efficiently on Gadi, the high-performance computing (HPC) machine at the National Computational 
Infrastructure (NCI).

.. admonition:: Learning Outcomes
   :class: note

   By the end of this course, participants will be able to:

   1. **Navigate Gadi’s Architecture:** Identify the key components of the Gadi supercomputer and select the appropriate file system (scratch, home, or project) for different stages of their project.

   2. **Operate in a Remote HPC Environment:** Confidently use the Australian Research Environment (ARE) to access Gadi via web-based interfaces, including Jupyter Notebooks and Virtual Desktops.

   3. **Use the Command Line Interface:** Perform essential remote file management and text editing using Linux commands tailored for a high-performance computing context.

   4. **Manage Computational Jobs:** Write and submit batch scripts to the job scheduler, and differentiate between interactive and batch modes to optimize resource usage.

   5. **Utilise Specialised Hardware:** Configure ARE sessions to request and utilise GPU resources for accelerated computing tasks in Jupyter and desktop environments.

   6. **Apply HPC Best Practices:** Navigate NCI’s specific queues and resource limits to ensure efficient job execution and collaboration within the Australian research ecosystem.

.. admonition:: Prerequisites
   :class: attention

   1. Know how to use a computer. 
   2. Familiar with Linux command line interface is recommended, but we will cover the basics in the workshop.

.. list-table:: Suggested Workshop Agenda
  :widths: 58 42
  :header-rows: 1

  * - Topics
    - Duration
  * - Introduction to HPC, NCI and Gadi
    - 20 minutes
  * - Logging in to Gadi
    - 10 minutes
  * - Navigating Gadi File System
    - 30 minutes
  * - Modules
    - 10 minutes
  * - Using Python on Gadi
    - 10 minutes
  * - Requesting Resources
    - 30 minutes
  * - Run Jupyter Notebooks on Gadi
    - 20 minutes
  * - Virtual Desktop in ARE
    - 10 minutes
  * - **Total**
    - **140 minutes**


Contents
--------

.. toctree::
  :maxdepth: 1
  :caption: Before the Workshop

  access_and_setup.rst

.. toctree::
  :maxdepth: 2
  :caption: Tutorials
  :numbered:

  tutorial/hpc.rst
  tutorial/login.rst
  tutorial/basics.rst
  tutorial/modules.rst
  tutorial/packages.rst
  tutorial/jobs.rst
  tutorial/use-jupyterlab.md
  tutorial/are_desktop.rst
   
.. toctree::
  :maxdepth: 1
  :caption: References

  references

