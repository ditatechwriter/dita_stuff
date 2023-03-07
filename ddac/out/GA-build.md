# Building output with GitHub Actions

The following code is a simple GitHub Actions workflow builds GitHub-flavored Markdown files from my MDITA content and deposits them in a branch called *docsify*. And this all happens every time I push content to the branch where my MDITA content is stored.

```
jobs:
  build-dita:
    name: Build DITA
    runs-on: ubuntu-latest
    steps:
      - name: Git checkout
        uses: actions/checkout@v2
      - name: Build GFM
        id: DITA-build
        uses: jason-fox/dita-build-action@master
          build: dita -i mymap.ditamap -o out -f markdown_github -v --propertyfile=myprops.properties
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
          BRANCH: docsify # The branch the action should deploy to.
          FOLDER: out # The folder the action should deploy.
          TARGET-FOLDER: docs          
```

The first job, `Git checkout`, is GitHub-provided action that checks out the branch the *MDITA* branch.

The real work is done by the next job, `Build GFM`. It uses a Github Action created by [Jason Fox](https://github.com/jason-fox/dita-build-action) which downloads the latest version of the DITA Open Toolkit and runs the build instruction.

The third job, `Upload DITA`, uploads the files outputted by the build to a folder called `out`.

The last job, `Deploy` uses a GitHub action written by [James Ives](https://github.com/JamesIves/github-pages-deploy-action) originally meant to deploy content to a GitHub Pages branch but used here to move to the `docs` folder in the `docsify` branch.

