![image](https://dl.dropboxusercontent.com/u/2402696/external/logo-sancho.png)

# Git Commit Message Guidelines

*version 1.0.0*

## Table of Contents
1. [**Introduction**](#introduction)
1. [**Submit a better commit message**](#submit-a-better-commit-message)
1. [**Format of the commit message**](#format-of-the-commit-message)
	- [**Subject**](#subject)
	- [**Body**](#body)
	- [**Message footer**](#message-footer)
	- [**Breaking changes**](#breaking-changes)
	- [**Referencing issues**](#referencing-issues)
1. [**Examples**](#examples)
1. [**References**](#references)
1. [**Contributors**](#contributors)
1. [**License**](#license)

## Introduction
This document defines general purpose Git Commit Message conventions. It aims at
improving collaboration and enabling supporting infrastructure.

Tune up your IDE or Git Tool to follow this rules.

## Submit a better commit message
Answer the following questions:

**Why is this change necessary?**

This question tells reviewers of your pull request what to expect in the commit, allowing them to more easily identify and point out unrelated changes.

**How does it address the issue?**

Describe, at a high level, what was done to affect change.
```introduce a red/black tree to increase search speed``` or ```remove <troublesome tag X>, which was causing <specific description of issue introduced by tag>``` are good examples.

If your change is obvious, you may be able to omit addressing this question.

**What side effects does this change have?**

This is the most important question to answer, as it can point out problems where you are making too many changes in one commit or branch. One or two bullet points for related changes may be okay, but five or six are likely indicators of a commit that is doing too many things.

## Format of the commit message
All commit messages should have the next format:

```
<subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

First line cannot be longer than **50 characters** or less, second line is always blank and other lines should be wrapped at **80 characters**. This allows the message to be easier to read on github as well as in various git tools.

Write comments in **English**.

### Subject
- Use imperative, present tense: “change” not “changed” nor “changes”.
- Don't capitalize first letter.
- No dot (.) at the end, or full stop.

### Body
- Includes motivation for the change and contrasts with previous behavior.

### Message footer
**Breaking changes**

All breaking changes have to be mentioned in footer with the description of the change, justification and migration notes.

**Referencing issues**

Closed bugs should be listed on a separate line in the footer prefixed with "Closes" keyword like this:

```
closes #234
```

or in case of multiple issues:

```
closes #123, #245, #992
```

## Examples
- A simple CSS update:

```
change position of the carousel module 10px less from the top
```

- A new module is added with breaking changes:

```
add directory list module

added new directory module:
- filled through ng-repeat directive
- get data from a JSONP request
- animated through CSS

breaks <div class="stores">, which was removed (use <div class="directory"> instead)
```

- Fixing documentation:

```
updated fixed docs from Google Docs

couple of typos fixed:
- indentation
- batchLogbatchLog -> batchLog
- start periodic checking
- missing brace
```

- An improvement related to a Trello or Basecamp comment:

```
redirect user to the requested page after login

https://trello.com/path/to/relevant/card or
https://basecamp.com/2111294/projects/project-name/todos/date#comment_ID

users were being redirected to the home page after login, which is less
useful than redirecting to the page they had originally requested before
being redirected to the login form.

- store requested path in a session variable
- redirect to the stored location after successfully logging in the user
```

## References

- [AngularJS Git Commit Message Conventions](https://docs.google.com/a/sanchobbdo.com.co/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit#)
- [A Note About Git Comment Messages by Tim Pope](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
- [5 useful tips for a better commit message by Caleb Thompson](http://robots.thoughtbot.com/post/48933156625/5-useful-tips-for-a-better-commit-message)

## Contributors

  - [View Contributors](../../../graphs/contributors)

## License

(The MIT License)

Copyright (c) 2013 Sancho BBDO

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
