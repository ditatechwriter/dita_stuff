---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Working with MDITA

With the advent of the upcoming Lightweight DITA (LwDITA) standard, the advantages of the docs-as-code approach are available in DITA. LwDITA is a simplified form of the DITA standard with only 48 tags in total and comes in 3 flavors:

-   XDITA - a subset of the main DITA standard XML elements.

-   HDITA - A DITA variant written in HTML5 rather than XML.

-   MDITA - A DITA variant written in Markdown rather than XML. MDITA is the same as GitHub-flavored Markdown but also incorporates MultiMarkdown features for tables.

MDITA is the real game changer for a docs-as-code approach for DITA but you need all 3 variants for a complete solution.

As with standard Markdown, you can include HTML tags, and in this case you can use HDITA tags in MDITA files. The use of HDITA tags allows important DITA features such as content referencing and content filtering. Use of HDITA tags doesn't add enough complexity to the MDITA source that they interfere with ease of editing for non-DITA savvy reviewer.

As with full-fat DITA, you organize MDITA files into maps. Although MDITA you can write maps in Markdown, there is little or no tool support for this yet. Therefore use maps written in standard DITA or XDITA. Maps are the organizing principle - the navigation table of contents - for a documentation site.

You can also add specialized HDITA files holding key definitions or content reference content used in build for processing only to maps along with the MDITA files.
