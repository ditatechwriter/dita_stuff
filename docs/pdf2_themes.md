---
author: Michael McLoughlin
publisherinformation: V1.0
---

# PDF2 theme files

For many years, DITA Information Architects have done battle with the mighty DITA Open Toolkit \(DITA-OT\) PDF2 plugin. Armed with Leigh White's indispensable tome [DITA for Print](https://xmlpress.net/publications/dita/dita-for-print/), they have struggled to create custom PDF plugins that produce good looking PDFs from DITA source files. And while for truly bespoke PDF output, customizing the PDF2 plugin is the only way, release 4.0 of the DITA-OT offers an somewhat easier \(but by no means simple\) way to work with the PDF2 plugin - *theme* files.

Prior to this, creating a custom PDF plugin involved creating a whole set of customization folders and override files \(the system was based largely on the methods used in the Docbook Style Sheets\). It involved hacking around in XSLT templates and attributes files. Generally this was done by consultants, usually when the team first converted to DITA. And generally the expertise was never passed on, or soon lost as team personnel changed. Something as simple as a logo change or an update to brand colors could prove an expensive nightmare for teams that did not have XSLT expertise on staff.

Theme files are YAML files whose key/value pairs represent CSS properties and values \(or actually XSL-FO properties which are *nearly* always the same\). Once configured, the theme file can be applied to the build instruction. For example:

```language-bourne
dita -i some.ditamap -o out --format=pdf2 --theme=mytheme.yaml
```

The theme YAML file feeds the theme file parameters to the build-in PDF2 plugin at build time with no requirement to actually go in and mess with the XSLT attributes files within the PDF2 plugin itself. And although it may not solve all the problems of PDF creation from DITA, it goes a long way to help documentation teams work with PDF output in a manageable and maintainable way.

-   **[Working with theme files](sample_theme_file.md)**  

-   **[Limitations](limitations.md)**  

-   **[Are theme files worth using?](conclusion.md)**  


