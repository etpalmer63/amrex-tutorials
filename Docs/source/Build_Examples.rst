Building Examples with CMake
============================

Building The Default Collection
-------------------------------

A convenient method for building many example codes at once is made
possible using CMake. We will walk through the necessary steps here to
build the default collection of examples.

Step 1: Create Build Directory and Configure
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Navigate to the ``ExampleCodes`` directory. In this directory, create a
build directory, called ``build``. In your build directory type,
::

  cmake ..

In calling this command, CMake will attempt to locate a previously install
version of AMReX. If it cannot locate the package, it will clone and build
AMReX from GitHub.

.. admonition:: *Note:* Specifying the Location of an AMReX Install

  To use a previously installed version of AMReX it is often necessary to 
  point CMake to the exact location of the installed ``AMReXConfig.cmake``
  file. To do this, use the CMake compile flag, ``AMReX_DIR`` as shown,
  ::

    cmake .. -DAMReX_DIR=/path/to/amrex/install_dir/
    

Step 2: Build Executables
~~~~~~~~~~~~~~~~~~~~~~~~~

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


The following tables contains the required flags for each example code. Please note that
these flags are not exclusive --adding additional flags may add additional functionality
to an example code.

.. table::

   +---------------------------------------+---------------------------------------------+
   | Example Code                          | Flags Required to Build                     |
   +---------------------------------------+---------------------------------------------+
   | *Amr*                                                                               |
   +---------------------------------------+---------------------------------------------+
   | Adevection_AmrCore                    | None                                        |
   +---------------------------------------+---------------------------------------------+
   | Adevection_AmrLevel - SingleVortex    | AMReX_FORTRAN=ON                            |
   +---------------------------------------+---------------------------------------------+
   | Adevection_AmrLevel - UniformVelocity | AMReX_FORTRAN=ON                            |
   +---------------------------------------+---------------------------------------------+
   | *Basic*                                                                             |
   +---------------------------------------+---------------------------------------------+
   | HelloWorld_C                          | None                                        |
   +---------------------------------------+---------------------------------------------+
   | main_C                                | None                                        |
   +---------------------------------------+---------------------------------------------+
   | HeatEquation_EX0_C                    | None                                        |
   +---------------------------------------+---------------------------------------------+
   | HeatEquation_EX1_C                    | None                                        |
   +---------------------------------------+---------------------------------------------+
   | HeatEquation_EX1_CF                   | AMReX_FORTRAN=ON                            |
   +---------------------------------------+---------------------------------------------+
   | HeatEquation_EX2_C                    | None                                        |
   +---------------------------------------+---------------------------------------------+
   | HeatEquation_EX2_CF                   | AMReX_FORTRAN=ON                            |
   +---------------------------------------+---------------------------------------------+
   | *Embedded Boundaries*                                                               |
   +---------------------------------------+---------------------------------------------+
   | CNS                                   | AMReX_EB=ON, AMReX_FORTRAN=ON               |
   +---------------------------------------+---------------------------------------------+
   | Possion                               | AMReX_EB=ON                                 |
   +---------------------------------------+---------------------------------------------+
   | MacProj                               | AMReX_EB=ON                                 |
   +---------------------------------------+---------------------------------------------+
   | GeometryGeneration                    | AMReX_EB=ON                                 |
   +---------------------------------------+---------------------------------------------+
   | *ForkJoin*                                                                          |
   +---------------------------------------+---------------------------------------------+
   | ForkJoin - Simple                     | None                                        |
   +---------------------------------------+---------------------------------------------+
   | ForkJoin - MLMG                       | AMReX_FORTRAN=ON                            |
   +---------------------------------------+---------------------------------------------+
   | *GPU*                                                                               |
   +---------------------------------------+---------------------------------------------+
   | CNS (GPU)                             | AMReX_GPU_BACKEND=[CUDA/SYCL/HIP]           |
   +---------------------------------------+---------------------------------------------+
   | *Linear Solvers*                                                                    |
   +---------------------------------------+---------------------------------------------+
   | ABecLaplacian_C                       | AMReX_LINEAR_SOLVERS=ON                     |
   +---------------------------------------+---------------------------------------------+
   | ABecLaplacian_F                       | AMReX_LINEAR_SOLVERS=ON                     |
   +---------------------------------------+---------------------------------------------+
   | NodeTensorLap                         | AMReX_LINEAR_SOLVERS=ON                     |
   +---------------------------------------+---------------------------------------------+
   | NodalPoisson                          | AMReX_LINEAR_SOLVERS=ON                     |
   +---------------------------------------+---------------------------------------------+
   | MAC_Projection_EB                     | AMReX_LINEAR_SOLVERS=ON, AMReX_EB=ON        |
   +---------------------------------------+---------------------------------------------+
   | Nodal_Projection_EB                   | AMReX_LINEAR_SOLVERS=ON, AMReX_EB=ON        |
   +---------------------------------------+---------------------------------------------+
   | MultiComponent                        | AMReX_LINEAR_SOLVERS=ON                     |
   +---------------------------------------+---------------------------------------------+
   | *Particles*                                                                         |
   +---------------------------------------+---------------------------------------------+
   | NeighborList                          | AMReX_PARTICLES=ON                          |
   +---------------------------------------+---------------------------------------------+
   | ElectrostaticPIC                      | AMReX_PARTICLES=ON, AMReX_SPACEDIM=2        |
   +---------------------------------------+---------------------------------------------+
   | ElectromagneticPIC                    | AMReX_PARTICLES=ON,                         |
   |                                       | AMReX_GPU_BACKEND=[CUDA/SYCL/HIP]           |
   +---------------------------------------+---------------------------------------------+
   | CellSortedParticles                   | AMReX_PARTICLES=ON, AMReX_FORTRAN=ON        |
   +---------------------------------------+---------------------------------------------+
