# NAMD_REST

REST (Replica Exchange Solute Tempering) Implementation in NAMD. The implementation is based on NAMD version 2.10. Various tests for verification of the implementation and actual examples are included in this repository.

This work has been published in [Compute. Phys. Comm.](http://dx.doi.org/10.1016/j.cpc.2015.08.030)

> A generic implementation of replica exchange with solute tempering (REST2) algorithm in NAMD for complex biophysical simulations. Sunhwan Jo and Wei Jiang. Computer Physics Communications. 2015. 197. 304-311. DOI:10.1016/j.cpc.2015.08.030

#------------------- MODIFIED BY JNGJIE YEO -------------------#
Please read "Compilation Instructions" provided in this git for details on how to merge this git with NAMD_2.10_Source.

A slightly-modified "rest2_remd.namd" has been provided to enable users who are familiar with NAMD's default "replica.namd" to run REST2 in a similar manner.

#------------------- MAIN DIFFERENCE FROM STANDARD TEMPERATURE REMD IN NAMD -------------------#
Other than the usual files for running temperature REMD, the user would need to provide an additional input file to specify the solute. This can be done by loading the desired .pdb file into VMD and do:
set sel [atomselect top "protein"]
$sel set beta 1.0
set sel [atomselect top "all not protein"]
$sel set beta 0.0
set sel [atomselect top "all"]
$sel writepdb spt.pdb

In the "rest2_base.namd" file, include the following commands:
spt						on
sptCol					B
sptFile					input/spt.pdb
sptScaleAll				no

For more details, simply refer to the examples provided in this git. It is also highly recommended to be familiar with running plain vanilla temperature REMD prior to attempting REST2.
