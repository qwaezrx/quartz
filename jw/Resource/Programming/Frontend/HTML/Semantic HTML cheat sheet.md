#Cheat-sheet

There are hundreds of semantic tags to help describe the meaning of your [[HTML]] documents.

[Mozilla web HTML elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)
## Sectioning tags
> Use the following tags to organize your HTML document into structured sections.

| Tag | Description |
|:---|:---|
| `<header>` | The header of a content section or the web page. The web page header often contains the website branding or logo. |
| `<nav>` | The navigation links of a section or the web page. |
| `<fotter>` | On the web page, it often contains secondary links, the copyright notice, privacy policy and cookie policy links |
| `<main>` | Specifies the main content of a section or the web page. |
| `<aside>` | A secondary set of content that is not required to understand the main content. |
| `<article>` | An independent, self-contained block of content such as a blog post or product. |
| `<section>` | A standalone section of the document that is often used within the body and article elements.|
| `<details>` | A collapsed section of content that can be expanded if the user wishes to view it. |
| `<summary>` | Specifies the summary or caption of a `<details>` element. |
| `<h1><h2><h3><h4><h5><h6>` | Headings on the web page. |
## Content tags

| Tag | Description |
|:---|:---|
| `<blockquote>` | <quotation>Used to describe a quotation.</quotation> |
| `<dd>` | Used to define a description for the preceding `<dt>` element. |
| `<dl>` | Used to define a description list. |
| `<dt>` | Used to describe terms inside `<dl>` elements. |
| `<figcaption>` | Defines a caption for a photo image. |
| `<figure>` | Applies a horizontal line to the parent element. |
| `<hr>` | Adds a horizontal line to the parent element. |
| `<li>` | List item |
| `<menu>` | A semantic alternative to `<ul>` tag. |
| `<ul>` | Unordered list |
| `<ol>` | Ordered list |
| `<p>` | Paragraph |
| `<pre>` | Used to represent preformatted text. Typically rendered in the web browser using a monospace font. |
## Inline tags

| Tag | Description |
|:---|:---|
|`<a>`| <a href="https://www.coursera.org/learn/html-and-css-in-depth/supplement/ZIzeF/semantic-html-cheat-sheet">An anchor link to another HTML document.</a> |
|`<abbr>`| <abbr>Specifies that the containing text is an abbreviation or acronym.</abbr>|
| `<b>` | <b>Bold. When used to indicate importance use `strong` instead.</b> |
| `<strong>` | <strong>Displays the containing text in bold. Used to indicate importance.</strong> |
| `<br>` | A line break. |
| `<cite>` | <cite>Defines the title of creative work (for example a book, poem, song, movie, painting or sculpture). The text in here is usually rendered in italics.</cite> |
| `<code>` | <code>Indicates that the containing text is a block of computer code.</code> |
| `<data>` | <data>Indicates machine-readable data.</data> |
| `<em>` | <em>Emphasizes the containing text.</em> |
| `<i>` | <i>Italic. Used to indicate idiomatic text or technical terms.</i> |
| `<mark>` | <mark>A containing text should be marked or highlighted.</mark> |
| `<q>` | <q>Quotation</q> |
| `<s>` | <s>Strikethrough</s> |
| `<samp>` | <samp>Sample</samp> |
| `<small>` | <small>Used to represent small text, such as copyright and legal text.</small> |
| `<span>` | <span>A generic element for grouping content for CSS styling</span> |
| `<sub>` | <sub>Subscript text, displayed in lowered baseline.</sub> |
| `<sup>` | <sup>Superscript text, displayed with a raised baseline.</sup> |
| `<time>` | <time>2010/3/1</time> A semantic tag used to display both dates and times. |
| `<u>` | <u>Underline</u> |
| `<var>` | <var>Variable in mathematical expression.</var> |
## Embedded content and media tags
| Tag | Description |
|:---|:---|
| `<audio>` | Used to embed audio in web pages. <audio controls><source src="https://www.computerhope.com/jargon/m/example.mp3" /></audio>|
| `<canvas>` | <canvas id="stockGraph" width="150" height="150">current stock price: $3.15 +0.15</canvas> |
| `<embed>` | <embed src="https://blog.hubspot.com/marketing/how-to-add-html-embed-codes-ht" width="150" height="150"> |
| `<iframe>` | <iframe width="150" height="100" src="https://www.youtube.com/embed/eGUEAvNpz48" title="Iframe example"></iframe> |
| `<img>` | <img src="https://picsum.photos/300/200"/> |
| `<object>` | Similar to `<embed>` but the content is provided by a web browser plug-in |
|`<picture>`| <picture><source srcset="/media/cc0-images/surfer-240-200.jpg" media="(orientation: portrait)" /><img src="/media/cc0-images/painted-hand-298-332.jpg" alt="" />An element that contains one `img` element and one or more source `source` elements to offer alternative images for different displays/devices.</picture> |
| `<video>` | <video controls width="250"><source src="https://www.youtube.com/watch?v=-pvfoNH9SDU"/></video>
| `<source>` | Specifies media resources for `<picture>`, `<audio>` and `<video>` elements. |
| `<svg>` | Used to define Scalable Vector Graphics within a web page. |
## Table tags

| Tag | Description |
|:---|:---|
| `<table>` | Defines a table element. |
| `<thead>` | Represents the main content of a table. Contains one or more `<tr>` elements.|
|`<tbody>` | Represents the main content of a table. Contains one or more `<tr>` elements. |
| `<tfoot>` | Represents the footer content of a table. Typically contains one `<tr>` element.|
|`<tr>`| Table Row. Contains one or more `<td>` elements when used within `<tbody>` or `<tfoot>`. When used within `<thead>`, contains one or more `<th>` elements.|
| `<td>` | Cell in table. Contains the text content of the cell. |
| `<th>` | Header cell of a table. Contains the text content of the header. |
|`<caption>`| Caption of table element. |
| `<colgroup>` | Defines a semantic group of one or more columns in a table for formatting. |
|`<col>`| Semantic columns in a table. |
