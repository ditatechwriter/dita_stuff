---
id: publish-MDITA
---

# Publishing MDITA content

Even though MDITA is Markdown you can't just drop raw MDITA file into your static site generator `/docs` folder and expect it all to work like common or garden Markdown.

In order to take advantage of content reuse and filtering features that DITA gives you, you must run it through the DITA Open Toolkit markdown transform. Doing that will resolve keys and conrefs, and apply filters. The output you get will be standard GitHub-flavored Markdown that you can then use in your static site generator.



