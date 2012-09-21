# Code Guide
Standards for developing flexible, durable, and sustainable HTML and CSS.



## Table of contents

* [Golden rule](#golden-rule)
* [HTML](#html)
  * [Syntax](#html-syntax)
* [CSS](#css)
* [Writing copy](#copy)



## Golden rule

> All code in any code base should look like a single person typed it, no matter how many people contributed.

This means strictly enforcing these agreed upon guidelines at all times. For additions or contributions, please [file an issue on GitHub](https://github.com/markdotto/code-guide).



## HTML

### HTML syntax

* Use soft-tabs with two spaces
* Nested elements should be indented once (2 spaces)
* Always use double quotes, never single quotes
* Don't include a trailing slash in self-closing elements

**Incorrect example:**

  &lt;!DOCTYPE html&gt;
  &lt;html&gt;
  &lt;head&gt;
  &lt;title&gt;Page title&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
  &lt;img src='images/company-logo.png' alt='Company' /&gt;
  &lt;h1 class='hello-world'&gt;Hello, world!&lt;/h1&gt;
  &lt;/body&gt;
  &lt;/html&gt;

**Correct example:**

&lt;!DOCTYPE html&gt;
&lt;html&gt;
  &lt;head&gt;
    &lt;title&gt;Page title&lt;/title&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;img src="images/company-logo.png" alt="Company"&gt;
    &lt;h1 class="hello-world"&gt;Hello, world!&lt;/h1&gt;
  &lt;/body&gt;
&lt;/html&gt;



## CSS



## Copy



-----



### Thanks

Heavily inspired by [Idiomatic CSS](https://github.com/necolas/idiomatic-css) and the [GitHub Styleguide](http://github.com/styleguide).

Designed and built with all the love in the world by [@mdo](http://twitter.com/mdo).
