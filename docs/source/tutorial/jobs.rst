Requesting Resources
--------------------

.. admonition:: Overview
    :class: Overview

    **Tutorial:** 30 min

    **Objectives:**
        * Learn how to write a PBS job script for Gadi.
        * Learn how to launch a job in Gadi.

Planning Jobs
**************

To run compute tasks such as simulations, weather models, and sequence assemblies on Gadi, users need to submit them as **‘jobs’** to **‘queues’**. 
Each queue has different hardware capabilities and limits to run different types of jobs. Ideally, we should know the answers to the following questions before running a job:

::

   1.  Which project will you use for this job?
   2.  Which queue will you submit the job to?
   3.  How many CPU cores does your task require?
   4.  Do you need any GPUs, and if so, how many?
   5.  What is the anticipated runtime (walltime) for your job?
   6.  Which modules must be loaded for your software?
   7.  What command or script will run your main program?

However, this is not always possible, especially for new users or running a new workflow for the first time. In this case, we can follow the following steps:

#. **Gather information:** Find out the available queues, and software modules to run your program.
#. **Run test jobs:** use a small sample of the data and small number of cores/walltime to test the script/program.
#. **Adjust resources:** gradually increase the resources and improve code efficiency to find the performance sweet spot.
#. **Accounting:** check your project allocation and estimate the cost (time, RAM, compute cores etc.) of full job.
#. **Full run:** run the job with the full dataset and monitor the job status.

.. note:: 

    The sweet spot is where the job can take advantage of parallelism and achieve a shorter execution time, while **utilising at least 80% of the resources requested**. 

    Searching for this sweet spot can take time and experimentation, some code will need several iterations before that efficiency is found.     

 
Running Batch Jobs
********************

The overall procedure to run a job on Gadi takes a few steps:

1.  Write a job script (where you specify the **queue, duration, and resource** needed).
2.  Submit the job script to the queue 
3.  Monitor the job status (**If the job uses more than it requested, it will be terminated immediately.**)
4.  View the job output and error files (by default, they will be saved in the directory you submitted the job from)
5.  Cancel the job if needed



.. note::

    **Batch jobs**

    A batch job is a non-interactive job submitted to the scheduler (like PBS or SLURM) to run at a later 
    time. It executes your code or script without requiring your direct involvement during execution.

To run a batch job on Gadi, users need to create a PBS script. The script is a text file formed of two sections: **resource requests** and **job steps**. 
Resource requests involves specifying the required number of CPUs/GPUs, expected job duration, amounts of RAM, disk space, and so on. 
Job steps involves shell commands of what needs to be done (i.e. loading environment/software modules, running computing steps, parameter space, etc.).

Here is an example of a PBS script:

.. code-block:: bash
    :linenos:

    #!/bin/bash

    #PBS -P vp91 
    #PBS -q normal
    #PBS -l ncpus=48
    #PBS -l mem=10GB
    #PBS -l storage=gdata/vp91+scratch/vp91
    #PBS -l walltime=00:02:00
    #PBS -N testScript
    #PBS -l wd

    module load python3/3.11.0
    module load papi/7.0.1

    . /g/data/vp91/Training-Venvs/intro-to-numba/bin/activate
    which python

    python3 main.py $PBS_NCPUS> /g/data/vp91/$USER/job_logs/$PBS_JOBID.log

#. Specifies which shell to use
#. **-P** - Gadi project (sometimes called account) to use
#. **-q** - Gadi queue to use
#. **-l ncpus** - Total number of cores requested
#. **-l ngpus** - Total number of GPUs requested
#. **-l mem** - Total memory requested
#. **-l storage** - Storage in ``g/data`` and ``/scratch`` to come from project ``vp91``
#. **-l walltime** - Total wall time for which the resources are provisioned (in hours:minutes:seconds)
#. **-N** - Name of the job 
#. **-l wd** - Enter the working directory once the job has started.

.. note::

   For more PBS directives, see the `PBS directive list <https://opus.nci.org.au/display/Help/PBS+Directives+Explained>`_. 
   
   Check `queue limit page <https://opus.nci.org.au/spaces/Help/pages/236881198/Queue+Limits...>`_ for core numbers, memory and walltime limits.
   
   For different Gadi queues, see the `queue structure page <https://opus.nci.org.au/display/Help/Queue+Structure>`_.

Practice: Write a PBS job script
********************************

