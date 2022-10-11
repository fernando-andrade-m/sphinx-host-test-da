Usage
=====


Building the libraries, examples, and unit-testing codes
--------------------------------------------------------

#. Set environment variables ``FC`` (the Fortran 2003 compiler) and ``FCFLAGS`` (compiler flags). Examples are provided in the ``Compiler-flags.md file`` (:doc:`link <compiler-flags>`).

#. Set environment variables ``RRTMGP_ROOT`` to the top-level RTE+RRTMGP directory and ``RTE_KERNELS`` to ``openacc`` if you want the OpenACC/OpenMP kernels rather than the default.

#. ``make libs`` in the top-level directory will make the RTE and RRTMGP libraries.

#. The examples and testing codes use netCDF. Set the variables ``NCHOME`` and ``NFHOME`` to the roots of the C and Fortran netCDF installations, then ``make tests`` to build and run these. (A few files need to be downloaded for ``examples/rfmip-clear-sky``. The default is to download these with ``wget`` but a Python script is also available.)

#. Evaluating the results of the tests requires ``Python`` with the ``xarray`` package and its dependencies installed. Comparisons can be made with ``make check`` in the top level directory.

#. ``make`` invoked without a target in the top level attempts all three steps.

Examples
--------
Two examples are provided in **examples/**, one for clear skies and one including clouds. Directory tests/ contains regression testing (e.g. to ensure that answers are independent of orientation) and unit testing (to be sure all the code paths are tested). See the README file and codes in each directory for further information.

Clear Sky Example
^^^^^^^^^^^^^^^^^

**rfmip-rrtmgp**

This directory contains programs and support infrastructure for running the `RTE+RRTMGP <https://github.com/RobertPincus/rte-rrtmgp>`_ radiation parameterization for the `RFMIP <https://www.earthsystemcog.org/projects/rfmip/>`_ cases.

Note that this example is run, and the results checked automatically, when ``make`` is invoked in the root directory.

A Python script ``stage_files.py`` is used to download relevant files from the `RFMIP web site <https://www.earthsystemcog.org/projects/rfmip/resources/>`_.This script invokes another Python script to create empty output files.

Use Python script ``run-rfmip-examples.py`` to run the examples. The script takes some optional arguments, see ``run-rfmip-examples.py -h``

Python script ``compare-to-reference.py`` will compare the results to reference answers produced on a Mac with Intel 19 Fortran compiler. Differences are normally within 10-6 W/m2.

The Python scripts require modules ``netCDF4``, ``numpy``, ``xarray``, and ``dask``. Install with ``pip`` requires ``pip install dask[array]`` for the latter.

All Sky Example
^^^^^^^^^^^^^^^

This example provides a modestly more realistic setting the clear-sky problem done in the parallel ``rfmip-clear-sky`` directory in that it does an 'all-sky' calculation including both gases and clouds. It may be useful as a tutorial for users integrating RTE+RRTMGP into host models. We are also using it as a regression test for continuous integration and as a testbed for accelerators (currently GPUs using OpenACC).

The example uses the first of the Garand atmosphere used for developing RRTMGP, as described in the `paper <https://doi.org/10.1029/2019MS001621>`_ documenting the code, repeats the column a user-specified number of times, computes the optical properties of an arbitrary cloud in each column, and computes the broadband fluxes. Fractional cloudiness is not considered, and the clouds are extensive but quite boring, with uniform condensate amount and particle size everywhere (though with different values for liquid and ice).

Note that this example is run, and the results checked automatically, when ``make`` is invoked in the root directory.

Compiler Flags Index
--------------------

.. toctree::

    compiler-flags