# AGENTS.md — SudoSodokuApp.github.io (site: https://sudosodoku.kaichen.dev)

Marketing site for **SudoSodoku**, a terminal-fantasy sudoku for iPhone
(<https://github.com/SudoSodokuApp/SudoSodoku>). Served by Vercel at the
canonical domain (GitHub Pages mirror still exists), no build step.
Extensionless links require `cleanUrls` in vercel.json — don't remove it. The design follows Apple's design principles: minimal,
content-first, paper-fast, plain HTML.

## Hard constraints

- **Plain HTML + CSS only.** No frameworks, no bundlers, no npm, no build
  step. JavaScript only when a feature is impossible without it, and then
  vanilla, inline-sized, and progressive (the page must work with JS off).
- **Paper-fast.** Every page must be usable on first paint: system fonts
  only, no webfonts, no external requests (except App Store / GitHub links),
  images sized with explicit `width`/`height`.
- **Both color schemes.** All pages support light and dark via CSS
  `light-dark()`. The terminal visual is the one exception: it is always
  dark — that is the product.
- **Respect `prefers-reduced-motion`** for every animation.

## Design tokens (source of truth: docs/DESIGN.md)

- Terminal background: `#0D121A` (from the app's `TerminalBackground.swift`)
- Phosphor green accent: `light-dark(hsl(140, 65%, 30%), hsl(142, 70%, 55%))`
- Prose: `-apple-system` stack. Terminal/code accents: `ui-monospace` stack.

## Behavioral guidelines

Derived from [karpathy-guidelines](https://github.com/multica-ai/andrej-karpathy-skills).

1. **Think before coding.** State assumptions; if multiple interpretations
   exist, present them instead of picking silently. Push back when a simpler
   approach exists.
2. **Simplicity first.** Minimum code that solves the problem. No
   speculative features, no abstractions for single-use code. If a section
   can be plain HTML, it is plain HTML.
3. **Surgical changes.** Touch only what the task requires. Match existing
   style. Don't "improve" adjacent code; clean up only your own orphans.
4. **Goal-driven execution.** Define the success check before editing.
   For this repo that means: open the page in a browser and verify light
   mode, dark mode, mobile (375px) and desktop (1280px) before calling
   anything done.

## File map

```
index.html        Landing page
privacy.html      Privacy policy (App Store requirement)
css/main.css      All styles, one file
img/appicon/      App icon renditions (source: app repo AppIcon_V3.png)
docs/DESIGN.md    Design language spec — read before any visual change
docs/CONTENT.md   Copy guidelines and canonical strings
.github/          Issue/PR templates, SECURITY.md, Proof HTML workflow
```

Community files (LICENSE — MIT, CONTRIBUTING.md, CODE_OF_CONDUCT.md)
mirror the app repo; keep them in sync with it rather than diverging.

## Verify checklist (run before finishing any task)

1. `python3 -m http.server 8080` and open the changed page.
2. Check light + dark scheme, 375px + 1280px widths.
3. No horizontal scroll, no console errors, no external requests.
4. Links resolve (App Store link:
   <https://apps.apple.com/us/app/sudosodoku/id6779813086>).
