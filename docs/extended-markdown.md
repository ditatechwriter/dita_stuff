---
author: [Michael McLoughlin, Michael]
publisherinformation: V1.0
---

# New functionality for Markdown

MDITA extends what Markdown can do. As you have already seen, you can add videos to your Markdown content in [MDITA topic syntax](mdita_syntax.md), but the real power of MDITA lies in the DITA content reuse features that it brings to Markdown content.

-   Text variables using key definitions to create variable text that allows you to update keywords in your document in one place and have the changes reflected throughout the document immediately. For more detail on this, see [Using keys](MDITA-keys.md).

-   Key references that allow you to assign a new name to a file or external resource that you can use when referencing that resource. You can happily change the file name, location, or URL in a ditamap without breaking any links in the document. For more detail on this, see [Using keys](MDITA-keys.md).

-   Content references that you can use to reference content in many places in the document without having many copies of the content. If the content ever needs updated, you can do it in one place and the changes automatically reflected everywhere else in the document. For more detail on this, see [Using content references with MDITA](MDITA-conrefs.md).

-   Text filtering that you can deploy to exclude elements of text from a build to produce different versions of a document for different purposes (perhaps different audiences, releases, software platforms etc.).For more detail on this, see [Using filters with MDITA](MDITA-filters.md).
