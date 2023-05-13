---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Organizing topics with maps

A collection of MDITA topics is organized using a ditamap. Ditamaps are XML files that function like a table of contents to determine the order and the heading level of a topic within a document. Ditamaps are written in XML.

Although the Lw-DITA specification does allow you to create ditamaps in MDITA, it is more practical to use XDITA or standard DITA for the following reasons:

-   Ditamaps are not something that you need reviewers to update so there is no need to keep them in Markdown.

-   Ditamaps can be outputted in Markdown format as an *index.md* file by the DITA Open Toolkit Markdown transform so there is no requirement to keep the map in Markdown.


As with standard DITA, you can have a root map that can contain content submaps as well as external links or key definition maps that have a processing-only role. As is also standard best practice, you can add "warehouse" topics to hold images and content that will used in multiple locations and accessed via the context reference \(or "conref"\) mechanism.

A sample ditamap:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "map.dtd">
<map id="intro-to-MDITA">    
    <title>DITA-as-code<title>
    <topicref format="markdown" href="Dita-dac.md" keys="ddac"/>
    <topicref format="markdown" href="DITA4dac.md" keys="d4dac">
        <topicref format="markdown" href="write-review-MDITA.md" keys="write-MDITA"/>
        <topicref format="markdown" href="Ditamaps4dac.md" keys="MDITA-maps"/>
        <topicref format="markdown" href="MDITA-keys.md" keys="MDITA-keys"/>
        <topicref format="markdown" href="MDITA-conrefs.md" keys="MDITA-conrefs"/>
        <topicref format="markdown" href="MDITA-filters.md" keys="MDITA-filters"/>
        <topicref format="markdown" href="publish-MDITA.md" keys="publish-MDITA"/>
    </topicref>
    <mapref href="externallinks.ditamap" keys="extlinksmap" processing-role="resource-only"/>
    <mapref href="keydefs.ditamap" keys="keydefsmap" processing-role="resource-only"/>
    <topicref format="markdown" href="conrefs.md" keys="conrefs" processing-role="resource-only"/>
    <topicref format="mardown" href="images.md" keys="images" processing-role="resource-only"/>   
</map>
```

## Ditamap tags

The first tag provides information the version of XML used. The second tag references the Document Type Definition \(DTD\) for the map. This DTD defines what XML tags can appear in a map and in what order. These first 2 tags appears in all ditamaps of this type and, luckily, we don't ever really need to concern ourselves with them.

The other tags, though are of interest to us:

-   **map** - The <map\> tag contains all the other tags and always requires an *id* attribute as a unique identifier for the map.

-   **title** - The <title\> tag gives the document as a whole its title.

-   **topicref** - <topicref\> tags are used to refer to topics. <topicref\> tags can contain other <topicref\> tags. The following attribute can be used with the <topicref\> tag:

    -   *href* - The *href* attribute contains the path to the MDITA topic.This attribute is mandatory.

    -   *format* - This attribute defines the format of the file referenced. For our purposes, this will usually have a value of *markdown*. This attribute is mandatory.

    -   *keys* - The *keys* attribute contains a value that functions as an alternative name when refering to the topic. Keys in general are discussed at greater length in [Using keys](MDITA-keys.md), but bascially using a key allows you to change the name or location of a topic \(in the *href* attribute\) without breaking any links or references to it elsewhere in the document.

    -   *processing-role* - The *processing-role* attribute is only used for certain special topics \(and maps\) that usually containing content that is reused elsewhere in the document. For that reason you do not want that topic to appear *as-is* in the document. The *processing-role* attribute usually has a value of *resource-only*.

-   **mapref** - You can also references other maps within your map. The <mapref\> is used to reference whole maps. It uses the same attributes as the <topicref\> tag, but the *format* attribute is not mandatory as the format will always be *ditamap*.


There are quite a few other tags and attributes that can be used in a map \(see [Using keys](MDITA-keys.md) for some more of those\). The 4 tags listed above are the ones that are used on a day-to-day basis when you work with maps.

## Types of map

The basic type of map shown here is usually called a *root* map. It is used to define the structure of the document. However, there are other types of map. To make full use of MDITA's content reuse functionality, you can also employ key defintion maps and external link maps. These maps are usually sub-maps within the root maps and are used to define variables and store external links, respectively. Again see [Using keys](MDITA-keys.md) for more information on key definition and external links maps.

**Parent topic:**[Working with MDITA](mdita.md)

