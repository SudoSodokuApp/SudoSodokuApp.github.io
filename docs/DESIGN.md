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
4. Screenshots — CSS scroll-snap strip, 640px JPEGs, lazy-loaded except
   the first. Two distinct layouts split at 640px:
   - **Mobile (≤640px)**: free-scrolling strip, no arrows, images at
     clamp(200–250px) — the original layout, touch/trackpad drag only.
   - **Desktop/tablet (>640px)**: exactly two screenshots visible at a
     time. The strip's width is the source of truth
     (`min(680px, 100vw - 7.5rem)`) and figure width is derived from it
     — `calc((100% - gap) / 2)` — so two cards + one gap always fill it
     exactly, no peek of a third. `box-sizing: border-box` on the img
     is load-bearing here: without it the 1px border adds on top of
     the 100% width and clips the second card by a couple pixels.
     Prev/next arrows page by exactly one card — the one deliberate JS
     exception on this page: a tiny inline script (`<html class="js">`
     toggle + `scrollBy` on click) enhances the strip, which is already
     fully usable via drag with JS off. The `.js` gate means the
     buttons don't render at all without JS, so there's no dead control
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
