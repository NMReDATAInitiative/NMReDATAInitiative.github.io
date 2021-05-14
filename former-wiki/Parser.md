---
title: Parser
permalink: /Parser/
---

### Reading the SDF file

Libraries for divers languages exist to read SDF files. This section is
only relevant if you write your own reader/writer

We recommend having in mind, when reading, that an SDF file will have to
be written at some point later. We recommend to write tags in the same
oder as they apear in the .sdf file if you can control this, but don't
expect all writers to do so, so be ready for the tags to appear in any
order, but try to have them in the "right" order

If not too large, the content of the input should be kept in memory so
that it can be written later. Since SDF files may contain divers tags
(not only the NMREDATA tags) they should all be written in the output
SDF file.

We recommend to

-   Open the SDF file
-   Read/store the molblock as chain of characters
-   Read/store the TAGS as chain of characters
-   Close the file

Analyses/check the molblock if needed (see [possible object structure of
NMReDATA](/nmredata_object_structure "wikilink")).

### Determine how to read the NMREDATA tags

Scan the tags and list the index of the ones including NMREDATA_ in
their name

Read the NMReDATA tags (see below). Keep in mind the [end of line
problem](/end-of-line "wikilink").

First read and analyse the NMREDATA_VERSION to

-   determine what character should be ignored (ASCII 10, except for
    version 1)
-   determine the line separator

<!-- -->

-   -   For version 1: ASCII 10

Analyse directly the tag (hopen there is no missing/spourious ASCII 10
in the text)

-   -   For version \>1: "\\" + ASCII 10

Before analysing the text of the TAG, ignore ASCII 10 and replace "\\"
with ASCII 10.

### Read the NMREDATA tags

Many simple tags have no particular format. (NMREDATA_SOLVENT,
NMREDATA_VERSION, etc.)

But most "complex" tags (NMREDATAT_ASSIGNMENT, NMREDATA_J, NMREDATA_1H,
etc.) all have a common general structure:

Two type of lines should be distinguished:

-   Property lines
-   Item from a list

The "property lines" contain a serie of characters (letters) followed
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

The "Item from a list" have a format that depends on the tag. NMREDATA
defines simple tags with just one line of data, and four types of
complex tags:

-   NMREDATA_ASSIGNMENT
-   NMREDATA_J
-   NMREDATA_1D_ ...
-   NMREDATA_2D_ ...

For NMREDATA_1D_ and NMREDATA_2D_ see the caracteristics of lists:
[1D_attributes](/1D_attributes "wikilink") and
[2D_attributes](/2D_attributes "wikilink").

We recommend the store the list as an array of array of characters, and
analyse it later. We suggest that when analysing a tag, each line is
tested to see if it is a "property line" (see the format above). If it
is not a property line, it is a item from a list.

This allows to have a single functions testing properties.

### Analyse the individual NMR tag

Depending on the program, what data will be extracted will vary, but all
Properties (whether they are understood/analysed/exploited or not)
should be send to the output when writing the file. They don't need to
be analysed. Same argument for the properties of peaks. They should all
be stored (even if not understood/analysed/exploited) to be written
later.

### Labels

Keep it mind the
[possibility](/NMReDATA_tag_format#Labels_including_comma_or_other_special_characters "wikilink")
that labels are put in \<""\> and the assignment may be vague!

A good idea may be to convert all labels into index numbers as a
pre-parser (keeping a list of labels obviously) and then work with the
numbers. Finally replace the indices with the lablels when writing the
output. This will faciliate the cases where labels have special
caracters imposing the insert them in \<""\>.

Note that some labels may appear in the spectra (NMREDATA_1D... )
without being listed in the NMREDATA_ASSIGNMENT tag - because some may
not be assigned. So do not rely on the NMREDATA_ASSIGNMENT and
NMREDATA_J to have the full list of labels... you have to read all
spectra tags before.

Similarly, one can imagine situation where a label is used in the
NMREDATA_J tag, without being found in the NMREDATA_ASSIGNMENT tag.

Finally, note that the situation where a 2D peak is not given a label,
but a chemical shift value should not be a problem. This may occur when
a peak is not not assigned - or partially assigned.
[More](https://nmredata.org/wiki/2D_attributes#Examples_attributes_of_2D_signal).
In this case the label is the text of the chemical shift. This should be
fine - if not very elegant.

These reasons speak for a replacement of the labels, with label number
before making the true analysis of the NMREDATA tags.

### example of names and role of basic function reading NMReDATA

#### get_list_nmredata_files

list the nmredata.sdf file in the NMR record. Search in:

-   the root of the .zip file (./\*nmredata.sdf) and
-   the /nmredata folder (./nmredata/\*.sdf) if exist)

#### read_nmredata_tags

Extract all tags with names starting with "NMREDATA_" for the specified
nmredata.sdf file

Examples of zip files will be provided to developers.

#### get_parameters

Extract all the parameters of a NMReDATA tag (a line with a name
followed by "=")

`the name of the paramter is before the "=", the value is the string up to the EOF or the ";", the comment start from the ";" and the EOL. the comment should be stored. We should have two fields for each object: the value and the comment`

Examples of .sdf files will be provided to testers.

#### get_param(tag_number,parameter name,'float')

extract the value of the parameter and the comment. examples:

`get_param(1,"Larmor","float") Will extract the floating point from the string of the parameter Larmor. Also extract the comment`

#### get_assignment(tagnumber of NMREDATA_ASSIGNMENT, tagnumber of NMREDATA_J)

extract the chemical shifts and couplings (when present) from the
NMREDATA_ASSIGNMENT, and NMREDATA_J. Handle so that there is no error
when the tag do no exist or are empty.

-   subfunction to read the chemical structures
-   subfunction to read the label,chemical shift, atom number(or code
    for implicit H)
-   subfunction to check the consistency of atom number atom code and
    the mol block
-   subfunction to read the coupling (check labels make sens)
-   subfuction to read and code the "Equivalent" and "Interchangeable"
    from the two tags.

#### get_list_of_peaks_1Dtag(tag number)

extract the list of 1D signals and properties and comment

#### get_list_of_peaks_2Dtag(tag number)

extract the list of 2D signals and properties and comment

### example of names and role of basic function checking NMReDATA

#### check_chem_shift

check consistency of chemical shifts given in the ASSIGNMENT and J tags
with the values in the 1D_ and 2D_ spectra