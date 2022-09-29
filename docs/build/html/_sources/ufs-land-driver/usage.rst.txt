Usage
=====


Clone the ufs-land-driver repository:
-------------------------------------

.. code-block:: console

    git clone --recurse-submodules https://github.com/barlage/ufs-land-driver.git

Ensure your computer has a Fortran compiler and NetCDF software installed.


Navigate to your driver:
------------------------

.. code-block:: console

    cd ufs-land-driver

Configuration 
-------------

Create a ``user_build_config`` file.

.. code-block:: console

    ./configure

If not done by default, edit the ``user_build_config`` file to setup compiler and library paths to be consistent with environment.

**OPTIONAL:** If you'd like to use a different ``ccpp-physics`` directory from the one automatically downloaded with the clone, set the ``PHYSDIR`` in ``user_build_config`` to point to the top of the ``ccpp-physics`` directory (path relative to the mod directory).

Compile
-------

.. code-block:: console

    make

Running
-------

All the modules from **ccpp-physics** should be compiled in the ``mod`` directory, and all the drivers in the ``driver`` directory, and the executable is in the ``run`` directory.