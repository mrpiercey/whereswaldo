# Where's Waldo? Ashland Elementary Edition

A find-the-teachers game for 4th and 5th graders. Open `index.html` (or host it on GitHub Pages).

- Every round hides the same 7 teachers (Piercey, Yoo, Laborio, White, Gaddis, Hill, Givan) in a fresh set of spots.
- One secret bonus character (Mr. Richards, Mr. Rampulla, or Eddie the Eagle) is also hidden each round. Players aren't told who.
- Timer counts up. A hint zooms near a missing teacher and adds 15 seconds.
- Drag to pan, scroll / pinch to zoom, tap a teacher to find them. Green check appears on their card.
- Sounds are synthesized in the browser (no audio files). Best time is saved in the browser.

## Editing

Everything lives in `index.html`:

- `SPOTS` is the list of hand-picked hiding places (`[x, y]` = where the feet go, in pixels of the 6300x3600 background). Add or remove spots there.
- `standingHeight(y)` controls how big people are drawn (bigger lower in the picture).
- `TEACHERS` / `BONUS` hold names, tile colors, and per-pose size tweaks.

## Images

`img/` holds the compressed WebP files the game uses (about 2.2 MB total). The original PNG/JPEG sources in `images/`
are git-ignored. To rebuild the WebP files from the originals you need Python with Pillow and the `cwebp` CLI.
