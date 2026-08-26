# Polymorphism-NDI-C6-Input-Files


The files are organized in the following manner:

## Pristine Alpha and Pristine Gamma

The directories containing the files for the simulations of pristine alpha and gamma, are "pristine_alpha" and "pristine_gamma". The simulation cells are 5x5x5 supercell and have been constructed with Moltemplate by appropriate translations. These directories contain the files:

- ndi_c6_alpha/gamma_single_molecule.data = LAMMPS data file of a single molecule of the alpha/gamma phase. The molecular geometry is extracted from the experimental XRD structures deposited in the CCDC. This files containes the definition of the atom types, point charges, bond/angles/dihedrals constants and van der Waals paramters that are used throughout the entire work.
- ndi_c6_alpha/gamma_single_molecule.lt = file for Moltemplate, it contains the same information of the .data file but in a Moltemplate-readable format. It has been obtained with the ltemplify utility.
- system.lt = instructions for moltemplate. It describes that the single molecule should be translated 5 times along each crystallographic axis. It also contains the definition of the supercell.
- system.pristine_alpha/gamma.data and system.pristine_alpha/gamma.in.settings = these describe the actual simulation box, with all the atomic positions and all the parameters of the force field. These are read by LAMMPS.
- input_pristine_alpha.inp = actual MD input, it already contains the equilibration-NVT-NPT sequence. In the case of gamma, we report the input for the simulation at 327 K, to reproduce the simulation at 450 K it is sufficient to change the temperature of the thermostat, all the other lines remain unchanged (it is advisable to change the name of the dump files as well). 

## Heating of the Alpha Phase to 600 K

- input_heating_alpha_300_600.in = input for the heating of the equilibrated (after 20 ns) pristine alpha phase. Heating from 300 K to 600 K in 10 ns.
- alpha_after_20_ns_equilibration.data = LAMMPS data file describing the equilibrated pristine alpha. It is the endopoint of the equilibraton procedure reported in the "pristine_alpha" directory

## Equilibration at 590 K

- input_1_ns_590K.in = input the for the 1-ns equilibration at 590 K
- snapshot_at_590K.restart = LAMMPS restart file saved during the heating cycle. Here it is used to read the starting geometries and velocites for the equilibration

## Cooling to 300 K

- after_equlibration_at_590K.data = LAMMPS data file obtained after the 590 K equilibration, starting point of the cooling simulation
- input_cooling.in = input for the cooling simulation with a 30K/ns temperature gradient 

## Equilibration at 300 K
- input_equilibration_300K.in = input for the 500 ns equilibration of the system after cooling
- after_cooling.data = last frame of the cooling simulation, here used as starting configuration
