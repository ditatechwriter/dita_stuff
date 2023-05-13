---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Using MkDocs

[MkDocs](https://www.mkdocs.org/) is Python-based static site generator that converts Markdown to HTML and was written with technical documentation site particularly in mind. It also plays quite nicely with the markdown content produced by the DITA Open Toolkit LwDITA plugin.

MkDocs has many impressive built-in features \(like lunr-based search\) and a range of plugins and themes. The steps below explain how to install and configure MkDocs to publish DITA content.

## Publishing DITA content with MkDocs

Getting good looking HTML-based output from DITA content is not always easy. Oxygen's built-in *Webhelp Responsive* plugin is eminently configurable and produces some lovely looking output but comes with a $3000 US price tag \(at time of writing\) if you want to run it from the command line. Infotexture's open source [*DITA Bootstrap*](https://infotexture.github.io/dita-bootstrap/) plugin is cheaper but requires reasonable knowledge of [*Bootstrap 5*](https://getbootstrap.com/docs/5.0/getting-started/introduction/) to configure it. It's also missing important features like a built-in search \(which can be difficult to implement\).

If you haven't got the cash to do nightly builds of your content using *Webhelp Responsive*, or the time or energy to learn Bootstrap, MkDocs comes with a relatively shallow learning curve and can be used to produce impressive looking documentation in a few minutes.

## Installing Python, MkDocs, and its dependencies

MkDocs is a Python package, so you will need to have both Python and its packet manager `pip` installed.

1.  Check if you have Python3 already installed:

    ```console
    python3 --version
    ```

    If you get *command not found*, you'll need to install it.

    Follow[these instructions for installing Python](https://python.land/installing-python) for your operating system.

2.  `pip` is usually installed automatically when you install Python, you can test that by issuing the following command:

    ```console
    pip3 --version
    ```

    Again, if you get *command not found*, you'll need to install it. Follow[these instructions for installing pip](https://pip.pypa.io/en/stable/installation/) for your operating system.

3.  Once you have Python and pip up and running, you can proceed to install MkDocs:

    ```console
    pip3 install mkdocs
    ```

    This command installs the basic MkDocs page with the default themes and features. Use the `mkdocs --version` command to check that it has installed properly.

    **Tip:** If the `mkdocs --version` does not work, use `python3 -m mkdocs --version`.

    The [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/getting-started/) theme is easily configurable theme for MkDocs that has many plugins and extensions. To install it, use the following command:

    ```console
    pip3 install mkdocs-material
    ```

    Finally, in order to make configuration of your new site's documentation navigation easier, install the [mkdocs-literate-nav](https://github.com/oprypin/mkdocs-literate-nav) plugin for MkDocs:

    ```console
    pip3 install mkdocs-literate-nav
    ```


## Converting DITA to GitHub-flavored Markdown

MkDocs consumes Markdown files so before it can display your DITA content, you need to convert it to GitHub-flavored Markdown using the LwDITA plugin that comes with the DITA-OT 2.4 or later. See the information on the [LwDITA plugin](https://github.com/jelovirt/org.lwdita) GitHub page for the build command to use with your version of the DITA-OT. For the most recent release, use:

```console
dita -i my-map.ditamap -o docs --format=markdown_github
```

MkDocs automatically looks for content in the `docs` folder but you can call the output folder whatever you want and use the MkDocs configuration file to point to it. You can also add any further build parameters you need to the `dita` command \(or use a [project file](project-file-structure.md)\).

## Configuring MkDocs

MkDocs can be configured mostly by using a single configuration file: `mkdocs.yml`. This file must be added to the folder that contains the `docs` folder.

A basic `mkdocs.yml`:

```yaml
site_name: My site name

theme:
  name: material

plugins:
  - search
  - literate-nav:
      nav_file: index.md
```

-   `site_name` - the name of the site that will appear in the site header
-   `theme` - the name of the MkDocs theme - in this case it is set to the Material for MkDocs theme installed earlier.
-   `plugins` - the lunr search plugin that indexes the site content, and the *mkdocs-literate-nav* plugin that uses the `index.md` file produced by the LwDITA transform to create the site navigation correctly.

You will almost certainly want to configure more features in the `mkdocs.yml` file. It's worth your time to go through the [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/getting-started/) site \(as well as the [Best of MkDocs](https://github.com/mkdocs/best-of-mkdocs) GitHub repository\) to see the range of configuration options available.

## Viewing and building the site

Once you have transformed your DITA content to Markdown, and configured the `mkdocs.yml` file, you are ready to test and build the site using MkDocs.

1.  Open a terminal at the folder containing your `mkdocs.yml` file, and issue the `mkdocs serve` command. This MkDocs built-in HTTP service that serves your content at `127.0.0.1:8000`. Open a browser at that address to your converted content in MkDocs.
2.  You can make changes to the `mkdocs.yml` file \(and the markdown content - although it is recommended you do that in DITA and rebuild\) and the MkDocs server will display them immediately.
3.  When you are finished, use `Ctrl+c` to stop the MkDocs HTTP service, and then issue the `mkdocs build` command. This command builds the site to a `site` folder. The site folder and/or its contents can then be uploaded to a web server.

