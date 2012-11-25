![Nucleo logo](http://elnucleo.co/logoSmall.png)

#HTML/CSS Style Guide

*version 1.0.0*

##Table of Contents
1. [**Introduction**](#introduction)
1. [**General Style Rules**](#general-style-rules)
	- [Protocol](#protocol)
1. [**General Formatting Rules**](#general-formatting-rules)
	- [Indentation](#indentation)
	- [Capitalization](#capitalization)
	- [Trailing whitespace](#trailing-whitespace)
1. [**General Meta Rules**](#general-meta-rules)
	- [Encoding](#encoding)
	- [Comments](#comments)
	- [Action items](#action-items)
1. [**HTML Style Rules**](#html-style-rules)
	- [Document type](#document-type)
	- [HTML validity](#html-validity)
	- [Semantics](#semantics)
	- [Multimedia fallback](#multimedia-fallback)
	- [Separation of concerns](#separation-of-concerns)
	- [Entity references](#entity-references)
	- [Optional tags](#optional-tags)
	- [Type attributes](#type-attributes)
1. [**HTML Formatting Rules**](#html-formatting-rules)
	- [General formatting](#general-formatting)
	- [HTML quotation marks](#html-quotation-marks)
1. [**CSS Style Rules**](#css-style-rules)
	- [CSS validity](#css-validity)
	- [Using ID selectors](#using-id-selectors)
	- [ID and class naming](#id-and-class-naming)
	- [ID and class name style](#id-and-class-name-style)
	- [Type selectors](#type-selectors)
	- [Shorthand properties](#shorthand-properties)
	- [0 and units](#0-and-units)
	- [Leading 0s](#leading-0s)
	- [Hexadecimal notation](#hexadecimal-notation)
	- [Prefixes](#prefixes)
	- [ID and class name delimiters](#id-and-class-name-delimiters)
	- [Hacks](#hacks)
1. [**CSS Formatting Rules**](#css-formatting-rules)
	- [Declaration order](#declaration-order)
	- [Block content indentation](#block-content-indentation)
	- [Declaration stops](#declaration-stops)
	- [Property name stops](#property-name-stops)
	- [Selector and declaration separation](#selector-and-declaration-separation)
	- [Rule separation](#rule-separation)
	- [CSS quotation marks](#css-quotation-marks)
1. [**CSS Meta Rules**](#css-meta-rules)
	- [Section comments](#section-comments)
1. [**References**](#references)
1. [**Contributors**](#contributors)
1. [**License**](#license)

##Introduction

This document defines formatting and style rules for HTML and CSS. It aims at improving collaboration, code quality, and enabling supporting infrastructure. It applies to raw, working files that use HTML and CSS. Tools are free to obfuscate, minify, and compile as long as the general code quality is maintained.

**[[⬆]](#table-of-contents)**

##General Style Rules

###Protocol

Omit the protocol from embedded resources.

Omit the protocol portion (http:, https:) from URLs pointing to images and other media files, style sheets, and scripts unless the respective files are not available over both protocols.

Omitting the protocol—which makes the URL relative—prevents mixed content issues and results in minor file size savings.

HTML

```html
<!-- Not recommended -->
<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>

<!-- Recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>

```


CSS


```css
/* Not recommended */
.example {
	background: url(http://www.google.com/images/example);
}

/* Recommended */
.example {
  	background: url(//www.google.com/images/example);
}
```

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

###Capitalization

Use only lowercase.

All code has to be lowercase: This applies to element names, attributes, attribute values (unless text/CDATA), selectors, properties, and property values (with the exception of strings).

```html
<!-- Not recommended -->
<A HREF="/">Home</A>

<!-- Recommended -->
<img src="google.png" alt="Google">
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

##General Meta Rules

###Encoding

Use UTF-8 (no BOM).

Make sure your editor uses UTF-8 as character encoding, without a byte order mark.

Specify the encoding in HTML templates and documents via ```<meta charset="utf-8">```. Do not specify the encoding of style sheets as these assume UTF-8.

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
{# TODO(john.doe): revisit centering #}
<center>Test</center>

<!-- TODO: remove optional tags -->
<ul>
  <li>Apples</li>
  <li>Oranges</li>
</ul>
```

**[[⬆]](#table-of-contents)**

##HTML Style Rules

###Document type

Use HTML5.

HTML5 (HTML syntax) is preferred for all HTML documents: ```<DOCTYPE html!>```.

> It’s recommended to use HTML, as ```text/html```. Do not use XHTML. XHTML, as ```application/xhtml+xml```, lacks both browser and infrastructure support and offers less room for optimization than HTML.

Although fine with HTML, do not close void elements, i.e. write ```<br>```, not ```<br />```.

**[[⬆]](#table-of-contents)**

###HTML validity

Use valid HTML where possible.

Use valid HTML code unless that is not possible due to otherwise unattainable performance goals regarding file size.

Use tools such as the [W3C HTML validator](http://validator.w3.org/nu/) to test.

Using valid HTML is a measurable baseline quality attribute that contributes to learning about technical requirements and constraints, and that ensures proper HTML usage.

```html
<!-- Not recommended -->
<title>Test</title>
<article>This is only a test.

<!-- Recommended -->
<!DOCTYPE html>
<meta charset="utf-8">
<title>Test</title>
<article>This is only a test.</article>
```

**[[⬆]](#table-of-contents)**

###Semantics

Use HTML according to its purpose.

Use elements (sometimes incorrectly called “tags”) for what they have been created for. For example, use heading elements for headings, p elements for paragraphs, a elements for anchors, etc.

Using HTML according to its purpose is important for accessibility, reuse, and code efficiency reasons.

```html
<!-- Not recommended -->
<div onclick="goToRecommendations();">All recommendations</div>

<!-- Recommended -->
<a href="recommendations/">All recommendations</a>
```

**[[⬆]](#table-of-contents)**

###Multimedia fallback

Provide alternative contents for multimedia.

For multimedia, such as images, videos, animated objects via ```canvas```, make sure to offer alternative access. For images that means use of meaningful alternative text (```alt```) and for video and audio transcripts and captions, if available.

Providing alternative contents is important for accessibility reasons: A blind user has few cues to tell what an image is about without ```@alt```, and other users may have no way of understanding what video or audio contents are about either.

> For images whose alt attributes would introduce redundancy, and for images whose purpose is purely decorative which you cannot immediately use CSS for, use no alternative text, as in ```alt=""```.

```html
<!-- Not recommended -->
<img src="spreadsheet.png">

<!-- Recommended -->
<img src="spreadsheet.png" alt="Spreadsheet screenshot.">
```

**[[⬆]](#table-of-contents)**

###Separation of concerns

Separate structure from presentation from behavior.

Strictly keep structure (markup), presentation (styling), and behavior (scripting) apart, and try to keep the interaction between the three to an absolute minimum.

That is, make sure documents and templates contain only HTML and HTML that is solely serving structural purposes. Move everything presentational into style sheets, and everything behavioral into scripts.

In addition, keep the contact area as small as possible by linking as few style sheets and scripts as possible from documents and templates.

Separating structure from presentation from behavior is important for maintenance reasons. It is always more expensive to change HTML documents and templates than it is to update style sheets and scripts.

```html
<!-- Not recommended -->
<!DOCTYPE html>
<title>HTML sucks</title>
<link rel="stylesheet" href="base.css" media="screen">
<link rel="stylesheet" href="grid.css" media="screen">
<link rel="stylesheet" href="print.css" media="print">
<h1 style="font-size: 1em;">HTML sucks</h1>
<p>I’ve read about this on a few sites but now I’m sure:
<u>HTML is stupid!!1</u>
<center>I can’t believe there’s no way to control the styling of my website without doing everything all over again!</center>

<!-- Recommended -->
<!DOCTYPE html>
<title>My first CSS-only redesign</title>
<link rel="stylesheet" href="default.css">
<h1>My first CSS-only redesign</h1>
<p>I’ve read about this on a few sites but today I’m actually doing it: separating concerns and avoiding anything in the HTML of my website that is presentational.
<p>It’s awesome!</p>
```

**[[⬆]](#table-of-contents)**

###Entity references

Do not use entity references.

There is no need to use entity references like ```&mdash;```, ```&rdquo;```, or ```&#x263a;``, assuming the same encoding (UTF-8) is used for files and editors as well as among teams.

The only exceptions apply to characters with special meaning in HTML (like ```<``` and ```&```) as well as control or “invisible” characters (like no-break spaces).

```html
<!-- Not recommended -->
The currency symbol for the Euro is &ldquo;&eur;&rdquo;.

<!-- Recommended -->
The currency symbol for the Euro is “€”.
```

**[[⬆]](#table-of-contents)**

###Type attributes

Omit ```type``` attributes for style sheets and scripts.

Do not use ```type``` attributes for style sheets (unless not using CSS) and scripts (unless not using JavaScript).

Specifying ```type``` attributes in these contexts is not necessary as HTML5 implies ```text/css``` and ```text/javascript``` as defaults. This can be safely done even for older browsers.

```html
<!-- Not recommended -->
<link rel="stylesheet" href="//www.google.com/css/maia.css"
  type="text/css">

<!-- Recommended -->
<link rel="stylesheet" href="//www.google.com/css/maia.css">

<!-- Not recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"
  type="text/javascript"></script>

<!-- Recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

**[[⬆]](#table-of-contents)**

##HTML Formatting Rules

###General formatting

Use a new line for every block, list, or table element, and indent every such child element.
Independent of the styling of an element (as CSS allows elements to assume a different role per display property), put every block, list, or table element on a new line.

Also, indent them if they are child elements of a block, list, or table element.

(If you run into issues around whitespace between list items it’s acceptable to put all li elements in one line. A linter is encouraged to throw a warning instead of an error.)

```html
<blockquote>
  <p><em>Space</em>, the final frontier.</p>
</blockquote>
<ul>
  <li>Moe
  <li>Larry
  <li>Curly
</ul>
<table>
  <thead>
    <tr>
      <th scope="col">Income
      <th scope="col">Taxes
  <tbody>
    <tr>
      <td>$ 5.00
      <td>$ 4.50
</table>
```
**[[⬆]](#table-of-contents)**

###HTML quotation marks

Use double quotation marks for attribute values where necessary.
When quoting attribute values, use double ("") rather than single quotation marks ('').

```html
<!-- Not recommended -->
<a class='maia-button maia-button-secondary'>Sign in</a>

<!-- Recommended -->
<a class="maia-button maia-button-secondary">Sign in</a>
```

**[[⬆]](#table-of-contents)**

##CSS Style Rules

###CSS validity

Use valid CSS where possible.

Unless dealing with CSS validator bugs or requiring proprietary syntax, use valid CSS code.

Use tools such as the [W3C CSS validator](http://jigsaw.w3.org/css-validator) to test.

Using valid CSS is a measurable baseline quality attribute that allows to spot CSS code that may not have any effect and can be removed, and that ensures proper CSS usage.

**[[⬆]](#table-of-contents)**

###Using ID selectors
To be clear, using ID attributes in your HTML can be a good thing and in some cases, absolutely necessary. For example, they provide efficient hooks for JavaScript. For CSS, however, ID selectors aren’t necessary as the performance difference between ID and class selectors is nearly non-existent and can make styling more complicated due to increasing specificity.

```css
/* Not recommended */
#header{ color: red; }

/* Recommended */
.header{ color: red; }

```

**[[⬆]](#table-of-contents)**

###ID and class naming

Use meaningful or generic ID and class names.

Instead of presentational or cryptic names, always use ID and class names that reflect the purpose of the element in question, or that are otherwise generic.

Names that are specific and reflect the purpose of the element should be preferred as these are most understandable and the least likely to change.

Generic names are simply a fallback for elements that have no particular or no meaning different from their siblings. They are typically needed as “helpers.”

Using functional or generic names reduces the probability of unnecessary document or template changes.

```css
/* Not recommended: meaningless */
.yee-1901 {}

/* Not recommended: presentational */
.button-green {}
.clear {}

/* Recommended: specific */
.gallery {}
.login {}
.video {}

/* Recommended: generic */
.aux {}
.alt {}
```

**[[⬆]](#table-of-contents)**

###ID and class name style


Use ID and class names that are as short as possible but as long as necessary.

Try to convey what an ID or class is about while being as brief as possible.

Using ID and class names this way contributes to acceptable levels of understandability and code efficiency.

```css
/* Not recommended */
#navigation {}
.atr {}

/* Recommended */
.nav {}
.author {}
```

**[[⬆]](#table-of-contents)**

###Type selectors

Avoid qualifying ID and class names with type selectors.

Unless necessary (for example with helper classes), do not use element names in conjunction with IDs or classes.

Avoiding unnecessary ancestor selectors is useful for performance reasons.

```css
/* Not recommended */
ul#example {}
div.error {}

/* Recommended */
.example {}
.error {}
```

**[[⬆]](#table-of-contents)**

###Shorthand properties

Use shorthand properties where possible.

CSS offers a variety of shorthand properties (like font) that should be used whenever possible, even in cases where only one value is explicitly set.

Using shorthand properties is useful for code efficiency and understandability.

```css
/* Not recommended */
border-top-style: none;
font-family: palatino, georgia, serif;
font-size: 100%;
line-height: 1.6;
padding-bottom: 2em;
padding-left: 1em;
padding-right: 1em;
padding-top: 0;

/* Recommended */
border-top: 0;
font: 100%/1.6 palatino, georgia, serif;
padding: 0 1em 2em;
```

**[[⬆]](#table-of-contents)**

###0 and units

Omit unit specification after “0” values.

Do not use units after 0 values unless they are required.

```css
margin: 0;
padding: 0;
```

**[[⬆]](#table-of-contents)**

###Leading 0s

Omit leading “0”s in values.

Do not use put 0s in front of values or lengths between -1 and 1.

```css
font-size: .8em;
```

**[[⬆]](#table-of-contents)**

###Hexadecimal notation

Use 3 character hexadecimal notation where possible.

For color values that permit it, 3 character hexadecimal notation is shorter and more succinct.

```css
/* Not recommended */
color: #eebbcc;

/* Recommended */
color: #ebc;
```

**[[⬆]](#table-of-contents)**

###Prefixes

Prefix selectors with an application-specific prefix (optional).

In large projects as well as for code that gets embedded in other projects or on external sites use prefixes (as namespaces) for ID and class names. Use short, unique identifiers followed by a dash.

Using namespaces helps preventing naming conflicts and can make maintenance easier, for example in search and replace operations.

```css
.adw-help {} /* AdWords */
#maia-note {} /* Maia */
```

**[[⬆]](#table-of-contents)**

###ID and class name delimiters

Separate words in ID and class names by a hyphen.

Do not concatenate words and abbreviations in selectors by any characters (including none at all) other than hyphens, in order to improve understanding and scannability.

```css
/* Not recommended: does not separate the words “demo” and “image” */
.demoimage {}

/* Not recommended: uses underscore instead of hyphen */
.error_status {}

/* Recommended */
.video-id {}
.ads-sample {}
```

**[[⬆]](#table-of-contents)**

###Hacks

Avoid user agent detection as well as CSS “hacks”—try a different approach first.

It’s tempting to address styling differences over user agent detection or special CSS filters, workarounds, and hacks. Both approaches should be considered last resort in order to achieve and maintain an efficient and manageable code base. Put another way, giving detection and hacks a free pass will hurt projects in the long run as projects tend to take the way of least resistance. That is, allowing and making it easy to use detection and hacks means using detection and hacks more frequently—and more frequently is too frequently.

**[[⬆]](#table-of-contents)**

##CSS Formatting Rules

###Declaration order

Alphabetize declarations.

Put declarations in alphabetical order in order to achieve consistent code in a way that is easy to remember and maintain.

Ignore vendor-specific prefixes for sorting purposes. However, multiple vendor-specific prefixes for a certain CSS property should be kept sorted (e.g. -moz prefix comes before -webkit).

```css
background: fuchsia;
border: 1px solid;
-moz-border-radius: 4px;
-webkit-border-radius: 4px;
border-radius: 4px;
color: black;
text-align: center;
text-indent: 2em;
```

**[[⬆]](#table-of-contents)**

###Block content indentation

Indent all block content.

Indent all block content, that is rules within rules as well as declarations, so to reflect hierarchy and improve understanding.

```css
@media screen, projection {

  html {
    background: #fff;
    color: #444;
  }

}
```

**[[⬆]](#table-of-contents)**

###Declaration stops

Use a semicolon after every declaration.

End every declaration with a semicolon for consistency and extensibility reasons.

```css
/* Not recommended */
.test {
  display: block;
  height: 100px
}

/* Recommended */
.test {
  display: block;
  height: 100px;
}
```

**[[⬆]](#table-of-contents)**

###Property name stops

Use a space after a property name’s colon.

Always use a single space between property and value (but no space between property and colon) for consistency reasons.

```css
/* Not recommended */
h3 {
  font-weight:bold;
}

/* Recommended */
h3 {
  font-weight: bold;
}
```

**[[⬆]](#table-of-contents)**

###Selector and declaration separation

Separate selectors and declarations by new lines.

Always start a new line for each selector and declaration.

```css
/* Not recommended */
a:focus, a:active {
  position: relative; top: 1px;
}

/* Recommended */
h1,
h2,
h3 {
  font-weight: normal;
  line-height: 1.2;
}
```

**[[⬆]](#table-of-contents)**

###Rule separation

Separate rules by new lines.

Always put a line between rules.

```css
html {
  background: #fff;
}

body {
  margin: auto;
  width: 50%;
}
```

**[[⬆]](#table-of-contents)**

###CSS quotation marks

Use single quotation marks for attribute selectors and property values where necessary.

When quoting attribute selectors and property values, use single ('') rather than double ("") quotation marks. Do not use quotation marks in URI values (url()).

```css
/* Not recommended */
@import url("//www.google.com/css/maia.css");

html {
  font-family: "open sans", arial, sans-serif;
}

/* Recommended */
@import url(//www.google.com/css/maia.css);

html {
  font-family: 'open sans', arial, sans-serif;
}
```

**[[⬆]](#table-of-contents)**

##CSS Meta Rules

###Section comments

Group sections by a section comment (optional).

If possible, group style sheet sections together by using comments. Separate sections with new lines.

```css
/* Header */

.adw-header {}

/* Footer */

.adw-footer {}

/* Gallery */

.adw-gallery {}
```

**[[⬆]](#table-of-contents)**

##Resources
**Other Styleguides**

  - [GitHub CSS Style Guide](https://github.com/styleguide/css)
  - [Nicolas Gallagher's Idiomatic CSS](https://github.com/necolas/idiomatic-css)
  - [Harry Robert's CSS Style](http://csswizardry.com/2012/04/my-html-css-coding-style/)
  - [ThinkUp CSS Style Guide](https://github.com/ginatrapani/ThinkUp/wiki/Code-Style-Guide:-CSS)
  - [WordPress CSS Coding Standards](http://make.wordpress.org/core/handbook/coding-standards/css/)
  - [Jonathan Snook's Scalable and Modular Architecture for CSS](http://smacss.com/)

**[[⬆]](#table-of-contents)**

##References
- Based on [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)

**[[⬆]](#table-of-contents)**

##Contributors

  - [View Contributors](https://github.com/NucleoDigital/guides/graphs/contributors)

**[[⬆]](#table-of-contents)**

##License

(The MIT License)

Copyright (c) 2012 El Núcleo Digital

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[[⬆]](#table-of-contents)**