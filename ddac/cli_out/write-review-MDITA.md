---
author: michael.mcloughlin@puppet.com
---

# Writing and Reviewing MDITA

MDITA *is* Markdown and so learning how to use it is much simpler than learning how to use full-blown DITA. The DITA Open Toolkit website provides a cheat-sheet for MDITA mark-up: [MDITA syntax reference](https://www.dita-ot.org/dev/topics/markdown-dita-syntax-reference.html).

Writers may need a little more training on how to incorporate DITA mechanism like keys, conrefs and ditaval filters when writing in MDITA but a couple of hours at most will train any new writer with no knowledge of Markdown or DITA how to write effective MDITA.

Writers would still probably be advised to use an XML editor especially to validate any XDITA or HDITA tags they use. Reviewer however should be able to use their favorite text editor to review and make updates, up load to their VCS and issue a pull request just as if they were editing source code.

Normally, to get DITA content reviewed, writers had to transform it into another format such as PDF and circulate that to a reviewer for comments. Then, use those comments to manually update the DITA source files. Or, technical publication departments would have to invest in online XML editors like Oxygen Web Author or Xeditor, that provide a WYSIWYG front-end that hides the XML complexity from reviewers. With MDITA, DITA writers can enjoy the same easy review workflow as writers in Markdown.

**Parent topic:**[Using DITA for docs-as-code](DITA4dac.md)