.. admonition:: Exercise
    :class: attention

    To run our compiled ``hello_mpi`` program on Gadi, we need to wrap it in a PBS job script:

    #. Go to ``/scratch/vp91/$USER/first_job``.
    #. Inside ``first_job``, create new file ``job_script.sh`` and paste the template below, change ``<Project code>`` to ``vp91``, and save.

    .. code-block:: bash
       :linenos:

       #!/bin/bashs

       #PBS -P <Project code>
       #PBS -q normal
       #PBS -l ncpus=4
       #PBS -l mem=16gb
       #PBS -l walltime=00:10:00

       module load openmpi/4.1.5
       mpirun hello_mpi


Submit and Monitor Jobs
************************

Once you have saved this script as a '.sh' file, you will be able to submit it using the 'qsub' command, followed by the file name.

To submit a job use the command

.. code-block:: bash

    qsub <jobscript.sh>

After your job has been successfully submitted, you will be given a **jobID** (e.g. 12345678.gadi-pbs). You can use this **jobID** to monitor the status of your job.

To know the status of your job use the command

.. code-block:: bash

    qstat <jobid>

To know get the details about the job use the command

.. code-block:: bash

    qstat -swx <jobid>

We recommend checking the Job Monitor regularly to ensure that your jobs are running efficiently, especially if you are running a new workflow for the first time.

When the job is completed, it will produce two new text files in the working directory, with a filename ``script.sh.o<JobID>`` and ``script.sh.e<JobID>``. 

The first file, with 'o' in the file name, is the output of the job, which should have run successfully on Gadi. 

The second file, with 'e' in the file name, is the error stream. this will document any errors that occured while the job was running. In this case, the error stream file should be empty. 

Practice: Submit and Monitor Your First Job
********************************************

.. admonition:: Exercise
    :class: attention

    #. Submit the job script you created in the previous exercise.
    #. Check the status of the job using the `qstat` command.
    #. Check the output and error stream of the job using the `less` command.
    #. Use other commands to check the job status and utilisation of resources.

Other monitoring commands
===================================

+-----------------------------+-----------------------------------------------------------------------+
| Command                     | Description                                                           |
+=============================+=======================================================================+
| man qstat                   | View the manual for qstat and a range of helpful commands             |
+-----------------------------+-----------------------------------------------------------------------+
| qdel <jobid>                | Delete the job with jobID <jobid>                                     |
+-----------------------------+-----------------------------------------------------------------------+
| nqstat_anu <jobID>          | See how much CPU and memory your job has actually been using          |
+-----------------------------+-----------------------------------------------------------------------+
| qstat -swx <jobid>          | Display the job status in the queue with comment                      |
+-----------------------------+-----------------------------------------------------------------------+
| qstat -fx <jobid>           | Display full job status information                                   |
+-----------------------------+-----------------------------------------------------------------------+
| qps <jobid>                 | Take a snapshot of the process status of all current processes        |
|                             | in the running job                                                    |
+-----------------------------+-----------------------------------------------------------------------+
| qcat [-s/-o/-e] <jobid>     | Display [submission script/STDOUT/STDERR] of the running job          |
+-----------------------------+-----------------------------------------------------------------------+
| qls <jobid>                 | List contents in the folder $PBS_JOBFS                                |
+-----------------------------+-----------------------------------------------------------------------+
| qcp <jobid> <dst>           | Copy files and directories from the folder $PBS_JOBFS to              |
|                             | the destination folder <dst>                                          |
+-----------------------------+-----------------------------------------------------------------------+



Interactive Jobs
********************

An interactive job allows you to interact directly with the HPC system and the job while it's 
running. This means you have a command-line shell (e.g., terminal) on the compute node where you 
can run commands in real-time. NCI recommends that users utilise this resource to debug large parallel jobs or install applications that have to be built when GPUs are available.  

``qsub -I`` is the command to request an interactive job.

.. code-block:: bash

    qsub -I -q normal  -P vp91 -l walltime=00:10:00,ncpus=4,mem=10GB


.. admonition:: Hint
    :class: hint

    Check your shell prompt before and after running the command. Why did it change?

    .. dropdown:: See answers

        Your access changed from the login node to the compute node during the interactive session.


Once you are finished with the job, run the command

.. code-block:: bash

    exit

to terminate the job.


.. admonition:: Key Points
   :class: hint

    #. Multiple PBS directives are available request a job.
    #. Gadi uses some custom directives.
    #. There are two modes to request a job - batched and interactive. You can also use interactive jobs to test your script/program.

