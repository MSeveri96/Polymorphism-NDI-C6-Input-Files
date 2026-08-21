# Polymorphism-NDI-C6-Input-Files

This repository contains all the input files used in "TITLE", DOI.

The files are organized in the following manner:

## Pristine Alpha and Pristine Gamma

The directories containing the files for the simulations of pristine alpha and gamma, are "pristine_alpha" and "pristine_gamma". The simulation cells are 5x5x5 supercell and have been constructed with Moltemplate by appropriate translations. These directories contain the files:

- ndi_c6_alpha/gamma_single_molecule.data = this is the LAMMPS data file of a single molecule of the alpha/gamma phase. The molecular geometry is extracted from the experimental XRD structures deposited in the CCDC. This files containes the definition of the atom types, point charges, bond/angles/dihedrals constants and van der Waals paramters that are used troughout the entire work.
- ndi_c6_alpha/gamma_single_molecule.lt = this is a file for Moltemplate, it contains the same information of the .data file but in a Moltemplate-readable format. It has been obtained with the ltemplify utility.
- system.lt = this file contains the instructions for moltemplate. It describes that the single molecule should be translated 5 times along each crystallographic axis. It also contains the definition of the supercell.
- system.pristine_alpha/gamma.data and system.pristine_alpha/gamma.settings = these describe the actual simulation box, with all the atomic positions and all the parameters of the force field. These are read by LAMMPS.
- input_pristine_alpha.inp = the actual MD input, it already contains the equilibration-NVT-NPT sequence
