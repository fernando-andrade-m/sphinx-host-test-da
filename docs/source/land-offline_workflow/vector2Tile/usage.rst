Usage
=====


Compiling on hera
-----------------

.. code-block:: console

   configure

select hera

Load Modules
------------

.. code-block:: console

   make

Running 
-------

.. code-block:: console

   vector2tile_converter.exe namelist.vector2tile

**Details**:

The vector2tile pathway assumes that the vector file exists in the vector_restart_path directory and overwrites/creates tile files in the output_path

The tile2vector pathway is a little tricky, it assumes the tile files exist in tile_restart_path and overwrites only the snow variables in the vector file in the output_path. If the vector file does not exist in output_path, the process will fail.

The overall assumption here is that we will have a full model vector restart file, then convert the vector to tiles for only snow variables, and then convert the updated snow variables back to the full vector restart file