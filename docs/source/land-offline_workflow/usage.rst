Land Offline Workflow Usage
===========================


COMPILING and TESTING
---------------------

* Fetch sub-modules.

.. code-block:: console

    git submodule update --init --recursive

* Compile sub-modules.

.. code-block:: console

    cd vector2tile then follow instructions in README. cd ..

Vector2Tile
^^^^^^^^^^^
Compiling on hera
"""""""""""""""""

.. code-block:: console

   configure

select hera

Load Modules
""""""""""""

.. code-block:: console

   make

Running 
"""""""

.. code-block:: console

   vector2tile_converter.exe namelist.vector2tile

**Vector2Tile Details**:

The vector2tile pathway assumes that the vector file exists in the vector_restart_path directory and overwrites/creates tile files in the output_path

The tile2vector pathway is a little tricky, it assumes the tile files exist in tile_restart_path and overwrites only the snow variables in the vector file in the output_path. If the vector file does not exist in output_path, the process will fail.

The overall assumption here is that we will have a full model vector restart file, then convert the vector to tiles for only snow variables, and then convert the updated snow variables back to the full vector restart file

UFS Land Driver
^^^^^^^^^^^^^^^

.. code-block:: console

    cd ufs-land-driver
    git submodule update --init (if did not use --recursive flag above)

Configuration 
"""""""""""""

Create a ``user_build_config`` file.

.. code-block:: console

    ./configure

If not done by default, edit the ``user_build_config`` file to setup compiler and library paths to be consistent with environment.

**OPTIONAL:** If you'd like to use a different ``ccpp-physics`` directory from the one automatically downloaded with the clone, set the ``PHYSDIR`` in ``user_build_config`` to point to the top of the ``ccpp-physics`` directory (path relative to the mod directory).

Compile
"""""""

.. code-block:: console

    make

Running
"""""""

All the modules from **ccpp-physics** should be compiled in the ``mod`` directory, and all the drivers in the ``driver`` directory, and the executable is in the ``run`` directory.

DA Update
^^^^^^^^^

.. code-block::

    cd DA_update

Installation
""""""""""""

OPTIONAL: Install the JEDI fv3-bundle and IODA converters if you will be modifying, otherwise use the default installation.
**Note:** For tests to pass, you must have the same version that Clara has on hera.

Create links to JEDI files:
"""""""""""""""""""""""""""

.. code-block:: console

    cd jedi/fv3-jedi/Data make_links.sh [ path-to-jedi-fv3-bundle-build ]
    cd ../../ioda make_links.sh [ path-to-jedi-ioda-bundle-src ] cd ../../../

Fetch submodules:
"""""""""""""""""

.. code-block:: console

    git submodule update --init

Compile directories 
"""""""""""""""""""

.. code-block:: console

    cd add_jedi_incr build.sh cd .. cd IMS_proc/ build.sh cd ..

Running Offline Workflow
------------------------

Edit settings file, edit ``submit_landDA.sh`` (your account details, your settings file)

.. code-block:: console

    sbatch submit_landDA.sh










.. code-block:: console

    cd DA_update then follow instructions in README.
    
* Run the test.

in settings_cycle_test check WORKDIR and OUTDIR are OK create OUTDIR in submit_cycle.sh change #SBATCH --account=gsienkf to point to your own account.

.. code-block:: console

    submit_test.sh

Once completed:

.. code-block:: console

    check_test.sh


RUNNING YOUR OWN EXPERIMENTS
----------------------------

#. Prepare a settings file, using settings_template. Must fill in all variables, unless otherwise commented.

#. Set start and end dates in **analdates.sh**

#. Make sure there is a restart in your ICSDIR, and that the start date in analdates.sh match the restart.

    restart filename example:ufs_land_restart.2015-09-02_18-00-00.nc ICSDIR points to the experiment directory with the restart. If creating a new dircetory, the structure is: $ICSDIR/output/modl/restarts/vector/ufs_land_restart.2015-09-02_18-00-00.nc

#. in submit_cycle.sh change #SBATCH --account=gsienkf to point to your own account.

#. Submit your job

.. code-block:: console

    sbatch submit_cycle.sh your-settings-filename

.. toctree::

    perturbation