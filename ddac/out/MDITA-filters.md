# Using filters with MDITA

MDITA filters are used to apply build conditions. In other words, to exclude certain text elements that are not relevant, for example, to certain readers, or for certain software versions, or releases. By applying different filters to an MDITA document you can produce different versions of the document to suit different purposes.

To incorporate text that can be filtered out at build time, MDITA topics must include HDITA tags that use the *props* attribute. Note in the example below that the entire unordered list must be in HDITA markup not simply the list items that are to be filtered.

```
## Supported Operating Systems

The following operating systems are supported by the [product_name] companion app:

<ul>
  <li props="mac">Mac</li>
  <li>Windows</li>
  <li props="linux">Linux</li>
  <li>BSD</li>
</ul>
```

To filter out the first list item, the ditaval filter file used by the build instruction is:

```
<?xml version="1.0" encoding="UTF-8"?>
<val>
    <prop action="exclude" att="props" val="mac"/>
</val>
```

The *props* attribute can also used at the map level to filter out whole files from a build:

```
<topicref href="somefile.md" format="markdown" props="mac"/>
```

