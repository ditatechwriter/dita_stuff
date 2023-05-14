---
author: Michael McLoughlin
publisherinformation: V1.0
---

# MDITA frontmatter

Frontmatter refers to the content in YAML format that you can place at the start of an MDITA file. This content is essentially metadata that's useful when converting to other formats. This content, for example, is passed to the META tags in the HEAD of an HTML file. The content is also useful is the markdown file is ever converted to standard DITA XML.

Markdown delineates frontmatter with 3 dashes above and below and must be the first thing in the topic. There can be no spaces or empty lines before the frontmatter. For example:

```xml
---
author: Michael
---

# MDITA frontmatter

Frontmatter refer to the contttnt in YAML format that can be placed at the start of an MDITA file.
This content is essentially metadata that is useful when converting to other formats. 
This content, for example, is passed to the META tags in the HEAD of an HTML file. 
The content is also useful is the markdown fie is ever converted to standard DITA XML.

...
```

Two items of frontmatter are required: an *id* which serves as a unique identifier for the MDITA file, and the *author* so that the writer of the topic can be identified in the future. You can also use the value of the *id* as a key for the topic when you add it to the ditamap.

Other possible frontmatter items include:

-   publisher

-   source

-   permissions

-   audience

-   category

-   keywords

-   resourceid


**Parent topic:**[Writing and Reviewing MDITA](write-review-MDITA.md)

