---
title: End-of-line
permalink: /End-of-line/
---

In ordert to avoid the problem that CDK librairies ignore the
end-of-line (<EOL>, ASCII code 10) and sometimes add them in an
uncontroled manner. We introduced a reliable line separator. We use
backslash + <EOL> in NMReDATA tags) (In principle only the backslash is
necessary since the <EOL> should be ignored when parsing. But we request
using both for increased readability for humans.)

For version \>1 (only!) the usual <EOL> should be ignored.

Tag should look like this...

`>  `<NMREDATA_ASSIGNMENT>
`A, 48.3010, 1 ;the label "A" corresponds to atom one which is the carbon of the CH2`<span style="color:#0808F8">**`\`**</span>
`B, 20.3220, 2 ;atom two is the carbon of the CH3`<span style="color:#0808F8">**`\`**</span>
`a, 2.6100, H3 ;"H3" refers to the hydrogen atom of atom 3 (the oxygen)`<span style="color:#0808F8">**`\`**</span>
`b, 4.8020, H1 ;"H1" refers to the hydrogen atoms of atom 1 (of the CH2)`<span style="color:#0808F8">**`\`**</span>
`c, 1.4010, H2`<span style="color:#0808F8">**`\`**</span>

but it may look like this *(note how data items 2, 3 and 4 are split
across two lines)*

`>  `<NMREDATA_ASSIGNMENT>
`A, 48.3010, 1 ;the label "A" corresponds to the atom one which is the carbon of the CH2`<span style="color:#0808F8">**`\`**</span>
`B, 20.3220, `
`2 ;atom two is the carbon of the CH3`<span style="color:#0808F8">**`\`**</span>
`a, 2.61`
`00, H3 ;"H3" refers to the hydrogen atom of atom 3 (the oxygen)`<span style="color:#0808F8">**`\`**</span>
`b, 4.8020, H1 ;"H1" refers to the hydrogen `
`atoms of atom 1 (of the CH2)`<span style="color:#0808F8">**`\`**</span>
`c, 1.4010, H2`<span style="color:#0808F8">**`\`**</span>

Note: There will never be two consecutive <EOL>, because this is the
end-of-tag signal.

Conclusion: For V \> 1.0 the <EOL> should be ignored and then the "\\"
be replaced with <EOL>. When writing, the <EOL> should always come after
a backslash.