---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Creating a `cc_config.xml` file

The Oxygen `cc_config.xml` file allows you define which DITA elements and attributes are displayed in the Elements and Attributes windows in the Oxygen UI. By configuring element proposals in the `cc_config.xml` file, you can control which elements and attributes your users can add to topics and maps.

**Note:** You are not writing a new DTD here, so a writer could technically manually type in any legal DITA element or attribute and the topic would still validate.

To create a new `cc_config.xml` file, you could copy and edit the default file that lives in the `[Oxygen install folder]/frameworks/dita/resources` folder. Alternatively you can create one from scratch using a conveniently-provided template that you can open from **File**\>**New**\>**Framework templates**\>**Oxygen extensions**\>**Content Completion Configuration**.

The template contains some sample code \(which you can adopt or delete\). The Oxygen online help provides fairly comprehensive information on how work with the `cc_config.xml` file.

For more information, see [OxygenXML Help: Customize Content Completion](https://www.oxygenxml.com/doc/versions/25.0/ug-editor/topics/customize-content-completion.html).

## A sample cc\_config.xml file

I have created a sample `cc_config.xml` file based largely on the Lightweight DITA 1.0 XDITA proposal for a reduced list of DITA elements. Of course, your `cc_config.xml` file could contain any elements and attributes you deem necessary.

In addition to restricting the available elements and attributes for users, this `cc_config.xml` file also defines child elements or mandatory attributes and attribute values to be included \(or omitted\) for some elements. To give one example, if you add a `<section>` element, Oxygen will also add a `<title>` and `<p>` child elements.

```language-xml
<?xml version="1.0" encoding="UTF-8"?>
<!-- 
    Allows contributing to the values presented on content completion for element and attribute values.
    You can append to the values obtained from the schema or replace them all together.
    These values can be given as literal values or they can be obtained by executing an XSLT script.
    
    IMPORTANT: This file must be saved as cc_config.xml in a folder that is present in the Classpath
    of the Document Type (or framework).
-->
<?xml-model href="http://www.oxygenxml.com/ns/ccfilter/config/ccConfigSchemaFilter.sch" type="application/xml" schematypens="http://purl.oclc.org/dsdl/schematron"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.oxygenxml.com/ns/ccfilter/config http://www.oxygenxml.com/ns/ccfilter/config/ccConfigSchemaFilter.xsd"
    xmlns="http://www.oxygenxml.com/ns/ccfilter/config">

    <elementProposals
        possibleElements="
        
        topic title shortdesc prolog body section p 
        ph ul ol li dl 
        dlentry dt dd pre 
        simpletable sthead strow stentry 
        fig image object desc alt note tt xref
        
        map topicref topicmeta navtitle data mapref keydef keywords keyword	    	
        "
        
        possibleAttributes="
        DITAArchVersion 
        domains class outputclass 
        id href conref keyref keys 
        processing-role scope format type 
        props others dir xml:lang translate"/>
    
    <elementProposals path="ol/li" insertElements="p"/>
    <elementProposals path="ul/li" insertElements="p"/>
    <elementProposals path="image" rejectAttributes="alt"/>
    <elementProposals path="image" insertElements="alt"/>
    <elementProposals path="fig" insertElements="title image"/>
    <elementProposals path="section" insertElements="title p"/>
    <elementProposals path="table" insertElements="title"/>
    <elementProposals path="topicref" rejectAttributes="navtitle"/>
    
    <elementProposals path="pre">
		<insertAttribute name="translate" value="no"/>
	</elementProposals>

	<elementProposals path="tt">
		<insertAttribute name="translate" value="no"/>
	</elementProposals>
    
    <match attributeName="translate">
        <items action="addIfEmpty">
            <item value="yes"/>
            <item value="no"/>
        </items>
    </match>
    
    <match elementName="note" attributeName="type" editable="onlyAllowedItems">
        <items action="replace">
            <item value="note"/>
            <item value="caution"/>
            <item value="tip"/>
            <item value="important"/>
            <item value="remember"/>
            <item value="restriction"/>
            <item value="other"/>
        </items>
    </match
    
</config>

```

**Parent topic:**[Simplifying DITA](simplifying-dita.md)

