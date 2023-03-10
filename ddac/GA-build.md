---
author: Michael
---

# Building output with GitHub Actions

The following code is a simple GitHub Actions workflow builds HTML5 files from MDITA content and deposits them in a branch called *published*. This build is kicked off manually from GitHub but, as you can see in the code snippet below, you can also set it start builds on push or on pull_requests to a certain branch. It is also possible to configure a cron job to run the build at a specific time.

```yaml

name: site-build

# Controls when the action will run. 
on:
  # Triggers the workflow on push or pull request events but only for the main branch
  # push:
  #   branches: [ main ]
  # pull_request:
  #   branches: [ main ]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

jobs:
  build-dita:
    name: Build DITA
    runs-on: ubuntu-latest
    steps:
      - name: Git checkout
        uses: actions/checkout@v2
      - name: Build HTML
        id: DITA-build
        uses: jason-fox/dita-build-action@master
        with:
          install: |        
            dita install https://raw.githubusercontent.com/ditatechwriter/plugins/main/com.custom.html5.zip
          build: 
            dita --project=myproject.xml -v          
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

The first step, *Git checkout*, is GitHub-provided action that checks out the current branch. 

The real work is done by the next step, *Build HTML*. It uses a Github Action created by [jason-fox] which downloads the latest version of the DITA Open Toolkit, installs a custom HTML 5 DITA-OT plugin from another repository and runs the build instruction using the *myproject.xml* project file stored in the branch. For more information configuring project files, see [project-files].

The third step, *Upload DITA*, uploads the files outputted by the build to a folder called *out*.

The last step, *Deploy* uses a GitHub action written by [james-ives] originally meant to deploy content to a GitHub Pages branch but used here to move to the *docs* folder in the *published* branch.