# Using MDITA keys for text variables

MDITA keys allow you to create text variables. This is functionality that is simply not possible with common-or-garden Markdown.

Keys in DITA provide an means of indirect referencing. Keys are defined in a ditamap. They can be added to a root map or - if there are many - contained in a map of their own which is referenced in the root map.

The recommended format for creating a key definition in an XDITA map is:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD LIGHTWEIGHT DITA Map//EN" "map.dtd">
<map id="Keydefs">    
    <topicmeta>
        <navtitle>Key Definitions</navtitle>
    </topicmeta>

    <keydef keys="product_name">
      <topicmeta>
        <linktext><ph>Grunt Master 6000</ph></linktext>
      </topicmeta>
    </keydef>
    
</map>    
```

Within an MDITA topic the key is referenced by putting it within square brackets:

```

The [product_name] represents a leap forward in home exercise technology! 

```

Once built, *\[product\_name\]* will be replaced by "Grunt Master 6000".

