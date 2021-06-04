---
title: Main Page
permalink: /Main_Page/
---

**Quick links**

Direct link to the page describing the [format of the NMREDATA tags
(version 1.0/1.1)](/NMReDATA_tag_format "link") and [format of the
NMREDATA tags (version 2.0)](/NMReDATA_tag_format_2.0 "link").

List of [compatible software and
webtools](/Compatible_software "Compatible software")

Tentative instruction for [journal submission of
NMReDATA](/Submission_NMReDATA "link").

Link to the [GitHub page](https://github.com/NMReDATAInitiative) of the
NMReDATA Initiative.

Introduction
============

The [NMReDATA working group](http://www.nmredata.org/partners.html)
decided to include data extracted from NMR spectra of small molecules in
[SDF files](/Sdf_files "link") using SD tags.

Link to the [MRC
article](https://onlinelibrary.wiley.com/doi/abs/10.1002/mrc.4737) on
the NMReDATA format.

An important task of the group is to define the format of the content of
the "\<NMREDATA_...\>" tags. [More details
here!](/NMReDATA_tag_format "link").

The version 1.0 has been decided in September at the "Round table" of
the Smash 2017 conference at Baveno, Italy.

The SDF file alone (that is without the spectra) cannot be used to
verify that the assignment corresponds to the spectra. It is therefore
important to always have the spectra with the SDF file! We call *"NMR
Record"* the combination of the spectra and the SDF file.

A 1.1 version was released to fix a problem in 1.0.

Version 2.0 adds extensions and was released after the [**1st NMReDATA
symposium**](/Symposium2019 "link") (Sept. 16, Porto, Portugal).

NMR records
===========

We call "NMR record", a folder (or .zip file including the folder) or a
database record including:

1\) All the NMR spectra (including FID, acquisition and processing
parameters). The format of these data is as produced by the manufacturer
of the instrument which acquired the data. That means that software
generating the data either has these crude data available or it will ask
the user to point to the crude data in order to include them in the *NMR
record*.

2\) The SDF file(s) including the NMReDATA (*.nmredata.sdf* file)

[600px\|center\|NMR record](../extra/Nmr_record.png "png") A more
detailed picture (see [600px\|center\|pictorial representation of NMR
record and example of SDF file](/File:test-2.pdf "wikilink")) was
presented in the
[poster](http://nmredata.org/euromar_2017_v5_optimized.pdf) presented in
July at the Euromar 2017. **Note:** The NMREDATA tag "SIGNALS" was
renamed "ASSIGNMENT" in Version 0.98.

NMR records will be [requested by *Magnetic Resonance in
Chemistry*](http://onlinelibrary.wiley.com/doi/10.1002/mrc.4631/full)
from 2018 on. The editors of software (ADC/Labs, Bruker, cheminfo,
Mestrelab) are able to grenerate MNR records.

Records will be either analysed on web pages, or downloaded, and the
nmredata.sdf file opened by the software which will access automatically
to the associated spectra.

The full description can be found [in the NMReDATA tag format
page](/NMReDATA_tag_format "link").

An example (**probably obsolete**) of .nmredata.sdf files with the
spectra can be found
[here](https://www.dropbox.com/sh/hu0qudy2bt56ix0/AACc8UiUoeEskSDVhYnP-cZna?dl=0)

A better source is the [GitHub example
page](https://github.com/NMReDATAInitiative/Examples-of-NMR-records) of
the [GitHub page of the
Initiative](https://github.com/nmredatainitiative).

Mixtures of compounds
---------------------

When more than one compound is present in a sample, multiple .sdf are
produced and called compound1.nmredata.sdf, compound2.nmredata.sdf, etc.

Current version of the format of NMReDATA
=========================================

The format can be found here : [NMReDATA tag
format](/NMReDATA_tag_format "wikilink")

Various examples of NMReDATA files can be found in the [github
repository](https://github.com/NMReDATAInitiative/Examples-of-NMR-records).

Database
========

The NMReDATA Inititiative define the format and rules for hosting and
provide data, but hosting data is not part of our mission.

Discussion on [about database providers](/Database_policy "link")

Versions
========

Changes to Versions 1.1
-----------------------

-   [Addition of backslash](/End-of-line "link") at the end of the
    line of NMReDATA tags.

Changes to Versions 2.0
-----------------------

-   Possibility to include Jcamp spectra on top of original data from
    the instrument.
-   Possibility to add a 3D structure (on top of the "flat" 2D
    structure).
-   Possibility to add author and institution information (to facilitate
    integration of these metadata in repositories).

For details, see [the
specification](/NMReDATA_tag_format_2.0 "link").

Changes to Versions 2.1 (future version)
----------------------------------------

<span style="color:#FF8C00"> ''Future version of the format! Suggestions
are welcome! '' </span>

-   Possibility to include [J-coupling assignment
    data](/Jassign "link") (coupling network and J-graph data).

Discussion and complete list on [future versions of the NMReDATA
format](/Future_version "link")

Jmol integration in this wiki
-----------------------------

NMReDATA is being integrated with [Jmol/JspecView](/Jmol "link")