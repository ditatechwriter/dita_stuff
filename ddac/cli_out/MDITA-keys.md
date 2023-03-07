---
author: michael.mcloughlin@puppet.com
---

# Using keys with MDITA

Keys in DITA provide an means of indirect referencing. Keys are defined in a ditamap. They can be added to a root map or - if there are many - contained in a map of their own which is referenced in the root map.

The recommended format for creating a key definition in an XDITA map is:

```
<keydef keys="product_name">
  <topicmeta>
    <linktext><ph>Grunt Master 6000</ph></linktext>
  </topicmeta>
</keydef>
```

Within an MDITA topic the key is referenced by putting it within square brackets:

```
The [product_name] represents a leap forward in home exercise technology! 
```

Once built, `[product_name]` will be replaced by "Grunt Master 6000".

**Parent topic:**[Using DITA for docs-as-code](DITA4dac.md)

