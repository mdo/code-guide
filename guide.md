<!DOCTYPE html>
<html>
  <head>
    <title>Code Guide &middot; Standards for developing flexible, durable, and sustainable HTML and CSS.</title>

    <!-- CSS -->
    <link rel="stylesheet" type="text/css" href="http://fonts.googleapis.com/css?family=Open+Sans:300,400,700">
    <link rel="stylesheet" type="text/css" href="js/google-code-prettify/prettify.css">
    <link rel="stylesheet" type="text/css" href="css/styleguide.css">

    <!-- Javascript -->
    <script src="js/google-code-prettify/prettify.js"></script>
  </head>

  <body onload="prettyPrint()">

    <div class="jumbotron">
      <div class="container">
        <h1>Code Guide</h1>
        <p class="lead">Standards for developing flexible, durable, and sustainable HTML and CSS.</p>
      </div>
    </div>

    <div class="container">


      <hr>

      <h1 id="toc">Table of contents <a class="docs-permalink" href="#toc" title="Link to this section">&infin;</a></h1>
      <ol class="contents">
        <li><a href="#golden-rule">The golden rule</a></li>
        <li><a href="#html">HTML</a>
          <ul>
            <li><a href="#html-syntax">Syntax</a></li>
            <li><a href="#html-doctype">HTML5 doctype</a></li>
            <li><a href="#html-pragmatism">Pragmatism over semantics</a></li>
            <li><a href="#html-attr-order">Attributes order</a></li>
            <li><a href="#html-generated-markup">Avoid generated markup</a></li>
          </ul>
        </li>
        <li><a href="#css">CSS</a>
          <ul>
            <li><a href="#css-syntax">Syntax</a></li>
            <li><a href="#css-declaration-order">Declaration order</a></li>
            <li><a href="#css-formatting-exceptions">Formatting exceptions</a>
              <ul>
                <li><a href="#css-formatting-prefixed">Prefixed properties</a></li>
                <li><a href="#css-formatting-single-line">Rules with single declarations</a></li>
              </ul>
            </li>
            <li><a href="#css-human-readable">Human readable</a>
              <ul>
                <li><a href="#css-human-comments">Comments</a></li>
                <li><a href="#css-human-classes">Classes</a></li>
                <li><a href="#css-human-selectors">Selectors</a></li>
              </ul>
            </li>
            <li><a href="#css-organization">Organization</a></li>
          </ul>
        </li>
        <li><a href="#copy">Writing copy</a>
          <ul>
            <li><a href="#copy-sentence-case">Sentence case</a></li>
          </ul>
        </li>
      </ol>



      <hr>



      <h1 id="golden-rule">
        I. The golden rule
        <a class="docs-permalink" href="#golden-rule" title="Link to this section">&infin;</a>
      </h1>

      <blockquote>
        <p>All code in any code base should look like a single person typed it, no matter how many people contributed.</p>
      </blockquote>
      <p>This means strictly enforcing these agreed upon guidelines at all times. For additions or contributions, please <a href="https://github.com/markdotto/code-guide">file an issue on GitHub</a>.</p>



      <hr>



      <h1 id="html">
        II. HTML
        <a class="docs-permalink" href="#html" title="Link to this section">&infin;</a>
      </h1>

      <h2 id="html-syntax">
        Syntax
        <a class="docs-permalink" href="#html-syntax" title="Link to this section">&infin;</a>
      </h2>
      <ul>
        <li>Use soft-tabs with two spaces</li>
        <li>Nested elements should be indented once (2 spaces)</li>
        <li>Always use double quotes, never single quotes</li>
        <li>Don't include a trailing slash in self-closing elements</li>
      </ul>
      <h4>Incorrect example:</h4>
<pre class="prettyprint linenums">
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
</pre>
      <h4>Correct example:</h4>
<pre class="prettyprint linenums">
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
</pre>

      <h2 id="html-doctype">
        HTML5 doctype
        <a class="docs-permalink" href="#html-doctype" title="Link to this section">&infin;</a>
      </h2>
      <p>Enforce standards mode in every browser possible with this simple doctype at the beginning of every HTML page.</p>
