.. _rte-rrtmgp:

Welcome to RTE+RRTMGP's documentation!
============================================

This is the documentation for the `repository <https://github.com/earth-system-radiation/rte-rrtmgp/tree/cec1e8e12d969c3c8c76574dbe4f40b366419cc7>`_ for RTE+RRTMGP, a set of codes for computing radiative fluxes in planetary atmospheres. RTE+RRTMGP is described in a `paper <https://doi.org/10.1029/2019MS001621>`_ in `Journal of Advances in Modeling Earth Systems <http://james.agu.org/>`_.

RRTMGP uses a k-distribution to provide an optical description (absorption and possibly Rayleigh optical depth) of the gaseous atmosphere, along with the relevant source functions, on a pre-determined spectral grid given temperatures, pressures, and gas concentration. The k-distribution currently distributed with this package is applicable to the Earth's atmosphere under present-day, pre-industrial, and 4xCO2 conditions.

RTE computes fluxes given spectrally-resolved optical descriptions and source functions. The fluxes are normally summarized or reduced via a user extensible class.

Example programs and documentation are evolving - please see examples/ in the repo and Wiki on the project's Github page. Suggestions are welcome. Meanwhile for questions please contact Robert Pincus and Eli Mlawer at **rrtmgp@aer.com**.

Contents
--------

.. toctree::
    :maxdepth: 2
    
    usage
    spectral-data


Recent Changes
--------------

#. The default method for solution for longwave problems that include scattering has been changed from 2-stream methods to a re-scaled and refined no-scattering calculation following `Tang et al. 2018 <https://doi.org/10.1175/JAS-D-18-0014.1>`_.

#. In RRTMGP gas optics, the spectrally-resolved solar source function in can be adjusted by specifying the total solar irradiance (``gas_optics%set_tsi(tsi)``) and/or the facular and sunspot indicies (``gas_optics%set_solar_variability(mg_index, sb_index, tsi)``)from the `NRLSSI2 model of solar variability <http://doi.org/10.1175/BAMS-D-14-00265.1>`_.

#. ``rte_lw()`` now includes optional arguments for computing the Jacobian (derivative) of broadband flux with respect to changes in surface temperature. In calculations neglecting scattering only the Jacobian of upwelling flux is computed. When using re-scaling to account for scattering the Jacobians of both up- and downwelling flux are computed.

#. A new module, ``mo_rte_config``, contains two logical variables that indicate whether arguments to routines are to be checked for correct extents and/or valid values. These variables can be changed via calls to ``rte_config_checks()``. Setting the values to ``.false.`` removes the checks. Invalid values may cause incorrect results, crashes, or other mayhem

Relative to commit ``69d36c9`` to ``master`` on Apr 20, 2020, the required arguments to both the longwave and shortwave versions of ``ty_gas_optics_rrtmgp%load()`` have changed.
