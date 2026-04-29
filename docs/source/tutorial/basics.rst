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

.. code-block:: bash

    ls -l 

Show hidden files:

.. code-block:: bash

    ls -a

`cd`: Change directory to a specified directory.

Move to a specified directory.

.. code-block:: bash

    cd /path/to/directory

Move up one directory level:

.. code-block:: bash

    cd ..

Move to your home directory:

.. code-block:: bash

    cd ~

`pwd`: Print the current working directory.

.. code-block:: bash
 
    pwd

`mkdir`: Create a new directory.

.. code-block:: bash
 
    mkdir test

`touch`: Create a new file.

.. code-block:: bash
 
    touch test.txt

`rm`: Remove files or directories.

Remove files:

.. code-block:: bash
 
    rm test.txt

Remove directories:

.. code-block:: bash
 
    rm -rf test

`cp`: Copy files or directories

Copy file1 to file2:

.. code-block:: bash
 
    touch file1.txt
    cp file1.txt file2.txt

Recursively copy directory1 to directory2

.. code-block:: bash
 
    mkdir dir1
    cp -r dir2

`mv`: Move or rename files or directories.

Move files:

.. code-block:: bash
 
    mv file1.txt file2.txt

Move directories:

.. code-block:: bash
 
    mv dir1 dir2


Process Management
*******************

`top`: Display real-time information about system processes

.. code-block:: bash
 
    top

`ps`: List currently running processes

.. code-block:: bash
 
    ps -aux

`kill`: Terminate a process

.. code-block:: bash
 
    kill <pid>


File Transfer
*******************

`scp`: Securely copy files between local and remote systems.

Copy local_file to a remote path on Gadi

.. code-block:: bash
 
    scp local_file user@gadi.nci.org.au:/remote/path

Copy file from Gadi to the current local directory.

.. code-block:: bash

    scp user@gadi.nci.org.au:/remote/path/file .


Text Viewing and Editing
************************

`cat`: Display the contents of a file.

.. code-block:: bash

    cat file.txt

`less`: View file content page by page.

.. code-block:: bash

    less file.txt

`nano`: Simple text editor.

.. code-block:: bash

    nano file.txt

`vim`: Advanced text editor.

.. code-block:: bash

    vim file.txt







