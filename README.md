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
`#demo` starts tap-to-play mode without a camera. Both work for `games/shadow-puppets/` too.

## Shadow Puppets

Hands held in the projector beam throw a shadow on the bright stage; the camera reads that shape and matches it against six hand-shadow animals (rabbit, dog, bird, swan, deer, crocodile). When one matches and holds for a moment, that animal's short film plays.

- By default the game asks for one animal at a time. Untick *Ask for one animal at a time* under Adjust to let any animal play its film; that mode is pickier, and the bird and dog get mixed up more than the others.
- *Check camera aim* shows red dots where the camera sees shadow, plus each animal's live match score. Use it with the *Match needed* and *Sensitivity* sliders to tune for your room.
- The films are drawn live on the canvas. To use real clips instead, drop an mp4 named after the animal into `games/shadow-puppets/videos/` (`rabbit.mp4`, `dog.mp4`, `bird.mp4`, `swan.mp4`, `deer.mp4`, `crocodile.mp4`). Any clip that's there plays in place of the drawn film; the rest keep their drawn film.
- The camera line-up from Block Table is reused if Shadow Puppets hasn't saved its own yet.
- *Teach the animals* (in settings) learns your own shadows: it talks you through all six, two takes each, capturing each when it's held still. Taught animals are matched against your takes instead of the drawn shapes, and must also beat every other taught animal and plain hands (fist, flat hand, open hand), so waving doesn't count. Takes are kept in the browser on that phone; *Forget them* goes back to the drawn shapes.

## Table Tune-Up

A one-minute check of the rig, as six short scenes, ending in a report card.

It starts by helping aim the camera: four coloured targets sit at the corners of the area it measures, and each shows a tick when the camera sees it fully, `!` when it's cut off by the edge of the camera's view, or `?` when it can't be seen. The measuring starts by itself once all four have held a tick for about a second. The gear stops it.

1. **Lights on**: where the projected picture lands in the camera's view, whether any of it is cut off, blown out or washed out by room light. The camera's exposure, white balance and focus are locked here if the phone allows it.
2. **Lightning**: full-screen flashes time the delay from screen to camera (mirroring plus camera).
3. **Fireflies land**: the four-dot line-up, then a 7×5 grid of dots measures how far off it is, in screen pixels and as a share of a Block Table block edge.
4. **Rainbow**: grey steps and pure red, green and blue teach it how projected colours come out in the camera, so it can predict what the camera should see for any picture.
5. **Magic window**: a busy moving picture over the empty table checks that prediction and sets how big a difference counts.
6. **Firefly hands**: hands are whatever the prediction can't explain, so they're found even over a moving picture. Fingertips are points of the hand's outline far from the palm, and fireflies gather just past each one. Shadows are told apart from hands by getting almost none of the projector's light.

Tap the gear for the report card. *Copy results* copies every number as text. The last results, line-up and delay are saved under `tableTuneUp`.

Things learned building it, which apply to any game that reads hands:
- Anything drawn dark on a hand hides it: under dark light a hand looks just like the table. Draw on hands only with bright colours.
- Don't draw right on a fingertip, and don't move things fast near one: the camera can't predict fast movement exactly, and the blur can join the finger and pull the "tip" outward.

## Block Table: staying lined up

After the four-dot line-up, Block Table keeps tracking crisp edges (pad borders, outlines, coral) in a dozen patches across the table and fits how the whole picture slid, twisted or tilted, so a phone that gets bumped keeps working without a new line-up. Detection pauses while the picture is still moving. If it can't find its place for about five seconds, it runs the four-dot line-up again by itself.
