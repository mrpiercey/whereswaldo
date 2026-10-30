# Where's Waldo? Ashland Elementary Edition

A find-the-teachers game for 4th and 5th graders. Open `index.html` (or host it on GitHub Pages).

- Every round hides the same 7 teachers (Piercey, Yoo, Laborio, White, Gaddis, Hill, Givan) in a fresh set of spots.
- One secret bonus character (Mr. Richards, Mr. Rampulla, or Eddie the Eagle) is also hidden each round. Players aren't told who.
- Timer counts up. A hint zooms near a missing teacher and adds 15 seconds.
- Drag to pan, scroll / pinch to zoom, tap a teacher to find them. Green check appears on their card.
- Sound effects are synthesized in the browser. Background music is the SimCity 2000 (AdLib) soundtrack, split into 14 tracks in `music/` and played in shuffled order. The 🔊 button mutes music and effects together. Best time is saved in the browser.

## Editing

Everything lives in `index.html`:

- `SPOTS` is the list of hand-picked hiding places (`[x, y]` = where the feet go, in pixels of the 6300x3600 background). Add or remove spots there.
- `standingHeight(y)` controls how big people are drawn (bigger lower in the picture).
- `TEACHERS` / `BONUS` hold names, tile colors, and per-pose size tweaks.

## Music

Tracks in `music/` are mono Opus in WebM at 32 kbps (about 4.8 MB total). Only the current track is downloaded while playing. The list of tracks is `TRACKS` in `index.html`.

## Images

`img/` holds the compressed WebP files the game uses (about 2.2 MB total). The original PNG/JPEG sources in `images/`
are git-ignored. To rebuild the WebP files from the originals you need Python with Pillow and the `cwebp` CLI.
