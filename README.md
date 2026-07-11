# SudoSodokuApp.github.io

Marketing site for [SudoSodoku](https://github.com/SudoSodokuApp/SudoSodoku) —
`sudo solve`, logic is root access. A terminal-fantasy sudoku for iPhone;
v2.0.0 App Store submission in progress.

Plain HTML + CSS, no build step, served by GitHub Pages. Design language:
Apple's design principles — minimal, content-first — carrying the app's
phosphor-green terminal identity.

## Local preview

```sh
python3 -m http.server 8080
# open http://localhost:8080
```

That's it. There is nothing to install and nothing to build.

## Structure

| Path | Purpose |
| --- | --- |
| `index.html` | Landing page |
| `privacy.html` | Privacy policy (App Store requirement) |
| `css/main.css` | All styles |
| `img/` | App icon renditions and future screenshots |
| `docs/DESIGN.md` | Design language spec |
| `docs/CONTENT.md` | Copy guidelines and canonical strings |
| `AGENTS.md` | Working agreement for AI agents (CLAUDE.md imports it) |
| `CONTRIBUTING.md` | How to contribute (what's welcome, verify checklist) |
| `LICENSE` | MIT, same as [the app](https://github.com/SudoSodokuApp/SudoSodoku) |
| `.github/` | Issue/PR templates, security policy, Proof HTML CI |

## Deploying

Push to `main`. GitHub Pages serves the repo root at
<https://sudosodokuapp.github.io>.

## Before launch

- [ ] Replace the `TODO(app-store-url)` placeholder once the App Store page is live
- [ ] Add the 6 simulator screenshots (1320×2868, from Kai: landing / breach /
      archives / stats / whoami / in-game) to a screenshots section
