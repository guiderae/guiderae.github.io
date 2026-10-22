# Adding a new discussion

Every page in this folder — `index.html` and each individual summary page
(`robotics.html`, `cashless-society.html`, etc.) — is **generated** from the
source PDFs, not hand-written. Don't edit them directly: the next time the
generator runs, your edits get silently overwritten.

This `README.md`, and the `tools/` folder below, are the exceptions — the
generator never touches either, so they're safe to keep here permanently.
(`tools/` is gitignored — it's maintainer tooling, not part of the published
site.)

## Where things live

| | Location |
|---|---|
| The build scripts | `RodinDiscussions/tools/` *(sibling of this file)* |
| Source PDFs (version-controlled separately) | `/Users/eliguidera/MyDocuments/Rodin/GitHubSummaries/` |
| This site's pages, assets, and downloadable PDFs | `RodinDiscussions/` *(you are here — this is the live, git-tracked copy)* |

There's only one copy of this site's content now — the generator writes
directly here.

## Steps to add one

See `tools/README.md` for the full detail; in short:

1. Drop the new PDF into `GitHubSummaries/`.
2. Add one entry to the `DISCUSSIONS` list in `tools/generate.py`.
3. Run:
   ```
   cd /Users/Shared/GuideraeGithubPages/RodinDiscussions/tools
   python3 generate.py /Users/eliguidera/MyDocuments/Rodin/GitHubSummaries ..
   ```
4. Review, commit, and push from the repo root:
   ```
   cd /Users/Shared/GuideraeGithubPages
   git status
   git add RodinDiscussions/
   git commit -m "Add <discussion title>"
   git push
   ```

## Why not just copy an `<article>` block in index.html?

That block is only the index *teaser* (title, date, blurb, two links) — it
doesn't create the full converted page those links point to, or move the
PDF into `pdf/`. The generator is what turns a PDF's headings and nested
bullet points into the styled HTML on each full page; hand-writing that is
real work the script already does correctly for all 8 existing discussions.
