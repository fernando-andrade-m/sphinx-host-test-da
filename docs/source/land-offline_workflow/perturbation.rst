Applying Perturbation Pattern
=============================

The **ensemble_part/** directory consists of code to apply the given perturbation pattern onto vectorized land surface variables.

We assume the perturbation pattern has been generated using the UFS `stochastic physics <https://github.com/pjpegion/stochastic_physics>`_ package and mapped to vector format used by the Noah-MP offline driver from the tile format used by the UFS atmospheric model with the following procedures.

**Documentation** for the **stochastic physics** package can be found `here <https://noaa-psd.github.io/stochastic_physics/>`_.

#. git clone the repo of the UFS `stochastic physics <https://github.com/pjpegion/stochastic_physics>`_ package:

    .. code-block:: console

        git clone https://github.com/pjpegion/stochastic_physics

#. run the UFS stochastic physics package to generate the perturbation pattern:

    .. code-block:: console

        cd stochastic_physics/unit_tests

    modify run_standalone.sh and run the script:

    #. modify SBATCH --account to the user account

    #. modify the resolution "RES"

    #. modify the INPUT directory, for an example, use the following directory

        **/scratch2/BMC/gsienkf/Tseganeh.Gichamo/stochastic_physics/unit_tests/INPUT**

    #. copy the INPUT directory or create a symbolic link

        .. code-block:: console
    
            ln -s /scratch2/BMC/gsienkf/Tseganeh.Gichamo/stochastic_physics/unit_tests/INPUT INPUT

    #. cp input.nml.template input.nml and made the following changes

    #. change lndp_var_list and iseed_lndp (the seed for randomization generator)

    #. n_var_lndp is the actual number of variables in lndp_var_list, change this value according to your choice.

#. map the perturbation pattern in tile format to the vector format

    go to the directory vector2tile and run the code to do the mapping

    The steps for applying the vectorized perturbation pattern onto land surface variables

#. compile the code on hera:

    .. code-block:: console
    
        configure

    choose hera

    load the modules indicated

    .. code-block:: console
    
        make

#. To run:

    .. code-block:: console
    
        cp template.namelist.lndp namelist.lndp

    modify namelist.lndp, the namelist defines the paths of the input/output files, the list of variables to be perturbed, and the perturbation magnitudes

    .. code-block:: console

        lndp_apply_pert.exe namelist.lndp


Zhichang Guo, Mike Barlage, Clara Draper. Aug 2022.