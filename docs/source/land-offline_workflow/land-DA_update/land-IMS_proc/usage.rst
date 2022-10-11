Usage
=====


Input
-----------------

Inputs: IMS ascii file, IMS index file (generated offline). IMS index file is model resolution specific.

Output
------------

Output files include:

#. IMS-derived snow cover fraction over land on UFS model grid.

#. Snow depth derived form the IMS snow cover fraction, using an inversion of the noah model snow depletion curve.

Compiling 
------------

.. code-block:: console

    ./build.sh

Test case on hera: 

.. code-block:: console

    /scratch2/BMC/gsienkf/Clara.Draper/DA_test_cases/snow/fIMS


Test Case
---------

The **test case/** directory includes a test case for processing the IMS observations onto UFS model grid.

Running
^^^^^^^

.. code-block:: console

    submit_job.sh

This can be run from the login node.

Output
^^^^^^

Output file will look like **IMSfSCA.20191215.C48.nc** and should match files in **./output/**