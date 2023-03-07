---
id: SSG-setup
---

# Setting up Docsify as your static site generator 

Docsify is the most easily configurable. Based on JavaScript, it has one main configuration file, good documentation and lots of community plugins.

Documentation on configuring is available on the [Docsify website](https://docsify.js.org/#/).

To set it up to display the content built by the GitHub actions:

1. Create an empty branch in the same repository as your MDITA source. I ahve acalled mine 'docsify'. 
1. Add a new folder called `docs`,
1. Within the `docs` folder add the index.html file as outlined in the [Docsify documentation](https://docsify.js.org/#/quickstart?id=manual-initialization).
1. Edit the index.html file to use index.md (which the markdown generates from your root ditamap) as a sidebar navigation file:

          <!-- index.html -->
          <!DOCTYPE html>
          <html>
          <head>
           <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
           <meta name="viewport" content="width=device-width,initial-scale=1">
           <meta charset="UTF-8">
           <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/themes/vue.css" />
          </head>
          <body>
           <div id="app"></div>
            <script>
             window.$docsify = {
              // load from index.md
              loadSidebar: 'index.md'
              };
        </script>
            <script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
            <script src="//cdn.jsdelivr.net/npm/docsify@4"></script>
            </body>
            </html>
1. Run run a build.
1. When the build completes check that the content has been deployed in the `docs` folder on the branch where you want it to be outputted. Open a terminal at the `docs` folder and (if you have Python installed) type:

        python -m SimpleHTTPServer 3000
        
1. Open your browser at `localhost:3000` to see your site.

To change themes and add more site functionality, see the [Docsify documentation](https://docsify.js.org/#/).


