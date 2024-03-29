---
author: Michael McLoughlin
publisherinformation: V1.0
---

# DITA-OT project file structure

A DITA project file is an XML file containing build parameters for one or more documents that you can pass to the `dita` build command.

The following is a sample project file in XML format:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://www.dita-ot.org/project">
  
  <deliverable name="Grunt Master 6000 Guide" id="ug_gruntmaster6000_html5"> 
    <context name="Grunt Master 6000 Guide" id="ug_gruntmaster6000">
        <input href="ug_gruntmaster6000.ditamap"/>
        <profile>
            <ditaval href="GM6000.ditaval"/>
        </profile>
    </context>
    <output href="out"/>
    <publication transtype="html5">
        <param name="args.css" href="../css/custom.css"/>
        <param name="args.copycss" value="yes"/>
    </publication>
  </deliverable>
  
</project>
```

|Element|Description|
|-------|-----------|
|project|The wrapper element for deliverables in the project file. It has only one attribute `xmlns` which defines the XML namespace for the elements in the file.|
|deliverable|The wrapper element for all the deliverable parameters. Its attributes define the deliverable name and a unique ID for the deliverable.|
|context|This element wraps the elements that hold the input information (the source ditamap) and filters that are used by the build. **Note:** You can use context elements independently of the deliverable elements and so can use their own name and unique ID attributes.|
|input|This element stores the relative path to the input ditamap you want to use for the build within a `href` attribute.|
|profile |The `<profile>` element wraps one or more `<ditamap>` elements.|
|ditaval|This element stores the relative path to the any filter file you want to use for the build within a `href` attribute. There can be many `<ditaval>` tags for each context.|
|output|This element stores the relative path to the output folder where you want to deposit the outputted content within a `href` attribute.|
|publication|The `<publication>` element wraps parameter elements which content the build parameters passed to the DITA-OT. Importantly, it also must contain a `transtype` attribute that tells the DITA-OT which output format to transform the content into.|
|param|This element stores the actual build parameters that the DITA-OT uses when creating the output. Builds differ according to the output you have defined in the `<publication>` element `transtype` attribute. For a full list of parameters by output format, see the [DITA-OT website](https://www.dita-ot.org/dev/parameters/parameters-pdf.html)|

Visit the DITA-OT website to see examples of project files in JSON and YAML formats, and for other information on [using project files](https://www.dita-ot.org/dev/topics/using-project-files.html).
