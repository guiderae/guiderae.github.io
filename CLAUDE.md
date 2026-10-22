# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repo (`guiderae/guiderae.github.io`) is the only way to get a
`*.github.io` URL on this GitHub account, so it hosts **multiple independent
static websites**, each a sibling folder at the repo root, routed by GitHub
Pages purely by path:

| Folder | Live at | What it is |
|---|---|---|
| `ScienceArticles/` | https://guiderae.github.io/ScienceArticles/ | Eli's Science Corner — static HTML science articles |
| `RodinDiscussions/` | https://guiderae.github.io/RodinDiscussions/ | Summaries of the Rodin group's discussions |

There is **no `index.html` at the repo root** — `https://guiderae.github.io`
itself intentionally serves nothing. Every link, whether internal navigation
or an external reference, should point at a specific site's folder
(`/ScienceArticles/...` or `/RodinDiscussions/...`), never at the bare root.

## Site isolation

Each site folder is fully self-contained: its own `index.html`, its own CSS,
its own images, its own `CLAUDE.md` with that site's specific conventions.
Nothing in one site's folder references a file in another site's folder or in
the repo root. When adding or editing a page, stay inside that one site's
folder — don't introduce a cross-site link or a shared asset.

Each site also has its own `.gitignore` for build artifacts specific to it;
this root `.gitignore` only holds generic, repo-wide ignores (OS files,
editor backups).

## Working in a specific site

Open (or `cd` into) that site's own folder and read its `CLAUDE.md` — it has
the real detail: theme/CSS conventions, page templates, article inventory,
migration or build notes, etc.
