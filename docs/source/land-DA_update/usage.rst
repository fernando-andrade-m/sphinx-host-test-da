Usage
=====


Installation
------------

OPTIONAL: Install the JEDI fv3-bundle and IODA converters if you will be modifying, otherwise use the default installation.
**Note:** For tests to pass, you must have the same version that Clara has on hera.

Create links to JEDI files:
---------------------------

.. code-block:: console

    cd jedi/fv3-jedi/Data make_links.sh [ path-to-jedi-fv3-bundle-build ]
    cd ../../ioda make_links.sh [ path-to-jedi-ioda-bundle-src ] cd ../../../

Fetch submodules:
--------------------

.. code-block:: console

    git submodule update --init

Compile directories 
----------------------

.. code-block:: console

    cd add_jedi_incr build.sh cd .. cd IMS_proc/ build.sh cd ..

Running
-------
Edit settings file, edit ``submit_landDA.sh`` (your account details, your settings file)

.. code-block:: console

    sbatch submit_landDA.sh