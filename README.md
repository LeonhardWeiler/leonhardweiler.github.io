# leonhardweiler.github.io

The personal GitHub Pages landing page served at
[leonhardweiler.github.io](https://leonhardweiler.github.io/). It lists every one
of the user's public repositories that has a live GitHub Pages site, shown as a
grid of cards with the project's Open Graph preview image, name, and description.

## How it works

The page is a single static `index.html` with inline CSS and JavaScript. On load
it:

1. Renders any list cached in `localStorage` right away, so returning visitors
   see content instantly.
2. Fetches the user's repositories from the GitHub API.
3. Sends a `HEAD` request to each candidate Pages URL and keeps only the sites
   that respond successfully.
4. Renders the live projects and caches the fresh list for next time.

The layout adapts to the viewport and follows the visitor's light or dark color
scheme preference.

## Structure

```
index.html      the entire site (markup, styles, and script inline)
LICENSE         GNU General Public License v3
README.md       this file
CHANGELOG.md    release history (Keep a Changelog format)
```

## Local preview

There is no build step and there are no dependencies. Open `index.html` in a
browser, or serve the directory with any static server:

```
python3 -m http.server
```

Then visit the printed local address.

## Configuration

The GitHub username is set in the `username` constant near the top of the script
in `index.html`. Change it to point the page at a different account.

## License

Licensed under the GNU General Public License, version 3 or (at your option) any
later version (`GPL-3.0-or-later`). See [LICENSE](LICENSE) for the full text.
