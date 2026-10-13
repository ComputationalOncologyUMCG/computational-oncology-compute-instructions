Big Machines (BMs)
==================

The Big Machines (BMs) are a set of four machines, available to Computational Oncology Group within the UMCG, meant for heavy calculations. 


.. _access:
Getting access to the BMs
------------------------------------

Access to the BMs is through a secure connection within the UMCG network, making use of private/public keys for authentication. To get access, you first need to create private/public SSH key if you have not done so before. You can find documentaion on how this exactly works `here <https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent>`_.
In short, you can create an SSH key like this:

.. code-block:: bash

    ssh-keygen -t ed25519 -C "yourusername"

Saving it in the default location is completely fine. Make note of the filename of the generated keyfile.

By default, the key is saved in the .ssh folder. On Mac or Linux, you need to enable showing hidden files/folders to be able to find the file. There should be at least two files generated. The keyfile name and the keyfile name with .pub appended to the end. 
The .pub file is the public part of your key, that you can share to be granted access to machines. The other file is your private key, and you should never share with anyone. Send the PUBLIC part of your key to the administrator, so you can be granted access to the BMs.

In addition to the key, you also need to have the Global Secure Access Client application active to connect to the BMs. You can download this application `here <https://drive.google.com/file/d/1Ll7D3y5unLWARqTQXEgrRC6yb1wcbx9B/view?usp=drive_link>`_. Unzip the file and install the file for Windows or Mac OS.


.. _connect_cli:
Connecting to the BMs using command line SSH
--------------------------------------------

To connect to the BMs on the command line, or to use port forwarding to the BMs, you need to have set up your .ssh config correctly. On Mac/Linux/WSL, you can make use of this `zip <https://drive.google.com/file/d/1QeKTN3RGofhzrUYNcPYuqHXw_RpHOaRt/view?usp=drive_link>`_. Unzip it and put the CONTENTS into the .ssh folder in your home directory.

Your folder should en up looking like this:

.. image:: images/bigmachines/ssh_setup_bm.png
   :alt: ssh_setup_bm
   :width: 50%


This will then allow you to use the aliases bm1, bm2, bm3 and bm4 for logging in like:

.. code-block:: bash

    ssh bm1


.. _connect_gui:
Connecting to the BMs using a graphical interface
-------------------------------------------------

To connect to the BMs using a graphical user interface, you need to use the ThinLinc client application. You can download this `here <https://www.cendio.com/thinlinc/download/thinlinc-client-archive/>`_, or on Mac OS you can use `brew <https://formulae.brew.sh/cask/thinlinc-client>`_ to install it.

After installing, open the application. Select Advanced. Use the username that the administrator gave you and make the Key point to the private SSH key. The server needs be the IP address of the specific machine you want to connect to, which you can find further down the page.

.. image:: images/bigmachines/gui_setup_bm.png
   :alt: gui_setup_bm
   :width: 50%


.. _machines:
BM information
--------------------------------------------

These are the specifications of the different BMs

+---------+---------------+-----------------------------------+-------+-----------------------------------------+
| Machine | IP            | CPU                               | RAM   | GPUs                                    |
+=========+===============+===================================+=======+=========================================+
| BM1     |  145.39.86.19 | Intel Xeon 8160                   |  754G | 2 x NVIDIA Quadro RTX 8000 50GB         |
+---------+---------------+-----------------------------------+-------+-----------------------------------------+
| BM2     |  145.39.86.26 | Intel Xeon Gold 6258R             | 1024G | 2 x NVIDIA Quadro RTX 8000 50GB         |
+---------+---------------+-----------------------------------+-------+-----------------------------------------+
| BM3     |  145.39.86.23 | Intel Xeon Platinum 8380          | 2048G | 2 x NVIDIA RTX 6000 Ada 50GB            |
+---------+---------------+-----------------------------------+-------+-----------------------------------------+
| BM4     |  145.39.86.15 | AMD Ryzen Threadripper PRO 7985WX |  500G | 2 x NVIDIA RTX PRO 6000 Blackwell 100GB |
+---------+---------------+-----------------------------------+-------+-----------------------------------------+


.. _storage:
BM storage
--------------------------------------------

There is shared storage available on BM3 and BM4 at /home/shared/. Use this for joint projects and datasets, to make sure data is easy to find and not duplicated. This is not however fit for archiving, data that needs to be kept long-term, should be placed on the OneDrive.


.. _considerations:
Considerations
--------------------------------------------

The BMs are shared among the users in the Computational Oncology Group. They are not managed by any job schedulers like SLURM. This gives more flexibility and potentially reduces overhead, but does give the users more responsibility. There are some important considerations to keep in mind:

- do not fill the storage drives to capacity, this will cause the system to become unresponsive and eventually crash
- do not use applications that can change the network status or routing of the machine (such as possible in Docker compose). This will mess up ssh routing and make the machines unreachable.
- communicate with your colleagues that your are using resources on these machines, so they know what is available and what is not.
- try to estimate the amount of resources you will consume, and the amount of resources still available on the machine, to not crash process already running on the machine.
- due to an inpending grant deadline, it might be that one of your colleagues has taken up a majority of the resources on the big machines. Please be understanding of these situations, while also taking into consideration what would be fair use.
- only run work-related tasks on these machine unless you were granted permissions to do so. (No running your own Minecraft server or mining Bitcoins)


.. _rstudio_server:
Using RStudio Server on BMs
------------------------------------

Rstudio is available via an Rstudio-server image, with preloaded libraries, and can be updated easily by contacting the maintainer.

Log in to the bm with ThinLinc, or with ssh

.. code-block:: bash

    ssh bm1


Then open a screen session in the terminal when into the bm:

.. code-block:: bash

    screen -S rstudio_server


A screen session will open. We will use this screen session, so that we can easily return to it later.

Next, we can try to start Rstudio server. There is a small shell script available to do this.

.. code-block:: bash

    /home/shared/SingularityImages/start_server.sh


If you are running this the first time, it will tell you that you have not selected a port to run on yet. It will tell you to which file to add the port.

.. code-block:: text

    no port selected in /home/username/SingularityImages/rstudio_server/etc/rserver.conf, add 'www-port=[portnr]' as for example 'www-port=8701' by selecting an available port


And add **www-port=8701** with your actual port number. Then save and exit (CTRL+O, ENTER, CTRL+X). Now you can start the server again:

.. code-block:: bash

    /home/shared/SingularityImages/start_server.sh


The message it should now be giving you is:

.. code-block:: text

    TTY detected. Printing informational message about logging configuration. Logging configuration loaded from '/etc/rstudio/logging.conf'. Logging to '/home3/p1234567/.local/share/rstudio/log/rserver.log'.


Now if you connected via ThinLinc, you can immediatly use RStudio Server in the browser, by going to that port in your browser.

.. image:: images/habrok/rstudiobrowser.png
   :alt: rstudiobrowser
   :width: 80%


To view Rstudio server from a browser on your local machine, forward the port on your local machine (make sure you are using the correct port and bm):

.. code-block:: bash

    ssh -N -f -L localhost:8701:localhost:8701 bm1


And then, we can also use RStudio Server in the browser, by going to that port in your browser.

.. image:: images/habrok/rstudiobrowser.png
   :alt: rstudiobrowser
   :width: 80%


To stop an interactive session, and thus the rstudio server, go back to the bm and first see which screen sessions are running:

.. code-block:: bash

    screen -ls


This will show you the screen sessions that are running. You can then re-attach to the screen by its name or ID:

.. code-block:: bash

    screen -r rstudio_server


Kill the rstudio server with CTRL+C. Then type 'exit' again to exit the screen session.
