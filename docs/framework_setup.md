---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Setting up a custom framework

Custom frameworks are a way to customize the Oxygen XML editor to work more easily with different XML vocabularies. We are not creating a new vocabulary here but rather restricting existing ones. We will need to create to custom frameworks: one for DITA topics, and one for DITA maps. These custom frameworks can then be shared with colleagues and imported into their Oxygen instances.

The first step in defining the new frameworks is to set up the location from which they will be shared. I created a GitHub repository call `tools` and added the following directory structure:

```language-markup
custom_frameworks
            - simple_dita
                - resources
                - templates
            - simple_ditamap
                - resources
                - templates
```

-   **custom\_frameworks** - this folder is the root folder for all custom frameworks.

-   **simple\_dita** - is the container for the `simple_dita.framework` file.

-   **simple\_ditamap** - is the container for the `simple_ditamap.framework` file.

-   **/resources** - holds the `cc_config.xml` file. There are many other files that could live here such as CSS or Schematron files if required.

-   **/templates** - contains the topic or map templates.


When complete, colleagues can clone this repository, and use some Oxygen preferences settings to access its files.

## Template and resource files

Now that you have the folder structure in place, it's time to add the template and resource files:

1.  First move a copy of the `cc_config.xml` file you created in to the resources folder in within both the `simple_dita` and `simple_ditamap` folders.

    **Note:** In the example I cited in [Creating a cc\_config.xml file](cc_config.md), both topic and map elements and attributes were configured. You could also create separate `cc_config.xml` files defining only the relevant elements and attributes for each framework.

2.  Next, copy the `Topic.dita` and `Topic.properties` files from `frameworks/dita/templates/topic` folder within your Oxygen install folder to the `simple_dita/templates` folder.

3.  Finally, copy the `Map.ditamap` and `Map.properties` files from `frameworks/dita/templates/map` folder within your Oxygen install folder to the `simple_ditamap/templates` folder.


**Parent topic:**[Simplifying DITA](simplifying-dita.md)

