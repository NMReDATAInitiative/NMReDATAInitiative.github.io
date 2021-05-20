---
title: 2D attributes
permalink: /2D_attributes/
---

Generalities
============

Unlike signal in 1d where signal can include range and include multiplet
overlaping resonances, 2D signals correlate a pair of spins. Chemical
shifts are not given, instead the labels of the spins are directly
provided. (This is to encode directly the data found in tables in
articles).

Using Level=2, ambiguities can be coded using "(a,b)" to express that
the labels is either a or b.

The attributes list the caracteristics of signals found in 2D spectra.
List of signal attributes ("D spectra)

**Note that they should apear in this order!**

[I= Intensity](/2D_attributes/#Signal_intensity "wikilink") (***float***)

[E= Volume](/2D_attributes/#Signal_Volume "wikilink") (crude integrals) (***float***)

[Ja= Active scalar coupling](/2D_attributes/#Active_scalar_coupling "wikilink") (***string***)

[J1= F1 passive coupling](/2D_attributes/#Passive_scalar_coupling "wikilink") (***string***)

[J2= F2 passive coupling](/2D_attributes/#Passive_scalar_coupling "wikilink") (***string***)

[W1= F1 signal width](/2D_attributes/#Signal_width "wikilink") (***float***)

[W2= F2 signal width](/2D_attributes/#Signal_width "wikilink") (***float***)

Examples attributes of 2D signal
================================

Examples of a correlation between spins *a* and *b* (see below for
description of the attributes)...

... Only indicating the presence of the cross peak:

`a/b`

... Providing the intensity of the signal:

`a/b, I=133.6`

... Including the extrcted coupling constants (from a high-resolution
DQF-COSY spectrum):

`H4eq/H6eq, Ja=2.2, J1= 3.0(H8ax), 3.2(H5e1), 3.3(H5ax), 12.75(H4ax), J2=4.0 (H8ax), 4.5(H10ax), 12.09(H6ax) [see paper...]`

If the signal is not assigned, the chemical shift replaces the labels

`1.5402/1.4423 I=133.6`

Attributes
==========

Signal intensity
----------------
I: This provides the signal intensity 

Signal volume
-------------
E: This provides the signal volume

Active scalar coupling
----------------------

Ja: Couplings in Hz with two digits after
the period separated by the [separator](/separator "wikilink"). For a
correlation between *i* & *j* (F1 first):

`i/j, Ja=9.30`

means the active coupling (between *i* & *j* ) is 9.3 Hz

Passive scalar coupling
-----------------------

J1/J2: For a correlation between *i* &
*j* :

`i/j, J1=9.30`
`i/j, J1=9.30, 4.80`

means: *i*, the spin in the F1 dimension, is coupled to one or more spin
(not the active coupling *j*) with J=9.3 and 4.8 Hz

For a correlation between *i* & *j* :

`i/j, J1=9.30(b)`
`i/j, J1=9.30(b), 4.80(a)`

means:J(i,b)=9.30 Hz J(i,a)=4.80 Hz(in the F1 dimension).

See also, <NMREDATA_J> tag where assigned coupling should be compiled.

Signal width
------------

W1/W2: Signal widht in F1/F2 in Hz

`W1=6.0`
`W2=1.2`
