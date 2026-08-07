Lamba local machine
===================

The Lamba machine is a small machine available in the Computational Oncology group within the UMCG, meant for lighter calculations and development.
The machine is located in office G1.20 at the Triade building

.. image:: images/lambda/lambdamachine.jpg
   :alt: lambdamachine
   :width: 50%

.. _access:
Getting access to the Lambda machine
------------------------------------

Access to the Lambda machine is currently managed by Roy Oelen. Contact him to have an account created on this machine. Once he has created the account, you will be prompted to make a password upon first login.


.. _software:
Software on the Lambda machine
------------------------------------

The lamba machine has the basic data science software such as R/Python/Conda installed. If you need additional software or libraries, request these to be installed by one of the administrators. 


.. _working:
Working on the Lambda machine
------------------------------------

The machine is outfitted with four Nvidia RTX 2080TI GPUs, 64GB of RAM and a 20-core Intel i9-9820X and runs on Ubuntu 26.04 LTS. This allows the machine to handle quite some compute, but not at the level of the Habrok clusters or the Big Machines. It is therefore mainly meant to be used as a machine to develop and test on, not to run long and heavy analyses.

Storage is somewhat limited with only a PCIe 3.0 2TB SSD. To prevent unnecessary copies of the same data, there is shared storage under /home/shared. Please create projects and datasets in the correct folders there.


.. _known_issues:
Known issues
------------------------------------

There are some small issues with the machine that we are aware of

- the front USB ports can give overcurrent warnings. Please use the back USB ports.
- openBLAS is used instead of Intel MKL. Linking the superior Intel MKL is currently broken and the (still good but not as good) OpenBLAS implementation is used instead.

Please let the administrators know if you run into any more issues.
