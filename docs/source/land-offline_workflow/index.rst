Land Offline Workflow Documentation
===================================


The `Land Offline Workflow repo <https://github.com/noaa-psd/land-offline_workflow>`_ includes script to run cycling DA using JEDI in cube sphere space, and offline Noah-MP model in vector space.

Clara Draper, Nov, 2021.

History Apr, 2022. Draper: Moved to PSL repo, restructuring and renaming of repos.

Contents
--------

.. toctree::

    Usage <usage>

Directory Structure
-------------------

Below is a shortened directory structure overview of the components. Subdirectories have been omitted unless they contain other Land DA components.

.. code-block::

    land-offline_workflow
    ├── DA_update
    │   └── IMS_proc
    ├── ufs-land-driver
    │   └── ccpp-physics
    │       └── physics
    │           └── rte-rrtmgp
    └── vector2tile
