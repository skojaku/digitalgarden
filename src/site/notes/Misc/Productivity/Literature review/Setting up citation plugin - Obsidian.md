---
{"dg-publish":true,"permalink":"/misc/productivity/literature-review/setting-up-citation-plugin-obsidian/","dgPassFrontmatter":true}
---


# Setting up citation plugin - Obsidian
updated: 2022-11-30

# Steps
1. Setting up Zotero 
	1. Install the better [BibTeX plugin](https://retorque.re/zotero-better-bibtex/)
	2. Generate CLS JSON file under the obsidian vault folder
2. Setting up the Obsidian 
	1. Install the citation plugin
	2. Open the setting of [the citation plugin](https://github.com/hans/obsidian-citation-plugin)
	3. Copy & Paste the template below


Template:
```
---
dg-publish: true
---

**{{title}}**
by {{authorString}}
*{{publisher}}* ({{year}})
[Web]({{URL}}) [Open in zotero]( {{zoteroSelectURI}})

**Tags**: 
#literature-note

---

**Background**

**Limitation**

**Research question**

**Approach**

**Results**

**Take away**
```


# Reference 
[Citations Plugin for Obsidian - YouTube](https://www.youtube.com/watch?v=QlUyHX30GWo)