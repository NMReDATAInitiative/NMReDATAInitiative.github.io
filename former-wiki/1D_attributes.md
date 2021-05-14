---
title: 1D attributes
permalink: /1D_attributes/
---

Generalities
============

The attributes list the caracteristics of signals found in spectra. List
of signal attributes (1D spectra)

**Note that they should apear in this order! All labels are optional,
the shift value is mandatory.**

[`S=`` ``Multiplicity`](/#S=_Multiplicity "wikilink")` (`***`string`***`)`
[`J=`` ``Scalar`` ``coupling`](/#J=_Scalar_coupling "wikilink")` (`***`string`***`)`
[`N=`` ``number`` ``of`` ``nuclei`](/#N=_number_of_nuclei "wikilink")` (rounded number of atoms) (`***`int`***`)`
[`L=`` ``Label`` ``of`` ``the`` ``signal`](/#L=_Label "wikilink")` (`***`string`***`)`
[`E=`` ``Integral`](/#E=_Signal_Integral "wikilink")` (crude integrals) (`***`float`***`)`
[`I=`` ``Intensity`](/#I=_Signal_intensity "wikilink")` (`***`float`***`)`
[`W=`` ``Width`](/#W"=_Signal_width "wikilink")` (`***`float`***`)`
[`T1=`` ``T1`` ``relaxation`` ``time`](/#T1/T2=_Relaxation_time "wikilink")` in second (`***`float`***`)`
[`T2=`` ``T2`` ``relaxation`` ``time`](/#T1/T2=_Relaxation_time "wikilink")` in second (`***`float`***`)`
[`Diff=`` ``for`` ``diffusion`` ``rate`](/#Diff=_Diffusion_rate "wikilink")` in m`<sup>`2`</sup>`/s`<sup>`-1`</sup>` (`***`float`***`)`

Examples of signal attribute in 1D spectrum
===========================================

Chemical shifts are given with four digits after the period (minimum).

Examples of a doublet in 1D <sup>1</sup>H spectrum: "4.182 (*s*, 2H,
H-(C3))"

`4.1823, S=d, N=2, L=H-(C3)   `
`4.1823, S=d, N=2, L=<>  `
`4.1820-4.1815, S=d, N=2, L=H-(C3) `

Examples of a typical signals in 1D <sup>13</sup>C spectra: "14.1823
CH<sub>2</sub>,C(5)"

`14.1823, S=2, L=C(5) `

Examples of a a negative signal for CH<sub>2</sub>,C(5) a DEPT
<sup>13</sup>C spectra

`14.1823, S=2, L=C(5), I=-95.12`

Attributes
==========

== S= Multiplicity ==

|      |               |
|------|---------------|
| s    | singlet       |
| d    | doublet       |
| t    | triplet       |
| q    | quartet       |
| ...  | ...           |
| hept | heptet        |
| bs   | broad singlet |
| m    | multiplet     |

multiplicity

In case of overlap, second-order effects, use "m". This is meant to be
the apparent multiplicity. For example a dd with similar coupling will
look as a triplet, can be called "t".

== J= Scalar coupling == === J= Scalar coupling (unassigned) ===
Couplings in Hz with two digits after the period separated by the
[separator](/separator "wikilink").

`4.1823, S=dd, N=1, L=a, J=9.30,4.81`

indicates a *dd* with J=9.30 and 4.81 Hz.

`4.1823, S=td, N=1, L=a, J=9.30,4.81 `

means: the first coupling of 9.30 causes a triplet shape and a doublet
with J=4.81 Hz.

Following the couplings, labels may be given in parentheses to assign
the coupling.

=== J= Scalar coupling (assigned) === Scalar couplings are given with
two digits following the period. For a signal assigned to "a":

`4.1823, S=d, N=1, L=a J=9.32(b) `

means: J(a,b)=9.32 Hz

`4.1823, S=dd, N=1, L=a J=9.32(b),4.80(c) `

means: J(a,b)=9.32 Hz and J(a,c)=4.80 Hz

See also, the [<NMREDATA_J>
tag](/NMReDATA_tag_format#.3CNMREDATA_J.3E "wikilink") where assigned
coupling should be compiled.

== N= number of nuclei == For 1D <sup>1</sup>H spectra: 1 for CH, 2 for
CH<sub>2</sub>, *N* for multiplet, where *N* is the number of protons in
the range

For 1D <sup>13</sup>C spectra: 0 for quaternary carbons, *N* for
CH<sub>*N*</sub>, where *N* is the number of protons bound to the carbon

This reflects the value of the integrals, but it is not the value of the
integral. The value of the integral can be specified using the "E="
attribute.

== L= Label == The label (according to list in the <NMR_ASSIGNMENT>
tag). Keep in mind the
[possibility](/NMReDATA_tag_format#Ambiguous_assignment_of_signals_.28ONLY_WITH_LEVEL.3E0.29 "wikilink")
of unambiguous assignment [when
level\>2](/NMReDATA_tag_format#.3CNMREDATA_LEVEL.3E "wikilink").

== E= Signal Integral == E integral (in arbitrary units).

== I= Signal intensity == I intensity (in arbitrary units).

== W= Signal width == W width of the signal at half height (in Hz).

== T1/T2= Relaxation time == Results of relaxation measurements, T1, T2,
etc. can be given in seconds as:

`4.8000, S=q, E=2, L=a, T1=0.7`

== Diff= Diffusion rate == Diffusion rates in
m<sup>2</sup>/s<sup>-1</sup>

`4.8000, S=q, E=2, L=a, Diff=1.12e-9`

Parsing data
------------

When reading these lines of data, the format is: The first field is a
chemical shift (or chemical shift range!!), followed by a number of
attributes separated by ", ". Note that we may not require the space
(ignore the space!) The structure of each "attribute" is always:

1.  the name of the attribute (usually in capital letters / no space).
2.  = (an "equal" sign)
3.  the value of the attribute. Read and store it as text (in the
    perspective of writing it later).

They can be directly used as name and value of object properties.

The order of the attributes may change, but we recommend writing them in
a certain order... (see above)

Some attributes may be quite complex (in particular the "J" field...)

Note that the J attribute may contain "," meaning that a comma alone is
not separating attributes. If the "," is separating J values, what
follows the "," is a number (the next J value) if what follows the ","
is the next attribute, what follows the "," is alphanumerical and "=".

Keep in mind the [possible issue with labels
including](/NMReDATA_tag_format#Labels_including_comma_or_other_special_characters "wikilink")
",", " ", etc.