# Other things you can do with project files

There are a couple of other things you can do with project files. You can publish deliverables from several different project files at once, or just one deliverable from a project file containing several. You can also use the DITA *deliverables* command as a quick and easy way to see what deliverables a project file contains.

## Using multiple project files together {.section}

The project file syntax also incorporates an \<include> element which you can use to chain several project files together and produce all their deliverables in one go. See the following example, *all_deliverables.xml*:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-model href="https://www.dita-ot.org/rng/project.rnc" type="application/relax-ng-compact-syntax"?>

    <project xmlns="https://www.dita-ot.org/project">
    
        <include href="product1_deilverables.xml"/>
        <include href="product2_deilverables.xml"/>
        <include href="product3_deilverables.xml"/>
        
    </project>        
```
The command below therefore would build all the deliverables contained in the *product1_deilverables.xml*, *product2_deilverables.xml*, and *product3_deilverables.xml* project files:

```language-bourne
dita --project=all_deliverables.xml
```
## Listing all the deliverables in a project file {.section}

If a project file contains many deliverables, and especially if it is written in XML, it can be no easy task to find exactly which deliverables it builds. Luckily, there is a command for just for that. For example:

```language-bourne
dita deliverables gm_deliverables.xml
```
The DITA *deliverables* command if used on the *gm_deliverables.xml* described in [build-multiple-docs] returns each deliverable's ID and name:

```language-bourne
ug_gruntmaster6000_html5 Grunt Master 6000 Guide
ug_gruntmaster3000_html5 Grunt Master 3000 Guide
ug_gruntmaster3000_pdf   Grunt Master 3000 Guide
```
## Building a single deliverable from a project file {.section}

If you only want to build a single deliverable and you know that its build parameters are contained in a certain project file you can pass the deliverable's unique ID to the *--deliverable* switch with the DITA build command. The following example builds the PDF version of the Grunt Master 3000 Guide listed in the *gm_deliverables.xml* project file:

```language-bourne
dita --project=gm_deliverables.xml --deliverable=ug_gruntmaster3000_pdf
```
<p><note>You can also build all (or just one) of the deliverables in a project file you have open in Oxygen by going to <b>Document</b>><b>Transformation</b>><b>Configure Transformation Scenario(s)</b> and selecting either <b>Publish DITA-OT Project (all deliverables)</b> or <b>Publish DITA-OT Project (select deliverable).</b></note></p>