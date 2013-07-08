![image](https://dl.dropboxusercontent.com/u/2402696/external/logo-sancho.png)

#CSS and SASS Guidelines

*version 1.0.0*

##Table of Contents
1. [**Introduction**](#introduction)
1. [**General Style Rules**](#general-style-rules)
	- [Protocol](#protocol)
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
  - [Declaration Block Separation](#declaration-block-separation)
	- [Selector and declaration separation](#selector-and-declaration-separation)
	- [Rule separation](#rule-separation)
	- [CSS quotation marks](#css-quotation-marks)
1. [**CSS Meta Rules**](#css-meta-rules)
	- [Section comments](#section-comments)
1. [**SASS Rules**](#sass-rules)
  - [List order](#list-order)
  - [Maximum Nesting](#maximum-nesting)
  - [Common rules](#common-rules)
1. [**References**](#references)
1. [**Contributors**](#contributors)
1. [**License**](#license)

##Introduction

This document defines formatting and style rules for CSS. It aims at improving collaboration, code quality, and enabling supporting infrastructure. It applies to raw, working files that use CSS. Tools are free to obfuscate, minify, and compile as long as the general code quality is maintained.

> Please also review our [**HTML Guidelines**](../html/README.md) along with this one.

**[[⬆]](#table-of-contents)**

##General Style Rules

> Please also review our [**General Guidelines**](../general/README.md) along with this one.

###Protocol

Omit the protocol from embedded resources.

Omit the protocol portion (http:, https:) from URLs pointing to images and other media files, style sheets, and scripts unless the respective files are not available over both protocols.

Omitting the protocol—which makes the URL relative—prevents mixed content issues and results in minor file size savings.

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
.header {
    color: red;
}
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

###Declaration Block Separation

Use a space between the last selector and the declaration block.

Always use a single space between the last selector and the opening brace that begins the [declaration block](http://www.w3.org/TR/CSS21/syndata.html#rule-sets).

The opening brace should be on the same line as the last selector in a given rule.

```css
/* Not recommended: missing space */
#video{
    margin-top: 1em;
}

/* Not recommended: unnecessary line break */
#video
{
    margin-top: 1em;
}

/* Recommended */
#video {
    margin-top: 1em;
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

##SASS Rules

###List order

####List @extend(s) First
Knowing right off the bat that this class inherits another whole set of rules from elsewhere is good.

```css
.weather {
    @extends %module;
    ...
}
```

####List "Regular" Styles Next
This visually separates the @extends and @includes as well as groups the @includes for easier reading. You might also want to make the call on separating user-authored @includes and vendor-provided @includes.

```css
.weather {
    @extends %module;
    background: LightCyan;
    ..
}
```

####List @include(s) Next

```css
.weather {
    @extends %module;
    background: LightCyan;
    @include transition(all 0.3s ease-out);
    ...
}
```

####Nested Selectors Last
Nothing goes after the nested stuff. And the same order as above within the nested selector would apply.

```css
.weather {
    @extends %module;
    background: LightCyan;
    @include transition(all 0.3s ease);
    > h3 {
        border-bottom: 1px solid white;
        @include transform(rotate(90deg));
    }
}
```

###Maximum Nesting

####Three Levels Deep
Chances are, if you're deeper than that, you're writing a crappy selector. Crappy in that it's too reliant on HTML structure (fragile), overly specific (too powerful), and not very reusable (not useful). It's also on the edge of being difficult to understand.

```css
.weather {
    .cities {
        li {
            // no more!
        }
    }
}
```

If you really want to use tag selectors because the class thing is getting too much for you, you may want to get pretty specific about it to avoid undesired cascading. And possibly even make use of extend so it has the benefit on the CSS side of re-usability.

```css
.weather
    > h3 {
        @extend %line-under;
    }
}
```

####50 Lines
If a nested block of Sass is longer than that, there is a good chance it doesn't fit on one code editor screen, and starts becoming difficult to understand. The whole point of nesting is convenience and to assist in mental grouping. Don't use it if it hurts that.

###Common rules

####All Vendor Prefixes Use @mixins
Vendor prefixes are a time-sensitive thing. As browsers update over time, the need for them will fall away. You can update mixins (or the libraries you use will update) to reflect those changes. Even if the mixin ends up being a one-liner, that's OK.

The only time you wouldn't @mixin a vendor prefix is when it's super proprietary, unlikely to be standardized as is, and so including other vendor prefixes or the non-prefixed version is likely to cause more harm that good. Things like -webkit-line-clamp or -ms-content-zoom-chaining or things like that.

####Global and Section-Specific Sass Files Are just Table of Contents
In other words, no styles directly in them. Force yourself to keep all styles organized into component parts.

####List Vendor/Global Dependancies First, Then Author Dependancies, Then Patterns, Then Parts
So the "table of contents" things comes together like:

```css
/* Vendor Dependencies */
@import "compass";

/* Authored Dependencies */
@import "global/colors";
@import "global/mixins";

/* Patterns */
@import "global/tabs";
@import "global/modals";

/* Sections */
@import "global/header";
@import "global/footer";
```

The dependencies like Compass, colors, and mixins generate no compiled CSS at all, they are purely code dependancies. Listing the patterns next means that more specific "parts", which come after, have the power to override patterns without having a specificity war.

####Partials are named _partial.scss
This is a common naming convention that indicates this file isn't meant to be compiled by itself. It likely has dependancies that would make it impossible to compile by itself. Personally I like dashes in the "actual" filename though, like _dropdown-menu.scss.

####In Deployment, Compile Compressed
Live websites should only ever have compressed CSS.

####Variablize All Common Numbers, and Numbers with Meaning
If you find yourself using a number other than 0 or 100% over and over, it likely deserves a variable. Since it likely has meaning and controls consistency, being able to tweak it enmasse may be useful.

If a number clearly has strong meaning, that's a use case for variablizing as well.

```css
$zHeader: 2000;
$zOverlay: 5000;
$zMessage: 5050;

.header {
    z-index: $zHeader;
}
.overlay {
    z-index: $zOverlay;
}
.message {
    z-index: $zMessage;
}
```

Those numbers are probably in a separate file @import-ed as a dependency. That way you can keep track of your whole z-index stack in one place.

####Variablize All Colors
Except perhaps white and black. Chances are a color isn't one-off, and even if you think it is, once it's in a variable you might see uses for it elsewhere. Variations on that color can often be handled by the Sass color functions like lighten() and darken() - which make updating colors easier (change in one place, whole color scheme updates).

**[[⬆]](#table-of-contents)**

##Resources
**Other Styleguides**

  - [GitHub CSS Style Guide](https://github.com/styleguide/css)
  - [Nicolas Gallagher's Idiomatic CSS](https://github.com/necolas/idiomatic-css)
  - [Harry Robert's CSS Style](http://csswizardry.com/2012/04/my-html-css-coding-style/)
  - [ThinkUp CSS Style Guide](https://github.com/ginatrapani/ThinkUp/wiki/Code-Style-Guide:-CSS)
  - [WordPress CSS Coding Standards](http://make.wordpress.org/core/handbook/coding-standards/css/)
  - [Jonathan Snook's Scalable and Modular Architecture for CSS](http://smacss.com/)

##References

- Based on [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)
- SASS guide based on [CSS Tricks SASS Style Guide](http://css-tricks.com/sass-style-guide/)

##Contributors

  - [View Contributors](../../../graphs/contributors)

##License

(The MIT License)

Copyright (c) 2013 Sancho BBDO

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