<pre class="prettyprint linenums">
&lt;!DOCTYPE html&gt;
</pre>

      <h2 id="html-pragmatism">
        Pragmatism over semantics
        <a class="docs-permalink" href="#html-pragmatism" title="Link to this section">&infin;</a>
      </h2>
      <p>Strive to maintain HTML standards and semantics, but don't sacrifice pragmatism. Use the least amount of markup with the fewest intricies whenever possible.</p>

      <h2 id="html-attr-order">
        Attribute order
        <a class="docs-permalink" href="#html-attr-order" title="Link to this section">&infin;</a>
      </h2>
      <p>HTML attributes should come in this particular order for easier reading of code.</p>
      <ul class="code">
        <li>class</li>
        <li>id</li>
        <li>data-*</li>
        <li>for|type|href</li>
      </ul>
      <p>Such that your markup looks like:</p>
<pre class="prettyprint linenums">
&lt;a class="" id="" data-modal="" href=""&gt;Example link&lt;/a&gt;
</pre>

      <h2 id="html-generated-markup">
        Avoid generated markup
        <a class="docs-permalink" href="#html-generated-markup" title="Link to this section">&infin;</a>
      </h2>
      <p>Writing markup in a javascript file makes the content harder to find, harder to edit, and less performant. Don't do it.</p>



      <hr>



      <h1 id="css">
        III. CSS
        <a class="docs-permalink" href="#css" title="Link to this section">&infin;</a>
      </h1>

      <h2 id="css-syntax">
        Syntax
        <a class="docs-permalink" href="#css-syntax" title="Link to this section">&infin;</a>
      </h2>
      <ul>
        <li>Use soft-tabs with two spaces</li>
        <li>When grouping selectors, keep individual selectors to a single line</li>
        <li>Include one space before the opening brace of declaration blocks</li>
        <li>Place closing praces of declaration blocks on a new line</li>
        <li>Include one space after <code>:</code> in each property</li>
        <li>Each declaration should appear on its own line</li>
        <li>End all declarations with a semi-colon</li>
        <li>Comma-separated values should include a space after each comma</li>
        <li>Don't include spaces after commas in RGB or RGBa colors, and don't preface values with a leading zero</li>
        <li>Lowercase all hex values, e.g., <code>#fff</code> instead of <code>#FFF</code></li>
        <li>Use shorthand hex values where available, e.g., <code>#fff</code> instead of <code>#ffffff</code></li>
        <li>Quote attribute values in selectors, e.g., <code>input[type="text"]</code></li>
        <li>Avoid specifying units for zero values, e.g., <code>margin: 0;</code> instead of <code>margin: 0px;</code></li>
      </ul>
      <h4>Incorrect example:</h4>
<pre class="prettyprint linenums">
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}
</pre>
      <h4>Correct example:</h4>
<pre class="prettyprint linenums">
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin: 0 0 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
</pre>
      <p>Questions on the terms used here? See the <a href="http://en.wikipedia.org/wiki/Cascading_Style_Sheets#Syntax">syntax section of the Cascading Style Sheets article</a> on Wikipedia.</p>

      <h2 id="css-declaration-order">
        Declaration order
        <a class="docs-permalink" href="#css-declaration-order" title="Link to this section">&infin;</a>
      </h2>
      <p>Related declarations should be grouped together, placing positioning and box-model properties closest to the top, followed by typographic and visual properties.</p>
<pre class="prettyprint linenums">
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
  line-height: 1.5
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
</pre>
      <p>For a complete list of properties and their order, please see <a href="http://twitter.github.com/recess">Recess</a>.</p>

      <h2 id="css-formatting-exceptions">
        Formatting exceptions
        <a class="docs-permalink" href="#css-formatting-exceptions" title="Link to this section">&infin;</a>
      </h2>
      <p>In some cases, it makes sense to deviate slightly from the default <a href="#css-syntax">Syntax</a>.</p>
      <h3 id="css-formatting-prefixed">Prefixed properties</h3>
      <p>When using vendor prefixed properties, indent each property such that the value lines up vertically for easy multi-line editing.</p>
