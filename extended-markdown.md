---
id: extended-markdown
author: Michael
---

# New functionality for Markdown

MDITA extends what markdown can do. We've already seen how you can add videos to your Markdown content in [mdita-syntax], but the real power of MDITA lies in the DITA content reuse features that it brings to Markdown content.

* Text variables using key definitions to create variable text that allows you update keywords in your document in one place and have the changes reflected throughout the document immediately. For more detail on this, see [MDITA-keys].
* Key references that allow you assign a new name to a file or external resource that you can use when referencing that resource. You can happily change the file name, location, or URL in a ditamap without breaking any links in the document. For more detail on this, see [MDITA-keys].
* Content references that you can use to refer to content in multiple places in the document without having multiple copies of the content. If the content ever needs updated, it can be done so in one place and the changes automatically reflected everywhere else in the document.For more detail on this, see [MDITA-conrefs].
* Text filtering that you can deploy to exclude elements of text from a build to produce different versions of a document for diffrent purposes (perhaps different audiences, releases, software platforms etc.).For more detail on this, see [MDITA-filters].
