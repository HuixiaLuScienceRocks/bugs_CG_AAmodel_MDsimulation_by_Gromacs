### This repository is for investigators who suffer facing bugs/errors while running MD simulations by gromacs using coarse-grained models.

## Example 1
Using Charmmgui constructed protein solvated in salty simulation box (Martini3 force field). Using VMD TKConsol checked the whole system's net charge = 0, after loading step3*.psf + step3*.pdb. However, when running MD using gromacs, fatal error is encountered while generating step4.0*tpr:
the net charge of the system is not 0 (eg. -4)

### Solution: remove 4 ions to make the system neutral charged and a new system-neutral.top and index-neutral.ndx needs to be generated.

## Example 2
Using Charmmgui to generate the simulation system (2 peptide monomers solvated in salty water), while generating the step4.0_minimization.tpr, it is complaining:

############
Program:     gmx grompp, version 2018.1
Source file: src/gromacs/gmxpreprocess/grompp.cpp (line 619)

Fatal error:
number of coordinates in coordinate file (step3_charmm2gmx.pdb, 39544)
             does not match topology (system.top, 38773)
############

### Reason: 
In system.top, the following two itp files were called:

#include "no360loop_dimer_2_proa.itp"

#include "no360loop_dimer_2_prob.itp"

However, Charmmgui made an error while generating no360loop_dimer_2_proa.itp:

-rwxrwxrwx 1 huixia huixia 1,5K oct 21 18:19 no360loop_dimer_2_proa.itp

-rwxrwxrwx 1 huixia huixia  95K oct 21 18:19 no360loop_dimer_2_prob.itp

### Solution:
fix no360loop_dimer_2_proa.itp

## Example 3
---------------------------------------------------------------------------------------------------------

# AA model:

### Using "Force Field Converter" module of CHARMMGUI takes CHARMM PSF and CRD files and produces input files with the selected force field (to run amber, gromacs, etc).

https://www.charmm-gui.org/?doc=input/converter.ffconverter

##### For example: To generate polymer.itp file (for gromacs force field), just upload its psf and crd files that is generated through  "PDB Reader & Manipulator" module of CHARMMGUI

---------------------------------------------------------------------------------------------------------
### To be continued... ...
