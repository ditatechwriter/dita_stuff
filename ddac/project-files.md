---
id: project-files
author: Michael
---

# Using DITA project files

A DITA project file is an XML file containing build parameters for one or more documents that you can pass to the *dita* build command.

The following is a sample project file:

```xml
<project xmlns="https://www.dita-ot.org/project">
  <context name="Grunt Master 6000 Guide" id="ug_gruntmaster6000">
    <input href="ug_gruntmaster6000.ditamap"/>
    <profile>
      <ditaval href="filter.ditaval"/>
    </profile>
  </context>
  
  <deliverable name="Grunt Master 6000 Guide" id="ug_gruntmaster6000_html5">
    <context idref="ug_gruntmaster6000"/>
    <output href="out"/>
    <publication transtype="html5">
      <param name="args.css" href="../css/custom.css"/>
      <param name="args.copycss" value="yes"/>
    </publication>
  </deliverable>
</project>
```
DITA project files can be divided into 2 parts: context and deliverable. The context section provides an unique ID for the build, the path to the source ditamap, and the path to any ditaval files if used. The deliverable section contains:

* the deliverable name
* a unique id for this build type
* the path to the build output folder
* any build parameters

The project file is passed to the *dita* build command thus:

```bourne
dita --project=myproject.xml -v
```
The *-v* switch simply tells the DITA Open Toolkit to use verbose mode and run the log file in the command prompt window as the build runs.