---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Are theme files worth using?

Despite their limitation, theme files are definitely worth using. Yes, you will still need some knowledge of XSL-FO properties but anyone with some knowledge of CSS would be able to pick that up pretty quickly. True, your docs will not look quite as pretty as those made with a custom PDF plugin, but you can still make pretty good looking and totally functional documents using theme files.

The big benefit here is ease of use and maintenance. Currently if a request to change some styling on our PDF output comes in while I'm away on holiday, it has to wait until I come back because no-one else in the team dares touch the custom plugins with any confidence. But a little training is all it takes for anyone on the team to take a stab at replacing a cover image or changing the corporate colors in a theme file.

And when it comes to developing PDFs from DITA content, using theme files comes a whole lot cheaper than paying a consultant to write a plugin.

I work for a company that has a lot of very long, complex documents that are outputted to PDF. I am actively looking at ways we can simplify the styling and structure of our documents so that they can be build using a theme file and the standard PDF2 plugin rather than the current custom PDF2 customization layer plugin I wrote. This will enable the team to continue to style and maintain the PDF output when I am not around. However, if you have a complicated PDF plugin doing fancy things with map variables, cover pages, and header/footer content, theme files will simply not be able to replicate everything.

**Parent topic:**[PDF2 theme files](pdf2_themes.md)

