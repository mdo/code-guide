# HTML and CSS code guide

Rules and guidelines for writing flexible, durable, and sustainable HTML and CSS at any scale.



----------



## Table of contents

* [Golden rule](#golden-rule)
* [HTML](#html)
  * [Syntax](#html-syntax)
  * [HTML5 doctype](#html5-doctype)
  * [Practicality over purity](#practicality-over-purity)
  * [Attribute order](#attribute-order)
  * [Boolean attributes](#boolean-attributes)
  * [JavaScript generated markup](#javascript-generated markup)
* [CSS](#css)
  * [CSS syntax](#css-syntax)
  * [Declaration order](#declaration-order)
  * [Media query placement](#media-query-placement)
  * [Formatting exceptions](#formatting-exceptions)
    * [Prefixed properties](#prefixed-properties)
    * [Rules with single declarations](#rules-with-single-declarations)
  * [Human readable](#human-readable)
    * [Comments](#comments)
    * [Classes](#classes)
    * [Selectors](#selectors)
  * [Organization](#organization)
* [Editor preferences](#editor-preferences)
* [Writing copy](#copy)
  * [Sentence case](#sentence-case)



----------



## Golden rule

> Every line of code should appear to be written by a single person, no matter the number of contributors.

Enforce these, or your own, agreed upon guidelines at all times.  Small or large, call out what's incorrect. For additions or contributions to this Code Guide, please [open an issue on GitHub](https://github.com/mdo/code-guide).



----------



## HTML


### HTML syntax

* Use soft-tabs with two spaces.
* Nested elements should be indented once (2 spaces).
* Always use double quotes, never single quotes.
* Never include a trailing slash in self-closing elements (e.g., `<img>` or `<hr>`.

**Incorrect example:**

```html
<!DOCTYPE html>
<html>
<head>
<title>Page title</title>
</head>
<body>
<img src='images/company-logo.png' alt='Company' />
<h1 class='hello-world'>Hello, world!</h1>
</body>
</html>
```

**Correct example:**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Page title</title>
  </head>
  <body>
    <img src="images/company-logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
  </body>
</html>
```


### HTML5 doctype

Enforce standards mode with this simple doctype at the beginning of every HTML page.

```html
<!DOCTYPE html>
```


### Practicality over purity

Strive to maintain HTML standards and semantics, but not at the expense of practicality. Use the least amount of markup with the fewest intricacies whenever possible.


### Attribute order

HTML attributes should come in this particular order for easier reading of code.

* `class`
* `id`
* `data-*`
* `for`, `type`, or `href`

Such that your HTML looks like:

```html
<a class="" id="" data-modal="" href="">Example link</a>
```

### Boolean attributes

A boolean attribute is one that needs no declared value. XHTML required you to declare a value, but HTML5 has no such requirement.

```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
	<option value="1" selected"></option>
</select>
```

For further reading, consult the [WhatWG section on boolean attributes](http://www.whatwg.org/specs/web-apps/current-work/multipage/common-microsyntaxes.html#boolean-attributes):

> The presence of a boolean attribute on an element represents the true value, and the absence of the attribute represents the false value.

If you *must* include the attribute's value, and **you don't need to**, follow this WhatWG guideline:

> If the attribute is present, its value must either be the empty string or [...] the attribute's canonical name, with no leading or trailing whitespace.

In short, don't add a value.

### Reducing markup

Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML. Take the following example:

```html
<!-- Not so great -->
<span class="avatar">
  <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```

### JavaScript generated markup

Writing markup in a JavaScript file makes the content harder to find, harder to edit, and less performant. Avoid it whenever possible.



----------



## CSS

### CSS syntax

* Use soft-tabs with two spaces.
* When grouping selectors, keep individual selectors to a single line.
* Include one space before the opening brace of declaration blocks.
* Place closing braces of declaration blocks on a new line.
* Include one space after `:` for each declaration.
* Each declaration should appear on its own line for more accurate error reporting.
* End all declarations with a semi-colon.
* Comma-separated values should include a space after each comma.
* Don't include spaces after commas *within* `rgb()` or `rgba()` colors, and don't preface values with a leading zero.
* Lowercase all hex values, e.g., `#fff`.
* Use shorthand hex values where available, e.g., `#fff` instead of `#ffffff`.
* Quote attribute values in selectors, e.g., `input[type="text"]`.
* Avoid specifying units for zero values, e.g., `margin: 0;` instead of `margin: 0px;`.

**Incorrect example:**

```css
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}
```

**Correct example:**

```css
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin: 0 0 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

Questions on the terms used here? See the [syntax section of the Cascading Style Sheets article](http://en.wikipedia.org/wiki/Cascading_Style_Sheets#Syntax) on Wikipedia.


### Declaration order

Related declarations should be grouped together, placing positioning and box-model properties closest to the top, followed by typographic and visual properties.

```css
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
```

For a complete list of properties and their order, please see [Recess](http://twitter.github.com/recess).

### Media query placement

Place media queries as close to their relevant rule sets whenever possible. Don't bundle them all in a separate stylesheet or at the end of the document. Doing so only makes it easier for folks to miss them in the future.

A typical setup might look like this:

```css
.element { ... }
.element-avatar { ... }
.element-selected { ... }

@media (min-width: 480px) {
	element { ... }
	.element-avatar { ... }
	.element-selected { ... }
}
```

### Formatting exceptions

In some cases, it makes sense to deviate slightly from the default [syntax](#css-syntax).

#### Prefixed properties

When using vendor prefixed properties, indent each property such that the declaration's value lines up vertically for easy multi-line editing.

```css
.selector {
  -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
          box-shadow: 0 1px 2px rgba(0,0,0,.15);
}
```

In Textmate, use **Text &rarr; Edit Each Line in Selection** (&#8963;&#8984;A). In Sublime Text 2, use **Selection &rarr; Add Previous Line** (&#8963;&#8679;&uarr;) and **Selection &rarr;  Add Next Line** (&#8963;&#8679;&darr;).

#### Rules with single declarations

In instances where a rule set includes only one declaration, consider removing line breaks for readability and faster editing. Consider this mixed example:

```css
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 220px; }

.sprite {
  display: inline-block;
  width: 16px;
  height: 15px;
  background-image: url(../img/sprite.png);
}
.icon           { background-position: 0 0; }
.icon-home      { background-position: 0 -20px; }
.icon-account   { background-position: 0 -40px; }
```

### Preprocessors (LESS and SASS)

Preprocessors have additional features on top of CSS, so be aware of these additional guidelines.

#### Nesting

Avoid unnecessary nesting. Just because you can nest, doesn't mean you always should. Consider nesting if you must scope styles to a parent and if there are multiple elements to be nested.

```css
// Without nesting
.table > thead > tr > th { … }
.table > thead > tr > td { … }

// With nesting
.table > thead > tr {
	> th { … }
	> td { … }
}
```

Build your components to avoid nesting, like so:

```css
.element {
  ...
}
.element-title {
  ...
}
.element-button {
  ...
}
```


### Human readable

Code is written and maintained by people. Ensure your code is descriptive, well commented, and approachable by others.

#### Comments

Great code comments convey context or purpose and should not just reiterate a component or class name.

**Bad example:**

```css
/* Modal header */
.modal-header {
  ...
}
```

**Good example:**

```css
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
```

#### Class names

* Keep classes lowercase and use dashes (not underscores or camelCase).
* Avoid arbitrary shorthand notation.
* Keep classes as short and succinct as possible.
* Use meaningful names; use structural or purposeful names over presentational.
* Prefix classes based on the closest parent component's base class.

**Bad example:**

```css
.t { ... }
.red { ... }
.header { ... }
```

**Good example:**

```css
.tweet { ... }
.important { ... }
.tweet-header { ... }
```

#### Selectors

* Use classes over generic element tags.
* Keep them short and limit the number of elements in each selector to three.
* Scope classes to the closest **only** parent when necessary (e.g., when not using prefixed classes).

**Bad example:**

```css
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
```

**Good example:**

```css
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
```

Additional reading:

- [Scope CSS classes with prefixes](http://markdotto.com/2012/02/16/scope-css-classes-with-prefixes/)
- [Stop the cascade](http://markdotto.com/2012/03/02/stop-the-cascade/)

### Organization

* Organize sections of code by component.
* Develop a consistent commenting hierarchy.
* If using multiple CSS files, break them down by component.



----------



## Editor preferences

Set your editor to the following settings to avoid common code inconsistencies and dirty diffs:

* Use soft-tabs set to 2 spaces
* Trim trailing white space on save
* Set encoding to UTF-8
* Add new line at end of files

Consider applying these preferences to your project's `.editorconfig` file, a la [Bootstrap's own](https://github.com/twbs/bootstrap/blob/master/.editorconfig).



----------



## Copy

### Sentence case

Always write copy, including headings and code comments, in [sentence case](http://en.wikipedia.org/wiki/Letter_case#Usage). In other words, aside from titles and proper nouns, only the first word should be capitalized.



----------



### Thanks

Heavily inspired by [Idiomatic CSS](https://github.com/necolas/idiomatic-css) and the [GitHub Styleguide](http://github.com/styleguide). Made with all the love in the world by [@mdo](https://twitter.com/mdo).
