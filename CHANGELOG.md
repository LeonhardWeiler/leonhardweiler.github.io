# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- `README.md` describing the project, how it works, and how to preview it.
- `CLAUDE.md` with an overview and working conventions.
- `CHANGELOG.md` (this file).
- `GPL-3.0-or-later` SPDX license identifier in `index.html`.

### Changed

- Translated the site to English: page language, all user-facing text, and code
  comments.

### Fixed

- HTML injection risk in the project rendering: repository names and
  descriptions from the GitHub API are now inserted as text instead of raw HTML.

## [0.3.0] - 2026-01-16

### Added

- GNU General Public License v3 text (`LICENSE`).

## [0.2.0] - 2025-11-11

### Added

- Light and dark color scheme support based on the visitor's system preference.
- Caching of the project list in `localStorage` so returning visitors see
  content immediately.

### Changed

- Various smaller layout and rendering improvements.

## [0.1.0] - 2025-11-11

### Added

- Initial landing page that lists the user's live GitHub Pages projects as a grid
  of cards.
