---
title: NMReDATA tag format
permalink: /NMReDATA_tag_format/
---

Direct link to the [1D spectra attributes
page](/1D_attributes "wikilink").

Direct link to the [2D spectra attributes
page](/2D_attributes "wikilink").

Possible [object structure of
NMReDATA](/nmredata_object_structure "wikilink").

[Note for programmers about reading and writing NMReDATA SDF
files](/parser "wikilink").

Direct link to a list of example [example of NMR records and NMReDATA
files](/examples "wikilink").

**Important note on separators:** In general we use ", " (comma + space)
as separator. The space after the “,” may become optional in future
version. Please generate files in a manner that could not use it
(replace “, “ with a variable in your code so that you can easily change
to “,” (no space) and be ready to read or write files with and without
the space).

**Important note on comments:** In all NMReDATA tags, everything
following ";" can be ignored. This is used to add comments in the files.

**Important note on tag names:** To comply with the SDF format
specification, tag names cannot contain hyphen (-), period (.), less
than (\<), greater than (\>), equal sign (=), percent sign (%) or blank
space ( ). Tag names must begin with an alpha character and can contain
alpha and numeric characters after that, including underscore.

Definition of the NMReDATA tags
===============================

There is no prescribed order of the tags. For human readability, we
recommend the order used here, but this is not required.

Header tags
-----------

We included in the header tags only the absolutely necessary information
about the NMR dataset.

#### <NMREDATA_VERSION>

This tag is used to specify the “VERSION” of the file format. Current
version : 1.1
````
>  <NMREDATA_VERSION>
1.1\
````
Note the <span style="color:#0808F8"> addition of the "**\\**" before
the end-of-line character. If is optional for tags with a single line,
but mandatory to reparate lines [(more
details)](/end-of-line "Wikilink").

#### <NMREDATA_LEVEL>

This tag is used to specify the level of complexity of the data. In most
cases, level 0 (the standard) will be used when an assignment is
complete. This tag will allow developers to avoid the difficulties of
reading complex data (with level \>0).

##### Level 0

When the data contain no ambiguities in the assignment, set to 0:
````
<NMREDATA_LEVEL>
0
````
##### Level 1

