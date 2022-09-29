Land Offline Workflow Usage
===========================


COMPILING and TESTING
---------------------

#. Fetch sub-modules.

    .. code-block:: console

        git submodule update --init --recursive

#. Compile sub-modules.

        .. code-block:: console

            cd vector2tile then follow instructions in README. cd ..

        .. code-block:: console

            cd ufs-land-driver
            git submodule update --init (if did not use --recursive flag above)
            configure

        select hera, load indicated modules

        .. code-block:: console
    
            make


        .. code-block:: console

            cd DA_update then follow instructions in README.
    
#. Run the test.

    in settings_cycle_test check WORKDIR and OUTDIR are OK create OUTDIR in submit_cycle.sh change #SBATCH --account=gsienkf to point to your own account.

    .. code-block:: console

        submit_test.sh

    Once completed:

    .. code-block:: console

        check_test.sh


RUNNING YOUR OWN EXPERIMENTS
----------------------------

#. Prepare a settings file, using settings_template. Must fill in all variables, unless otherwise commented.

#. Set start and end dates in analdates.sh

#. Make sure there is a restart in your ICSDIR, and that the start date in analdates.sh match the restart.

    restart filename example:ufs_land_restart.2015-09-02_18-00-00.nc ICSDIR points to the experiment directory with the restart. If creating a new dircetory, the structure is: $ICSDIR/output/modl/restarts/vector/ufs_land_restart.2015-09-02_18-00-00.nc

#. in submit_cycle.sh change #SBATCH --account=gsienkf to point to your own account.

#. Submit your job

.. code-block:: console

    sbatch submit_cycle.sh your-settings-filename

.. toctree::

    perturbation