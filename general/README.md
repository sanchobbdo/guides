![image](https://dl.dropboxusercontent.com/u/2402696/external/logo-sancho.png)

#General Style Guide

*version 1.0.0*

##Table of Contents
1. [**Introduction**](#introduction)
1. [**General Formatting Rules**](#general-formatting-rules)
	- [Indentation](#indentation)
	- [Trailing whitespace](#trailing-whitespace)
	- [Blank Lines](#blank-lines)
1. [**General Meta Rules**](#general-meta-rules)
	- [Encoding](#encoding)
	- [Comments](#comments)
	- [Action items](#action-items)
	- [Versioning](#versioning)
1. [**Contributors**](#contributors)
1. [**License**](#license)

##Introduction

This document defines general purpose formatting and style rules. It aims at improving collaboration, code quality, and enabling supporting infrastructure. It applies to raw, working files. Tools are free to obfuscate, minify, and compile as long as the general code quality is maintained.

Unless otherwise noted, projects must apply this guidelines and IDEs must be tuned up to follow them.

**[[⬆]](#table-of-contents)**

##General Formatting Rules

###Indentation

Indent by 4 spaces at a time.

Don’t use tabs or mix tabs and spaces for indentation.

HTML

```html
<ul>
∙∙∙∙<li>Fantastic
∙∙∙∙<li>Great
</ul>
```

CSS

```css
.example {
∙∙∙∙color: blue;
}
```

**[[⬆]](#table-of-contents)**

###Trailing whitespace

Remove trailing white spaces.

Trailing white spaces are unnecessary and can complicate diffs.

```html
<!-- Not recommended -->
<p>What?∙∙∙∙

<!-- Recommended -->
<p>Yes please.
```

**[[⬆]](#table-of-contents)**

###Blank lines

Never use more than a single blank line to separate lines of codes.

```html
<!-- Wrong -->
<h1>My title</h1>
∙∙∙∙
∙∙∙∙
<p>My paragraph</p>

<!-- Good -->
<h1>My title</h1>
∙∙∙∙
<p>My paragraph</p>
```

Never use trailing blank lines at the end of the file.

```html
<!-- Bad -->
</html>
∙∙∙∙
∙∙∙∙
∙∙∙∙

<!-- Yep. -->
</html>
```

**[[⬆]](#table-of-contents)**

##General Meta Rules

###Encoding

Use UTF-8 (no BOM).

Make sure your editor uses UTF-8 as character encoding, without a byte order mark.

**[[⬆]](#table-of-contents)**

###Comments

Explain code as needed, where possible.

Use comments to explain code: What does it cover, what purpose does it serve, why is respective solution used or preferred?

> This item is optional as it is not deemed a realistic expectation to always demand fully documented code. Mileage may vary heavily for HTML and CSS code and depends on the project’s complexity.

**[[⬆]](#table-of-contents)**

###Action items

Mark todos and action items with ```TODO```.

Highlight todos by using the keyword ```TODO``` only, not other common formats like ```@@```.

Append a contact (username or mailing list) in parentheses as with the format ```TODO(contact)```.

Append action items after a colon as in ```TODO: action item```.

```html
<!-- TODO: remove optional tags -->
<ul>
  <li>Apples</li>
  <li>Oranges</li>
</ul>
```

**[[⬆]](#table-of-contents)**

###Versioning

How to number versions:

1.3.2: major=1 minor=3 patch=2

Typically you will see a real version, such as “1.2.0”

**[[⬆]](#table-of-contents)**


##Contributors

  - [View Contributors](../../../graphs/contributors)

##License

(The MIT License)

Copyright (c) 2013 Sancho BBDO

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
