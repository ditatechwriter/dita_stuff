---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Pagefind Search Library

[Pagefind](https://pagefind.app/) is a JavaScript static search library than be easily integrated into the DITA-Bootstrap plugin. As it's written in Javascript, it runs the searches in the browser, and consequently is very fast.

To install Pagefind you will need to have `npm` installed first. For instructions on how to install that, see [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).

After you have installed `npm` (if you don't have it already), getting search fully up-and-running on your site involves the following steps:

1.  From the command line, run an ordinary build of your document using the DITA-Bootstrap plugin.
2.  Still in the command line, navigate to the output folder containing the HTML files and run the `pagefind` command:

    ```node
    npx pagefind --source .
    ```

    This creates a `_pagefind` folder within the output folder that stores the search index for the document.

3.  Make a copy of the `[DITA-OT Install Folder]/libexec/plugins/net.infotexture.dita-bootstrap/xsl/html5-bootstrap.xsl`file (rename it `html5-bootstrap.orig` or similar). This is so you can restore the original file if need be.
4.  The [Pagefind UI](https://pagefind.app/docs/ui/) page provides a code snippet you can insert into the `html5-bootstrap.xsl` file (or other files like `includes/bs-navbar-default.hdr.xml`). Insert it immediately before the content `<div>` in the `html5-bootstrap.xsl` file to display the search bar beneath the site header menu.

    ```xml
    ...
    
    <!--   Pagefind search snippet goes here   -->
          
          <div class="container-fluid  py-4" id="search-wrapper" style="background-color: #cfe2ff;">
          <link href="/_pagefind/pagefind-ui.css" rel="stylesheet"/>
          <script src="/_pagefind/pagefind-ui.js" type="text/javascript"></script>
          
            <div id="search" class="container-lg" style="max-width: 25%;"></div>
          <script>
            window.addEventListener('DOMContentLoaded', (event) => {
            new PagefindUI({ element: "#search" });
            });
          </script>
          </div>
          
    <!--   End of pagefind snippet   -->
          
          <div class="bs-container" id="content">
    
    ...
    ```

    In the example above, I have wrapped the Pagefind code snippet in a `<div>` and added some styling to the wrapper and the search `<div>`.

5.  Navigate to the folder that holds your document ditamap, and run another build.
6.  Move the output folder to a web server, and open a page to test the new search functionality.

    !!! Tip

        If you have Python 3 installed, you can spin up a local web server in the document output folder using a command similar to the following:

        ```py
        python3 -m http.server 8000
        ```

        Your content will be available at `http://localhost:8000/<mypage.html>`.
