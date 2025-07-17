---
layout: default
---

*Issues:*

Dont know how to make bold in code block
```
Replace:3
## <NMREDATA_VERSION>
with: *bold*
with: **bold**
<strong>bold text</strong>
with: <bold>bold</bold>
## \<NMREDATA_VERSION\>
```

````
Replace:4
## <NMREDATA_VERSION>
with: *bold*
with: **bold**
<strong>bold text</strong>
with: <bold>bold</bold>
## \<NMREDATA_VERSION\>
````


- In titles (with one or more #) the < and > char have to escaped using `\`
````
Replace:
## <NMREDATA_VERSION>
with:
## \<NMREDATA_VERSION\>
````
- For calls to other md pages, the *first* _only_ letter has to be set to its capital:
````
Replace:
[Link ...](main_Page).
with :
[Link ...](Main_Page).
````
- link to image

![sym.png](../extra/Hmbc_sym.png "png")

- For code blocks, replace the in-line with blocks:
````
Replace:
`a`
`b`
`c`
with (but ignore the \):
\````
a
b
c
\````
````

For now, please refer to the main normal web site at [nmredata.org](http://nmredata.org).

For now, please refer to the main wiki site at [nmredata.org/wiki](https://nmredata.org/wiki/Main_Page).



# Header 1

This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

## Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### Header 3
html try:

```HTML title="/src/components/HelloCodeTitle.js"
// Javascript code with syntax highlighting.
var fun = <bold>function</bold> lang(l) {
var fun = <!--<bold>function</bold>--> lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```


```md
// Javascript code with syntax highlighting.
var fun = *function* lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```md
// Javascript code with syntax highlighting.
var fun = <bold>function</bold> lang(l) {
var fun = <!--<bold>function</bold>--> lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```


```jsx title="title"
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```


```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
