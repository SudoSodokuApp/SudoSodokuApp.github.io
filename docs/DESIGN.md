# Design Language

The site sits at the intersection of two identities:

1. **Apple-minimal** (the CotEditor model): white/near-black page, system
   fonts, generous whitespace, centered single column, content-first.
2. **The app's terminal fantasy**: phosphor green on deep dark glass,
   all-monospace, `root@ios:~$` command lines, `ACCESS GRANTED`.

Rule of thumb: **the page is Apple; the product shots are terminal.**
The page chrome (nav, headings, prose, footer) stays quiet and neutral.
The green and the monospace appear only where the product itself shows
through — the hero terminal window, command-line snippets, accents.
If the whole page turns green-on-black, we've lost the plot.

## Tokens

| Token | Value | Notes |
| --- | --- | --- |
| `--background` | `light-dark(white, hsl(216, 33%, 7%))` | dark ≈ app's `#0D121A` family |
| `--text` | `light-dark(hsla(0,0%,0%,.85), hsla(0,0%,100%,.9))` | |
| `--secondary-text` | `light-dark(hsla(0,0%,0%,.6), hsla(0,0%,100%,.62))` | |
| `--separator` | `light-dark(hsla(0,0%,0%,.1), hsla(0,0%,100%,.12))` | |
| `--accent` | `light-dark(hsl(140,65%,30%), hsl(142,70%,55%))` | phosphor green, contrast-safe per scheme |
| `--terminal-bg` | `#0D121A` | fixed; from `TerminalBackground.swift` |
| `--terminal-green` | `hsl(142, 70%, 55%)` | fixed; on terminal-bg only |

## Typography

- Prose: `-apple-system, BlinkMacSystemFont, 'SF Pro', 'Helvetica Neue', sans-serif`
- Terminal/code: `ui-monospace, 'SF Mono', 'Menlo', monospace`
- Scale: hero `h1` is the app name in monospace (it's a command, after all);
  everything else follows CotEditor's quiet sizing — body ~1rem/1.6.

## Layout

Single centered column, `max-width` ~ 60rem for grids, ~40rem for prose.
Section order on the landing page (mirrors coteditor.com):

1. Hero — app icon, name, one-line tagline, App Store badge
2. Terminal window — the product visual (CSS-drawn, no image)
3. Lead line — one sentence, large, secondary color
4. Highlights — 3 cards: why this app
5. Features — 2–3 column grid of short feature cards
6. Feedback / GitHub section
7. Footer — copyright

## Motion

- One blinking cursor in the terminal window; subtle, 1s steps.
- Everything else static. Any future animation must respect
  `prefers-reduced-motion: reduce` (the app itself honors Reduce Motion —
  the site must too).

## Don'ts

- No webfonts, no icon fonts, no CSS frameworks.
- No green body text outside terminal surfaces.
- No stock imagery, no gradients-for-gradients'-sake.
- No layout shift: images always get `width`/`height` attributes.
