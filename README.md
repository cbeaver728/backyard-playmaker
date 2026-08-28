# Backyard Playmaker

A huddle app for backyard football at my parents' house. The background is the
actual satellite photo of the yard, rotated so play runs up the screen toward the
swing set. Draw your route with a finger, mark where you want the ball, show it to
whoever is playing quarterback.

## Using it

**Calling a play**

- **Draw** — drag on the field. Thin line, arrow on the end.
- **Colours** — white / yellow / blue for receivers, red for whoever is on defense.
- **🏈 football target** — tap the button, then tap the field: *throw it to this spot.*
- **⚡ lightning bolt** — tap the button, then tap the field: *let it go when I hit
  here.* Use it on the break in your route so the throw is already in the air.
- Both markers snap onto a nearby route, so you can pin the exact point of a break.
- **↶** undoes the last route or marker. **✕** wipes the play for the next huddle.
- **Moving the QB** — press and hold the QB puck until it lifts, then drag. He does
  not have to stay in the middle, and you can walk him upfield as you gain yardage.
  The dashed line of scrimmage follows him. A normal drag starting on the puck draws
  a route as usual, so the two never fight.

**Editing the map** (✎, top right)

Place reference markers along the sidelines so the QB has something to aim off:
bush, small tree, medium tree, large tree. Tap an empty spot to drop the selected
icon, tap an existing one to select it, drag to move, 🗑 to delete, DONE to go back.

The garden changes from year to year, so the map is yours to keep current. The
layout is saved on the phone *and* mirrored into the page URL — copy the address
bar and text it to someone and their phone gets the same map.

**Odds and ends**

- The play and the map are saved locally, so they survive the screen locking or the
  app being backgrounded mid-drive.
- The screen is kept awake while the app is open (needs HTTPS — use the Pages URL,
  not a local file).
- Add it to the home screen and it opens full screen with no browser chrome.

## How the field works

`field.jpg` is the satellite image rotated 90° counter-clockwise and cropped to the
yard, so:

- Play always goes **toward the swing set** — up the screen.
- **Left** is north: the tree line and the hedge.
- **Right** is south: the gravel path, the beds, the deck and house.
- **Behind the QB** is the concrete walk and the garden.
- The **end zone** is the bark bed under the swing set plus the grass beside it. The
  goal line is drawn on the bed's near edge, about 20 yards out, with faint 5 / 10 /
  15 yard references between there and the near end.

Everything the app stores — routes, markers, the QB, the map icons — is in
**normalised image coordinates** (0..1 across `field.jpg`). Nothing is in screen
pixels, so it all stays glued to the yard through rotation and resize, and it
survives dropping in a newer photo of the same crop.

To re-crop from a fresh satellite image, rotate it the same way and match the
existing framing, then check the four landmark constants in `F` near the top of the
script (`back`, `goal`, `near`, `left`, `right`) — they are fractions of the image
and are what the goal line and yard markers are drawn from.

## Deploying

Push to `main`. The Pages workflow publishes `index.html`, `field.jpg`,
`manifest.webmanifest` and `icon.svg`.
