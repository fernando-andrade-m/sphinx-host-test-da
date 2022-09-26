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

.. toctree::
    
   testing