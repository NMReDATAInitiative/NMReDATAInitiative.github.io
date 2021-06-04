---
title: Parser JSmol
permalink: /Parser_JSmol/
---

Introduction: using JSmol in a parser for NMReDATA zipfiles
-----------------------------------------------------------

*This page copies some contents in [Parser](/Parser "link") and
portions of [NMReDATA tag format](/NMReDATA_tag_format "link") with
added annotations of what is being implemented in the NMReDATA file
reader, HTML application using JSmol. It also includes the result of
email discussions.*

Reading the packaged contents
-----------------------------

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") The
content of the input is kept in memory so that it can be written later.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") Files
contained in the zipfile are listed in a folder and file tree on the
left column, alphabetically sorted. The tree is interactive in order to
display contents of those files.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") In the
case of file not found (filename called from a button) or non-zip
format, a warning is displayed.

Reading the SDF file
--------------------

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") The 3
header lines of the sdf file are displayed, for information, at the
bottom of the central section, for all models in the file.

[<File:Data-parser.png>](../extra/Data-parser.png "link_") *(For
debugging)* The full contents of the sdf file may be examined via the
right-click menu on the file tree.

### Several models

The SDF file may contain more than one structure, each one (molblock)
with its own tags. We expect that the NMReDATA tags will be included
only on the first model, but it might be otherwise.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") All
tags for all models are displayed in the central section, first the
group of NMReDATA tags and then the group with all other tags. If
needed, a number is added in front to identify the model number when
this is \>1.

The first model will usually be 2D. It is desirable to be 3D but this
will not always happen. Right now, we exepct the first model to be 2D
and, if available, a second model is the 3D structure.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") All
structure models are transferred to the JSmol panel, and displayed there
one at a time. Buttons are added below to switch the display from one
model to another. The 2D or 3D nature is detected using two methods: the
code in line 2 of the molblock (characters 21,22, according to the
MOL/SDF V2000 format specification) and the Z coordinates of all atoms.
The first takes precedence, but any discrepancies raise a warning.

It is important to keep any stereochemical information. Even in 2D data
the atoms may have extra information, i.e. for explicit hydrogen atoms
the chirality is given by the *fourth column* of the bond list in the
molblock (more precisely, characters 10 to 12, according to the MOL/SDF
V2000 format specification).

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK")
Explicit H atoms with stereo information in their bond are coloured
light salmon (*bisque*, bond up) or light blue (*powderBlue*, bond down)
in the JSmol structure. They are also moved 0.4Å up or down in the Z
axis direction for better viewing.

### Tags

The SDF files may contain diverse tags (not only the NMREDATA tags). Be
ready for the tags to appear in any order.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") They
are accepted in any order and are displayed as they arrive, except that
NMREDATA tags are grouped first. (We might sort them if needed)

All tags should be written in the output SDF file, keeping the original
order.

### Determine how to read the NMREDATA tags

Scan the tags and list the index of the ones including NMREDATA_ in
their name. Read the NMReDATA tags.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") Both
NMReDATA tags and any others are displayed, with their contents.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") Keep in
mind the end of line problem.

1.  Any <EOL> characters inside the tag contents are removed when this
    is parsed.
2.  Backslash is detected as the end-of-data-line, but it is removed for
    display.
3.  For convenience while displaying and editing, <EOL> is added at the
    end of each data-line.
4.  If the contents are edited, the backslash will be added back when
    storing the tag.
5.  A check detects the value of VERSION; if it is 1 (1.0), then the
    <EOL> must be preserved while reading.

### Read the NMREDATA tags

Many simple tags have no particular format. (NMREDATA_SOLVENT,
NMREDATA_VERSION, etc.)

But most "complex" tags (NMREDATA_ASSIGNMENT, NMREDATA_J, NMREDATA_1H,
etc.) all have a common general structure:

Two type of lines should be distinguished:

-   Property lines
-   Item from a list

The "property lines" contain a series of characters (letters) followed
the "=" sign followed by the value of the variable. They can be directly
used as name and value of object properties. The value should be read as
text , because they have to be revritten later when writing the .sdf
file ...

The "property lines" should be identified as such to distinguish them
from element of a list. Property lines should be located before the
list, but some may follow the list (not recommended, but possible).

**IMPORTANT**: Note that a property may appear more than once. In this
case, it should be read into an array (and be written in the same order
when writing the file).

The "Item from a list" have a format that depends on the tag. We have
four types of tags:

-   NMREDATA_ASSIGNMENT
-   NMREDATA_J
-   NMREDATA_1D_ ...
-   NMREDATA_2D_ ...

For NMREDATA_1D_ and NMREDATA_2D_ see
[1D_attributes](/1D_attributes "wikilink") and
[2D_attributes](/2D_attributes "wikilink").

We recommend the store the list as an array of array of characters, and
analyse it later. We suggest that when analysing a tag, each line is
tested to see if it is a "property line" (see the format above). If it
is not a property line, it is a item from a list.

This allows to have a single functions testing properties.

