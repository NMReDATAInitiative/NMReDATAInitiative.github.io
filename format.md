# NMReDATA initiative
*generate, store and share the data extracted from a set of NMR spectra associated to a compound*

***

[Home](/) **/** [Who are we](/partners) **/** **The Format** **/** [Compatible software and webtools](/Compatible_software "Compatible software") **/** [In the news ...](/timeline)

***

**Format main page** **/** [Format of the NMREDATA tags (version 1.0/1.1)](/NMReDATA_tag_format) **/** [Format of the NMREDATA tags (version 2.0)](/NMReDATA_tag_format_2_0) **/** [1D Attributes](/1D_attributes) **/** [2D Attributes](/2D_attributes) **/** [Examples](/Examples)

***

**Quick links**

Tentative instruction for [journal submission of NMReDATA](/Submission_NMReDATA "link").

Link to the [GitHub page](https://github.com/NMReDATAInitiative) of the NMReDATA Initiative.

Publication on V1.1 of the format: <span style="color: rgb(255, 147, 0); font-family: Georgia;">[MRC feature article presenting the format](https://onlinelibrary.wiley.com/doi/abs/10.1002/mrc.4737)</span>

<span style="color: rgb(4, 51, 255); font-family: Georgia;">Demonstration data and NMReDATA compatible software: [GitHub page of the Initiative](https://github.com/NMReDATAInitiative)</span>

Introduction
============

The [NMReDATA working group](/partners)
decided to include data extracted from NMR spectra of small molecules in
[SDF files](/Sdf_files "link") using SD tags.

Link to the [MRC article](https://onlinelibrary.wiley.com/doi/abs/10.1002/mrc.4737) on
the NMReDATA format.

An important task of the group is to define the format of the content of
the "\<NMREDATA_...\>" tags. [More details here!](/NMReDATA_tag_format "link").

The version 1.0 has been decided in September at the "Round table" of
the Smash 2017 conference at Baveno, Italy.

The SDF file alone (that is without the spectra) cannot be used to
verify that the assignment corresponds to the spectra. It is therefore
important to always have the spectra with the SDF file! We call *"NMR Record"* the combination of the spectra and the SDF file.

A 1.1 version was released to fix a problem in 1.0.

Version 2.0 adds extensions and was released after the [1st NMReDATA symposium](/symposium2019/Symposium2019 "link") (Sept. 16 2019, Porto, Portugal).

NMR records
===========

We call "NMR record", a folder (or .zip file including the folder) or a
database record including:

1\) All the NMR spectra (including FID, acquisition and processing
parameters). The format of these data is as produced by the manufacturer
of the instrument which acquired the data. That means that software
generating the data either has these crude data available or it will ask
the user to point to the crude data in order to include them in the *NMR record*.

2\) The SDF file(s) including the NMReDATA (*.nmredata.sdf* file)

A more detailed picture was presented in
July at the Euromar 2017. **Note:** The NMREDATA tag "SIGNALS" was
renamed "ASSIGNMENT" in Version 0.98.

<!-- NMR records will be [requested by *Magnetic Resonance in Chemistry*](http://onlinelibrary.wiley.com/doi/10.1002/mrc.4631/full)
from 2018 on. The editors of software (ADC/Labs, Bruker, cheminfo,
Mestrelab) are able to grenerate MNR records. --> 

Records will be either analysed on web pages, or downloaded, and the
nmredata.sdf file opened by the software which will access automatically
to the associated spectra.

The full description can be found [in the NMReDATA tag format page](/NMReDATA_tag_format).

<!-- An example (**probably obsolete**) of .nmredata.sdf files with the
spectra can be found
[here](https://www.dropbox.com/sh/hu0qudy2bt56ix0/AACc8UiUoeEskSDVhYnP-cZna?dl=0)-->

A better source is the [GitHub example page](https://github.com/NMReDATAInitiative/Examples-of-NMR-records) of
the [GitHub page of the Initiative](https://github.com/nmredatainitiative).

Mixtures of compounds
---------------------

When more than one compound is present in a sample, multiple .sdf are
produced and called compound1.nmredata.sdf, compound2.nmredata.sdf, etc.

Current version of the format of NMReDATA
=========================================

The format can be found here : [NMReDATA tag format](/NMReDATA_tag_format)

Various examples of NMReDATA files can be found in the [github repository](https://github.com/NMReDATAInitiative/Examples-of-NMR-records).

Database
========

The NMReDATA Inititiative define the format and rules for hosting and
provide data, but hosting data is not part of our mission.

Discussion [about database providers](/Database_policy).

Versions
========

Comments about [Version 0.98](V0.98)

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

For details, see [the specification](/NMReDATA_tag_format_2_0).

Changes to Versions 3.0
-----------------------

Makes NMReDATA records RO-Crate and FAIRSpec compatible.

Changes to Versions 3.1 (future version)
----------------------------------------

<span style="color:#FF8C00"> ''Future version of the format! Suggestions
are welcome! '' </span>

- Possibility to include (coupling network and J-graph data).
- Correct imperfections and consider how the format can accommodate solid-state NMR data, DFT-GIAO spectra, literature data.
- Consider the use of JCAMP format as open format for the spectra.

Discussion and complete list on [future versions of the NMReDATA format](/Future_version)

Consolidation of the Initiative
-------------------------------

The Initiative will be professionalized in order to propose a  service for the validation of NMR Records and present the NMReDATA at conferences

![logo](images/pasted-file_med.png) [Contact (Stefan Kuhn)](mailto:nmrshiftdb2-admin@uni-koeln.de)
