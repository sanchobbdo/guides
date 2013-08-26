![image](https://dl.dropboxusercontent.com/u/2402696/external/logo-sancho.png)

##Digital Team - Development Guidelines

The point of having development guidelines is to have a common vocabulary of coding so people can concentrate on *what* you’re saying rather than on *how* you’re saying it. We present global development rules here so people know the vocabulary, but local rules are also important. If code you add to a file looks drastically different from the existing code around it, it throws readers out of their rhythm when they go to read it. Avoid this.

Before reading this, you should have a general understanding for specificity, javascript, jQuery, HTML and CSS.

If you're visiting from the internet, feel free to learn from this guidelines. This is a guide we use for our own apps internally at **Sancho BBDO** inspired by other guidelines. We encourage you to set up one that works for your own team.

##Guides:

1. ####[General Guidelines](general/README.md)

2. ####[HTML Guidelines](html/README.md)

3. ####[CSS and SASS Guidelines](css/README.md)

4. ####[JavaScript Guidelines](javascript/README.md)
  - [Plugins directory](javascript/plugins-directory.md)

##Linters:

A lint tool performs static analysis of source code and flags patterns that might be errors or otherwise cause problems for the developer.

Below you can get the settings files you can use on your projects:

- [JS Hint File (.jshintrc)](linters/.jshintrc)
- [CSS Lint File (.csslintrc)](linters/.csslintrc)

##Tools:

- [JS Hint](http://www.jshint.com/): Is a tool to detect errors and potential problems in JavaScript code and can be used to enforce coding coventions.
- [CSS Lint](http://csslint.net/): This tool points out problems with your CSS code. It does basic syntax checking as well as applying a set of rules to the code that look for problematic patterns or signs of inefficiency.
- [HTML Inspector](https://github.com/philipwalton/html-inspector): It is a code quality tool to help you and your team write better markup. It's written in JavaScript and runs in the browser.
- [jsBeutifier](http://jsbeautifier.org/): This little beautifier will reformat and reindent bookmarklets, ugly JavaScript.
- [CSS Compressor](http://www.cssdrive.com/index.php/main/csscompressor/): Use this utility to compress your CSS to increase loading speed and save on bandwidth as well.
- [Sprite Cow](http://www.spritecow.com/): This site helps you get the background-position, width and height of sprites within a spritesheet as a nice bit of copyable css.
