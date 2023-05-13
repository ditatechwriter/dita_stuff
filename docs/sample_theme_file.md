---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Working with theme files

The `libexec/docsrc/samples/themes` folder within the 4.0 \(and later\) release of the DITA-OT contains several sample theme files. The most useful of which is the [dita-ot-docs-theme.yaml](https://github.com/dita-ot/docs/blob/develop/samples/themes/dita-ot-docs-theme.yaml) file. It's a long file which I won't reproduce here but click on the link to go to DITA-OT docs GitHub repository to see it in full.

The easiest way to work with theme files to copy and edit your own version of the `dita-ot-docs-theme.yaml`.

## What can theme files do?

Even though theme files are not as powerful as custom plugins, there is still a wide range of things you can do with them:

-   Define page, size, orientation and margins.

-   Define headers and footers.

-   Create a cover page and add an image and title to it.

-   Style a range of block level and inline elements.

-   Create style variables that you can use elsewhere in the theme file.

-   Extend existing theme files to produce variants \(e.g. versions of the document in A4 and US Letter formats\).


The [DITA-OT website](https://www.dita-ot.org/4.0/topics/pdf-themes.html) contains a reasonably good quickstart guide which, coupled with the sample theme file, are enough to get you started. A knowledge of XSL-FO properties \(or at least CSS\) would really help but a little trial and error, and practice styling some basic PDF output will prove fruitful.

The following videos from the 2022 DITA-OT Day conference explain about the feature's raison d'être.





**Parent topic:**[PDF2 theme files](pdf2_themes.md)