When using list of signals including [interchangeable
assignments](/#Assignment_tags "wikilink"), set to 1 or 3. See
*"Interchangeable="* in the <NMREDATA_ASSIGNMENT> tag below ...

##### Level 2

When using ambiguously assigned signals in 2D spectra, set to 2 or 3
(see below).

Instead of using a single label in the assignment of signals,

````
a
````

this level allows to list the possible candidate labels to the signal.

For example,

````
(a, b)
(a,b) 
(<"Unit1,C1">,<Unit2,C1>)
(<"1/C1">,<2/C1>)
````

Indicates that the assignment is ambiguous and corresponds to either *a*
or *b*. Note that here we don't require the space after the ",".

##### Level 3

When using interchangeable and ambiguous assignment, set to 3 (=2+1).

#### \<NMREDATA_ID\> (Very important for reference)

## "/<"NMREDATA_ID/> (Very important for reference)

## "/<NMREDATA_ID"/> (Very important for reference)
## '/<'NMREDATA_ID/> (Very important for reference)



#### /"</"NMREDATA_ID/> (Very important for reference)

## "<"NMREDATA_ID/> (Very important for reference)

## "<NMREDATA_ID"/> (Very important for reference)
## '<'NMREDATA_ID/> (Very important for reference)
 
This tag is optional but very much encouraged, in particular when data
are stored as NMR record with a DOI. The following are defined by the
NMReDATA format:

````
>  <NMREDATA_ID>
Doi= doi of the NMR record\
Record= URL pointing to the ziped file of the NMR record\
Path= pointer to the nmredata.sdf file relative to the root of the ziped NMR record\
...
````

Here is an working example:

````
>  `<NMREDATA_ID>
Doi=10.5281/zenodo.1146869\
Record=`[`https://zenodo.org/record/1146869/files/sample1.zip`](https://zenodo.org/record/1146869/files/sample1.zip)\
Path=compound1.nmredata.sdf\

````

When copied from database to database, multiple ID's may be included.
These will be defined by database manager and software producers. They
could have the following form:
````
...
DB_ID= the code or number is assigned by the hosting database\
Title= Full analysis of whatever from methanol extract  \
Comment= Here more details could be given on the record.\
Comment1= Here more details could be given on the record.\
Comment2= Here more details could be given on the record.\
Comment3= Here more details could be given on the record.\
AUTHOR=Doe John, University of Tougalpa, Swinerland (optional)\
ORIGIN_ONE=2345627486 (could be about the sample name)\
ORIGIN_TWO=323212KKDKKS (could give a date or other reference)\
Title_L1=after sep. hplc (this could be extracted from the first line of the title in the 1H spectrum)\
````

One or more identifier can be given under "ID". The ID will be generated
by the software generating data and/or the database storing the data,
etc. There may be more than one ID (for example one from the software
generating it, one from the university labelling the origin of the data,
one from the database, one from the publisher of the associated data,
etc.) it is to the “generator” of the file to decide if/how to make it
unique if desired. InChIKey/SMILES could be given if the soft generating
the data is able to specify it. CAS-number if it already exists.

#### <NMREDATA_FORMULA> (optional but desired)

Here should come the chemical formula of the compound. (optional, but if
possible, it should be included!)

````
>  <NMREDATA_FORMULA>
C6H12O6
````

#### <NMREDATA_SMILES> (optional but desired)

Here comes the *isomeric smiles* when the molecule contains explicit H.
Otherwise *canonical smile* is OK. This will allow to generate text
including all the NMReDATA into pure text (report, PhD, paper, etc.).
This be further developed, but it should be included.

Examples:

isomeric SMILES of glucose (when the .mol structure includes explicit
hydrogen atoms)

````
C([C@@H]1[C@H]([C@@H]([C@H]([C@H](O1)O)O)O)O)O
````

canonical SMILES (when the hydrogen atoms are implicit)

````
C(C1C(C(C(C(O1)O)O)O)O)O
````

#### /<NMREDATA_ALATIS/> (optional but desired)

Here should come the *ALATIS* code of the compound. (If possible, it
should be included!)

[More details about Alatis](http://alatis.nmrfam.wisc.edu/)

#### <NMREDATA_SOLVENT>

The solvent is specified using this tag.

````
>  <NMREDATA_SOLVENT>
CDCl3
````

For mixture of solvents, the most abundant is first and they are
separated by "/" followed by the ratio in % separated by ":"

````
>  <NMREDATA_SOLVENT>
CDCl3/DMSO 80:20
````

````
>  <NMREDATA_SOLVENT>
CDCl3/DMSO/D2O 80:10:10
````

By default, the numbers are percentages in volumes. This can be modified
when other units are necessary as for describing buffers:

````
>  <NMREDATA_SOLVENT>
D2O/"sodium phosphate"/"sodium azide"/DSS 100:50:500:0.1 %:mM:uM:% Solvent:Buffer:Cytocide:Reference
````

In the case of RDC measurements, the medium used can be specified in the
line following the name of the solvent.

#### <NMREDATA_PH> (optional)

````
>  <NMREDATA_PH>
5.73
````

The pH is imporant in metabolomics applications. We recommend including
it when relevant.

#### <NMREDATA_CONCENTRATION> (optional)

When known, the concentration should be given. Only “mM” are allowed,
but the unit is specified.

<NMREDATA_CONCENTRATION>

````
12.3 mM
````

#### <NMREDATA_TEMPERATURE> (optional but desired)

When available the temperature of the sample should be given (only K are
allowed, but the unit is given)

````
>  <NMREDATA_TEMPERATURE>
298.0 K
````

Agregated data tags
-------------------

Two properties can be "assigned":

-   Chemical shifts with the <NMREDATA_ASSIGNMENT> (previously named
    <NMR_SIGNALS>) tag.
-   Scalar couplings with the <NMREDATA_J> tag.

In most cases, only chemical shifts are assigned. Scalar couplings are
usually not systematically measured and/or assigned, but when they are,
the values measured in the spectra should be compiled in the
<NMREDATA_J> tag

#### <NMREDATA_ASSIGNMENT> (previously named <NMREDATA_SIGNALS>)

This tag makes the link between the labels (used in the description of
the spectra (see below) to the atoms of the molecules.

This tag also provides the chemical shift. (If the chemical shift is not
known, use 777.777).

Note that the chemical shifts are sometimes redundant (since they are
also given in the description of the 1D spectra). But in the later, the
chemical shift may not be clearly defined (as for example in a multiplet
defined using a chemical shift range). In the NMREDATA_ASSIGNMENT tag,
the chemical shift is clearly defined (as a scalar, it cannot be a range
of chemical shifts as in description of 1D spectra).

In liquid-state NMR, some signals are degenerate. This means that
multiple atoms can contribute to the same signal. For example, all
protons of a methyl group. We will have a “label” to the atom (or the
group of atoms) having a common chemical shift because of symmetry (not
by accident). In principle the labels could be included in the .mol file
part (this is part of the definition of .mol files), but this may cause
compatibility problems. For example, Chemdraw does not recognize the
atom types well when they have been given a name and marks them as red
(as if the atoms were unknown causing hybridization problems). Because
of this problem, we will NOT use the labels of the “.mol” file, but list
them in a specific RD tag called <NMREDATA_ASSIGNMENT> (previously named
<NMREDATA_SIGNALS>).

For each signal, we first give the label of the signal. Chemical shifts
follow the label. Finally, we list the atom(s) it refers to in the
structure file. For the signals, the atom numbers start with 1 and go
through all the atoms in the molfile. NMR signals always have a chemical
shift associated to it. Not all atoms of the molecules will be listed in
the <NMREDATA_ASSIGNMENT> tag, for example if they were not assigned or
have no NMR signal (like O, N, or other isotopes for which the spectra
were not recorded).

Example, for HO-CH<sub>2</sub>-CH<sub>3</sub>, with protons labelled a,
b and c, and carbons A and B, (names could be different, I don’t mean
that labels have to be called using letters for protons, and numbers for
carbons - this is just an example) the tag would be:

````
>  <NMREDATA_ASSIGNMENT>; ethanol with explicit hydrogen atoms
A, 48.301, 1 ;A corresponds to the carbon of CH2\
B, 20.322, 2 ;B corresponds to the carbon of CH3\
a, 2.610, 3 ;a corresponds to the hydrogen atom of the OH\
b, 4.802, 4, 5; b corresponds to the hydrogen atoms of the CH2\
c, 1.401, 6, 7, 8\
Ex, 3.6, 9\
````

We recommend to use the special label "Ex" to designate all the H of the
OH, NH, etc. that are quickly exchanging (for example the OH of glucose
in D<sub>2</sub>O).

For structures where the hydrogen atoms are implicit, the reference to
hydrogen is made by adding "H" right before the atom number to
distinguish the heavy atom from the H bound to it. When more than one
hydrogen atom is implicit, the second is also labelled with "H". It is
understood that with implicit hydrogen, the two hydrogen atoms will not
be distinguished. Assignment of diastereotopic protons will not be
possible. To avoid this problem, use explicit mol structures with
defined chirality.

Example for ethanol:

````
>  <NMREDATA_ASSIGNMENT>
A, 48.3010, 1 ;the label "A" corresponds to the atom one which is the carbon of the CH2\
B, 20.3220, 2 ;atom two is the carbon of the CH3\
a, 2.6100, H3 ;"H3" refers to the hydrogen atom of atom 3 (the oxygen)\
b, 4.8020, H1 ;"H1" refers to the hydrogen atoms of atom 1 (of the CH2)\
c, 1.4010, H2\
````

(atom 3 would be the oxygen of ethanol) Only explicit H are allowed. No
monomer unit, no “R” group.

Labels can, in principle contain any character and be of any length. We
normally exclude comma (,) and slash (/) because they are used as field
separators (see below) and the <EOL> and <LF> or they are used inside
\<"..."\>. These labels can be defined as the chemist wishes. If a
database manager wants to change the names of the labels to make them
“canonical” or use any norm, up to him, but we accept anything. In
principle, the labels should correspond to the ones used in the
manuscript of the paper submitted (when we have reviewing mind). In the
case of simple numbering, it could be C1, etc. and H-C1, H’-C1, etc. But
this is up to the author/file generator to satisfy the format of the
journal/database and the readability of the numbering – possibly IUPAC
and the need to distinguish what needs to be distinguished (like
diastereotopic protons).

##### Labels including comma or other special characters

Examples of labels (**Note the \<""\> is used when they the labels
include "," "/" "\\" "\|" "(" ")" or "&" characters**):

````
a
H-C1
Proton_1
H'
H''
<"Ha,Hb">
<"Ha/Hb">
<"H-C(1)">
````

No ranges of chemical shifts are allowed here, only single floating
point should be specified. (in 1D spectra description ranges are
accepted). This is necessary because 1D <sup>1</sup>H spectra may not be
included in the set of spectra and, if they are, signals overlap may
result in describing such as region analysed as “m” with many signals
in.

We propose to call “Ex” the spins that are exchanging with solvent
(typically OH, NH, etc. in protic solvents). The atoms that are not
assigned to at least one NMR signals in the spectra are not listed. (H,
C that were not assigned, heteronuclei that are NMR passive (say S, O,
N) or for which the spectrum was not recorded (<sup>19</sup>F,
<sup>31</sup>P, etc.) .

##### Interchangeable assignment (Only for Level\>0)

When the SDF files has a Level with odd values (1 or 3), allows to
include the possibility of ambiguous assignment. If two or more labels
may be interchanged, they are listed before the end of the
NMREDATA_ASSIGNMENT list, before the empty line with the keyword
"Interchangeable=":

````
>  <NMREDATA_ASSIGNMENT>
...
a, 5.610, 10\
b, 5.802, 41\
...
Interchangeable=a, b\
````

means that the assignment of a and b may be interchanged.

````
Interchangeable=(a, CA), (b, CB)
````


means that “a” together with “CA” may be interchanged with “b” together
with “CB”. (This may be if two -O-Me could not be assigned unambiguously
because of missing HMBC signals. We may know that carbon “CA” is bound
to proton “a” and carbon “CB” to “b” (from HSQC), but maybe we do not
know which of the two Me is bound where (no HMBC signal).

There may be multiple “Interchangeable” lines.

Note that displaying/working with data with such interchangeable signals
may be a challenge. When software cannot take into account exchangeable
assignment, they should generate a warning message, read the standard
form or, better, propose the choice among the different possibilities.

Note that in order to avoid the difficulty of dealing with
interchangeable signals, it may be easier to leave them unassigned (when
they are unimportant). Another possibility would be to produce two
.nmredata.sdf files, one for each possible assignment.

In principle, if a Interchangable line list two possibilities, a second
three, and a third two, the number of possible strucutures is 2x3x2. (In
the perspective of of edition of the NMReDATA, each could be generated
and user/tools determine which is the correct one...)

##### Equivalent spins

Most of the time, equivalent spins have their atom number listed for a
single "label". But in some cases, one needs two different labels for
chemically equivalent spin (for example when listing couplings in AA'XX'
systems). In this case the fact that pairs of "labels" correspond to
equivalent spins is indicated with the "Equivalent=" keyword. Follows
the list of the labels of the equivalent spins.

````
>  <NMREDATA_ASSIGNMENT>
...
a, 6.610, 10\
a', 6.610, 41\
...
Equivalent=a, a'\
````

means that the a and a' are equivalent.

Liting equivalence is important in the perspective of the refinement of
NMR parameters by best fit of simulated and experimental spectra.

For example, in a phenyl group where o, m and p, correspond to the
*ortho*, *meta* and *para* protons:

````
>  <NMREDATA_ASSIGNMENT>
...
o, 6.610, 10\
o', 6.610, 14\
m, 7.540, 11\ 
m', 7.540, 13\ 
p, 7.310, 12\
...
Equivalent=o, o'\ 
Equivalent=m, m'\
````

means that the o and o' are m and m' and are equivalent. This allows to
provide different couplings for J(m,o) than for J(m,o') which could not
be distinguished if a single label was used for both *ortho* protons.

See also equivalent coupling in the NMREDATA_J tag.

#### <NMREDATA_J>

If scalar couplings were measured and assigned, a <NMREDATA_J> tag
should be generated to list the couplings. This facilitates the
construction of the coupling network, a very powerful tool to verify
structures.

When known, the signs of the coupling constants should be specified,
otherwise the absolute values are listed.

The list can contain only J<sub>H,H</sub>, or only
<sup>1</sup>J<sub>C,H</sub>, or a mix of any type of scalar coupling
(the label indicates the isotope through the NMREDATA_ASSIGNMENT table –
see above).

````
`>  `<NMREDATA_J>
`a, b, 7.00`<span style="color:#080808">**`\`**</span>
`A, a, 150.3`<span style="color:#080808">**`\`**</span>
`B, a, 7.50`<span style="color:#080808">**`\`**</span>
````

The number of bonds can be added after the keyword "nb=".

````
`>  `<NMREDATA_J>
`a, b, 7.00, nb=3`<span style="color:#080808">**`\`**</span>
`A, a, 150.30, nb=1`<span style="color:#080808">**`\`**</span>
`B, a, 7.50, nb=3`<span style="color:#080808">**`\`**</span>` `
````

Alternatively comments can be used to specify the type of coupling, but
this is not part of the format, this is only to facilitate the work of
software developers.

````
`>  `<NMREDATA_J>
`a, b, 7.00 ;`<sup>`3`</sup>`JHH`<span style="color:#080808">**`\`**</span>
`A, a, 150.3 ;`<sup>`1`</sup>`JCH`<span style="color:#080808">**`\`**</span>
`B, a, 7.50 ;`<sup>`3`</sup>`JCH`<span style="color:#080808">**`\`**</span>
````

This may include J<sub>H,H</sub> (from 1D <sup>1</sup>H, or from COSY)
and/or J<sub>C,H</sub> from RDC measurements, long-range JCH from HMBC,
etc. These values may also be listed in the fields of the individual
spectra they originate from. In this “J” tag, there are “compiled” (with
average for example when a J<sub>A,X</sub> is not the same on the A and
X multiplets or if couplings are present in 1D <sup>1</sup>H and COSY).
This can also include coupling to <sup>19</sup>F, <sup>31</sup>P if the
label corresponds to such atom (see NMREDATA_ASSIGNMENT table). Note
that this table is compiling data from other spectra. It does not mean
that coupling should not be listed in each spectrum where they are
observed.

For the <sup>1</sup>H and <sup>19</sup>F of 1,3,5-trifluoro benzene:

````
`>  `<NMREDATA_ASSIGNMENT>
`a, 8.301, 7\`
`b, 8.301, 8\`
`c, 8.301, 9\`
`F1, 118.301, 10\ `
`F2, 118.301, 11\`
`F3, 118.301, 12\`
`Equivalent a, b, c\  `
`Equivalent F1,F2,F3\ `
`...`
`>  `<NMREDATA_J>
`a, F1, 17.00 ;`<sup>`3`</sup>`J`<sub>`H,H`</sub><span style="color:#080808">**`\`**</span>` `
`a, F2, 17.00 ;`<sup>`3`</sup>`J`<sub>`H,H`</sub><span style="color:#080808">**`\`**</span>
`a, F3, 7.00 ;`<sup>`5`</sup>`J`<sub>`H,H`</sub><span style="color:#080808">**`\`**</span>
`b, F2, 17.00 ;`<sup>`3`</sup>`J`<sub>`H,H`</sub><span style="color:#080808">**`\`**</span>` `
`b, F3, 17.00 ;`<sup>`3`</sup>`J`<sub>`H,H`</sub><span style="color:#080808">**`\`**</span>
`b, F1, 7.00 ;`<sup>`5`</sup>`J`<sub>`H,H`</sub><span style="color:#080808">**`\`**</span>
`c, F3, 17.00 ;`<sup>`3`</sup>`J`<sub>`H,H`</sub><span style="color:#080808">**`\`**</span>` `
`c, F1, 17.00 ;`<sup>`3`</sup>`J`<sub>`H,H`</sub><span style="color:#080808">**`\`**</span>
`c, F2, 7.00 ;`<sup>`5`</sup>`J`<sub>`H,H`</sub><span style="color:#080808">**`\`**</span>
`Equivalent a/F1,a/F2,b/F2,b/F2,c/F3,c/F1 `
`Equivalent a/F3,b/F1,c/F2`
````

for the protons of Cl-CH2-CH2-Br

````
`>  `<NMREDATA_ASSIGNMENT>
`a, 3.301, 5\`
`a', 3.301, 6\`
`b, 4.301, 7\ `
`b', 4.301, 8\`
`Equivalent a, a'\  `
`Equivalent b,b'\ `
`...`
`>  `<NMREDATA_J>
`a, b, 7.00\`
`a', b', 7.00\`
`a', b, 5.00\`
`a, b', 5.00\`
`Equivalent a/b, a'/b' `
`Equivalent a/b', a'/b`
````

Individual spectra tags
-----------------------

There is one SDF tag per spectrum in the NMR record.

The Larmor frequency of the detected isotope (Larmor) and the link to
the spectra (Spectrum_Location) are mandatory. Additional information
may be included (such as pulseprogram name, etc. *see below*). The
second part of the tag lists the signals.

Example of a 1D spectrum:

````
`>  `<NMREDATA_1D_1H>
`Larmor=500.13\`
`Pulseprogram=zg30\`
`Spectrum_Location=`[`file:./nmr/10/1/pdata/1\`](file:./nmr/10/1/pdata/1\)
`Signal 1\`
`Signal 2\`
`...`
````

For other isotopes:

````
`<NMREDATA_1D_`*`isotope`*`> `
````

Each 1D "signal" line start with a chemical shift (x.xxxx) or a
**chemical shift range** (x.xxxx-y.yyyy) (note: use four digits !!!).

Then follows the signal attributes characterizing the signal. (see below
for details)

For 2D spectra the general format is

````
<NMREDATA_2D_`*`IndirectIsotope_CodeMixing_DirectIsotope`*`> 
````


Example of HSQC spectrum:

````
`>  `<NMREDATA_2D_13C_1J_1H>
`Larmor=125.7567\`
`Spectrum_Location=`[`file:./nmr/11/1/pdata/1\`](file:./nmr/11/1/pdata/1\)
`C1/H-C1\`
`C2/H-C2\`
`...`
````

Definition of the [signal attributes for 1D
spectra](/1D_attributes "wikilink").

Definition of the [signal attributes for 2D
spectra](/2D_attributes "wikilink").

### Link to the spectra

For all experimental spectra, a link to the spectrum must be provided.
The spectrum must either be included in the NMReDATA file or be stored
in a permanently open and electronically accessible NMR database. By
spectrum, we mean the actual data of the spectrum (“2rr” , but also the
acquisition and processing parameters “fid/ser”, “acqus”, “procs”,
“proc2s”, etc.) in the manufacturer's format. The location of the record
is given in the NMREDATA_1D tag.

`Spectrum_Location=`[`file:./nmr/10/1/pdata/1`](file:./nmr/10/1/pdata/1)` `

The spectra are given in the native format of the manufacturer of the
spectrometer.

In order to avoid the spectrum refer to internet accessible spectra:

`Spectrum_Location=`[`https://www.dropbox.com/s/676w3chdbdf81kf/dj_GE425_DMSO_couplings_ax_eq_MP.zip?dl=0`](https://www.dropbox.com/s/676w3chdbdf81kf/dj_GE425_DMSO_couplings_ax_eq_MP.zip?dl=0)` ./nmr/10/1/pdata/1 `

In principle only DOI-based references are allowed in order to insure
long-term stability:

`Spectrum_Location=`[`https://zenodo.org/record/1146869/files/sample1.zip?download=1`](https://zenodo.org/record/1146869/files/sample1.zip?download=1)` ./djhap_benapyr/10/1/pdata/1 `

In the absence of consensus on Jcamp format to use for NMR spectra,
**Jcamp format for the spectra are not supported as source of
experimental spectra**.


However, it is suggested that as additional information the JCAMP
spectrum may be included too in the NMReDATA file. This will allow to
display the spectrum in a graphical, interactive way and even to link
the peaks to atoms in the molecular structure. A draft proposal to do so
is to provide the location and file name in a line starting with

`Jcamp_location=file:`

Note that in the file path (relative to the root of the zipfile)
backslashes are not allowed; only forward slashes.

### Ambiguous assignment of signals (ONLY WITH LEVEL\>0)

**ONLY WITH LEVEL\>0** In case of ambiguous assignment, the list of the
labels of the possible assignments are given in parentheses. For
example:

`4.8, L=(a|b)\`

means that the signal at 4.8 is assigned either to a or b. We need this
option to have the possibility to provide ambiguous data because they
are quite common, in particular in 2D spectra. This possibility will
cause difficulties when reading data for display, structure
verification, etc. Programmers will decide what to do: ignore ambiguous
assignment, try to resolve them, report them as such, warn about their
presence, etc.

### 1D spectra

##### <NMREDATA_1D_1H>

Example:

MD5 are not mandatory, but recommended if they can be easily generated

````
`>  `<NMREDATA_1D_1H>` `
`Larmor=500.13\`
`MD5_1r=5E77AB5838AA4C860BA8884A5B0BD9ED\`
`MD5_fid=ED8AD88199996436B40AAE283F0FB6F6\`
`4.8000, S=q, N=2, L=a, J=7.00\`
`2.1000, S=bs, N=1, L=b\`
`1.5000, S=t, N=3, L=c, J=7.10\`
````

where N is the number of protons, S the multiplicity, *etc*. More
details about the [attributes of 1D spectra](/1D_attributes "wikilink")
(N=, S= , etc.).

For multiple coupling:

````
`4.8000, S=dd, N=1, L=a, J=9.30, 4.89\`
````

Note that the coupling can be [assigned](/1D_attributes "wikilink").

Only the first number (the chemical shift) is mandatory. The other
fields are all optional. Because of overlap, there may be more than one
signal assigned to a chemical shift (or range of chemical shifts). They
are simply listed with "," as separator.

````
7.200-7.600, N=5, L=H-C1, H-C2, C-C4\
````

One reason for having chemical shifts listed in the
<NMREDATA_ASSIGNMENT> tag: is that signals may overlap and be given as a
range in the 1H 1D spectrum, but may be clearly determined from HSQC,
COSY, etc.

Ranges are accepted as small-to-large and large-to-small:

````
7.200-7.600, N=5, L=H-C1, H-C2, C-C4\
7.600-7.200, N=5, L=H-C1, H-C2, C-C4\
````

For the results of diffusion measurements, Diff, etc. are given in the
[proper units](/1D_attributes#Diff.3D_Diffusion_rate "wikilink"):

````
4.8, S=q, N=2, L=a, Diff=1.7e-11
````

Chemical shifts are given in ppm with four digits after the period (the
usual 3 is not enough at high field and high resolution!)

Integrals (E=...) can use any relative numbers, but preferably rescaled
to correspond to the number of protons (1.0 for the reference) or to
correspond to concentration when quantification was made (in mM). This
will be very useful when analysing mixtures. Integrals should not be
rounded up/down to the number of atoms: the values should reflect the
experimental values. If the 1D spectrum is homodecoupled at a given
chemical shift or totally decoupled (pureshift) one of the two following
lines should be added:

````
Decoupled=1H, 1.2\
Decoupled=1H\
````

If other spins are decoupled add:

````
Decoupled=19F\
...
````

...

##### <NMREDATA_1D_13C> etc.

1D <sup>13</sup>C spectra and other heteronuclear spectra (nuclei X)
````
>  <NMREDATA_1D_13C>
Larmor=125.0\
Decoupled=1H\
51.812, I=118.0\
20.123, I=123.1\
````

When the 1D X spectrum is not obtained from a simple pulse-detection
sequence (i.e. DEPT, APT, etc.) this is specified using an additional
label “Sequence”:

````
>  <NMREDATA_1D_13C>` or other isotopes
Larmor=125.0\
Decoupled=1H\
Sequence=DEPT135 (or DEPT45, DEPT90, ATP)\
Pulseprogram=dept135 \
51.812, I=-80.1\
20.123, I=123.1\
````

The peak intensity provides the signs of the DEPT-135 signal.

##### Selective 1D spectra

Selective 1D spectra, such as selective-NOESY or selective-TOCSY, etc.
use tags with names encoded similarly to 2D spectra:

````
>  <NMREDATA_1D_1H_D_1H>
Larmor=500.13
CorType=NOESY
F1_selected_window=2.500
Pulseprogram=selnogp
1.812, I=4.2E4
2.323, I=5.2E4
````

The tag name (1D_1H_D_1H) indicate that the source spin (first "1H") of
the NOE is a <sup>1</sup>H, that the mixing is of type "D" (Dipolar
coupling for NOE effect) and that the detection (second "1H") is done on
the <sup>1</sup>H channel.

For sel-TOCSY, the tag name would be

````
>  <NMREDATA_1D_1H_TJ_1H>
````

For selectively relayed magnetization from <sup>19</sup>F to
<sup>1</sup>H:

````
>  <NMREDATA_19F_1J_1H>
````

The position of the selective pulse in the first pseudo dimention is
specified with the keyword "F1_selected_window":

When multiple spectra are recorded, tags are numbered with "\#2", etc.
to avoid having multiple tags with the same name:

````
>  <NMREDATA_1D_1H_D_1H>
...
````


````
>  <NMREDATA_1D_1H_D_1H#2>
...
````


````
>  <NMREDATA_1D_1H_D_1H#2>
...
````

### 2D spectra

````
>  2D HSQC <NMREDATA_2D_13C_1J_1H>
Larmor=500.13\
MD5_2rr=5E77AB5838AA4C860BA8884A5B0BD9ED\
MD5_ser=ED8AD88199996436B40AAE283F0FB6F6\
CorType=HSQC ;(COSY; HSQC; HMBC; H2BC; TOCSY; NOESY)\
Pulseprogram=XXX\
a/C1, I=1.2\
b/48.43, I=1.2\
````

The Larmor frequency is the one of the detected isotope (last in the tag
label). “Types” and “Pulseprogram” can be specified.

More details about the [attributes of 2D
spectra](/2D_attributes "wikilink").

When signals are assigned, only their labels are given (no chemical
shifts). If a crosspeak is reported without assignment or partial
assignment, the chemical shift replaces the signal’s label. The
intensity of the signals (following “I=”. This simply corresponds to the
intensity of the spectrum at (or very close to) the coordinates of the
signals. They should be provided when possible (that is when the
software has them accessible). But this is not part of the format. i.e.
one should be able to read the .sdf files even in the absence of
intensities. The intensities are given in any arbitrary unit (integer of
floating point). If the signal has a shape such that the intensity is
zero at that center (phase sensitive COSY, for in the middle of a
doublet in HSQC, for example) the intensity can be the one at the
maximum amplitude of the multiplet. This intensity is not pretending to
be “quantitative”. Optional integration of the volume encouraged using
“S=” but this requires some “analysis” of the peak shape.

MD5 are not mandatory, but recommended if they can be easily generated

#### 2D HSQC <NMREDATA_2D_13C_1J_1H>

Here is an example of HSQC data:

````
>  2D HSQC <NMREDATA_2D_13C_1J_1H>
Larmor=500\
CorType=HSQC \
Pulseprogram=XXX\
a/C1, I=1.2\
b/48.43, I=1.2\
````

#### 2D HMBC <NMREDATA_2D_13C_NJ_1H>

Here is an example of HMBC data with two examples of ambiguous
assignment (could also occur in clusters of peaks):

````
>  <NMREDATA_2D_13C_NJ_1H>
Larmor=500.13\
C1/a; optional comment will be visible in the spectrum’s view
(C2,C3)/b, I=1.2\
C2/(b,c) , I=1.2\ 
C4,C5,C6)/(e,f) , I=1.2\
````

for HETCOR, the tag label would be

<NMREDATA_2D_1H_1J_13C>

to indicate that the first dimension in 1H and the detected dimension is
13C.

By default “2D” heteronuclear spectra are assumed to be
isotope1-decoupled during evolution of isotope2 and vice versa. If an
HSQC spectrum is recorded without 180 pulse during t1, or without 13C
decoupling during t2, (for RDC measurements for example) the following
lines should be added respectively:

`Nondecoupled=t1\`
`Nondecoupled=t2\`

If non-decoupled, or if the spectrum allows to measure couplings, the
heteronuclear couplings may be listed as :

`a/C1, Ja=155\`

(more details about the [attributes of 2D
spectra](/2D_attributes "wikilink")).

#### 2D COSY <NMREDATA_2D_1H_NJ_1H>

See discussion of COSY spectra (below) why using “Ja”.

A COSY spectrum will be coded with,

````
>  <NMREDATA_2D_1H_NJ_1H>
[CorType](/CorType "wikilink")=HSQC(COSY; HSQC; HMBC; ?? exact list is still to be defined. Consider this one tentative)
Larmor=500\
a/b, I=1.2, S=100\
b/a, I=1.2\
b/c, I=1.2\
c/b, I=1.2\
````

If couplings were measured from the cosy, the values should be specified

````
a/b, Ja=5\
where Ja means active coupling (present in f1 and f2)
where J1 means passive coupling(s) (present in f1).
where J2 means passive coupling(s) (present in f2).
````

Any number of couplings can be added. For example, the A-X crosspeak
with A and X coupling with M could be described as:

`A/X, Ja=5, J1=4, J2=2\`

Meaning that the active coupling JAX=5 Hz, the passive couplings JAM=4
Hz and JXM=2 Hz. If the assignment was made (as for 1D 1H), the assigned
couplings are specified:

````
A/X, Ja=5, J1=4(M), J2=2(M)\
A/X, Ja=5, J1=4(M), 6.1(K), J2=2(M), 3.1(K)\
````

This allows reporting the result of the analysis of high-resolution
DQF-COSY spectra or soft-COSY spectra. In this manner, high-resolution
COSY with coupling structures can be simulated for coupling constant
verification (refinement, including second-order effects, etc.). Note
that couplings can be obtained from the description of the 1D spectrum
if they were determined there. They should be included in the 2D fields
only if they were measured in the 2D spectrum. Note that, the program
generating these data should also generate a <J> tag (see above) to
compile J-couplings and present them in a manner that it is easier to
read.

#### 2D NOESY <NMREDATA_2D_1H_D_1H>

NOESY spectra will be described as:

````
>  <NMREDATA_2D_1H_D_1H>
Larmor=500\
a/b, I=1.2\
b/c, I=1.2\
````

#### 2D HOESY <NMREDATA_2D_19F_D_1H>

Heteronuclear <sub>19</sub>F-<sub>1</sub>H data would be in a tag called
if <sub>1</sub>H is detected and <sub>19</sub>F in F1:

````
>  <NMREDATA_2D_19F_D_1H>
````

#### Naming tags for *n*D

The structure of the name of the SD tag of spectra is constructed as
follows. It describes the pulse sequence.

````
1) The number of dimensions is given (e.g. “2D_...”)
2) Follows, the isotope of the first indirect dimension (e.g. “..._13C_...”)
3) Follows the code of the mixing to the next dimension (e.g. “..._1J_...”).
4) Finally, the detected isotope is given. (e.g. “..._1H”).
````

the TAG of the HSQC is therefore “<NMREDATA_2D_13C_1J_1H>”

Mixing can be:

````
1J for one bond (typ. HSQC)
NJ (multiple bound J, for cosy, hmbc)
TJ TOCSY
````

Examples:

````
2D_1H_NJ_1H    COSY/DQF-COSY
2D_1H_3QJ_1H   TQ-COSY (and other MQF)
2D_1H_EJ_1H    E-COSY/soft-COSY
2D_1H_RJ_1H    relayed cosy
2D_1H_TJ_1H    TOCSY
2D_13C_1J_1H   HSQC/HMQC/CT-HSQC
2D_13C_NJ_1H   HMBC
2D_13C_2J_1H   H2BC
2D_13C_1J(1H_J)_1H 2MBC (HSQC-COSY ?)
2D_13C_11CCJ_1H    1,1 adequate
2D_13C_N1CCJ_1H    n,1 adequate
2D_13C_1NCCJ_1H    1,n adequate
2D_13C_NNCCJ_1H    n,n adequate
2D_13C13C_1J_13C   2D-inadequate
2D_1H_D_1H NOESY 
2D_19F_D_1H    HOESY with 19F in F1 detection of 1H
2D_T1_1H   relax measurements
2D_F_1H    diffusion measurements
2D_13C_1J(1H_TJ)_1H    2D HSQC-TOCSY
2D_1H  J-res/DIAG/ d_resolved/SERF/G-SERF
3D_13C_1J_1H_TJ_1H 3D HSQC-TOCSY
3D_CO_1J_15N_1J_1H 3D-HNCO     
                       
````

For J-resolved and related experiments (DIAG, δ-resolved) where the
indirect dimension is not a chemical shift (no correlation present),
only the detected isotope is given.

````
2D_1H J-resolved
````

The spectrum is described as a 1D 1H spectrum (providing chemical shift,
couplings, etc.).