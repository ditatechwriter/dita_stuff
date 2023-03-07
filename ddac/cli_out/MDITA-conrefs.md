---
author: michael.mcloughlin@puppet.com
---

# Using content references with MDITA

For content that appears in several locations in document, DITA writers use the content referencing \(`conref`\) mechanism.

Best practice for using conrefs involves placing the content to be reused in a separate "warehouse" file which does not itself appear in the final output.

A MDITA Markdown topic can be used for a warehouse file but the content to be referenced must be in HDITA tags.

A sample MDITA conref warehouse topic:

```
---
id: conref-content
---

# Conref content

<p id="install-step1">First, download the appropriate installer for your operating system from the Grunt Master website [Downloads](https://gruntmaster.com/downloads) page.</p>

<p id="disclaimer">Grunt Master Industries accepts no liability for any injury, blindness, infertility, or death caused by even casual use of the Grunt Master 6000.</p>

...
 
```

To reference the shared content within an MDITA markdown file, an HDITA tag must be used along with the `data-conref` attribute. The value for the `data-conref` attribute uses the following format <TOPIC FILE NAME\>\#<TOPIC ID\>/<TAG ID\>. For example:

```
## Installing the Grunt Master 6000 companion app

Follow the instructions below to install the Grunt Master 6000 companion app:

- <p data-conref="conref.md#conref-content/install-step1"></p> <---! Reviewers go to conref.md and look at the paragraph with the install-step1 ID if you want to review this step. --->
- Double-click on the installer, and follower the installation wizard instructions.
- When installation is complete, restart your device.
```

Once built the HDITA tag will be replaced by the referenced text.

As in the above example, it's a good idea to add a comment that points reviewers towards the conref source in case they might want to review that content too.

**Parent topic:**[Using DITA for docs-as-code](DITA4dac.md)

