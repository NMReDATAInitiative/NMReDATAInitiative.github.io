---
title: Nmredata object structure
permalink: /Nmredata_object_structure/
---

Possible structure of the object including NMReDATA reflecting the
format of NMReDATA tags of SDF files.

**Note:** This is not designed to include ambiguities in the assignment.
This is therefore only for use with Level=0.

Chemical structure
==================

For the structure part originating from the .mol part of the SDF file:

`object.structure (from the .mol part of the file)`

`object.structure.atom[`*`n`*`] (for each atom `*`n`*`) `
`object.structure.atom[`*`n`*`].N `***`integer`***` atomic number of atom N) `
`object.structure.atom[`*`n`*`].X `***`float`***` x coordinate in A `
`object.structure.atom[`*`n`*`].Y `***`float`***` y coordinate in A `
`object.structure.atom[`*`n`*`].Z `***`float`***` z coordinate in A `

`object.structure.bond[`*`m`*`] (for each bond `*`m`*`)`
`object.structure.bond[`*`m`*`].a1 `***`int`***` first atom (1 to number of atoms)`
`object.structure.bond[`*`m`*`].a2 `***`int`***` second atom (1 to number of atoms)`
`object.structure.bond[`*`m`*`].type `***`int`***` 1:for single bond, 2: for double bond, 3: for triple bond`

Sample data
===========

Information about the sample

`object.version `***`string`***` version (content of the NMREDATA_VERSION tag)`
`object.level `***`int`***` level (content of the NMREDATA_LEVEL tag)`
`object.SMILE `***`String`***` smile code`

When H are explicit in the structure, the SMILE code must also include
all the H atoms in the smile code. The reason to include the smiles in
the NMReDATA is that it can be used to generate pure text MNR
description of spectra (This is under elaboration but it is very
important for stability of the format to include them in SDF files!)

`object.concentration `***`float`***` concentration in mM`
`object.temp `***`float`***` temperature in K`

Assignment
==========

For the <NMR_ASSIGNMENT> (previously named NMR_SIGNALS\>) of the SDF
file: The signals of all isotopes are listed together, they compile the
information from the tag describing the spectra (see below)

`object.assignment[`*`n`*`] (for each assignment `*`n`*`)`
`object.assignment[`*`n`*`].label `***`string`***` label given to the atom or set of atoms`
`object.assignment[`*`n`*`].cs `***`float`***` chemical shift (single value, no range accepted!)`
`object.assignment[`*`n`*`].atom[`*`m`*`] `***`integer`***` atom number(s) assigned to the signal (start numbering at 1)`

J couplings
===========

For the <NMR_J> of the SDF file: This includes all the coupling
extracted from the spectra (see below)

`object.J[`*`n`*`] (for each coupling `*`n`*` listed)`
`object.J[`*`n`*`].label1 `***`string`***` label of the first signal `
`object.J[`*`n`*`].label2 `***`string`***` label of the second signal `
`object.J[`*`n`*`].value `***`float`***` coupling constant between label1 and label2`

*optional because possibly involving difficulties:*

`object.J[`*`n`*`].nb[`*`m`*`] `***`int`***` number of bonds between the atoms corresponding to the labels. `

In most cases, *m* = 1, but when the two labels correspond to more than
one spin (for example in AA'XX' systems is described using a single
lable for A and A' and a single label for X and X') the number of bonds
depends on whether we consider A-X and A-X', this is why we need two
elements in the tabel.

1D spectra
==========

See also [1D spectra attributes page](/1D_attributes "link").

`object.spectrum1d[`*`n`*`] (for each 1D spectrum `*`n`*`)`
`object.spectrum1d[`*`n`*`].S Multiplicity (`***`string`***`)`
`object.spectrum1d[`*`n`*`].J Scalar coupling (`***`string`***`) This is a string because it contains the description of the coupling, assignment, etc.`
`object.spectrum1d[`*`n`*`].N number of nuclei (`***`int`***`)`
`object.spectrum1d[`*`n`*`].L Label of the signal (`***`string`***`)`
`object.spectrum1d[`*`n`*`].E Integral (`***`float`***`)`
`object.spectrum1d[`*`n`*`].I Intensity (`***`float`***`)`
`object.spectrum1d[`*`n`*`].T1 T1 relaxation time (`***`float`***`)`
`object.spectrum1d[`*`n`*`].T2 T2 relaxation time (`***`float`***`)`
`object.spectrum1d[`*`n`*`].Diff diffusion rate (`***`float`***`)`

2D spectra
==========

See also [2D spectra attributes page](/2D_attributes "link").

`object.spectrum2d[`*`n`*`] (for each 2D spectrum `*`n`*`)`
`object.spectrum2d[`*`n`*`].L1 Label of the signal in F1(`***`string`***`) (if the signal is not assigned, the chemical shift is given as a string)`
`object.spectrum2d[`*`n`*`].L2 Label of the signal in F2(`***`string`***`) (if the signal is not assigned, the chemical shift is given as a string)`
`object.spectrum2d[`*`n`*`].I Intensity (`***`float`***`)`
`object.spectrum2d[`*`n`*`].E Signal volume (`***`float`***`)`
`object.spectrum2d[`*`n`*`].Ja Active scalar coupling (`***`float)`**` ``i.e.`` ``from`` ``a`` ``COSY`` ``spectrum`*
`object.spectrum2d[`*`n`*`].J1[`*`m`*`] Passive scalar coupling(s) in F1 (`***`float`**`)i.e.`` ``from`` ``a`` ``high-resolution`` ``COSY`` ``spectrum`*
`object.spectrum2d[`*`n`*`].J2[`*`m`*`] Passive scalar coupling(s) in F2 (`***`float`**`)i.e.`` ``from`` ``a`` ``high-resolution`` ``COSY`` ``spectrum`*
`object.spectrum2d[`*`n`*`].JL1[`*`m`*`] Label of the assigned passive coupling in F1 (`***`string`**`)i.e.`` ``from`` ``a`` ``high-resolution`` ``COSY`` ``spectrum`*
`object.spectrum2d[`*`n`*`].JL2[`*`m`*`] Label of the assigned passive coupling in F2 (`***`string`**`')i.e.`` ``from`` ``a`` ``high-resolution`` ``COSY`` ``spectrum`*