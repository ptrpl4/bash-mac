---
description: Framework for static websites
---

# 🤗 Hugo

links

* [https://gohugo.io/](https://gohugo.io/)

## Commands

```bash
hugo new content posts/new-letters.md

hugo server
```

### dir structure

source - [https://gohugo.io/getting-started/usage/](https://gohugo.io/getting-started/usage/)

example:

```
public/
├── categories/
│   ├── index.html
│   └── index.xml  <-- RSS feed for this section
├── post/
│   ├── my-first-post/
│   │   └── index.html
│   ├── index.html
│   └── index.xml  <-- RSS feed for this section
├── tags/
│   ├── index.html
│   └── index.xml  <-- RSS feed for this section
├── index.html
├── index.xml      <-- RSS feed for the site
└── sitemap.xml
```
