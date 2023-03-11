# Automating DITA builds

Back in the day I used to automate my DITA-OT builds by writing shell scripts that chained DITA build commands along with their various build parameters one after the other.

Then *.properties* files came along and it became a lot easier to do builds because you could put most of a document's build parameters in a single file and call it from the DITA build command, as in the example below:

```language-bourne
dita -i my_map.ditamap -o out/pdfs --format=pdf2 --filter=my_filter.ditaval --propertyfile=my_build.properties
```

This made for more concise shell scripts because the build parameters for most documents were the same and you could call the same *.properties* file for most of your build commands. However, if you required different parameters for a document, you needed a different *.properties* file. Each *.properties* file could only list the parameters for one output format, and you still needed to use a different DITA build command in your script for every document you wanted to build.

## A New Dawn {.section}

Finally with DITA-OT release 3.4 came project files. Project files allow you to put all the build parameters (including input files, output folders, output formats, and filters) all in the same file for multiple documents. You can even define multiple outputs with different parameters for the same document.

Your DITA build command now looks something like this:

```language-bourne
dita --project=myproject.xml -v
```
<p><note>The <i>-v</i> switch simply tells the DITA Open Toolkit to use verbose mode and run the log file in the command prompt window.</note></p>

The above example uses a project file in XML format. You can also write them in YAML and JSON.