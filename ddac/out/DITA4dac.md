# DITA-as-code

With the advent of the upcoming Lightweight DITA \(LwDITA\) standard, the advantages of the docs-as-code approach can be brought to DITA. LwDITA is a simplified form of the DITA standard with only 48 tags in total and comes in 3 flavors:

-   XDITA - a subset of the main DITA standard XML elements.

-   HDITA - A DITA variant written in HTML5 rather than XML.

-   MDITA - A DITA variant written in Markdown rather than XML. This is based on GitHub-flavored Markdown but incorporates MultiMarkdown features for tables.


MDITA is the real game changer for docs as code but we will need all 3 variants for a complete solution.

As with normal Markdown, you can include HTML tags, and in this case HDITA tags can be used in MDITA files. The use of HDITA tags allows important DITA features such as content referencing and content filtering. Use of HDITA tags is does not add sufficient complexity to the MDITA source that they interfere with ease of editing for non-DITA savvy reviewer.

As with full-fat DITA, MDITA files are organized into maps. The maps are written in XDITA and would not normally need to be reviewed by non-writers. Maps provide the organizing principle - the navigation table of contents - for a documentation site. Specialized HDITA files holding key definitions or content reference content used in build processing only can also be added to maps along with the MDITA files.

