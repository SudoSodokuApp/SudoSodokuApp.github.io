# Contributing to SudoSodokuApp.github.io

Thanks for helping improve the SudoSodoku website! This repo is the
marketing site only — for the app itself, head to
[SudoSodokuApp/SudoSodoku](https://github.com/SudoSodokuApp/SudoSodoku)
and its own [CONTRIBUTING.md](https://github.com/SudoSodokuApp/SudoSodoku/blob/main/CONTRIBUTING.md).

## What we welcome

* 🐛 **Display bugs** — layout breakage, light/dark scheme issues,
  horizontal scroll on mobile, broken links
* 📝 **Copy fixes** — typos, grammar, clarity (canonical strings live in
  [docs/CONTENT.md](docs/CONTENT.md); don't paraphrase those)
* ♿ **Accessibility** — contrast, semantics, reduced-motion handling
* 🌍 **Localization** — discuss in an issue first

## What we will decline

* Frameworks, bundlers, npm, or any build step — this site is plain
  HTML + CSS on purpose
* Webfonts, analytics, or any external request
* JavaScript, unless the feature is impossible without it and the page
  still works with JS off
* Green body text outside terminal surfaces (see
  [docs/DESIGN.md](docs/DESIGN.md) — "the page is Apple; the product
  shots are terminal")

## Getting started

```sh
git clone https://github.com/SudoSodokuApp/SudoSodokuApp.github.io.git
cd SudoSodokuApp.github.io
python3 -m http.server 8080   # then open http://localhost:8080
```

Nothing to install, nothing to build.

## Before opening a PR

Run the verify checklist from [AGENTS.md](AGENTS.md):

1. Open every page you touched in a browser.
2. Check light + dark scheme, 375px + 1280px widths.
3. No horizontal scroll, no console errors, no external requests.
4. All links resolve.

Every push is also validated by the Proof HTML workflow (broken links,
invalid HTML).

## Code style

* Tabs for indentation in HTML/CSS (match the existing files).
* Design tokens and typography rules: [docs/DESIGN.md](docs/DESIGN.md).
* Copy voice and canonical strings: [docs/CONTENT.md](docs/CONTENT.md).
* Keep changes surgical — touch only what your fix requires.

## Code of Conduct

This project follows the [Contributor Covenant](CODE_OF_CONDUCT.md).
