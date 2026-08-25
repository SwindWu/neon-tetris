# NEON TETRIS

A modern, **guideline-compliant** Tetris that runs entirely in your browser — no build step, no dependencies. Open `index.html` and play.

![screenshot placeholder]

## Modern mechanics (Tetris Guideline)

- **SRS rotation** — Super Rotation System with full wall-kick data for I, J, L, S, T, Z (O is pure rotation).
- **7-bag randomizer** — every 7 pieces contain each tetromino exactly once, shuffled.
- **Hold piece** — store a piece and swap it back in later (one at a time).
- **Ghost piece** — translucent outline showing where the piece will land (toggleable).
- **Lock delay with move reset** — 500 ms before a grounded piece locks; move/rotate to "wiggle" it (capped at 15 resets).
- **DAS / ARR** — hold an arrow to slide the piece smoothly (150 ms delay, 40 ms auto-repeat).
- **T-Spins (3-corner rule)** — full and **mini** T-spin detection, with singles/doubles/triples.
- **Back-to-Back (B2B)** — ×1.5 for consecutive Tetrises / T-spin line clears.
- **Combos** — bonus for clearing lines on consecutive pieces.
- **Perfect Clear** — bonus for emptying the whole field.
- **Next queue (5 previews)** and **level-based gravity curve**.

## Modes

- **Endless** — level up every 10 lines, gravity increases.
- **Sprint 40** — clear 40 lines to finish.
- **Ultra 150** — clear 150 lines to finish.

## Controls

| Key | Action |
| --- | --- |
| ← / → | Move (hold to slide — DAS/ARR) |
| ↓ | Soft drop |
| Space | Hard drop |
| ↑ / X | Rotate clockwise |
| Z | Rotate counter-clockwise |
| C / Shift | Hold |
| P / Esc | Pause |

Touch controls appear automatically on small screens.

## The fun

- **Neon / synthwave aesthetic** — glowing blocks, animated starfield, glassmorphism panels.
- **Juicy feedback** — particle bursts on line clears, screen shake on Tetrises, hard-drop flash, floating score popups.
- **Procedural audio (Web Audio API)** — a generative synthwave loop plus SFX for every action (move, rotate, hold, drop, clear, T-spin, level-up, perfect clear, game over). No audio files — all synthesized live.
- **Best score** saved to `localStorage`.

## Run it

Just open `index.html` in any modern browser.

For local serving (optional):

```bash
# any static server works, e.g.
python3 -m http.server 8000
# then visit http://localhost:8000
```

Or enable **GitHub Pages** (Settings → Pages → Deploy from branch `main` / root) and play it online.

## Tech

- Single self-contained `index.html` (HTML + CSS + vanilla JS).
- Canvas 2D for the board, FX, and mini-piece previews.
- Web Audio API for all sound and music.
