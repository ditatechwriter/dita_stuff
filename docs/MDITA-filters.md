---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Using filters with MDITA

You use MDITA filters to apply build conditions. In other words, to exclude certain text elements that aren't relevant, for example, to certain readers, or for certain software versions, or releases. By applying different filters to an MDITA document you can produce different versions of the document to suit different purposes.

To incorporate text that you want to filter out at build time, MDITA topics must include HDITA tags that use the *props* attribute. Note in the example below that the entire unordered list must be in HTML markup not simply the list items you intend to filter.

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

You use a special *ditaval* filter file to filter content. To filter out the first list item, the ditaval file used by the build instruction is:

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

!!! warning

    If the *props* attribute is added to a `<topicref>` element that has child topics, the children will also be filtered out.
