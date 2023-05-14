---
author: Michael McLoughlin
publisherinformation: V1.0
---

# DITA CI/CD with GitHub Actions

GitHub Actions are a quick and easy way to automate build outputs form DITA content stored in a GitHub repository.

The following code is a simple GitHub Actions workflow that builds HTML5 files from DITA content and deposits them in a branch called *published*. This build is kicked off on push or on pull requests to a the `main` branch. it's also possible to configure a cron job to run the build at a specific time, or to run the build manually.

```yaml
name: site-build

# Controls when the action will run. 
on:

  # Triggers the workflow on push events but only for the main branch
  push:
    branches: [ main ]

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
          build:  |
            dita --project=myproject.xml          
      - name: Upload DITA
        id: upload
        uses: actions/upload-artifact@v2
        with:
          name: dita-artifact
          path: ‘out’
      - name: Deploy
        id: deploy
        uses: JamesIves/github-pages-deploy-action@3.7.1
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          BRANCH: published # The branch the action should deploy to.
          FOLDER: out # The folder the action should deploy.
          TARGET-FOLDER: docs          
```

The `jobs` section of the workflow file spins up an Ubuntu Linux instance and then runs a series of steps:

1.  The first step, `Git checkout`, is a GitHub-provided action that checks out the current branch.

2.  The real work is done by the next step, `Build HTML5`. It uses the `dita-build-action` GitHub Action created by [Jason Fox](https://github.com/jason-fox/dita-build-action) which downloads the latest version of the DITA Open Toolkit, installs 3 required plugins from the DITA-OT plugin registry, and runs the build instruction using the `myproject.xml` project file stored in the branch. The `myproject.xml` project file contains all the information on the source ditamap, output transtype, output folder, filter files, and any build parameters. For more information on configuring project files, see .

3.  The third step, `Upload DITA`, uploads the files outputted by the build to a folder called `out`.

4.  The last step, Deploy uses a GitHub action written by [James Ives](https://github.com/JamesIves/github-pages-deploy-action) originally meant to deploy content to a GitHub Pages branch but used here to move the content of the `out` folder on the `main` branch to the `docs` folder in the `published` branch. From there web hooks could be employed to upload the content to a service like Netlify.


## Manual builds

The example above runs when you push content to the `main` branch. When you are testing builds, it's easier to run builds manually. Adding the `workflow_dispatch` event trigger to your workflow file allows you to build manually by clicking **Run workflow** on the **Actions** tab in the GitHub UI.

```yaml
name: site-build

on:
  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

...
```

## Timed builds with cron

In a mature CI/CD docs environment, documentation can be built and deployed on a regular, perhaps daily, basis. Workflows can integrate cron jobs that kick off the builds on specified days and times. The example below runs the build every weekday night at 2am:

```yaml
name: site-build

on:
  schedule:
    # Runs "at 02:00 every Mon-Fri"
    - cron: '* 2 * * 1-5'

...
```
!!! tip

    For help with cron notation, [https://crontab.guru/](https://crontab.guru/) is useful resource.
