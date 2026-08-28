# Backyard Playmaker

A huddle app for backyard football at my parents' house. The screen is a map of the
actual backyard seen from the quarterback's end, looking downfield toward the swing
set. Draw your route with a finger, drop a sticker where you want the ball, show it
to whoever is playing QB.

## Using it

- **Draw** — drag on the field. Thin line, arrow on the end.
- **Colours** — white / yellow / blue for receivers, red for whoever is playing defense.
- **🏈** — tap the button, then tap the field to drop the throw marker. It snaps onto a
  route if you tap near one, so you can mark the exact spot on your break.
- **↶** — undo the last route or marker. **✕** — wipe the play for the next huddle.
- The play is saved in the browser, so it survives the screen locking or the app
  being backgrounded mid-drive.
- The screen is kept awake while the app is open (needs HTTPS, so use the Pages URL,
  not a local file).

Add it to the home screen on your phone and it opens full screen with no browser
chrome.

## The field

Everything is drawn from a model of the real yard in feet, then run through a
projective transform so it looks like you are standing behind the near end zone,
very high up, facing the swing set. Straight lines stay straight, so the geometry
is consistent — a route drawn parallel to the tree line really is parallel to it.

Orientation, taken from the satellite image:

- Play always goes **toward the swing set** — up the screen.
- **Left** of the screen is north: the big shade tree, the hedge wall, the arborvitae.
- **Right** of the screen is south: the rock border, the gravel path, the beds, the deck.
- **Behind you** is the concrete walk and the garden.
- The **end zone** is the bark bed under the swing set plus the grass to its right,
  starting at the goal line about 20 yards out.

The yard is modelled at roughly 83 ft long by 42 ft wide. Landmark positions live in
`index.html` in the `LAWN` / `MULCH` arrays and the `buildField()` function, all in
feet — if something is in the wrong spot, nudge the numbers there.

## Deploying

Push to `main`. The Pages workflow publishes `index.html`, `manifest.webmanifest`
and `icon.svg`.
