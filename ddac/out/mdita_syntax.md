# MDITA syntax

The DITA Open Toolkit website provides a cheat-sheet for MDITA mark-up: [MDITA syntax reference](https://www.dita-ot.org/dev/topics/markdown-dita-syntax-reference.html). In section I've provided a brief résumé of the most commonly used syntax items.

MDITA is based on [CommonMark](https://commonmark.org/).

## Headings

As DITA assigns heading level by position in the map, it's not a good idea to have more than on heading generally in an MDITA topic. If you want to have sections in your MDITA topic, assign a level heading and add the `{.section}` class value in curly brackets as in the following example:

```
# Topic title

## Section title {.section}
```

Do not include any level three or lower headings in a MDITA topic.

## Paragraphs

The first paragraph in an MDITA file is treated \(in traditional DITA terms\) as a *shortdesc* element.

## Links

Links use the following format:

```
[Markdown](test.md)
[DITA](test.dita)
[HTML](test.html)
[External](http://www.example.com/test.html)
```

## Images

Images can be inline as well as on their own line and can be given titles and *alt* content.

```
An inline ![Alt](test.jpg).

![Alt](test.jpg)

![Alt](test.jpg "Title")
```

## Inline elements

The following inline elements are possible:

```
**bold** or __bold__
*italic* or _italic_
```

Note that strikethough \(as in GitHub-flavoured Markdown\) is not permitted. Underline, subscript, and superscript can added by using the relevant HDITA tags with a HDITA snippet:

```
<p>This is an <u>underline</u>.</p>
<p>This is an <sub>subscript</sub>.</p>
<p>This is an <sup>superscript</sup>.</p>
```

## Alerts

There is no specific MDITA markup for Notes/Alerts/Callouts.

## Lists

Multi-level ordered and unordered lists are possible.

Unordered lists:

```
- Item 1
- Item 2
- Item 3

* Item 1
* Item 2
* Item 3

** Item 1
    * 2nd Item 1
* Item 2
* Item 2
    - 2nd level item 1 
    - 2nd level item 2      
* Item 3

```

Ordered lists:

```
1. Item 1
1. Item 2
1. Item 3

1. Item 1
1. Item 2
    1. 2nd level item 1
    1. 2nd level item 2
    1. 2nd level item 3
1. Item 3
```

## Tables

MDITA also incorporates [MultiMarkdown](https://fletcherpenney.net/multimarkdown/) or [GitHub-flavoured Markdown](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/organizing-information-with-tables) style tables:

```
| First Header | Second Header | Third Header |
| ------------ | :-----------: | -----------: |
| Content      | *Long Cell*                 ||
| Content      | **Cell**      | Cell         |
```

