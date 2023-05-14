# Organizing topics with maps

You organize a collection of MDITA topics using a ditamap. Ditamaps are XML files that function like a table of contents to decide the order and the heading level of a topic within a document. Ditamaps are XML files.

Although the Lw-DITA specification includes ditamaps written in MDITA, it's more practical to use XDITA or standard DITA for the following reasons:

-   Ditamaps aren't something that you need reviewers to update so there is no need to keep them in Markdown.

-   You can output ditamaps in Markdown format as an *index.md* file by the DITA Open Toolkit Markdown transform so there is no requirement to keep the map in Markdown.

As with standard DITA, you can have a root map that can contain content submaps as well as external links or key definition maps that have a processing-only role. As is also standard best practice, you can add *warehouse* topics to hold images and content that used in multiple locations and accessed using the context reference (or *conref*) mechanism.

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

The first tag provides information the version of XML used. The second tag references the Document Type Definition (DTD) for the map. This DTD defines what XML tags can appear in a map and in what order. These first 2 tags appears in all ditamaps of this type.

The other tags, though are of interest to us:

-   `map` - The `<map>` tag wraps all the other tags and always requires an *id* attribute as a unique identifier for the map.

-   `title` - The `<title>` tag gives the document as a whole its title.

-   `topicref` - You use `<topicref>` tags to reference topics. `<topicref>` tags can contain other `<topicref>` tags. You can use the following attributes with the `<topicref>` tag:

    -   *href* - The *href* attribute stores the path to the MDITA topic.This attribute is mandatory.

    -   *format* - This attribute defines the format of the file referenced. For our purposes, this usually has a value of *markdown*. This attribute is mandatory.

    -   *keys* - The *keys* attribute stores a value that functions as an alternative name when referencing to the topic. For a more in-depth discussion of keys, see in [Using keys](MDITA-keys.md). Using a key allows you to change the name or location of a topic (in the *href* attribute) without breaking any links or references to it elsewhere in the document.

    -   *processing-role* - The *processing-role* attribute is only used for certain special topics (and maps) that usually containing content that you want to reuse elsewhere in the document. For that reason you don't want that topic to appear *as-is* in the document. The *processing-role* attribute usually has a value of *resource-only*.

-   `mapref` - You can also reference other maps within your map. Use the `<mapref>` tag to reference whole maps. It uses the same attributes as the `<topicref>` tag, but the *format* attribute isn't mandatory as the format is always *ditamap*.


There are quite a few other tags and attributes that you can use in a map (see [Using keys](MDITA-keys.md) for some more of those). The 4 tags listed above are the ones that you can use on a day-to-day basis when you work with maps.

## Types of map

The basic type of map shown here is usually called a *root* map. You use it to define the structure of the document. However, there are other types of map. To make full use of MDITA's content reuse functionality, you can also use key definition maps and external link maps. These maps are usually sub-maps within the root maps and you use them to define variables and store external links, respectively. Again see [Using keys](MDITA-keys.md) for more information on key definition and external links maps.
