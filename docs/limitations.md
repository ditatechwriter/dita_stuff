---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Limitations

As theme files are a relatively recent innovation from the team behind the DITA-OT, there are limitations to what you can do with them. With new releases of the toolkit, there may well be further functionality added but theme files are likely not replace all the functionality you can achieve by building a custom PDF plugin. There are several reasons for this:

-   Theme files only interact with the XSL attributes files in the PDF2 plugin. They don't change anything in the XSLT templates. This means you can't do advanced configuration of PDFs (for example adding bookmap variables to a cover page).

-   There are also not insignificant financial reasons for not developing theme files beyond a certain point. Many supporters of the DITA-OT are DITA consultants who make a living out of writing custom PDF and other DITA-OT plugins, and they would not be happy if there was tool that allowed customers to do it for themselves.

    Similarly, some of the DITA-OT's sponsors are software houses that sell tools for producing PDF output from DITA (such as Syncrosoft's [Oxygen Styles Basket](https://www.oxygenxml.com/styles_basket.html), or Antenna House's [PDF5-ML](https://www.antennahouse.com/dita) plugin). Any open source tool that seriously rivalled their proprietary offerings could ultimately affect the DITA-OT project's funding. Of course that doesn't mean that an independent developer couldn't develop such an open source tool based on theme files.


## So what can't you do with theme files?

Having created several PDF templates now using theme files, here are some limitations that I found:

-   **Front covers** - Other than `<title>`, `<booktitle>` and `<booktitlealt>` (if you are using a bookmap) there are no other variables you put on the front page. I also was not able to find a way to style the `<booktitlealt>` to show subtitle content - which means I had to omit it.

-   **Back covers** - There is no way to add a back cover to your PDF document.

-   **Footers** - Configuration of footer content has limitations. You can add page numbers and even some text, but all footer content must be styled the same way. So if your page number is right-aligned and bold, so is any text be that you put in there. Basically, footers in theme files are good for page numbers, and anything else, like copyright text, would be better placed elsewhere in your document.

-   **Tables** - I could find no way to style table cell borders or content.

-   **Heading levels** - You can only style headings as far as H4. The output styles the H5 and H6 headings but there is no way change this. Although you can style `<example>` and `<section>` titles.

-   **Lists** - You can't stlye list item markers (numbers or bullets).

    Embedded lists (lists within lists) aren't styled differently from their parent. An embedded numbered list is styled 1, 2, 3, etc. rather than a, b, c, or i, ii, iii for example. Embedded unordered lists use the same bullet style as their parent list.

Despite the above reservations, the theme file feature is in active development, and the DITA-OT developer Jarno Elovirta has said that he would continue to add new features in upcoming releases. Hopefully, the issues outlined above are addressed in release 4.1.
