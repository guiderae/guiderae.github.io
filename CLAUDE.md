# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static HTML website for science articles written by Eli Guidera. Migrated from a Java/Spring MVC JSP application to plain static HTML + CSS, hosted on GitHub Pages. No build step — files are served directly.

## Deployment

Live at **https://guiderae.github.io** (GitHub Pages, repo `guiderae/guiderae.github.io`, branch `main`, root `/`).

## Article inventory

All articles migrated. Top-level files at the repo root:

| HTML file | Title |
|---|---|
| `index.html` | Science Articles (landing page) |
| `galaxiesArticle.html` | A Galaxy Far, Far Away |
| `cpuArticle.html` | How Does a Computer Execute a Program? |
| `nuclearArticle.html` | Where Did All the Elements Come From? |
| `airplanesFly.html` | How Do Airplanes Fly? |
| `fibonacci.html` | The Fibonacci Sequence |
| `climate.html` | Does Human Activity Affect Earth's Climate? |
| `relativityArticle.html` | Einstein's Theories of Relativity |

Sub-pages linked from `nuclearArticle.html` (not listed on the landing page):

| HTML file | JSP source |
|---|---|
| `atomicHistory.html` | `ScienceArticlesJSP/atomicHistory.jsp` |
| `protonChain.html` | `ScienceArticlesJSP/protonChain.jsp` |
| `manMadeNuclear.html` | `ScienceArticlesJSP/manMadeNuclear.jsp` |

`relativityArticle.jsp` is also referenced from within the nuclear article.
`sexDetermination.jsp` is commented out on the main page and not being migrated.

## Theme and CSS

The site uses an **editorial/magazine** theme (Merriweather serif body, Raleway sans-serif headings, light navy `#2b2ba1` header). All styles live in `assets/css/articles.css`.

Key CSS classes:
- `.site-header` / `.site-name` / `.site-tagline` — page header
- `.content-wrap` — centered max-width container (860px) for all page content
- `.page-heading` — navy h1 with bottom border, used on every page
- `.article-entry` + `.article-thumb` + `hr.article-divider` — index page article cards with floated thumbnail
- `.imageleft` / `.imageright` — floated images inside article body text
- `.container` + `.textcontent` — wraps a float + paragraph block inside articles
- `.back-link` — "« Back to Science Home" link used at the top of every article page

## Page template

Every article page should follow this shell:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ARTICLE TITLE — Eli's Science Corner</title>
    <link href="https://fonts.googleapis.com/css2?family=Merriweather:ital,wght@0,300;0,400;0,700;1,400&family=Raleway:wght@400;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" type="text/css" href="assets/css/articles.css">
</head>
<body>
<header class="site-header">
    <div class="inner">
        <a href="index.html" class="site-name">Eli's Science Corner</a>
        <span class="site-tagline">Science without the sensationalism</span>
    </div>
</header>
<main class="content-wrap">
    <a href="index.html" class="back-link">&laquo; Back to Science Home</a>
    <h1 class="page-heading">ARTICLE TITLE</h1>
    <!-- article body here -->
</main>
<footer>
    &copy; Eli Guidera &mdash; Eli's Science Corner
</footer>
</body>
</html>
```

## Migration rules

When converting a JSP file:
- `${scienceImageBase}/topic/file.ext` → `assets/images/science/topic/file.ext`
- `${pageContext.request.contextPath}/scienceCorner` → `index.html`
- `${pageContext.request.contextPath}/scienceCorner/ARTICLE` → `ARTICLE.html`
- `<spring:message code="science.main.TOPIC.title"/>` → use the title from the inventory table above
- Strip all JSP taglib declarations, `<c:set>`, `<t:layout>`, and `<%--` comment blocks
- Replace `<table>`-based layout with `.container` + `.imageleft`/`.imageright` + `.textcontent` divs
- Images that were in `<td>` cells beside text become floated with `.imageleft` or `.imageright`
- Any jQuery UI dialog widgets (periodic table enlargement, etc.) can be preserved or replaced with a simple `<a>` link to the full image

## Tooling note

`Gruntfile.js`, `gulpfile.js`, and `bower.json` are empty NetBeans scaffolds — not used. `package.json` has no dependencies. Nothing to install or build.
