# CLAUDE.md

Guidance for working in this repository.

## Overview

This is the personal GitHub Pages landing page served at
`https://leonhardweiler.github.io/`. It is a single static page that queries the
GitHub API for the user's public repositories, keeps the ones that have a live
GitHub Pages site, and renders them as a grid of cards.

## Structure

- `index.html`: the entire site. Markup, CSS, and JavaScript live inline in this
  one file. There is no build step and there are no dependencies.
- `LICENSE`: GNU General Public License v3 text.
- `README.md`: project description for humans.
- `CHANGELOG.md`: release history following the Keep a Changelog format.
- `AGENT/`: working files for automated agents (TODO list, reports). Not part of
  the published site.

## How it works

On load, `index.html`:

1. Reads a cached result list from `localStorage` (key `cachedPages`) and renders
   it immediately, so returning visitors see content without waiting.
2. Fetches `https://api.github.com/users/<username>/repos`, then sends a `HEAD`
   request to each candidate Pages URL to check which sites are actually live.
3. Renders the live projects and writes the fresh list back to `localStorage`.

The GitHub username is set in the `username` constant near the top of the script.

## Local preview

There is no toolchain. Open `index.html` in a browser, or serve the directory
with any static server, for example:

```
python3 -m http.server
```

## Conventions

- Keep the site dependency-free and contained in `index.html`.
- All user-facing text and code comments are in English.
- Repository descriptions come from the GitHub API and are untrusted input. When
  inserting them into the DOM, use `textContent` (or equivalent), never
  `innerHTML`, to avoid HTML injection.
