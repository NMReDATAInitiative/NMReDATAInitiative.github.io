---
title: Jreader
permalink: /Jreader/
---

[*J_reader*](http://www3.uah.es/nmr_e_data/reader/reader.htm) is a
webtool for reading and editing NMReDATA files that can be accessed
through the web or [installed](/Jreader#Installation "wikilink") on a
local computer. In both cases, the program is running on the users's
computer. No data (structure, etc.) are sent to any server via the net.

**This page is under construction and will be improved...**

### Main features

-   Display the structure(s)
-   Display the data in the signal assignment tags (NMREDATA_ASSIGMENT)
-   Display the data in the J-coupling assignment tags (NMREDATA_J)
-   For each NMREDATA_1D tag, display the 1D spectrum if available in
    JCAMP format; additionally, the data found in the tag (chemical
    shifts, couplings) are displayed on top of the structure display.

This work was presented at the [1st NMReDATA symposium in Sept.
2019](/Symposium2019 "wikilink").

### 2D to 3D conversion

JSmol can display 3D structures
(<jmolSmiles text="example">aspirin</jmolSmiles>), but for now the
NMReDATA .SDF files include "flat" structures.

J_reader allows to start from the 2D model, add the implicit hydrogens
and generate an “optimized” 3D structure that may be added to the
original NMReDATA file and later saved to disk. The assignments and
couplings are remapped accordingly on the 3D model.

### Installation

For local installation:

Download [the J_reader
package](http://www3.uah.es/nmr_e_data/J_reader.zip) that contains a
copy of [the web
application](http://www3.uah.es/nmr_e_data/reader/reader.htm) and
ancillary files. Extract everything.


This download uses JSmol, a part of the full [Jmol
distribution](https://sourceforge.net/projects/jmol/files), version
14.29.46.

It does not include any of the sample files used for demonstration by
the web application.

The files should be arranged according to this schema:

-   `reader.htm` (the interface)
-   `combined.js` (utilities; contains code from jsTree, jQueryModal,
    AlertifyJS)
-   `combined.css` (ditto)
-   `img/` icons used in the page
-   `JSmol.min.js` (main file of the JSmol library)
-   `php/jsmol.php` (a component from JSmol library)
-   `js/JSmolJSV.js` (a component from JSmol library; other files in
    that folder are not needed)
-   `j2s/` (components forming the JSmol library; includes about 1300
    files and subfolders)

The application works well from a web server; from local disk, it will
work at least in some browsers. When running locally, due to security
policy of the browsers, loading of data files is restricted to the
folder where the htm file is (sometimes it works as well for subfolders
and parent folders). Additionally, some browsers will require setting
internal parameters (in [`about:config`](about:config) or equivalent
feature), like `security.fileuri.strict_origin_policy = false` or
`privacy.file_unique_origin = false`

### Funding

This development was funded, in part, by the University of Geneva, Gr.
D. Jeannerat, in spring 2019.

### Acknowledgements

We thank Marion Pupier for multiple examples of NMR records used for
this work.