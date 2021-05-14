---
title: Jmol testpage2
permalink: /Jmol_testpage2/
---

Pop-up models
-------------

A user action will open a popup window with a model.

<table style="width:100%;">
<tr>
<td style="vertical-align:top;">

### jmolFile tag

The link <jmolFile text='cyclohexane'>Chair.cml</jmolFile> will open a
popup window displaying Chair.cm taken from this wiki

`<jmolFile text='cyclohexane'>Chair.cml</jmolFile>`

</td>
<td style="vertical-align:top;">

### jmolMol tag

The link <jmolMol text='in your coffee'>caffeine</jmolMol> will open a
popup window displaying caffeine

`<jmolMol text='something in your coffee'>caffeine</jmolMol>`

and <jmolMol text='something in vinegar'>acetic acid</jmolMol>

</td>
</tr>
<tr>
<td style="vertical-align:top;">

### jmolSmiles tag

The link
<jmolSmiles text='nitrobenzene'>c1ccccc1\[N+\](=O)\[O-\]</jmolSmiles>
will open a popup window displaying nitrobenzene

`<jmolSmiles text='nitrobenzene'>c1ccccc1[N+](=O)[O-]</jmolSmiles>`

</td>
<td style="vertical-align:top;">

### jmolPdb tag

The link <jmolPdb text='adipocyte lipid binding protein'>1ab0</jmolPdb>
will open a popup window displaying 1ab0.pdb

`<jmolPdb text='adipocyte lipid binding protein'>1ab0</jmolPdb>`

</td>
</tr>
</table>
<table style="width:100%;">
<tr>
<td style="vertical-align:top;">

### jmolAppletButton tag

<jmol>

` `<jmolAppletButton>
`   `<urlContents>` `[`https://files.rcsb.org/download/1ab0.pdb.gz`](https://files.rcsb.org/download/1ab0.pdb.gz)` `</urlContents>
`   `

<title>

1AB0.pdb Murine adipocyte lipid binding protein at pH 4.5

</title>

`   `<text>` Adipocyte lipid binding protein`</text>
` `</jmolAppletButton>

</jmol>

</td>
<td style="vertical-align:top;">

### jmolAppletLink tag

<jmol>

` `<jmolAppletLink>
`   `<urlContents>` `[`https://files.rcsb.org/download/1ab0.pdb.gz`](https://files.rcsb.org/download/1ab0.pdb.gz)` `</urlContents>
`   `

<title>

1AB0.pdb Murine adipocyte lipid binding protein at pH 4.5

</title>

`   `<text>` Adipocyte lipid binding protein `</text>
` `</jmolAppletLink>

</jmol>

</td>
</tr>
</table>

Pop-in models
-------------

User action will insert a model within the page.

### jmolAppletInlineLink tag

Using urlContents <jmol>

` `<jmolAppletInlineLink>
`   `<urlContents>` `[`https://files.rcsb.org/download/1ab0.pdb.gz`](https://files.rcsb.org/download/1ab0.pdb.gz)` `</urlContents>
`   `

<title>

1AB0.pdb Murine adipocyte lipid binding protein at pH 4.5

</title>

`   `<text>` Adipocyte lipid binding protein `</text>
`   `<size>`250`</size>
`   `<color>`linen`</color>
` `</jmolAppletInlineLink>

</jmol>

In-page models
--------------

A model is inserted as part of the page at page load time.

### jmolApplet tag

<table style="width:100%;">
<tr>
<td style="vertical-align:top;">

#### Using uploadedFileContents

<jmol>

` `<jmolApplet>
`   `<name>`B`</name>` `
`   `

<title>

A model stored in a file in this wiki

</title>
<caption>

Chair conformation of cyclohexane

</caption>

`   `<color>`greenTint`</color>` `
`   `<size>`260`</size>` `
`   `<uploadedFileContents>` Chair.cml `</uploadedFileContents>
`   `<controls>`spin popup`</controls>` `
` `</jmolApplet>

</jmol>

</td>
<td style="vertical-align:top;">

#### Using urlContents

<jmol>

` `<jmolApplet>
`   `<name>`BB`</name>` `
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

</td>
</tr>
<tr>
<td style="vertical-align:top;">

#### Using inlineContents

<jmol>

` `<jmolApplet>
`   `<name>`C`</name>` `
`   `<color>`lightGray`</color>` `
`   `<size>`240`</size>` `
`   `

<caption>

This is 1-propanol

</caption>

`   `<inlineContents>` `

C3H8O APtclcactv02181912073D 0 0.00000 0.00000

`12 11  0  0  0  0  0  0  0  0999 V2000`
`   0.5267   -0.4947   -0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0`
`  -0.5950    0.5458   -0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0`
`  -1.9499   -0.1649    0.0000 C   0  0  0  0  0  0  0  0  0  0  0  0`
`   1.7922    0.1691    0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0`
`   0.4436   -1.1185    0.8900 H   0  0  0  0  0  0  0  0  0  0  0  0`
`   0.4436   -1.1185   -0.8900 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -0.5119    1.1696    0.8900 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -0.5119    1.1696   -0.8900 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -2.0330   -0.7887   -0.8900 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -2.0330   -0.7887    0.8900 H   0  0  0  0  0  0  0  0  0  0  0  0`
`  -2.7490    0.5764    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0`
`   2.5508   -0.4305   -0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0`
` 1  2  1  0  0  0  0`
` 2  3  1  0  0  0  0`
` 1  4  1  0  0  0  0`
` 1  5  1  0  0  0  0`
` 1  6  1  0  0  0  0`
` 2  7  1  0  0  0  0`
` 2  8  1  0  0  0  0`
` 3  9  1  0  0  0  0`
` 3 10  1  0  0  0  0`
` 3 11  1  0  0  0  0`
` 4 12  1  0  0  0  0`

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

spacefill 23%

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

</td>
<td style="vertical-align:top;">

#### Using wikiPageContents

<jmol>

` `<jmolApplet>
`   `<name>`D`</name>` `
`   `

<title>

Data read from the page Models/2-propanol

</title>

`   `<color>`yellowtint`</color>` `
`   `<size>`260`</size>` `
`   `

<caption>

This is 2-propanol

</caption>

`   `<wikiPageContents>` Models/2-propanol `</wikiPageContents>
` `</jmolApplet>

</jmol>

</td>
</tr>
<tr>
<td style="vertical-align:top;">

#### Using script

<jmol>

` `<jmolApplet>
`   `<name>`A`</name>` `
`   `

<title>

This box might hold a 3D model

</title>

`   `<color>`blueTint`</color>` `
`   `<size>`150`</size>` `
`   `

<script>

echo Hi there!

</script>

` `</jmolApplet>

</jmol>

</td>
<td style="vertical-align:top;">

``
`<jmol>`
`  <jmolApplet>`
`    <name>A</name> `
`    <title>This box might hold a 3D model</title> `
`    <color>blueTint</color> `
`    <size>150</size> `
`    <script> echo Hi there! </script>`
`  </jmolApplet>`
`</jmol>`

</td>
</tr>
</table>

....