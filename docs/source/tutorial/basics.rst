Basics Linux Commands
----------------------

.. admonition:: Overview
   :class: Overview

    * **Tutorial:** 30 min

        **Objectives:**
            * Learn how to use Gadi terminal.
            * Learn some basic Linux commands.


File and Directory Management
********************************

`ls`: List files and directories.

Detailed list view with permissions, size, and timestamps:

.. code-block:: console
    :linenos:

    ls -l 

Show hidden files:

.. code-block:: console
    :linenos:

    ls -a

`cd`: Change directory to a specified directory.

Move to a specified directory.

.. code-block:: console
    :linenos:

    cd /path/to/directory

Move up one directory level:

.. code-block:: console
    :linenos:

    cd ..

Move to your home directory:

.. code-block:: console
    :linenos:

    cd ~

`pwd`: Print the current working directory.

.. code-block:: console
    :linenos:
 
    pwd

`mkdir`: Create a new directory.

.. code-block:: console
    :linenos:
 
    mkdir test

`touch`: Create a new file.

.. code-block:: console
    :linenos:
 
    touch test.txt

`rm`: Remove files or directories.

Remove files:

.. code-block:: console
    :linenos:
 
    rm test.txt

Remove directories:

.. code-block:: console
    :linenos:
 
    rm -rf test

`cp`: Copy files or directories

Copy file1 to file2:

.. code-block:: console
    :linenos:
 
    touch file1.txt
    cp file1.txt file2.txt

Recursively copy directory1 to directory2

.. code-block:: console
    :linenos:
 
    mkdir dir1
    cp -r dir2

`mv`: Move or rename files or directories.

Move files:

.. code-block:: console
    :linenos:
 
    mv file1.txt file2.txt

Move directories:

.. code-block:: console
    :linenos:
 
    mv dir1 dir2


Process Management
*******************

`top`: Display real-time information about system processes

.. code-block:: console
    :linenos:
 
    top

`ps`: List currently running processes

.. code-block:: console
    :linenos:
 
    ps -aux

`kill`: Terminate a process

.. code-block:: console
    :linenos:
 
    kill <pid>


File Transfer
*******************

`scp`: Securely copy files between local and remote systems.

Copy local_file to a remote path on Gadi

.. code-block:: console
    :linenos:
 
    scp local_file user@gadi.nci.org.au:/remote/path

Copy file from Gadi to the current local directory.

.. code-block:: console
    :linenos:

    scp user@gadi.nci.org.au:/remote/path/file .


Text Viewing and Editing
************************

`cat`: Display the contents of a file.

.. code-block:: console
    :linenos:

    cat file.txt

`less`: View file content page by page.

.. code-block:: console
    :linenos:

    less file.txt

`nano`: Simple text editor.

.. code-block:: console
    :linenos:

    nano file.txt

`vim`: Advanced text editor.

.. code-block:: console
    :linenos:

    vim file.txt