### Edit and save the NMREDATA tags

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") The
content of NMREDATA tags may be edited and will be immediately saved
into memory; eventually, if the file is saved, the updated tag will be
included. The effect of the change may be tested immediately on the
molecular structure, in the case of assignments and couplings.

Changed content supports only format according to version 1.1+

### Analyse the individual NMR tag

Depending on the program, what data will be extracted will vary, but all
Properties (whether they are understood or not) should be sent to the
output when writing the file. They don't need to be analysed. Same
argument for the properties of peaks. They should all be stored (even if
not understood) to be written later.

### <NMREDATA_ASSIGNMENT>

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") List of
assignments is read and displayed on the structure using labels on each
atom referenced. Labels for implicit Hydrogens are added to those of the
heavy atom, as 2nd, 3rd lines.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") Labels
must come enclosed in \<""\> when they include "," "/" "\\" "\|" or "&"
characters. All these have been tested and are properly working:

<table>
<tr>
<td>

    a
    H-C(1)
    Proton_1
    H'
    H<nowiki>''</nowiki>
    Ha or Hb

</td>
<td>

    <"Ha,Hb">
    <"Ha/Hb">
    <"Ha\Hb">
    <"Ha|Hb">
    <"Ha&Hb">
    <"Ha & Hb">

</td>
<td>

    <"Ha,Hb,Hc">
    <"Ha/Hb/Hc">
    <"Ha\Hb\Hc">
    <"Ha|Hb|Hc">
    <"Ha&Hb&Hc">
    <"Ha & Hb & Hc">

</td>
</tr>
</table>

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") The
possibility that the assignment may be vague. Interchangeable or
ambiguous assignment, with the keyword "Interchangeable=".

-   If such option is selected (drop-down menu), the labels of each pair
    of interchangeable atoms are painted in the same colour, different
    to the generic label colour. A warning alert is also displayed, with
    the count.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK")
Equivalent spins, with the keyword "Equivalent=".

-   If such option is selected (drop-down menu), the labels of each pair
    of equivalent atoms are painted in the same colour, different to the
    generic label colour. A warning alert is also displayed, with the
    count.

When there are two structures (e.g. 2D and 3D) in the same SDF file, we
might need one ASSIGNMENT tag per structure.

-   If the same atom labels are in both models, maybe just one
    ASSIGNMENT tag is valid.
-   They may also be different with respect to the "Interchangeable="
    lines. *This has not been examined, but most likely it can be solved
    by manual inspection and editing of the tag contents.*

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") This is
conflictive, and we will not do it in such a way. A second model needs
its own ASSIGNMENT tag and that's the one that will be applied. We are
expecting the 2nd model to be 3D and have the implicit H's included
explicitly, so they receive now their own labels. The new, modified, tag
is being created when 2nd model comes from the user-assisted 3D
generation routine in the reader.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK")
<NMREDATA_SIGNALS> (present in files using older versions of the format)
is detected and processed like <NMREDATA_ASSIGNMENT>. However, editing
the contents of this tag is not supported (i.e. any changes will not be
kept).

### <NMREDATA_J> (couplings)

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") This
tag includes atom labels defined in <NMREDATA_ASSIGNMENT>.

-   Couplings are displayed on the structure using a line that connects
    the two atoms involved.
-   Additionally, a label near the line displays the J value. (This may
    be hidden with a checkbox)
    -   Problem: when there are implicit Hydrogens involved in the
        coupling, the line may go to the respective heavy atom but needs
        to be differentiated. **Implemented:** two different colours;
        **implemented but not enabled:** different directions (z\>0,
        z\<0) for the lines.
    -   Problem: the heavy atom may not have a label in the Assignment
        tag. This makes it hard to draw the line pointing to it (in lieu
        of to its H atom). **Implemented**.
    -   Limitation: coupling of the 1JC-H type cannot be represented for
        implicit H. **Implemented:** the line comes out of the heavy
        atom, with its label showing the J value.
    -   Problem: too crowded. **Implemented:** a drop-down menu allows
        to limit the display to a subset: J(X,X), J(H,X), J(H,H) or
        J(H,H)\>3 Hz.
