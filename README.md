# Play Table

Projector games played with real blocks on a table, watched by a phone camera.
Live at https://dataskier.github.io/block-table/

## Layout

- `index.html` — the games menu. Every game is one entry in its `GAMES` list.
- `games/<name>/index.html` — each game, self-contained in its own folder, with a `cover.jpg` for the menu.

## Adding a game

1. Put the game in a new folder under `games/`, with a 16:9 `cover.jpg`.
2. Add an entry to `GAMES` in `index.html` (name, path, cover, blurb, chips).
3. In the game, link back to the menu with `href="../../"`.

Games run from https (GitHub Pages) because phone browsers only allow the camera on secure pages.
Games on this site share one origin, so anything a game saves in the browser (settings, the camera line-up) should use a key named after that game.

## Running a game on a fixed rig

Open `games/block-table/#kiosk` to start by itself and reuse the saved camera line-up.
`#demo` starts tap-to-play mode without a camera.
