# Design Language

The site sits at the intersection of two identities:

1. **Apple's design principles**: white/near-black page, system fonts,
   generous whitespace, centered single column, content-first.
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
- Scale: `html { font-size: 110% }` sets the global type scale — all
  rem-based sizes and max-widths grow together, so tune sizes in rem and
  the scale in that one place. Hero `h1` is the app name in monospace
  (it's a command, after all); body is 1rem/1.6 on that scale.

## Layout

Single centered column, `max-width` ~ 60rem for grids, ~40rem for prose.
Section order on the landing page:

1. Hero — app icon, name, one-line tagline, App Store badge
2. Terminal window — the product visual (CSS-drawn, no image)
3. Lead line — one sentence, large, secondary color
4. Screenshots — CSS scroll-snap strip, no JS; 640px JPEGs, lazy-loaded
   except the first; each thumbnail opens a lightbox (pure CSS `:target`,
   no JS) showing the same image larger, closable via the × button,
   clicking the image, or clicking the backdrop
5. Highlights — the four philosophy pillars
6. Features — 2–3 column grid of short feature cards
7. Feedback / GitHub section
8. Footer — copyright

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
