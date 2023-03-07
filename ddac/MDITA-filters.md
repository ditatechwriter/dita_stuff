---
id: MDITA-filters
---

# Using filters with MDITA

MDITA filters are used to apply build conditions. In other words, to exclude certain text elements that are not relevant, for example, to certain readers, or for certain software versions, or releases. By applying different filters to an MDITA document you can produce different versions of the document to suit different purposes.

To incorporate text that can be filtered out at build time, MDITA topics must include HDITA tags that use the *props* attribute. Note in the example below that the entire unordered list must be in HTML markup not simply the list items that are to be filtered.

```xml
## Supported Operating Systems

The following operating systems are supported by the [product_name] companion app:

<ul>
  <li props="mac">Mac</li>
  <li>Windows</li>
  <li props="linux">Linux</li>
  <li>BSD</li>
</ul>
```

You use a special *ditaval* filter file is used to filter content. To filter out the first list item, the ditaval file used by the build instruction is:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<val>
    <prop action="exclude" att="props" val="mac"/>
</val>
```

The *props* attribute can also added at the map level to filter out whole files from a build:

```xml
<topicref href="somefile.md" format="markdown" props="mac"/>
```
<p><note type="caution">If the <em>props</em> attribute is added to a &#60;topicref&#62; element that has child topics, the children will also be filtered out.</note></p>


