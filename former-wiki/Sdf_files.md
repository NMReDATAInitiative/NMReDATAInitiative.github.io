---
title: Sdf files
permalink: /Sdf_files/
---

The SD Format
=============

In their simplest form, SDF files include a molecular structure in the
.mol format.

But SDF files offer more possibilities: they can include multiple
structures and add meta data called "Tags" below the "Mol Block" of the
file.

For more information on SDF format see ...

SDF tags
--------

A SDF tag, has the following structure:

`>  `<TAG_NAME>
`... tag content line 1 ... `
`... tag content line 2 ... `
`... tag content line 3 ...`
`[Empty line to indicate the end of the tag]`

For more information on SDF tags and how to read/write them see ...

SDF tags including NMR data
---------------------------

The working group decided to use a set of tags to include the NMR data
extracted from the NMR spectra in SDF files.

The labels of the NMReDATA tags all start with "NMREDATA_".

Direct link to page describing the [format of the "\<NMREDATA_...\>"
tags](/NMReDATA_tag_format "link").