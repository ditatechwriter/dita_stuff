# MDITA topic syntax

The DITA Open Toolkit website provides a cheat-sheet for MDITA mark-up: [MDITA-syntax-ref]. Here I've provided a brief résumé of the most commonly used syntax items.

MDITA is based on [CommonMark](https://commonmark.org/).

## Headings {.section}

As DITA assigns heading level by position in the map, it's not a good idea to have more than one heading generally in an MDITA topic. If you want to have sections in your MDITA topic, assign a level 2 heading and add the *.section* class value in curly brackets as in the following example:

```xml
# Topic title

## Section title {.section}
```

Do not include any level three or lower headings in a MDITA topic. You can only 1 level 1 heading in a topic but you can have as many level 2 sections as you like, although you **cannot** have sections within sections.

If you a complex multi-level heading topic, break it up into smaller topics and assign the required heading levels in the map.

## Paragraphs {.section}

Paragraphs are separated by 2 returns as in most flavors of Markdown

The first paragraph in an MDITA file is treated (in traditional DITA terms) as a *shortdesc* element by transform plugins.

## Links {.section}

Links use the following format:

```xml
[Markdown](test.md)
[DITA](test.dita)
[HTML](test.html)
[External](http://www.example.com/test.html)
```
However if you are refering to a markdown file in the same document, and that file has a key defined for it in the ditamap, you can just refer to the key within square brackets. For example:

```
For more information, see [using-maps].
```
When the document is built the key is replaced by the title of the topic. The same applies for keys defined in an external links map. For more information, see [MDITA-keys].

## Images {.section}

Images can be inline as well as on their own line and can be given titles and *alt* content.

```xml
An inline ![Alt](test.jpg).

![Alt](test.jpg)

![Alt](test.jpg "Title")
```
## Inline elements {.section}

The following inline elements are possible:

```xml
**bold** or __bold__
*italic* or _italic_
```

Note that strikethough (as in GitHub-flavoured Markdown) is not permitted. Underline, codephrase, subscript, and superscript can added by using the relevant HDITA tags with a HDITA snippet:

```xml
<p>This is an <u>underline</u>.</p>
<p>This is an <sub>subscript</sub>.</p>
<p>This is an <sup>superscript</sup>.</p>
```
## Alerts {.section}

There is no specific MDITA markup for Notes/Alerts/Callouts. Use the HDITA *\<note>* tag wrapped in a *\<p>* tag. Use the *type* attribute to define different types of alert. The options are given below:

```xml
<p><note>This is a note</note></p>
<p><note type="caution">This is a caution </note></p>
<p><note type="danger">This is a danger</note></p>
<p><note type="notice">This is a notice</note></p>
<p><note type="trouble">This is a trouble</note></p>
<p><note type="warning">This is a warning</note></p>
```
## Lists {.section}

Multi-level ordered and unordered lists are possible.

Unordered lists:

```xml
- Item 1
- Item 2
- Item 3

* Item 1
* Item 2
* Item 3

* Item 1
    * 2nd Item 1
* Item 2
* Item 3
    - 2nd level item 1 
    - 2nd level item 2      
* Item 4

```
- Item 1
- Item 2
- Item 3

Example with asterisks:

* Item 1
* Item 2
* Item 3

Example with 2nd level lists items:

* Item 1
    * 2nd Item 1
* Item 2
* Item 3
    - 2nd level item 1 
    - 2nd level item 2      
* Item 4


Ordered lists:

```xml
1. Item 1
1. Item 2
1. Item 3
    1. 2nd level item 1
    1. 2nd level item 2
    1. 2nd level item 3
1. Item 4
```
1. Item 1
1. Item 2
1. Item 3
    1. 2nd level item 1
    1. 2nd level item 2
    1. 2nd level item 3
1. Item 4


## Tables {.section}

MDITA also incorporates [multimarkdown] or [gfm] style tables:

```xml
| First Header | Second Header | Third Header |
| ------------ | :-----------: | -----------: |
| Content      | *Long Cell*                 ||
| Content      | **Cell**      | Cell         |
```
| First Header | Second Header | Third Header |
| ------------ | :-----------: | -----------: |
| Content      | *Long Cell*                 ||
| Content      | **Cell**      | Cell         |

Admittedly MDITA, like any flavor of Markdown, is weak when it comes to tables. Markdown tables must be short and simple or they become virtually impossible to read. Reviewing Markdown content that content long and/or complex tables is very difficult and defeats the purpose.

<p><note type="warning">If you have a documentation that contains many tables then Markdown-based systems are probably less useful. A more robust system like standard DITA is more appropriate in that case.</note></p>

## Video {.section}

Generally you cannot add videos to a Markdown file but by adding the HDITA HTML5 tags to the file you can access video:

```xml
Check out the video below for more information:

<video title="My New Video" controls autoplay loop muted>
    <source src="media/vid1.mp4" poster="vid1.jpg"/>
</video>    
```
Note that you will need to provide an image to be displayed in place of the video for the user to access it.

## Escaping special characters  {.section}

Special characters are escaped using a backslash.
