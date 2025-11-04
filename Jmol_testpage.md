---
title: Jmol testpage
permalink: /Jmol_testpage/
---

Note that I could not find a `includes/mime.types` file in main wiki
folder ...


Newer MW versions locate that in `includes/libs/mime/mime.types`

I may be related: I could not manage to allow the upload of .sdf .mol .
But .cml files works (I followed [these
instructions](https://www.mediawiki.org/wiki/Extension:Jmol#Installing_Jmol_Extension))

this works
----------

<jmolSmiles>aspirin</jmolSmiles>

`<jmolSmiles>aspirin</jmolSmiles>`

<jmolFile>Chair.cml</jmolFile>

`<jmolFile>Chair.cml</jmolFile>`

this also works...
------------------

<jmol>

` `<jmolApplet>
`   `<uploadedFileContents>`Chair.cml`</uploadedFileContents>
` `</jmolApplet>

</jmol> `<jmol>` `<jmolApplet>`
`<uploadedFileContents>Chair.cml</uploadedFileContents>` `</jmolApplet>`
`</jmol>`

this also works...
------------------

<jmol>

` `<jmolApplet>
`   `<name>`C`</name>` `
`   `<color>`lightGray`</color>` `
`   `<size>`400`</size>` `
`   `

<caption>

demo - note: needs at least one char on first line of inline content

</caption>

`   `<inlineContents>

Menthol OpenBabel02151916433D

31 31 0 0 0 0 0 0 0 0999 V2000

`   0.6797    1.2651   -0.2387 C   0  0  0  0  0  0  0  0  0  0  0  0`
`   1.3944   -0.0096    0.2024 C   0  0  0  0  0  0  0  0  0  0  0  0`
`   0.6695   -1.3027   -0.2371 C   0  0  2  0  0  0  0  0  0  0  0  0`
`  -0.8129   -1.2397    0.2137 C   0  0  1  0  0  0  0  0  0  0  0  0`
`  -1.5089    0.0539   -0.2208 C   0  0  0  0  0  0  0  0  0  0  0  0`
`  -0.7680    1.3033    0.2480 C   0  0  2  0  0  0  0  0  0  0  0  0`
`  -1.4711    2.5652   -0.2509 C   0  0  0  0  0  0  0  0  0  0  0  0`
`  -1.5752   -2.3115   -0.3340 O   0  0  0  0  0  0  0  0  0  0  0  0`
`   1.4325   -2.5688    0.2868 C   0  0  0  0  0  0  0  0  0  0  0  0`
`   0.7873   -3.8964   -0.1292 C   0  0  0  0  0  0  0  0  0  0  0  0`
`   2.8961   -2.5942   -0.1835 C   0  0  0  0  0  0  0  0  0  0  0  0`
`   1.2254    2.1343    0.1484 H   0  0  0  0  0  0  0  0  0  0  0  0`
`   0.7117    1.3341   -1.3336 H   0  0  0  0  0  0  0  0  0  0  0  0`
`   2.4050    0.0252   -0.2178 H   0  0  0  0  0  0  0  0  0  0  0  0`
`   1.5013   -0.0027    1.2947 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -1.6086    0.0630   -1.3151 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -2.5371    0.0569    0.1639 H   0  0  0  0  0  0  0  0  0  0  0  0`
`   0.6850   -1.3476   -1.3355 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -0.8654   -1.3281    1.3056 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -0.7714    1.3230    1.3457 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -1.4921    2.6034   -1.3455 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -0.9581    3.4631    0.1088 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -2.5048    2.6021    0.1085 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -1.4957   -2.2720   -1.3025 H   0  0  0  0  0  0  0  0  0  0  0  0`
`   1.4411   -2.5381    1.3844 H   0  0  0  0  0  0  0  0  0  0  0  0`
`   0.5863   -3.9212   -1.2054 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -0.1467   -4.0734    0.4111 H   0  0  0  0  0  0  0  0  0  0  0  0`
`   1.4390   -4.7445    0.1088 H   0  0  0  0  0  0  0  0  0  0  0  0`
`   2.9614   -2.5170   -1.2741 H   0  0  0  0  0  0  0  0  0  0  0  0`
`   3.3900   -3.5247    0.1184 H   0  0  0  0  0  0  0  0  0  0  0  0`
`   3.4778   -1.7803    0.2581 H   0  0  0  0  0  0  0  0  0  0  0  0`
` 1  2  1  0  0  0  0`
` 1 12  1  0  0  0  0`
` 1 13  1  0  0  0  0`
` 2  3  1  0  0  0  0`
` 2 14  1  0  0  0  0`
` 2 15  1  0  0  0  0`
` 3  4  1  1  0  0  0`
` 3  9  1  0  0  0  0`
` 3 18  1  0  0  0  0`
` 4  5  1  0  0  0  0`
` 4  8  1  0  0  0  0`
` 4 19  1  1  0  0  0`
` 5  6  1  0  0  0  0`
` 5 16  1  0  0  0  0`
` 5 17  1  0  0  0  0`
` 6  1  1  0  0  0  0`
` 6  7  1  0  0  0  0`
` 6 20  1  1  0  0  0`
` 7 21  1  0  0  0  0`
` 7 22  1  0  0  0  0`
` 7 23  1  0  0  0  0`
` 8 24  1  0  0  0  0`
` 9 10  1  0  0  0  0`
` 9 11  1  0  0  0  0`
` 9 25  1  0  0  0  0`
`10 26  1  0  0  0  0`
`10 27  1  0  0  0  0`
`10 28  1  0  0  0  0`
`11 29  1  0  0  0  0`
`11 30  1  0  0  0  0`
`11 31  1  0  0  0  0`

M END

`   `</inlineContents>
` `</jmolApplet>

` `<jmolButton>
`   `

<script>

spacefill on

</script>

`   `<text>` spacefill `</text>
`   `<target>` C `</target>
` `</jmolButton>

` `<jmolLink>
`   `

<script>

spacefill 2%

</script>

`   `<text>` ball and stick `</text>
`   `<target>` C `</target>
` `</jmolLink>

` `<jmolCheckbox>
`   `<scriptWhenChecked>` spin on `</scriptWhenChecked>
`   `<scriptWhenUnchecked>` spin off `</scriptWhenUnchecked>
`   `<checked>` false `</checked>` `
`   `<text>` spin `</text>
`   `<target>` C `</target>
` `</jmolCheckbox>

` `<jmolMenu>
`   `<target>` C `</target>
`   `<item>
`     `<text>` color CPK `</text>
`     `<checked>` true `</checked>
`     `

<script>

color cpk

</script>

`   `</item>
`   `<item>
`     `<text>` blue `</text>
`     `

<script>

color dodgerBlue

</script>

`   `</item>
`   `<item>
`     `<text>` green `</text>
`     `

<script>

color green

</script>

`   `</item>
` `</jmolMenu>

` `<jmolRadioGroup>
`   `<target>` C `</target>
`   `<vertical>`false`</vertical>
`   `<item>
`     `<text>` color CPK `</text>
`     `<checked>` true `</checked>
`     `

<script>

color cpk

</script>

`   `</item>
`   `<item>
`     `<text>` blue `</text>
`     `

<script>

color dodgerBlue

</script>

`   `</item>
`   `<item>
`     `<text>` green `</text>
`     `

<script>

color green

</script>

`   `</item>
` `</jmolRadioGroup>

</jmol>

Using script
------------

<jmol>

` `<jmolApplet>
`   `<name>`A`</name>` `
`   `

<title>

This box might hold a 3D model

</title>

`   `<color>`blueTint`</color>` `
`   `<size>`500`</size>` `
`   `

<script>

echo Hi there!

</script>

` `</jmolApplet>

</jmol>

``
`<jmol>`
`  <jmolApplet>`
`    <name>A</name> `
`    <title>This box might hold a 3D model</title> `
`    <color>blueTint</color> `
`    <size>500</size> `
`    <script> echo Hi there! </script>`
`  </jmolApplet>`
`</jmol>`

</tr>

Using urlContents
-----------------

<jmol>

` `<jmolApplet>
`   `<name>`B`</name>` `
`   `

<title>

A file retrieved from the PDB

</title>
<caption>

Murine adipocyte lipid binding protein at pH 4.5 (1AB0.pdb)

</caption>

`   `<color>`blueTint`</color>` `
`   `<size>`300`</size>` `
`   `<urlContents>` `[`https://files.rcsb.org/download/1ab0.pdb.gz`](https://files.rcsb.org/download/1ab0.pdb.gz)` `</urlContents>
`   `<pspeed>`2`</pspeed>` `
`   `<controls>`spin popup`</controls>` `
` `</jmolApplet>

</jmol>