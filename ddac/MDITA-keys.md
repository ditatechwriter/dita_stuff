---
id: MDITA-keys
author: Michael
---

# Using keys

The use of keys in root maps is not mandatory but it is best practice. Keys can play an important role in:

* Managing internal links so that path and names of topics in a map can be changed without breaking cross references.
* Managing external links so that links to external resources that are used more than once in a document can be more easily updated if the URL changes.
* Creating text variables for things like company and product names so that these can be easily and safely updated everywhere in the document if they change, without resorting to risky global find and replace commands, or painful manual updating.

## Using keys for internal links {.section}

By adding a *keys* attribute value to a topic's \<topicref> in your map, you can refer to the key value within square brackets in any topic and the output generates a link to the topic with the topic title. For example, you link to this topic in the following way:

```markdown
For more information, see [using-maps].
```

The key *using-maps* is the value of the *keys* attribute for the topic reference for this topic in the current document ditamap.

By using this method, you can change the name or the path to the markdown file referenced in the *href* attribute in your \<topicref> without breaking any references to the file in the document itself.

## Using keys for external links {.section}

As you have no control over the URL of an external link, and you might use the same external link multiple times in a document, it is best practice to keep your external links in their own ditamap and refer to them using keys (just as you would for internal links). Here is a sample external links ditamap:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "map.dtd">
<map id="extlinks">    
    <title>External links</title>
    <topicref format="html" href="https://www.commonmark.org" keys="commonmark" scope="external" >
        <topicmeta>
            <navtitle>CommonMark specification</navtitle>
        </topicmeta>
    </topicref>
    <topicref format="html" href="https://books.google.co.uk/books/about/Docs_Like_Code.html)" keys="docs-like-code" scope="external" > 
        <topicmeta>
            <navtitle>Docs like code</navtitle>
        </topicmeta>
    </topicref>
    <topicref format="html" href="https://www.dita-ot.org/dev/topics/markdown-dita-syntax-reference.html" keys="MDITA-syntax-ref" scope="external">
        <topicmeta>
            <navtitle>MDITA syntax reference</navtitle>
        </topicmeta>
    </topicref>    
</map>

```
A few things of note:

* The *format* attribute uses *html* as a value because the reference is to a web page.
* Unlike internal links, you have to explicitly define the link text for external links via the \<topicmeta> and \<navtitle> tags. If you omit the \<topicmeta> and \<navtitle> tags, the link text is replaced by the URL. 
* The \<topicmeta> tag is a container for metadata (in this case title of the web page that appears in the link). 
* The \<navtitle> tag contains the link text that the reader sees when the document is built.

To refer to the last item in the map, use the following:

```markdown
For more information see [MDITA-syntax-ref].
```
When built, the key value is replaced by link entitled "MDITA syntax reference".

Although you can use the standard markdown linking format to place external links in the body of a topic (and initially that might seem easier), the use of external links maps makes updating external URLs much easier.

An external links map is added as a submap to the root map using a \<mapref> tag with the *processing-role* set to *resource-only* (see [using-maps] for an example).

## Using MDITA keys for text variables {.section}

MDITA keys also allow you to create text variables. This is functionality that is simply not possible with common-or-garden Markdown. 

Keys in DITA provide an means of indirect referencing. Keys are defined in a ditamap. They can be added to a root map or - if there are many - contained in a map of their own which is referenced in the root map.

The recommended format for creating a key definition in an XDITA map is:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "map.dtd">
<map id="Keydefs"> 
    <title>Key Definitions</title>

    <keydef keys="company_name">
      <topicmeta>
        <keywords>
            <keyword>Grunt Industries</keyword>
       </keywords>
      </topicmeta>
    </keydef>
    <keydef keys="product_name">
      <topicmeta>
        <keywords>
            <keyword>Grunt Master 6000</keyword>
       </keywords>
      </topicmeta>
    </keydef>
    
</map>    
```
As you can see, this ditamap does not reference any topics. It is used solely to define keys, and added to the root map using a \<mapref> tag with the *processing-role* set to *resource-only* (see [using-maps] for an example). Here are the tags that are used in the above example in more detail:

* **keydef** - You use this tag to define the key itself by setting a value in the *keys* attribute.
* **topicmeta** - This tag is a container for metadata (in this case the variable string that is used by the key). The \<topicmeta> tag can container a number of tags but for our purposes generally, it only contains those you see in the above example.
* **keywords** - The \<keywords> tag holds the keyword that it is the value of the key. 
* **keyword** - The \<keyword> tag contains the text string itself.

When you are defining keys always use the format of tags shown above.

Within an MDITA topic the key is referenced by putting it within square brackets, for example:

```
The [product_name] represents a leap forward in home exercise technology by [company_name]! 
```
Once built, *\[product_name\]* will be replaced by "Grunt Master 6000", and *\[company_name\]* by "Grunt Industries".

## Referencing keys in HTML5 content

Because some content in MDITA files, such as notes and context references (for more information on context references see [MDITA-conrefs]), is in HTML and not Markdown. The usual methods for referencing keys do not work.

So to add a text variable in HTML text in an MDITA, use *\<span data-keyref="company_name">\</span>* in stead of *\[company_name\]*. For example:

```xml
<p id="disclaimer"><note><span data-keyref="company_name"></span> accepts no liability for any mental illness, blindness, infertility, or death caused by even casual use of the <span data-keyref="product_name"/></span>.</note></p>
```
The next example includes a key reference for an external link defined in the external links dita map:

```xml
<p id="install-step1">First, download the appropriate installer for your operating system from the <span data-keyref="company_name"></span> website <span data-keyref="grunt-downloads"></span> page. </p>
``` 
The example below is for an internal link, referencing a key from the root map:

```xml
<p><note type="tip">For more information on using filters in MDITA documents, see <span data-keyref="MDITA-filters"></span>.</note></p>
```
