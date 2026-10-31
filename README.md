# Where Are We? Ashland Elementary School

A find-the-teachers game for 4th and 5th graders. Live at https://waldo.ashlandthegame.com (GitHub Pages with a custom domain, set by the `CNAME` file and a GoDaddy CNAME record `waldo` pointing to `mrpiercey.github.io`).

- Players pick a scene on the title page: Ashland Elementary, Downtown Lexington, Kroger Field, Keeneland Race Course, the University of Kentucky, Gatton Park, Rupp Arena, Kenwick, The East End, or Bell Court. After finishing, they pick the next one.
- Each scene has its own Top 100 leaderboard in Firestore (project ashlandthegame, path `waldo/{scene}/top100`; reset on 2026-10-31, and the old Top 50 scores are still in `waldo/{scene}/scores`, visible only in the Firebase console). Only a top-100 time can be saved, and only as two capital letters (first and last initial). "FU" is blocked in the game and in `firestore.rules`. To block more combos, add them to `BLOCKED_INITIALS` in `index.html` and the list in `firestore.rules`, then run `firebase deploy --only firestore:rules`.
- To remove a score: `firebase firestore:delete waldo/<scene>/top100/<id> --project ashlandthegame` or delete it in the Firebase console.
- Every round hides the same 7 teachers (Piercey, Yoo, Laborio, White, Gaddis, Hill, Givan) plus Eddie the Eagle, 8 to find, in a fresh set of spots.
- One secret bonus visitor is also hidden each round, picked at random: Mr. Richards, Mr. Rampulla, Mrs. Lewis, or Mrs. Walker and Mrs. Todd (one cutout, so the principal and assistant principal always appear together). Players are not told who.
- Timer counts up. A hint zooms near a missing teacher and adds 15 seconds.
- Drag to pan, scroll / pinch to zoom, tap a teacher to find them. Green check appears on their card.
- Sound effects are synthesized in the browser. Background music is the SimCity 2000 (AdLib) soundtrack, split into 14 tracks in `music/` and played in shuffled order. The 🔊 button mutes music and effects together. Best time is saved in the browser.

## Deploying

The game is hosted two ways:

- **Firebase (for students, since GitHub is blocked):** https://waldoashland.web.app. Deploy with `firebase deploy --only hosting` from this folder. It goes to the `waldoashland` site in the Ashland The Game project. The original images in `images/` are not uploaded.
- **GitHub Pages:** https://waldo.ashlandthegame.com updates automatically on every push to `main`.

After a change, push to GitHub and run the Firebase deploy so both stay the same.

## Editing

Everything lives in `index.html`:

- `SCENES` lists each background. Each scene has its own hand-picked `spots` (`[x, y]` = where the feet go, in background pixels), a `size(y)` function for how tall people are drawn, and its max zoom. To add a scene, drop a WebP in `img/` and add an entry.
- `TEACHERS` / `BONUS` hold names, tile colors, and per-pose size tweaks.

## Music

Tracks in `music/` are mono Opus in WebM at 32 kbps (about 4.8 MB total). Only the current track is downloaded while playing. The list of tracks is `TRACKS` in `index.html`.

## Images

`img/` holds the compressed WebP files the game uses (about 2.2 MB total). The original PNG/JPEG sources in `images/`
are git-ignored. To rebuild the WebP files from the originals you need Python with Pillow and the `cwebp` CLI.
