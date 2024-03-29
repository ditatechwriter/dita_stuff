---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Simplifying DITA

One of the issues that teams that use DITA often have is finding writers with DITA skills. The base implementation of DITA has around 190 elements and many more attributes. The most popular DITA XML editor, Oxygen XML Author, is an powerful but not infrequently daunting tool for new users. The learning curve therefore can be steep for new writers, and the cost of hiring experienced DITA writers expensive.

So, is it possible to simplify DITA and Oxygen to make them more user friendly for new writers?

At the time of writing (Spring 2023), there is no news on when exactly the new Lightweight DITA 1.0 (LwDITA) standard is going to be released. From what I've seen it will be a great step forward in simplifying DITA and easing the steep learning curve encountered by many writers when taking on DITA for the first time.

However, in the meantime, what do we do?

Even though there is growing editor support for the new LwDITA DTDs and functionality, it's not quite there yet.

And even when it comes online, LwDITA might be just too lightweight for your needs. I have worked with document sets that contained many complex tables and which were published to PDF. LwDITA only supports simple (as opposed to CALS) tables and doesn't support bookmaps at all. In a case like this, LwDITA would not be powerful enough.

I think it's possible to simplify standard DITA 1.3 use for ordinary - especially new - writers, without having to write whole new DTDs.

Here's how:

-   **Stop worrying about Information Typing**

    For many projects, the information type makes no difference in how you manage the content. You can forget about whether a topic is a task, a reference, or a concept. Just use the *topic* type for all topics. This is essentially the approach in LwDITA.

    This might have some DITA purists clutching their pearls over the very idea of using an ordered list for procedures instead of steps but, in the end, you can't tell in the output, and you may be saving someone from learning all those task elements.

-   **Stick to the `<map>` ditamap type wherever possible**

    Again, this is the approach taken by the team creating LwDITA. Admittedly, jettisoning bookmaps may not be feasible if you need to publish PDF outputs.

-   **Radically reduce available elements you use**

    Full-fat DITA 1.3 has something like 193 elements in its base implementation alone. The vast majority of which most writers don't use. I suggest auditing your content and looking at the type of elements and attributes you use and make a point of restricting access for writers to all the rest.

-   **Simplify the Oxygen XML Author UI**

    Oxygen XML Editor/Author is my favorite software application. it's unbelievably powerful, well-designed, and no other editor comes even close when working with DITA. And it can be a bit daunting for first-time users. Luckily, it's UI is extensible, and there are many things you can do to hide a lot of the more complex functionality that most writers, especially relatively inexperience ones, simply don't use on a regular basis.

    Here are somethings you can do to make the Oxygen Editor more user friendly:

    -   Edit the `cc_config.xml` file so that only the elements (and attributes) you actually use are available in the **Elements** and **Attributes** windows. Editing this file also hides the unwanted elements and attributes in the right-click content completion menus.

        You can also use the `cc_config.xml` file to enforce element patterns (for example always having a `<p>` element inside a `<li>` element).

    -   Create a shareable custom frameworks for topics and maps that novice OxygenXML users can install allow them work with the reduced list of elements and attributes.

    -   Define a simple editor layout with only the windows that are necessary, and share this with new team members. This is a big help for new users.
