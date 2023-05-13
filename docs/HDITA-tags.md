---
author: Michael McLoughlin
publisherinformation: V1.0
---

# HTML5 tags in MDITA topics

HDITA is the HTML5 flavor of LwDITA. Entire topics can be written in HDITA of course but we are interested here in those tags that can be used to augment functionality in MDITA topics. The following HDITA/HTML5 tags can be used in MDITA:

-   **<em\>** - to italicize text.

-   **<strong\>** - to embolden text.

-   **<u\>** - to underline text \(please avoid using underlining\).

-   **<dl\>** - a definition list

-   **<dt\>** inside **<dl\>** - a definition term.

-   **<dd\>** inside **<dt\>** - a definition description.

-   **<figure\>** - a container for an image.

-   **<img\>** - an image.

-   **<ol\>** - to introduce an ordered list.

-   **<ul\>** - to introduce an unordered list.

-   **<li\>** inside **<ul\>** or **<ol\>** - a list item.

-   **<p\>** - a paragraph. Especially important when using context references.

-   **<span\>** - a span of text. Used mostly for key references within notes and context referenced text.

-   **<codeblock\>** - to indicate code or teletype text.

-   **<section\>** - To designate a new section in HTML content.

-   **<a href\>** - an anchor tag for links.

-   **<sub\>** - for subscript content.

-   **<sup\>** - for superscript content.

-   **<audio\>** - to embed audio content.

-   **<video\>** - to embed video content.

-   **<source\>** inside **<audio\>** or **<video\>** - to indicate the path to a video or audio source file.

-   **<table\>** - a table

-   **<tr\>** inside **<table\>** - a table row.

-   **<th\>** inside **<tr\>** - a table header row.

-   **<td\>** inside **<tr\>** - a table cell.


Each tag also has one or more attributes but please refer to the latest LwDITA specification doc for those details.

Many of the tags do have Markdown counterparts so why would you use them? Well, the short answer is for encapsulating text you want to reuse or filter. You can find out about that in more detail further on in [Using content references with MDITA](MDITA-conrefs.md) and [Using filters with MDITA](MDITA-filters.md).

## When to use HTML5 tags in MDITA files

There are 4 main occasion when you need to include HTML code in your MDITA markdown content:

1.  For notes/alerts/admonitions \(for more information, see [MDITA topic syntax](mdita_syntax.md)\).

2.  For context reference \(conref\) content pulled in from another file \(for more information, see [Using content references with MDITA](MDITA-conrefs.md)\).

3.  For text to which a filter is to be applied \(for more information, see [Using filters with MDITA](MDITA-filters.md)\).

4.  For embedding video \(for more information, see [MDITA topic syntax](mdita_syntax.md).


**Parent topic:**[Working with MDITA](mdita.md)

