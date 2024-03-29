# Using content references with MDITA

For content that appears in several locations in document, DITA writers use the content referencing (*conref*) mechanism. Again, this is functionality that was impossible with Markdown on its own. Some static site generators, such as Jekyll, permitted the use of *includes* but each include had to be a separate HTML file. You can use a *conref* file (also sometimes called a *warehouse* file) to put all referenced content in one place.

The bst practice for using conrefs involves placing the content you want to reuse in a separate *warehouse* file which doesn't itself appear in the final output.

You can use a MDITA Markdown topic as a warehouse file but the content you want to reference must be in HDITA tags. The Markdown warehouse topic must include a YAML header with an idea (as in the example below).

A sample MDITA conref warehouse topic:

```xml
---
id: conref-content
---

# Conref content

<p id="install-step1">First, download the appropriate installer for your operating system from the Grunt Master website [Downloads](https://gruntmaster.com/downloads) page.</p>

<p id="disclaimer">Grunt Master Industries accepts no liability for any injury, insanity, infertility, or death caused by even casual use of the Grunt Master 6000.</p>

...
 
```

To reference the shared content within an MDITA Markdown file, you must use an HDITA tag must along with the *data-conref* attribute. The value for the *data-conref* attribute uses the following format `<TOPIC FILE NAME>#<TOPIC ID>/<TAG ID>`. For example:

```xml
## Installing the Grunt Master 6000 companion app

Follow the instructions below to install the Grunt Master 6000 companion app:

1. <p data-conref="conref.md#conref-content/install-step1"></p> 
<--! Reviewers go to conref.md and look at the paragraph with the install-step1 ID if you want to review this step. -->
1. Double-click on the installer, and follower the installation wizard instructions.
1. When installation is complete, restart your device. 
<p data-conref="conref.md#conref-content/disclaimer"></p>
```

The build process replaces HDITA tag with the referenced text.

As in the above example, it's a good idea to add a comment that points reviewers towards the conref source in case they might want to review that content too.

## Keys in conref text

Because conref content is HTML not Markdown you can't use references to any keys you have defined in the ditamap. For example if you used *[company_name]* in a the conref snippet, the build process renders literally as "*[company_name]*" and not *Grunt Industries*"*. Therefore, as a general rule, try to avoid using content that you have also made into text variables in conref content.
