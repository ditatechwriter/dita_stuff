# A sample DITA docs-as-code CI/CD pipeline

What follows is an outline of doc-as-code publication toolchain. This is the toolchain used here to produce this website. Different tools could of course be substituted at various points in the pipeline.

## GitHub

I've used GitHub for versioning, writer collaboration, and for technical reviews. Using standard Git workflows makes easy to version documents, and along with Git's pull\_request feature, allows multiple writers to work on the same document without getting in one another's way.

GitHub's built-in editor for Markdown, along with pull requests makes editing of MDITA docs very easy for developers.

## GitHub Actions

This relatively new feature in GitHub provides a lot of powerful and easy-to-use CI/CD functionality. Writing GitHub Action workflows is relatively straightforward and there are many open source GitHub Actions available. The linting, build and deployment actions used on this site are composed from third-party GitHub Actions chained together

## DITA Open Toolkit

The DITA Open Toolkit performs all the DITA magic of filtering, conreffing, and key addressing while converting the MDITA content into standard GitHub-flavored markdown.

Transforming the content into HTML5 or PDF is also possible but both require significant customization to produce good-looking content.

Rather than try to customize a plugin to produce a documentation website \(which is what you need to do with standard DITA\), it is easier and preferable to produce simple markdown and configure your static site generator.

## Docsify

Docisfy is my static site generator of choice. It is configure and provides lots of useful pre-built features to make a great documentation website.

I also show how to create output suitable for two other static site generators commonly used for documentation: Gitbook and MkDocs.

## Netlify

Netlify is host I use for this site. It provide webhooks to pull built content from GitHub and display it on the web. I also use it for domain management and proxying.

## Slack

I use Slack, via GitHub Actions, to notify me about the success or failure of linting, builds and deployments. I also have itset up to let me know when someone raises a PR against my content in one of my repositories.

