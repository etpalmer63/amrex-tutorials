.. role:: cpp(code)
   :language: c++

.. role:: fortran(code)
   :language: fortran

.. include:: <isonum.txt>


.. _tutorials_basic:

Basic
==========================

The tutorials in ``amrex_tutorials/ExampleCodes/Basic`` demonstrate the most fundamental
operations supported by AMReX.

**Hello World**
----------------

``HelloWorld_C`` and ``HelloWorld_F`` demonstrate the GNU Make system -- with
a sample Make.package and GNUmakefile -- and the :cpp:`amrex::Initialize`
and :cpp:`amrex::Finalize` functions.

In addition, in ``HelloWorld_C``, the :cpp:`amrex::Print()` operation,
which only prints from the I/O processor, is used to print out
the AMReX version (as defined by :cpp:`amrex::Version()`) being used.

``HelloWorld_F`` is a simple example of how to use the F_Interface routines,
which are Fortran wrappers for the underlying C++ data strutures and
iterators.  Here, for example, rather than calling :cpp:`amrex::Print()` in C++, we
test on whether :cpp:`amrex_parallel_ioprocessor()` is true, and if so, invoke
the usual Fortran print call.


**main**
--------

``main_C`` and ``main_F`` introduce the following:

1. By default, AMReX initializes MPI and uses MPI_COMM_WORLD as its communicator.
   However, applications could choose to initialize MPI themselves and pass in an
   existing communicator.

2. By default, AMReX treats command line arguments as inputs parameters.  The expected
   format of argv is,

   .. code-block:: console

      executable inputs_file parm=value

   Here, ``executable`` is the filename of the executable, ``inputs_file`` is the file containing
   runtime parameters used to build AMReX ParmParse database, and ``parm=value`` is an input
   parameter that will override its value in ``inputs_file``.  Both ``inputs_file`` and
   ``parm=value`` are optional.  At most one ``inputs_file`` is allowed. However, there can be
   multiple instances of ``parm=value``.

   The parsing of the command line arguments is performed in `amrex::Initialize`. Applications
   can choose to skip command line parsing.  Applications can also provide a function that
   adds parameters to AMReX ParmParse database.


**Heat Equation**
-----------------

The Heat Equation examples solve a 2D or 3D (determined by how you set DIM in the GNUmakefile)
heat equation explicitly on a domain-decomposed mesh. This example is described in detail in
the `Heat Equation`_ section of the Guided Tutorials.

.. _`Heat Equation`: https://amrex-codes.github.io/amrex/tutorials_html/HeatEquation_EX1_C.html#guided-heat

