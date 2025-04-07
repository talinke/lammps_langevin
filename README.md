# An Updated Formulation of the Langevin GJF Method in LAMMPS

## Authors

Tim Linke (UC Davis, LLNL), Niels Gronbech-Jensen (UC Davis)

This repository holds an adaptation from the LAMMPS software package.
It presents a clean and comprehensive form of the GJF method using the
splitting form, changing the langevin dynamics input from force 
evaluations to an integration of position and velocity.

## Main changes

We provide an updated formulation of the GJF method in the langevin framework. The fundamental functionality of the fix langevin is maintained, including the results obtained from the gjf option. In the new implementation, we have isolated noise and friction into two independent steps using the splitting formulation of the GJF method. This rewrite of the same algorithm allows a better integration with the NVE/fix langevin structure in LAMMPS. As a result, the new formulation solves several artifacts of the original implementation, including

* Restart glitch in restart using either vfull or vhalf
* Unnatural placing in input script of fix langevin gjf that differed from fix langevin
* Now allows for user to compare implementation directly to equations in publication

In addition, it improves memory performance, declutters the code by separating position and velocity treatment from force update and shortens code by 100+ lines.

## Implementation Notes

This fix is implemented by editing the files fix_langevin.cpp and fix_langevin.h. The documentation fix_langevin.rst is updated and now also clarifies correct attribution to the fix_langevin algorithm. The example/gjf files are updated, and new log files are provided. Correctness was verified via a direct comparison with the original implementation.


----------------------------------------------------------------------

## LAMMPS

LAMMPS stands for Large-scale Atomic/Molecular Massively Parallel
Simulator.

Copyright (2003) Sandia Corporation.  Under the terms of Contract
DE-AC04-94AL85000 with Sandia Corporation, the U.S. Government retains
certain rights in this software.  This software is distributed under
the GNU General Public License.

LAMMPS is a classical molecular dynamics simulation code designed to
run efficiently on parallel computers.  It was developed at Sandia
National Laboratories, a US Department of Energy facility, with
funding from the DOE.  It is an open-source code, distributed freely
under the terms of the GNU Public License (GPL) version 2.

The code is maintained by the LAMMPS development team who can be emailed
at developers@lammps.org.  The LAMMPS WWW Site at www.lammps.org has
more information about the code and its uses.

The LAMMPS distribution includes the following files and directories:

README                     this file
LICENSE                    the GNU General Public License (GPLv2)
CITATION.cff               Citation information for LAMMPS in CFF format
bench                      benchmark inputs
cmake                      CMake build files
doc                        documentation
examples                   example inputs for many LAMMPS commands
fortran                    Fortran 2003 module for LAMMPS
lib                        additional provided or external libraries
potentials                 interatomic potential files
python                     Python module for LAMMPS
src                        source files
tools                      pre- and post-processing tools
unittest                   test programs for use with CTest
.github                    Git and GitHub related files and tools
