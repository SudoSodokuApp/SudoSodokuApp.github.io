# Content Guidelines

Copy is written in the app's voice: terse, technical, a little deadpan.
The joke is always played straight — the site never winks at the reader.

## Canonical strings

Use these exactly; do not paraphrase:

- Name: `SudoSodoku` (one word, camel-case S's; never "Sudo Sodoku")
- Tagline: **`sudo solve` — root access for logical purists.**
- Victory line: `ACCESS GRANTED`
- Prompt: `root@ios:~$`
- Rank ladder: `SCRIPT_KIDDIE → USER → SUDOER → SYS_ADMIN → KERNEL_HACKER → THE_ARCHITECT`
- Difficulty flags: `--easy` `--medium` `--hard` `--master`
- Platform line: iPhone · iOS 17.0+ · v2.0.0

## Product facts (keep the site honest)

- No ads, no lives, no pay-to-win, no fail state. Timer optional.
- Real-time procedural generation; every puzzle has a unique solution and
  a logical-solver difficulty score (0–100). Never a canned database.
- ELO from 1200, adaptive K-factor, anti-smurfing. Game Center
  leaderboards + 11 achievements (one secret). Fully playable offline.
- Everything stays on device: single local JSON file, atomic writes.
  Game Center is optional. (This drives privacy.html.)
- v1 was released on GitHub only; v2.0.0 is the App Store debut.
- Free and open source: MIT License, © 2026 Kai Chen. No third-party
  dependencies (pure Apple frameworks), so there is nothing to credit
  beyond the license itself. Footer format:
  `© 2026 Kai Chen · MIT License · Privacy`.

## Status

Until launch: the download button says "Coming soon to the App Store" and
carries the `TODO(app-store-url)` marker. Swap in the real badge + URL on
launch day.
