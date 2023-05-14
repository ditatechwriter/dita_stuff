---
author: Michael McLoughlin
publisherinformation: V1.0
---

# Adding search

The [DITA-Bootstrap](https://www.dita-ot.org/plugins#!net.infotexture.dita-bootstrap) plugin (or to give it its proper name, the *net.infotexture.dita-bootstrap* plugin) is a customized version of the DITA Open Toolkit (DITA-OT) HTML5 plugin that uses the Bootstrap 5 CSS framework. The DITA-OT HTML5 plugin produces unstyled HTML5 output. The DITA Bootstrap plugin look and feel replicates the Bootstrap 5 documentation template.

You can install the plugin into the DITA-OT by using the `dita install` command:

```language-markup
dita install net.infotexture.dita-bootstrap
```

It's not necessary to go into the many styling and configuration possibilities offered by the DITA Bootstrap plugin here. See the [DITA Bootstrap GitHub](https://infotexture.github.io/dita-bootstrap/index.html) pages site for information on the various plugin configuration options.

Many Bootstrap widgets and other features have been integrated into the plugin, but it lacks a search bar and any integrated search functionality. It's possible to integrate 3rd party server-based search functionality (such as Algolia DocSearch or Google Custom Search), as well as client-based JavaScript search libraries.
