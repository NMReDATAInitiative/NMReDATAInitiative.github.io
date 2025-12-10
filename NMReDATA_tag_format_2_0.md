---
title: NMReDATA tag format 2.0
permalink: /NMReDATA_tag_format_2_0/
---
# NMReDATA initiative
*generate, store and share the data extracted from set of NMR spectra associated to a compound*

***

[Home](/) **/** [Who are we](partners) **/** **The Format** **/** [In the news ...](timeline)

***

[Format main page](/format) **/** [Format of the NMREDATA tags (version 1.0/1.1)](/NMReDATA_tag_format) **/** **Format of the NMREDATA tags (version 2.0)** **/** [Compatible software and webtools](/Compatible_software "Compatible software") **/** [1D Attributes](/1D_attributes) **/** [2D Attributes](/2D_attributes) **/** [Examples](Examples)

***

The NMReDATA 2.0 format consists of the [1.1
format](/NMReDATA_tag_format "wikilink") with the following extensions:

Author
------

Author are given with their orcid number (preference) or lastname,
comma, first name(s) (to facilitate separation of first and lastname).
For data originating from article we would accept the names as listed in
the article (initials and order).

Organization should be given as ISNI code when possible. Otherwise the
name, the city and the country separated by comma. The country should be
coded according to ... There may be multiple institutions associated to
an author. They are listed in sequence.

We can also define one or multiple roles to each author (Assignment,
Validation, Curation, Principal investigator, Supervisor, Service
manager, *etc.*

Example:

````
>  <NMREDATA_AUTHOR>
Author=0000-0001-7018-4288\
Role=Assignm t, Supervisor\
Organization=https://www.isni.org/isni/0000000121752154\
Department=isni of the Department if it exist\
Author=van Halle, John\ 
Organization=De Montfort University, Leicester, UK\
Department=Department of chemical sciences\
````
If a record is updated, the history of the authors/versions are listed
with version numbers:
````
Version=1\
Author=van Halle, John\
Role=Assignment\
Version=2\
Author=Doe, Peter\
Role=Assignment, correction of assignement of C1 an C3\
````
For automated changes, the software is given as Software name and
version, comma, source of the software.

Example:
````
>  <NMREDATA_AUTHOR>
...
Version=2\
Robot=Sup\
Role=Assignment\
Organization=https://www.isni.org/isni/0000000121752154\
Department=isni of the Department if it exist\
````

Molblock (2D/3D) structures
---------------------------

In version \<2.0, we do not specify if the structure in the .sdf file is
"flat", or a true "3D structure". Version 2.0 clarifies this.

The proposition is that sdf files could have two structures (.sdf files
allows for any number of structure - we don't violate any rule here).
When there is only one structure, it should be "flat" (z coordinate set
to zero) with all known stereo information encoded properly in it. When
there are two structures, the two should have the same numbering of the
atoms, but one is for "flat" display, and one the 3D structure for
distances measurement, measure of angles, dihedral angled, etc.

The SDF file format allows to include multiple structures/model/frames
in a single SDF file. They are separated by a line with "$$$$".

For the NMReDATA format, there is always one (first) structure
representing the "flat" 2D structure. By flat we don't mean that
chirality is not specified, but that it has a *z*-coordinate set to
zero.

For version 2.0, we will introduce the possibility to include a 3D
structure (additional to the first - not replacing it!).

The second structure (3D with non-zero *z* coordinates) may be added by
simply appending a molblock to the SDF file and terminate (as usual),
the file with "$$$$".

It should fulfil the following conditions: the order of atoms and bonds
should be the same as for the main (first) structure. The "only"
difference should be the *x, y, z* coordinates that will correspond to
the determined 3D structure, instead of having *z* set to zero as for
"flat" structure.

To obey the [official
specification](http://accelrys.com/products/informatics/cheminformatics/ctfile-formats/no-fee.php)
of the MOLfile format and, hence, assure compatibility of the files with
other software, the second line in the header of each molblock should
include either "2D" or "3D" (the 'dimensional codes') in columns 21 and
22 (the *dd* below):

    Line 2 has the format:
    IIPPPPPPPPMMDDYYHHmmddSSssssssssssEEEEEEEEEEEERRRRRR
    A2<--A8--><---A10-->A2I2<--F10.5-><---F12.5--><-I6-> )
    User's first and last initials (I), program name (P), date/time (M/D/Y,H:m),
    dimensional codes (d), scaling factors (S, s), energy (E) if modelling program input,
    internal registry number (R) if input through MDL form.

Note that future developments may impose to include additional
structures (for example for multiple conformations DFT/GIAO data...). We
will need to make sure the software can unambiguously find the correct
3D structures. We may therefore have to add addition flag to indicate
the 3D structure corresponding to the main structure of the NMReDATA.
For now, we can consider the that the second structure in the file will
be the 3D structures and ignore any addition ones (third, fourth,
*etc.*)

We strongly recommend to have all the NMReDATA tags associated with the
first structure, i.e. included before the first "$$$$" line. This is
because the current reader may stop reading the SDF file at the first
occurrence of "$$$$" and would miss them if they are listed after the 3D
structure.
The NMREDATA tags go with the 2D structure, so the overall file will
look like this:


    ;xxxxxxxxxxxxxxxxxxxx2D

    <2d structure>
    M  END
    >  <NMREDATA_VERSION>
    1.1\

    <other tags>

    $$$$

    ;xxxxxxxxxxxxxxxxxxxx3D

    <3d structure>
    M  END

    $$$$

2D to 3D conversion
-------------------

When a 3D visualizer does not find a 3D structure, it could generate and
add the 3D structure to the output, BUT ask for permission/warning to
the user and warn him on the consequences and/or guide him through the
process:

* Transforming 2D into 3D is not innocent. If two enantiotopic hydrogen
atoms are drawn with regular bonds (simple straight line) and assigned
two different signals in the spectrum, it may be for the good reason
that the assignment is not known. Introducing a 3D structure will erase
the "unknown" and introduce the risk of error. When there is a risk for
this to occur, one should use the
[http://nmredata.org/wiki/NMReDATA_tag_format#interchangeable-assignment-only-for-level0](interchangeable assignment) statement in the "NMREDATA_ASSIGNMENT" tag.

* Other problems of this type probably exist...

In principle transforming 2D into 3D is quite important and useful but
has to be done carefully to avoid introducing error or removing
information!

Jcamp integration
=================

JCAMP spectra can be included in NMR records (for version \>= 2.0).
Jcamp do not replace the manufacturer's format (in the files or through
links), but can be provided in addition in order the make the NMR record
more [FAIR](https://www.go-fair.org/). We require only minimal spectral
information (see below), no fid and other acquisitions and processing
parameters that are notoriously difficult to interconvert.

We do not impose to have the JCAMP files generated by the software
generating/reading NMReDATA, (only recommend to) but to have them ready
to read the JCAMP files when the manufaturers data are not available
(something that should, in principle, not occur!). The feature of adding
JCAMP spectra in NMR Records could be added by "smart" repository
servers (using API), or other software tools. The jcamp spectra are
expected to be proposed when records are provided by web-based data
providers.

All versions of JCAMP are accepted. Below are some hints on what would be in the JCAMP files ideally. 
Given that we have information in the NMReDATA file, this is only in addition and if JCAMP files are there.

Example of reference to the JCAMP file (**Spectrum_Jcamp=**):
````
>  <NMREDATA_1D_1H>
Larmor=500.13
Spectrum_Location=file:./nmr/10/1/pdata/1
Spectrum_Jcamp=file:./jcamp_folder/spectrum1.jcp
Signal 1
Signal 2
...
````
You will find below, for both 1D and 2D spectra, the prefered format,
and the alternatively accepted format to increase compatibility.

For 1D spectra
--------------

Note that the Larmor frequency can also be found in the .sdf file, but
should be given in the camp file as well.

Preferred format to be used for new developments
[example](Jcamp_example2):

```
Frequency of the first point (left side) ***`FIRSTX=`***
Frequency of the last point (right side) ***`LASTX=`***` 
Larmor frequency ***LARMOR=*** (or ***.OBSERVE FREQUENCY=*** accepted for compatibility)
Number of points ***NPOINTS=***
*NPOINTS* data points
````

Alternative accepted parameters (Bruker type...):
````
Spectral width in ppm ***SW=***
Chemical shift of the center of the spectrum (to allow to switch to Hz scale) ***SFO1=***
Larmor frequency ***BF1=***
Number of points ***SI=***
*SI* data points
````

The reader should be able to manage both types of parameters.

For 2D spectra
--------------

We consider correlation spectra (with chemical shift in both
dimensions) but also J-resolved spectra (Hz in F1), 2D spectra with
double quantum scales (in F1), and Diffusion "spectra" (DOSY), assuming the direct dimension is always in ppm.

Preferred format

"**D**" is for *direct* dimension "**I**" stands for *indirect*
dimension.
````
Type of indirect dimension: ***TYPE_F1_SCALE=*** "ppm", "Hz", "dq", "diff"
Spectral within ppm in the direct and indirect dimensions **SWD= / SWI=** 
Chemical shift of the first point (bottom / left side) ***FIRSTXD= / FIRSTXI=***
Chemical shift of the last point (top / right side) ***LASTXD= / LASTXI=***
Larmor frequencies (to allow switch to Hz) ***LARMORD= / LARMORI=*** (0 if not relevant - for type "Hz")
Number of points in the direct and indirect dimensions ***NPOINTSD= / NPOINTSI=***
*NPOINTSDxNPOINTSI* data points (all points of the direct dimension before starting the second point of the indirect dimension)
````

For compatibility with existing Bruker JCAMP

A line "$$ Bruker specific parameters for F1" separates F2 from F1
parameters with the same names

````
Spectral within ppm in the direct and indirect dimensions **SW=** 
Chemical shift of center of the spectrum (bottom / left side) ***SFO1=***
Larmor frequencies ***BF1=*** (0 if not relevant - for type "Hz")
Number of points in the direct and indirect dimensions ***SI=***
*SI(1)xSI(2)* data points (all points of the direct dimension before starting the second point of the indirect dimension)
````
