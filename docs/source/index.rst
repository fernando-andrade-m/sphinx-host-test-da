.. Land DA documentation master file, created by
    sphinx-quickstart on Fri Sep 23 09:03:59 2022.

Welcome to Land DA's documentation!
===================================

Documentation on each of the Land DA's components is listed below.

.. note ::
    Development is currently underway on implementing ecbuild and CMake. 
    Usage of the Land DA system will change and should be simplified following this update.

Directory Structure
-------------------

Below is a shortened directory structure overview of the components. Subdirectories have been omitted unless they contain other Land DA components.

.. code-block::

    land-offline_workflow
    ├── DA_update
    │   ├── IMS_proc
    │   └── add_jedi_incr
    ├── ufs-land-driver
    │   └── ccpp-physics
    │       └── physics
    │           └── rte-rrtmgp
    └── vector2tile

Usage Overview
--------------
General order for usage of the Land DA Offline Workflow is as follows:

#. Clone the offline workflow repo and initiate submodules
#. Set up vector2Tile
#. Set up the UFS Land Driver and submodules
#. Set up DA_Update
#. Run and check the test

.. toctree::
    :hidden:

    Land Offline Workflow <land-offline_workflow/index>
    Vector2Tile           <land-offline_workflow/vector2Tile/index>
    UFS Land Driver       <land-offline_workflow/ufs-land-driver/index>
    CCPP Physics          <land-offline_workflow/ufs-land-driver/ccpp-physics/index>
    RTE-RRTMGP            <land-offline_workflow/ufs-land-driver/ccpp-physics/rte-rrtmgp/index>
    DA Update             <land-offline_workflow/land-DA_update/index>
    IMS Proc              <land-offline_workflow/land-DA_update/land-IMS_proc/index>
    


.. Vector2Tile           <land-offline_workflow/vector2Tile/index>
.. UFS Land Driver       <land-offline_workflow/ufs-land-driver/index>
.. DA Update             <land-offline_workflow/land-DA_update/index>

.. CCPP Physics          <land-offline_workflow/ufs-land-driver/ccpp-physics/index>
.. RTE-RRTMGP            <land-offline_workflow/ufs-land-driver/ccpp-physics/rte-rrtmgp/index>
.. IMS Proc              <land-offline_workflow/land-DA_update/land-IMS_proc/index>

Table of Contents
-----------------


#. :ref:`Offline Workflow <land-offline-workflow>`
#. :ref:`Vector2Tile <vector2tile>`
#. :ref:`UFS Land Driver <ufs-land-driver>`
#. :ref:`CCPP Physics <ccpp-physics>`
#. :ref:`RTE RRTMGP <rte-rrtmgp>`
#. :ref:`DA Update <land-DA-update>`
#. :ref:`IMS Proc <land-IMS-proc>`