-   If present, display the "number of bonds" using different colours
    for the lines and labels. (Conflict with the colours for
    implicit/explicit H's). This might be possible, but is not yet
    implemented.

### <NMREDATA_1D_1H>

Spectrum data, also contains atom labels and couplings.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") If a
line starts with `Jcamp_location=file:` followed by the path to a file
in JCAMP format (inside the zipfile), the spectrum will be displayed in
the right-hand section at the same time the contents of the tag are
displayed in the central section.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK")

-   Coupling information inside the 1D_XX tags may be used for display
    instead of that coming from the J tag, via a drop-down menu.

[<File:Data-parser.png>](../extra/Data-parser.png "link_")

-   If there is content about couplings in the NMREDATA_J tag, should we
    ignore the coupling information inside the 1D_1H tag?
-   If the NMREDATA_J tag is empty (unassigned couplings),
    -   and the coupling information in 1D_1H does not include atom
        labels, what to display?


    `example: 4.1823, S=dd, N=1, L=a J=9.30,4.80;`

    -   and the coupling information in 1D_1H includes atom labels, try
        to display the coupled pairs of atoms on the structure.


    `example: 4.1823, S=dd, N=1, L=a J=9.30(b), 4.80(c);`
-   How to manage the display of couplings when there are several
    spectrum tags? (e.g. 1D_1H, 1D_13C, 2D_13C_1J_1H)

### <NMREDATA_ALATIS> (optional but desired)

Here should come the *ALATIS* code of the compound. (If possible, it
should be included!)

[<File:Data-parser.png>](../extra/Data-parser.png "link_")
Pre-implemented: access the ALATIS server, send the 2D SDF moldata and
retrieve both the 3D structure, the ALATIS Key code and the InChI.

Problem: the model coming from Alatis has lost the original atom
numbering, so we cannot use the assignments on it.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") A
button allows to transfer the ALATIS Key code and the InChI to newly
created NMReDATA tags.

Reading other files in the NMReDATA zipfile
-------------------------------------------

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") When
clicked on an item in the directory (file tree),

-   If the file is known to be in **plain-text** format, its content is
    displayed in the central section.

    Extensions: `txt, temp, output, info, par, xml, mol`

    Filenames:
    `acqu*, gpnam*, spnam*, proc*, title, pulseprogram, wave, *readme*`

    Specific (reserved for internal use): `JmolManifest`
-   If the file is known to be **binary**, its content cannot be
    displayed; an explanation warning is shown. Same when the file type
    is not known for sure.

    Filenames: `fid, ser, 1r, 1i, 2rr, 2ir, 2ri, 2ii, peaks`
-   The **spectrum thumbnail** is displayed (scaled ×2, `thumb.png`
    file, even several subfolder levels below) in the central column
    when:

:\* the file is named `thumb.png`, or

:\* the item is a subfolder with numeric name that contains a
`thumb.png` file, or

:\* the item is a subfolder named `pdata` that contains a `thumb.png`
file

-   **Images**: if the file has `gif, jpg, jpeg, png` extension, it is
    displayed in the central column.
-   **JCAMP spectrum**: if the item has a `dx, jdx, jcamp` extension,
    the spectrum is drawn in JSpecView within the rightmost column and
    also the plain text file contents in the central column.

Generation of a 3D molecular structure
--------------------------------------

Caveats:

-   Getting the proper stereo configuration is not possible in an
    automated way. We need a wizard manually assisted and validated by
    the user.
-   The added H atoms (now explicit) need to be relabelled in the
    ASSIGNMENT tag, J couplings tag or spectrum tags.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") Two
methods are currently available for calculating a reasonable 3D
structure. They also involve adding the implicit hydrogens which are not
included in the original 2D structure.

-   Sending the structure to the ALATIS server and retrieving the 3D
    structure data.



The model is good, but we can no longer use it for display of
assignments or couplings since the atoms are renumbered.

-   Using JSmol capabilities; 2 variants are being tested:

:\# Random push of the C's out of the z=0 plane + add hydrogens + short
optimisation + add hydrogens again + full optimisation.

:\# Find C's with 3 bonds to heavy atoms (these atoms seem to be those
with \*problems in the original simple method) + attach a new hydrogen
to them, positioned out of the z=0 plane + run a full optimisation.



Testing with different molecules is needed to decide which method is
better.

<!-- -->



In both cases, further runs of optimisation may be necessary, driven by
the user with the aid of numerical reports of the drop in energy
(convergence of he minimisation).

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") Once
the 3D model with added H atoms is accepted, the now explicit H atoms
are relabelled in the new ASSIGNMENT tag for this model. The new
labelling is also used for display of couplings on the 3D model.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") On the
3D model (before transfer to the main structure panel), the user may
pick atoms that will be tagged as either **interchangeable** or
**equivalent** in the resulting ASSIGNMENT tag for the 3D model.

*Pending:*

Addition of H's to CR<sub>2</sub> is particularly problematic:

-   No problem when the two H are isochronous and the two H's will
    receive the same label with and without primes. The option should be
    offered to add "a"/"b" labels, or else just allow edition of the
    labels.
-   When the two H are not isochronous, user intervention is required to
    assign them properly or, if the answer is unknown, to use the
    "Interchangeable=label1, labels\\" line in the ASSIGNMENT tag.
    Possibly four options:
    1.  correct
    2.  reverse (flip the two labels)
    3.  ignore (write no "interchangeable" line)
    4.  flag labels as Interchangeable

We could have a link to provide some additional explanation in a wiki
page. If this text could be in a separate file, it could be edited
easily without changing the "code" part of the page. (Nice for updates -
this is not necessary.)

Desirable: to display in a different style the bonds with unknown
chirality.

Question: is it necessary to modify the 2D file according to the result
of the 3D model and its labeling?

Resaving files
--------------

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") Any
modification of the contents (added or edited tags, added 3D structure,
added or removed files) may be saved as an NMReDATA package to a
zipfile.

[<File:Data-parser-ok.png>](../extra/Data-parser-ok.png "link_OK") The
changes applied (edited tags, 3D model added, files added or removed
from the package, manual assignment of interchangeable atoms) are
logged. The log may be checked at any time and is included as an extra
file when the modified package is saved.