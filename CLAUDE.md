# CLAUDE.md

Guidance for working in this repository.

## Overview

This is the personal landing page served at
`https://leonhardweiler.github.io/`. It is a single static page that queries the
GitHub API for the user's public repositories and renders them as a
git.suckless.org-style table (gray/white/black), with one row per repo.

## Structure

- `index.html`: the entire site. Markup, CSS, and JavaScript live inline in this
  one file. There is no build step and there are no dependencies.
- `LICENSE`: ISC license text.
- `README`: plain-text file (no extension, so GitHub renders it monospace)
  holding the license.
- `AGENT/`: working files for automated agents (reports). Not part of the
  published site.

## How it works

On load, `index.html`:

1. Fetches `https://api.github.com/users/<username>/repos` from the GitHub API.
2. Sorts the repos alphabetically by name and renders one table row each with
   three columns: Name (linking to the repo's `html_url`), Description, and Last
   commit (the `pushed_at` date). Load errors and an empty result render a
   single message row.

The GitHub username is set in the `user` constant near the top of the script.

## Local preview

There is no toolchain. Open `index.html` in a browser, or serve the directory
with any static server, for example:

```
python3 -m http.server
```

## Conventions

- Keep the site dependency-free and contained in `index.html`.
- Keep it minimal: solve the problem simply and let the code explain itself.
  Prefer clear names over comments; do not add comments. The only exception is
  the `@license` / `@license-end` labels wrapping the inline script: they are
  required for FSF LibreJS compliance (magnet link for ISC) and must be kept.
- The page is dark-themed in gray/white/black; keep it that way.
- All user-facing text is in English.
- Data from the GitHub API (repository names and descriptions) is untrusted
  input. When inserting it into the DOM, use `textContent` (or equivalent),
  never `innerHTML`, to avoid HTML injection.
