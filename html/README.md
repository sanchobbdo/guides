![Nucleo logo](http://dl.dropbox.com/u/2402696/external/elnucleo-logo.png)

#HTML Style Guide

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
	- [Using ID selectors](#using-id-selectors)
	- [Multimedia fallback](#multimedia-fallback)
	- [Separation of concerns](#separation-of-concerns)
	- [Entity references](#entity-references)
	- [Optional tags](#optional-tags)
	- [Type attributes](#type-attributes)
1. [**HTML Formatting Rules**](#html-formatting-rules)
	- [General formatting](#general-formatting)
	- [HTML quotation marks](#html-quotation-marks)
1. [**Images in HTML**](#images-in-html)
	- [Inline and background images](#inline-and-background-images)
	- [The alt attribute](#the-alt-attribute)
	- [The title attribute](#the-title-attribute)
	- [Using longdesc for complex images](#using-longdesc-for-complex-images)
	- [Faster image display](#faster-image-display)
1. [**HTML Naming Conventions**](#html-naming-conventions)
1. [**Resources**](#resources)
1. [**References**](#references)
1. [**Contributors**](#contributors)
1. [**License**](#license)

##Introduction

This document defines formatting and style rules for HTML. It aims at improving collaboration, code quality, and enabling supporting infrastructure. It applies to raw, working files that use HTML. Tools are free to obfuscate, minify, and compile as long as the general code quality is maintained.

> Please also review our [**CSS Style Guide**](http://github.com/NucleoDigital/guides/blob/master/css/readme.md) along with this one.

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

###Using ID selectors
To be clear, using ID attributes in your HTML can be a good thing and in some cases, absolutely necessary. For example, they provide efficient hooks for JavaScript. For CSS, however, ID selectors aren’t necessary as the performance difference between ID and class selectors is nearly non-existent and can make styling more complicated due to increasing specificity.

```html
/* Not recommended */
<div id="nav"></div>

/* Recommended */
<div class="nav"></div>
```

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

##Images in HTML

###Inline and background images

There are two main ways to add images to a document: content images using the img element and background images applied to elements using CSS. When to use what is dependent on what you want to do:

1. If the image is crucial to the content of the document, for example a photo of the author or a graph showing some data, it should be added as an img element with proper alternative text.
1. If the image is there as “eye candy” you should use CSS background images. The reason is that these images should not have any alternative text (what use is “round green corner with a twinkle” to a blind person?) and you have a lot more options to deal with image styling in CSS than in HTML.

**[[⬆]](#table-of-contents)**

###The ```alt``` attribute

In order to make an image understandable for everybody you need to add a proper alternative text.

The ```alt``` attribute contains the text that should be displayed when the image is not available. The information in the ```alt``` attribute should not be displayed when the image was successfully loaded and shown; Internet Explorer gets this wrong, and shows it as a tooltip when you hover your mouse pointer over the image for a while. This is a mistake, as it leads a lot of people to add additional information about the image into the alt attribute. If you wanted to add additional information, you should use the title attribute instead, which I’ll get on to in the next section.

```html
<img src="balconyview.jpg" alt="View from my balcony, showing a row of houses, trees and a castle">
```

**[[⬆]](#table-of-contents)**

###The ```title``` attribute

Most browsers will display the value of an ```img``` element’s ```title``` attribute as a tool-tip when you hover your mouse cursor over it. This can help a visitor learn more about the image, but you cannot rely on each visitor to have a mouse. The ```title``` attribute can be very useful, but it is not a safe way of providing crucial information. Instead it offers a good way to, for example, write about the mood of the image, or what it means in context.

```html
<img src="balconyview.jpg" alt="View from my balcony, showing a row of houses, trees and a castle" title="What I see when I look out of my window; the castle was one reason to move there.">
```

**[[⬆]](#table-of-contents)**

###Using ```longdesc``` for complex images

If the image is a very complex image, like for example a chart, you can offer a more lengthy description of it using the ```longdesc``` attribute, so that people using screenreaders or browsing with images turned off can still access the information conveyed by the image.

```html
<img src="chart.png" width="450" height="150" alt="Chart showing the fruit consumption amongst under 15 year olds. Most children ate Pineapples, followed by Pears" longdesc="fruitconsumption.html">
```

**[[⬆]](#table-of-contents)**

###Faster image display

When the user agent finds an img element in the HTML, it starts loading the image the src attribute points to. By default, it doesn’t know the image’s dimensions, so it’ll just display all the text lumped together, then shift the rest of the document around when the images finally load and appear. This can slow down page loading and looks a bit confusing to the page visitors. To stop this happening you can tell the user agent to allocate the right amount of space for the images before they load by giving it the image’s dimensions using the width and height attributes.

```html
<img src="balconyview.jpg" alt="View from my balcony, showing a row of houses, trees and a castle" width="400" height="186">
```

**[[⬆]](#table-of-contents)**


##HTML Naming Conventions

HTML pages should be saved with the .html extension. While this isn’t vital on every page, 90% of the time the home page of your site will have to be named *index.html* in order to be picked up as the default home page, so you may as well stick to this naming convention for all pages.

Use alphanumerics only in page names. That is, a-z, 0-9. The only exceptions are: ```-``` (dash), ```_``` (underscore) and ```~``` (tilde).

Never use spaces in the file name of anything destined for the web. Replace spaces with hyphens.

Use lowercase exclusively when naming files (some web servers are sensitive to case).
```
<!-- Not recommended -->
frontPage.html
my$ite.html
main page.html

<!-- Recommended -->
about.html
porftolio.html
contact.html
```

When planning a site, create a naming convention for pages and stick to it without exception.

Always title a page the moment you create it, using a titling convention you have created. Too often this task falls by the wayside and is neglected, resulting in pages that have irrelevant or confusing titles, or no title at all.

```html
<!-- Not recommended -->
<title>Untitled</title>

<!-- Recommended -->
<title>El Núcleo Digital | Portfolio</title>
```

**[[⬆]](#table-of-contents)**

##Resources

  - [Introduction to The Web Standards on Opera Developers](http://dev.opera.com/articles/view/1-introduction-to-the-web-standards-cur/)

##References
- Based on [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)


##Contributors

  - [View Contributors](https://github.com/NucleoDigital/guides/graphs/contributors)


##License

(The MIT License)

Copyright (c) 2012 El Núcleo Digital

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.