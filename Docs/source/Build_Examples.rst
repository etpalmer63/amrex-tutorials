Building Examples with CMake
============================


A convenient method for building all the example codes at once is made 
possible using CMake. We will walk through the necessary steps here to
build the default collection of examples.


Building The Default Collection 
-------------------------------


Navigate to the ``ExampleCodes`` directory. In this directory, create a
build directory, called ``build``. In your build directory type,
::

  cmake ..

This will attempt to locate a previously install version of AMReX. If it 
cannot locate the package, it will clone and build the necessary AMReX files
from GitHub. 

.. admonition:: *Note:* Specifying AMReX Install Location

  Often it will be necessary to point CMake to the exact location of
  the ``AMReX_Config.conf`` file it order to use your installed version
  of AMReX. To do this, use the CMake compile flag, ``AMReX_ROOT`` as shown,
  ::

    cmake .. -DAMReX_ROOT=/path/to/amrex/installdir/<mroe here>

After CMake has configured the build, you can build the examples by typing,::
   
  cmake --build .

in the same build directory. This will build the selected example codes. They
should now be available in child directories. For example, with the default 
build, typing ``ls`` should show the following.
::

  Amr    CMakeCache.txt  cmake_install.cmake  ForkJoin       Makefile
  Basic  CMakeFiles      _deps                LinearSolvers

To find each executable, you can now simply navigate to the desired directory.

Building Other Examples
-----------------------

For examples not included in the default collection, specify the desired 
example as an option to CMake. For example, one can build the GPU examples
with,
::

  cmake .. -DAMReX_GPU=CUDA



