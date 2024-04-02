[![DOI](https://zenodo.org/badge/642097811.svg)](https://zenodo.org/doi/10.5281/zenodo.10045190)

# VASP Force Correction Patch
Force correction patch for VASP 5.4.4 and 6.4.1

## Installation
 in the `src` folder,
```
patch -i "path_to_patch_file"/force_correction.patch
```

## How to use

There are 6 new INCAR tags from the patch.

`FORCES_X`
: Individual forces of ions in the x direction, in the order that appears in POSCAR. Corresponds to Born effective charge tensor component $Z^*_{\alpha x}$ in constrained-forces calculation, where the electric field direction is $\alpha$. Default is 0 for all ions.

`FORCES_Y`
: Individual forces of ions in the y direction, in the order that appears in POSCAR. Corresponds to Born effective charge tensor component $Z^*_{\alpha y}$ in constrained-forces calculation, where the electric field direction is $\alpha$. Default is 0 for all ions.

`FORCES_Z`
: Individual forces of ions in the z direction, in the order that appears in POSCAR. Corresponds to Born effective charge tensor component $Z^*_{\alpha z}$ in constrained-forces calculation, where the electric field direction is $\alpha$. Default is 0 for all ions.

`SCALING`
: Sets the scaling parameter of forces. Corresponds to $-\mathcal{E}$ (electric field, V/&#8491;) in constrained-forces calculation. Default is 0.

`LFIX_XY`
: Does not relax lattice vector a and b if set to `TRUE`. (perpendicular z) Default is `FALSE`.

`LFIX_Z`
: Does not relax lattice vector c if set to `TRUE`. (perpendicular z) Default is `FALSE`.

There are 2 new INCAR tags for VASP 6 patch, `LFIX_XY_COL` and `LFIX_Z_COL`. [They fix Cartesian components of the lattice vector, instead of the vector themselves](https://seongjoojung.github.io/posts/update/).

Both `IBRION=1` and `IBRION=2` works, but if you're trying to converge to a saddle point, only `IBRION=1` works.

## :warning: **Symmetry is your enemy!** :warning:

If you're trying to polarize your structure starting from non-polar one, you have to either set `ISYM` to 0 or alter your `POSCAR` so that it is the same space group of the polarized structure. In general, It is recommended to set `ISYM` to 0 to avoid internal symmetrization of k-points, unless you have a good idea of symmetry in your polarized system.

## Tutorial
[https://seongjoojung.github.io/posts/force-correction-tutorial/](https://seongjoojung.github.io/posts/force-correction-tutorial/)

## Reference

[Fu, H., & Bellaiche, L. (2003) *Phys. Rev. lett.* 91(5), 057601.](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.91.057601)

[Jung at el. (2023) *Nat. Comm.* 14, 7795](https://www.nature.com/articles/s41467-023-43641-0)

[Sai, Rabe & Vanderbilt (2002) *Phys. Rev. B* 66, 104108](https://journals.aps.org/prb/abstract/10.1103/PhysRevB.66.104108)

## Disclaimer
VASP is commercial package requiring a valid liscence for use.
