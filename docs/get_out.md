---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Getting out of MDITA

All source format content is always in a state of transition. Whatever format your source files are in, you need be sure you can get them into a different source format, if you need to.

MDITA may be the new flavour of the month, but like all tech writing technologies it's going to be old hat some day. Something newer and shinier may come along that answers your needs even better. Or simply, events (such as a corporate takeover) may require you to migrate your MDITA content to another format to fit in with your new parent company's documentation system.

So how do you get out of MDITA?

1.  The first step would be to transform it in a way that merges in all your referenced and filtered content to an intermediate format like HTML or a standard Markdown. Converting to Markdown, owing to its simplicity, gives you lots of options for conversion.

2.  Once you have the content in Markdown, you have several options:

    1.  Use a tool like Oxygen XML Editor's Batch Convertor tool to switch from Markdown to DITA/Docbook/XHTML. The Batch Convertor tool in Oxygen is probably the cleanest way to get Markdown into DITA proper and provides excellent results.

    2.  Use [Pandoc](https://pandoc.org/) the universal converter which convert Markdown to a range of formats (including other docs-as-code formats like asciidoc).

    3.  If you want to convert to DITA and don't use Oxygen XML Editor, you can use the DITA-OT's *Normalized DITA* transform. This works pretty well but requires a bit more clean-up than the Batch Convertor tool. The converted files still have a *.md* extension which you have to change to *.dita*, for example, and the transform adds some unnecessary attributes and other stuff which you need to remove.


**Parent topic:**[Working with MDITA](mdita.md)

