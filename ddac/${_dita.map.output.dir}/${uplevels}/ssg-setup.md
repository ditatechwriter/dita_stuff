<?xml version="1.0" encoding="UTF-8"?><?workdir /home/michael/Documents/ddac/ddac/temp/pdf?><?workdir-uri file:/home/michael/Documents/ddac/ddac/temp/pdf/?><?path2project?><?path2project-uri ./?><?path2rootmap-uri ./?><topic xmlns:ditaarch="http://dita.oasis-open.org/architecture/2005/" xmlns:dita-ot="http://dita-ot.sourceforge.net/ns/201007/dita-ot" class="- topic/topic " ditaarch:DITAArchVersion="1.2" domains="(topic hi-d) (topic ut-d) (topic indexing-d) (topic hazard-d) (topic abbrev-d) (topic pr-d) (topic sw-d) (topic ui-d)" id="setting-up-docsify-as-your-static-site-generator" xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="topic:1;182:3" specializations=""><title class="- topic/title " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="title:1;182:3">Setting up Docsify as your static site generator</title><prolog class="- topic/prolog " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="prolog:1;182:3"><data class="- topic/data " name="id" value="SSG-setup" xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="data:1;182:3"/></prolog><body class="- topic/body " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="body:1;182:3"><p class="- topic/p " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="p:1;182:3">Docsify is the most easily configurable. Based on JavaScript, it has one main configuration file, good documentation and lots of community plugins.</p><p class="- topic/p " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="p:2;182:3">Documentation on configuring is available on the <xref class="- topic/xref " href="https://docsify.js.org/#/" format="html" scope="external" xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="xref:1;182:3">Docsify website</xref>.</p><p class="- topic/p " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="p:3;182:3">To set it up to display the content built by the GitHub actions:</p><ol class="- topic/ol " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="ol:1;182:3"><li class="- topic/li " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="li:1;182:3"><p class="- topic/p " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="p:4;182:3">Create an empty branch in the same repository as your MDITA source. I ahve acalled mine 'docsify'.</p></li><li class="- topic/li " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="li:2;182:3"><p class="- topic/p " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="p:5;182:3">Add a new folder called <codeph class="+ topic/ph pr-d/codeph " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="codeph:1;182:3">docs</codeph>,</p></li><li class="- topic/li " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="li:3;182:3"><p class="- topic/p " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="p:6;182:3">Within the <codeph class="+ topic/ph pr-d/codeph " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="codeph:2;182:3">docs</codeph> folder add the index.html file as outlined in the <xref class="- topic/xref " href="https://docsify.js.org/#/quickstart?id=manual-initialization" format="html" scope="external" xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="xref:2;182:3">Docsify documentation</xref>.</p></li><li class="- topic/li " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="li:4;182:3"><p class="- topic/p " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="p:7;182:3">Edit the index.html file to use index.md (which the markdown generates from your root ditamap) as a sidebar navigation file:</p><codeblock class="+ topic/pre pr-d/codeblock " xml:space="preserve" xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="codeblock:1;182:3">   &lt;!-- index.html --&gt;
   &lt;!DOCTYPE html&gt;
   &lt;html&gt;
   &lt;head&gt;
    &lt;meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"&gt;
    &lt;meta name="viewport" content="width=device-width,initial-scale=1"&gt;
    &lt;meta charset="UTF-8"&gt;
    &lt;link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/themes/vue.css" /&gt;
   &lt;/head&gt;
   &lt;body&gt;
    &lt;div id="app"&gt;&lt;/div&gt;
     &lt;script&gt;
      window.$docsify = {
       // load from index.md
       loadSidebar: 'index.md'
       };
 &lt;/script&gt;
     &lt;script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"&gt;&lt;/script&gt;
     &lt;script src="//cdn.jsdelivr.net/npm/docsify@4"&gt;&lt;/script&gt;
     &lt;/body&gt;
     &lt;/html&gt;</codeblock></li><li class="- topic/li " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="li:5;182:3"><p class="- topic/p " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="p:8;182:3">Run run a build.</p></li><li class="- topic/li " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="li:6;182:3"><p class="- topic/p " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="p:9;182:3">When the build completes check that the content has been deployed in the <codeph class="+ topic/ph pr-d/codeph " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="codeph:3;182:3">docs</codeph> folder on the branch where you want it to be outputted. Open a terminal at the <codeph class="+ topic/ph pr-d/codeph " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="codeph:4;182:3">docs</codeph> folder and (if you have Python installed) type:</p><codeblock class="+ topic/pre pr-d/codeblock " xml:space="preserve" xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="codeblock:2;182:3"> python -m SimpleHTTPServer 3000</codeblock></li><li class="- topic/li " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="li:7;182:3"><p class="- topic/p " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="p:10;182:3">Open your browser at <codeph class="+ topic/ph pr-d/codeph " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="codeph:5;182:3">localhost:3000</codeph> to see your site.</p></li></ol><p class="- topic/p " xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="p:11;182:3">To change themes and add more site functionality, see the <xref class="- topic/xref " href="https://docsify.js.org/#/" format="html" scope="external" xtrf="file:/home/michael/Documents/ddac/ddac/ssg-setup.md" xtrc="xref:3;182:3">Docsify documentation</xref>.</p></body></topic>