# CLAUDE.md

Guidance for working in this repository.

## Overview

This is the personal GitHub Pages landing page served at
`https://leonhardweiler.github.io/`. It is a single static page that queries the
GitHub API for the user's public repositories, keeps the ones that have GitHub
Pages enabled, and renders them as a plain list of links.

## Structure

- `index.html`: the entire site. Markup and JavaScript live inline in this one
  file. There is no build step and there are no dependencies.
- `LICENSE`: ISC license text.
- `README.md`: project description and license.
- `AGENT/`: working files for automated agents (reports). Not part of the
  published site.

## How it works

On load, `index.html`:

1. Fetches `https://api.github.com/users/<username>/repos` from the GitHub API.
2. Keeps the repos whose `has_pages` flag is set and appends each one as a link
   using the Pages URL convention `https://<username>.github.io/<repo>/`.

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
  Prefer clear names over comments; do not add comments.
- All user-facing text is in English.
- Repository descriptions come from the GitHub API and are untrusted input. When
  inserting them into the DOM, use `textContent` (or equivalent), never
  `innerHTML`, to avoid HTML injection.
