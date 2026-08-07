RUG HPC Habrok
==============

Habrok is the university High Performance Cluster (HPC). This cluster is set up to crunch many jobs, and is shared amoung RUG employees and students. It is meant for running your extensive pipelines that 

This cluster has its own documentation, so for details, please refer to that `page <https://www.rug.nl/society-business/center-for-information-technology/research/services/hpc/habrok>`_

.. _access:
Getting access to Habrok
------------------------------------

To get access to Habrok, you need an S-number (student) or P-number (staff). When you get your UMCG account, you should also receive an email that tells you instructions on how to activate your RUG account (which has your s/p-number).
Next, you can request a Habrok account `here <https://wiki.hpc.rug.nl/habrok/introduction/policies#getting_access>`_. 


.. _logging_in:
Logging into to Habrok
------------------------------------

There are a number of machines that can be logged into on Habrok. Again, for details go `here <https://wiki.hpc.rug.nl/habrok/connecting_to_the_system/connecting>`_. In short: 

- There are two login nodes where you can check your folders/files, as well as start jobs. The login nodes will quickly kill any process that is trying to use too much memory, and are NOT meant for calculations.
- There are also two interactive nodes which allow using more memory to test and develop your software/pipelines. They will however kill any processes that uses resources for an extended amount of time, and are thus NOT meant to run your full pipeline or full computation.
- There are finally two interactive GPU nodes, that allow you to test GPU-accelerated software/pipelines. Again, these will kill any processes that uses resources for an extended amount of time, and are thus NOT meant to run your full pipeline or full computation.

For long-running computations and pipelines, always request resources. Only use the interactive (GPU) nodes for testing and development.

To prevent having to memorize all the URLs for all nodes on Mac/Linux/WSL, you can make use of this `zip <https://drive.google.com/file/d/1QeKTN3RGofhzrUYNcPYuqHXw_RpHOaRt/view?usp=drive_link>`_. Unzip it and put the CONTENTS into the .ssh folder in your home directory. Then update the conf.d/01-common.conf file with a text editor to have your p/s number under User.
This will then allow you to use the aliases hblogin1, hblogin2, hbinter1, hbinter2, hbgpu1 and hbgpu2 for logging in like:

.. code-block:: bash

    ssh hblogin1


.. _data:
Data on Habrok
------------------------------------

The Computational Oncology group in the UMCG uses the hb-computational-oncology and hb-bioinfo-fehrmann groups. If you don't have access to these yet, please email your supervisor.
