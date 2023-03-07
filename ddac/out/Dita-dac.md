# DITA versus docs-as-code

The docs-as-code philosophy has revolutionized the way technical documentation in software projects is written, managed and published.

Documentation is treated in the same manner as the code developed for the software itself. It is written in the same text editors, and it is stored and managed using the same version control systems \(VCS\) as the code \(most commonly Git\).

Publishing content produced in this manner has never been easier. Technical writing team have a whole array of static site generators that produce full-featured, elegant, and easy-to-use documentation websites.

There are many advantages for technical writing teams in using a docs-as-code approach:

-   Documents are generally written in Markdown. Markdown is simple, can be learned in a few minutes, and can be written in any text editor.

-   All the main online VCS services \(GitHub, GitLab, Bitbucket\) have built in Markdown interpreters.

-   Developers use Markdown a lot, so the format is no barrier to getting documentation reviewed.

-   Static site generators \(SSG\) for Markdown content are often simple to set up and configure \(although that might depend on the SSG you choose and the complexity of what you want it to do\).

-   It is relatively cheap, quick and easy for a documentation team to start using a docs-as-code tool-chain to produce a documentation website.


That said, however, the docs-as-code approach also has limitations:

-   Markdown's simplicity is also it's greatest weakness. There are no mechanisms to allow for content reuse, text variables, or conditional filtering, making documentation updates a chore.

-   Lack of content reuse features makes managing documentation difficult.

    -   If content exists in multiple places in a document, it needs to be updated in all those places if changed.

    -   If there are multiple variants of a product \(e.g. Lite, Professional, Enterprise\) discreet copies of the documentation need to be kept even if the content is mostly identical. Any updates to shared content will need to be made in each copy.


## What about DITA?

The Darwin Information Typing Architect - DITA for short - is the most popular XML vocabulary for technical documentation at Enterprise level.

DITA files are flat XML files and so are perfect to use with a modern VCS like Git.

DITA real selling point is that it has all the content reuse features that Markdown documentation lacks which makes it very useful when working with large document sets and complex publishing needs. But, it also has quite a few drawbacks:

-   The DITA element set is large - 189 tags. The learning curve for new writers can be steep.

-   Writing in DITA requires writers to use an XML editor that validates the XML they write.

-   Editing raw DITA is not possible for anyone not trained to use it and without a an XML editor.

-   DITA uses the DITA Open Toolkit to transform DITA XML into other formats. The output, however, is basic and it requires a lot of \(usually specialist\) work in XSLT and CSS to produce a good-looking documentation website from DITA source files.

-   Moving to DITA can be lengthy and costly in terms of training and specialist consultancy.


