---
id: frontmatter
author: Michael
---

# MDITA frontmatter

Frontmatter refers to the content in YAML format that can be placed at the start of an MDITA file. This content is essentially metadata that is useful when converting to other formats. This content, for example, is passed to the META tags in the HEAD of an HTML file. The content is also useful is the markdown file is ever converted to standard DITA XML.

Frontmatter is delineated by 3 dashes above and below and must be the first thing in the topic. There can be no spaces or empty lines before the frontmatter. For example:

```
---
id: frontmatter
author: Michael
---

# MDITA frontmatter

Frontmatter refers to the content in YAML format that can be placed at the start of an MDITA file. This content is essentially metadata that is useful when converting to other formats. This content, for example, is passed to the META tags in the HEAD of an HTML file. The content is also useful is the markdown file is ever converted to standard DITA XML.

...
```

For our purposes, only 2 items of front maatter are required: an *id* which serves as a unique identifier for the MDITA file, and the *author* so the writer of the topic can be identified i nthe future. The value of the *id* should be used also as key for the topic when it is added to the ditamap.

Other possible frontmatter items include:

* publisher
* source
* permissions
* audience
* category
* keywords
* resourceid