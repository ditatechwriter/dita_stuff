---
id: MDITA-filters
author: Michael
---

# Using filters with MDITA

To incorporate text that can be filtered out at build time, MDITA topics must incorporate HDITA tags that use the 'data-props' attribute. Note in the example below that the entire unordered list must be in HDITA markup not simply the list items that are to be filtered.
```
## Supported Operating Systems

The following operating systems are supported by the [product_name] companion app:

- Windows
- Linux
- BSD
```
To filter out the first list item, the ditaval filter file used by the build instruction is:
```
<?xml version="1.0" encoding="UTF-8"?>
<val>
    <prop action="exclude" att="data-props" val="mac"/>
</val>
```


