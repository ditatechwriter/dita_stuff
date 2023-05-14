---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Configuring the dita-ot-action

There are several ways to configure the *dita-ot-action* GitHub Action. The [DITA-OT website](https://www.dita-ot.org/dev/topics/using-github-actions.html) has detailed instructions and the `docsrc/samples/github-actions` folder (within the DITA-OT install folder) has several sample workflow files, and on the [DITA-OT docs GitHub repository](https://github.com/dita-ot/docs/tree/develop/samples/github-actions).

The use of [Project files](automating-builds.md#project-files) is the simplest course of action when building using the *dita-ot-action* because a lot of the configuration is in the project file itself and doesn't have to be added to the workflow YAML file.

## Installing community plugins

There are a limited number of basic plugins included with the DITA-OT. However, other community developed plugins are available in the [DITA-OT plugin registry](https://www.dita-ot.org/plugins). These can be installed using the `dita install` command as in the following excerpt:

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
          **install: \|
            dita install fox.jason.extend.css
            dita install net.infotexture.dita-bootstrap
            dita install fox.jason.prismjs**
          build:  |
            dita --project=myproject.xml  
...
```

## Installing custom plugins

Most companies that use DITA develop custom DITA-OT plugins at some point. There are two ways to add a custom plugin: via a [custom registry](https://www.dita-ot.org/dev/topics/plugins-registry.html#plugin-registry__adding-custom-registries) or, the old-fashioned way, via a plugin ZIP archive. The former method involves forking the DITA-OT plugin registry, uploading your plugins to it, and creating a JSON registry file for each plugin. This is only worthwhile in my opinion if you have a lot of custom plugins, and a lot of folks installing and uninstalling them on a regular basis. As far as GitHub actions are concerned, simply installing a plugin as a ZIP archive from another repository is a lot easier.

To do this, upload you custom plugin files unzipped to a dedicated branch in a GitHub repository. GitHub zips the content in the background and you can install the ZIP archive by passing it as a URL to the `dita install` command.

The following example installs a plugin from a user (myCompany) repository (DITA-plugins) custom\_pdf branch.

```yaml
...

jobs:
  build-dita:
    name: Build DITA
    runs-on: ubuntu-latest
    steps:
      - name: Git checkout
        uses: actions/checkout@v2
      - name: Build Custom PDF
        id: DITA-build
        uses: dita-ot/dita-build-action@master
        with:
          **install: \|
            dita install https://github.com/myCompany/DITA-plugins/archive/custom\_pdf.zip**
          build:  |
            dita --project=myproject.xml  
...
```

**Parent topic:**[DITA CI/CD with GitHub Actions](GA-build.md)

