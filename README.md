# VASP-force-correction-patch
Force correction patch for VASP 5.4.4

## Installation
 in the `src` folder,
```
patch -i "path_to_patch_file"/force_correction.patch
```



## How to use

There are 6 new INCAR tags.

`FORCES_X`
: Individual forces of ions in the x direction, in the order that appears in POSCAR. Corresponds to Born effective charges in constrained-forces calculation.

`FORCES_Y`
: Individual forces of ions in the y direction, in the order that appears in POSCAR. Corresponds to Born effective charges in constrained-forces calculation.

`FORCES_Z`
: Individual forces of ions in the z direction, in the order that appears in POSCAR. Corresponds to Born effective charges in constrained-forces calculation.

`SCALING`
: Sets the scaling parameter of forces. Corresponds to $-\mathcal{E}$ (electric field, V/$\textrm{\AA}$) in constrained-forces calculation. Default is 0.

`LFIX_XY`
: Does not relax lattice constants a and b if set to `TRUE`. (independent z) Default is `FALSE`.

`LFIX_Z`
: Does not relax lattice constant c if set to `TRUE`. (independent z) Default is `FALSE`.

## Symmetry is your enemy

It is recommended to set `ISYM` to 0, unless you have a very good idea of symmetry in your polarized system. Also, if you're trying to polarize non-polar structure, you have to either set `ISYM` to 0 or alter your POSCAR so that it is the same space group of the polarized structure.

## Papers to cite

[Fu, H., & Bellaiche, L. (2003). Physical review letters, 91(5), 057601.](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.91.057601)

[Jung at el., (2023). ChemRvix](https://chemrxiv.org/engage/chemrxiv/article-details/63fd7308897b18336f3a59aa) (Paper under review)

## Disclaimer
VASP is commercial package requiring a valid liscence for use.
