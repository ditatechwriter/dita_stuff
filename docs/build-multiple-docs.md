---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Building multiple documents

The example shown in [DITA-OT project file structure](project-file-structure.md) was for one document deliverable in one output format. But with project files you can include many different deliverables and even several different deliverables for the same ditamap. See the following sample project file, `gm_deliverables.xml`:

```language-xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://www.dita-ot.org/project">

<--! Grunt Master 6000 Guide deliverables -->

<deliverable name="Grunt Master 6000 Guide" id="ug_gruntmaster6000_html5"> 
    <context name="Grunt Master 6000 Guide" id="ug_gruntmaster6000">
        <input href="ug_gruntmaster6000.ditamap"/>
        <profile>
            <ditaval href="GM6000.ditaval"/>
        </profile>
    </context>
    <output href="./html5-output"/>
    <publication transtype="html5">
        <param name="args.css" href="../css/custom.css"/>
        <param name="args.copycss" value="yes"/>
    </publication>
  </deliverable>

<--! Grunt Master 3000 Guide deliverables -->

  <context name="Grunt Master 3000 Guide" id="ug_gruntmaster3000">
    <input href="ug_gruntmaster3000.ditamap"/>
    <profile>
      <ditaval href="GM3000.ditaval"/>
    </profile>
  </context>
  
  <deliverable name="Grunt Master 3000 Guide" id="ug_gruntmaster3000_html5">
    <context idref="ug_gruntmaster3000"/>
    <output href="./html5-output"/>
    <publication transtype="html5">
      <param name="args.css" href="../css/custom.css"/>
      <param name="args.copycss" value="yes"/>
    </publication>
  </deliverable>

<deliverable name="Grunt Master 3000 Guide" id="ug_gruntmaster3000_pdf">
    <context idref="ug_gruntmaster3000"/>
    <output href="./pdf-output"/>
    <publication transtype="pdf2">
      <param name="args.chapter.layout" href="BASIC"/>
      <param name="outputFile.base" value="Grunt Master 3000 Guide"/>
    </publication>
  </deliverable>
  
</project>
```

The above example builds 3 deliverables from 2 source ditamaps. All 3 deliverables can be built with just one command:

```language-bourne
dita --project=gm_deliverables.xml
```

The first part builds HTML5 output for the *Grunt Master 6000 Guide*.

The second part builds HTML5 and PDF outputs for the *Grunt Master 3000 Guide* using two different filter files.

Notice in this section of the project file that the `context` is independent of the `deliverable` sections, and that there are two `deliverable` sections that both have their own <context\> elements which reference the same `context` ID via the `idref` attribute.

**Parent topic:**[Automating DITA builds](automating-builds.md)

