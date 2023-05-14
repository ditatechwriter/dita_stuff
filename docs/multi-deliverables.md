---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Building multiple deliverables in GitHub

The beauty of using [Project files](automating-builds.md#project-files) in your GitHub builds is that a lot of the build information is already contained in the project file itself. You can use one `dita` command to build not just multiple documents from different ditamaps but also different output types for the same document, provided that:

1.  Your GitHub workflow file downloads all the required plugins for the output types you want to build.

2.  Your project file includes all the transtype information you need to define the output formats.


The following project file defines three deliverables for the *Grunt Master 3000 Guide*: a HTML5 website, a PDF version built with a custom PDF plugin, and another PDF version that uses the basic PDF2 plugin and which requires a theme file (for more information, see [PDF2 theme files](pdf2_themes.md)). Because of conflicting ditaval filter files, there are 2 different contexts for the *Grunt Master 3000 Guide* - one for each output format.

```language-xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://www.dita-ot.org/project">

<--! Grunt Master 3000 Guide HTML 5 deliverable -->

  <context name="Grunt Master 3000 Guide" id="html5_ug_gruntmaster3000">
    <input href="ug_gruntmaster3000.ditamap"/>
    <profile>
      <ditaval href="exclude_pdfonly.ditaval"/>
    </profile>
  </context>
  
  <deliverable name="Grunt Master 3000 Guide" id="ug_gruntmaster3000_html5">
    <context idref="html5_ug_gruntmaster3000"/>
    <output href="./html5-output"/>
    <publication transtype="html5">
      <param name="args.css" href="../css/custom.css"/>
      <param name="args.copycss" value="yes"/>
    </publication>
  </deliverable>

<--! Grunt Master 3000 Guide PDF deliverables -->

  <context name="Grunt Master 3000 Guide" id="pdf_ug_gruntmaster3000">
    <input href="ug_gruntmaster3000.ditamap"/>
    <profile>
      <ditaval href="exclude_html5only.ditaval"/>
    </profile>
  </context>

 <deliverable name="Grunt Master 3000 Guide" id="ug_gruntmaster3000_custpdf">
    <context idref="pdf_ug_gruntmaster3000"/>
    <output href="./pdf-output"/>
    <publication transtype="custom_pdf">
      <param name="args.chapter.layout" href="BASIC"/>
      <param name="outputFile.base" value="Grunt Master 3000 Guide"/>
    </publication>
  </deliverable>

 <deliverable name="Grunt Master 3000 Guide" id="ug_gruntmaster3000_pdf">
    <context idref="pdf_ug_gruntmaster3000"/>
    <output href="./pdf-output"/>
    <publication transtype="pdf2">
      <param name="args.chapter.layout" href="BASIC"/>
      <param name="outputFile.base" value="Grunt Master 3000 Guide"/>
    </publication>
  </deliverable>
  
</project>
```

The GitHub Actions workflow file build section required to produce all three versions looks something like this:

```yaml
...

jobs:
  build-dita:
    name: Build DITA
    runs-on: ubuntu-latest
    steps:
      - name: Git checkout
        uses: actions/checkout@v2
      - name: Build HTML5
        id: DITA-build
        uses: dita-ot/dita-build-action@master
        with:
          install: |
            dita install fox.jason.extend.css
            dita install net.infotexture.dita-bootstrap
            dita install fox.jason.prismjs
            dita install https://github.com/myCompany/DITA-plugins/archive/custom_pdf.zip
          build:  |
            dita --project=gm_3000.xml  --theme=mytheme.xml
...
```

!!! note

    The  HTML5 build uses the first 3 plugins. The last for the custom PDF build. There is no need to install the PDF2 plugin as it's bundled with each DITA Open Toolkit release. The theme file is required for the PDF2 build. If not included, the output will revert to the default PDF2 styles. The theme file parameter is ignored by the other deliverable builds.
