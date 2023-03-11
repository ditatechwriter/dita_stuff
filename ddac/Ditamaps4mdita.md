# Creating Ditamaps for MDITA topics

Although the Lw-DITA specification does allow you to create ditamaps in MDITA, it is more practical to use XDITA or standard DITA for the following reasons: 
- Ditamaps are not something that you need reviewers to update so there is no need to keep them in Markdown.
- Ditamaps can be outputted in Markdown format as an *index.md* file by the DITA Open Toolkit Markdown transform so there is no requirement to keep the map in Markdown.

As with standard DITA, you can have a root map that can contain content submaps as well as external links or key definition maps that have a processing-only role. As is also standard best practice, you can add "warehouse" topics to hold images and content that will used in multiple locations and accessed via the context reference (or "conref") mechanism.

A sample DITA map:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "map.dtd">
<map id="dita-as-code">    
    <topicmeta>
        <navtitle>DITA as code</navtitle>
    </topicmeta>
    <topicref format="markdown" href="dita-as-code.md" keys="dac"/>
    <topicref format="markdown" href="DITA4dac.md" keys="mdita">
        <topicref format="markdown" href="write-review-MDITA.md" keys="write-MDITA"/>
        <topicref format="markdown" href="Ditamaps4dac.md" keys="MDITA-maps"/>
        <topicref format="markdown" href="MDITA-keys.md" keys="MDITA-keys"/>
        <topicref format="markdown" href="MDITA-conrefs.md" keys="MDITA-conrefs"/>
        <topicref format="markdown" href="MDITA-filters.md" keys="MDITA-filters"/>
        <topicref format="markdown" href="get_out.md" keys="get-out"/>
    </topicref>
    <topicref format="ditamap" href="externallinks.ditamap" keys="extlinksmap" processing-role="resource-only"/>
    <topicref format="ditamap" href="keydefs.ditamap" keys="keydefsmap" processing-role="resource-only"/>
    <topicref format="markdown" href="conrefs.md" keys="conrefs" processing-role="resource-only"/> 
</map>
```