<pre class="prettyprint linenums">
.selector {
  -webkit-border-radius: 3px;
     -moz-border-radius: 3px;
          border-radius: 3px;
}
</pre>
      <p>In Textmate, use <strong>Text &rarr; Edit Each Line in Selection</strong> (&#8963;&#8984;A). In Sublime Text 2, use <strong>Selection &rarr; Add Previous Line</strong> (&#8963;&#8679;&uarr;) and <strong>Selection &rarr;  Add Next Line</strong> (&#8963;&#8679;&darr;).</p>
      <h3 id="css-formatting-single-line">Rules with single declarations</h3>
      <p>In instances where several rules are present with only one declaration each, consider removing new line breaks for readability and faster editing.</p>
<pre class="prettyprint linenums">
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
</pre>


      <h2 id="css-human-readable">
        Human readable
        <a class="docs-permalink" href="#css-human-readable" title="Link to this section">&infin;</a>
      </h2>
      <p>Code is written and maintained by people. Ensure your code is descriptive, well commented, and approachable by others.</p>

      <h3 id="css-human-comments">
        Comments
        <a class="docs-permalink" href="#css-human-comments" title="Link to this section">&infin;</a>
      </h3>
      <p>Great code comments convey context or purpose and should not just reiterate a component or class name.</p>
      <h4>Bad:</h4>
<pre class="prettyprint linenums">
/* Modal header */
.modal-header {
  ...
}
</pre>
      <h4>Good:</h4>
<pre class="prettyprint linenums">
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
</pre>

      <h3 id="css-human-classes">
        Class names
        <a class="docs-permalink" href="#css-human-classes" title="Link to this section">&infin;</a>
      </h3>
      <ul>
        <li>Keep classes lowercase and use dashes (not underscores or camelCase)</li>
        <li>Avoid arbitrary shorthand notation</li>
        <li>Keep classes as short and succinct as possible</li>
        <li>Use meaningful names; use structural or purposeful names over presentational</li>
        <li>Prefix classes based on the closest parent component's base class</li>
      </ul>
      <h4>Bad:</h4>
<pre class="prettyprint linenums">
.t { ... }
.red { ... }
.header { ... }
</pre>
      <h4>Good:</h4>
<pre class="prettyprint linenums">
.tweet { ... }
.important { ... }
.tweet-header { ... }
</pre>

      <h3 id="css-human-selectors">
        Selectors
        <a class="docs-permalink" href="#css-human-selectors" title="Link to this section">&infin;</a>
      </h3>
      <ul>
        <li>Use classes over generic element tags</li>
        <li>Keep them short and limit the number of elements in each selector to three</li>
        <li>Scope classes to the closest parent when necessary (e.g., when not using prefixed classes)</li>
      </ul>
      <h4>Bad:</h4>
<pre class="prettyprint linenums">
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
</pre>
      <h4>Good:</h4>
<pre class="prettyprint linenums">
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
</pre>


      <h2 id="css-organization">
        Organization
        <a class="docs-permalink" href="#css-organization" title="Link to this section">&infin;</a>
      </h2>
      </h2>
      <ul>
        <li>Organize sections of code by component</li>
        <li>Develop a consistent commenting hierarchy</li>
        <li>If using multiple CSS files, break them down by component</li>
      </ul>



      <hr>



      <h1 id="copy">
        IV. Writing copy
        <a class="docs-permalink" href="#copy" title="Link to this section">&infin;</a>
      </h1>

      <h2 id="copy-sentence-case">
        Sentence case
        <a class="docs-permalink" href="#copy-sentence-case" title="Link to this section">&infin;</a>
      </h2>
      <p>Always write copy, including headings, in <a href="http://en.wikipedia.org/wiki/Letter_case#Usage">sentence case</a>. In other words, aside from titles and proper nouns, only the first word should be capitalized.</p>



      <hr>



      <div class="footer">
        <p>Heavily inspired by <a href="https://github.com/necolas/idiomatic-css">Idiomatic CSS</a> and the <a href="http://github.com/styleguide">GitHub Styleguide</a>.</p>
        <p>Designed and built with all the love in the world by <a href="http://twitter.com/mdo">@mdo</a>.</p>
      </div>

  </body>
</html>
