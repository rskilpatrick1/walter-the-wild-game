# Walter the Wild: Run Home

A 3D running game based on *Walter the Wild*, for kids ages 5 to 9. Walter runs
through the woods toward home, following the bear tracks that Major's stardust made
glow. He dodges rocks, stumps and thorn bushes, jumps logs and streams, ducks
branches, and collects bear tracks and stars on the way. Friends from the book drop
in along the trail. The run ends at his house, where Mom and Dad are waiting.

## How to play

**Play online:** https://rskilpatrick1.github.io/walter-the-wild-game/

Or download it and double-click `index.html`. It needs an internet connection the first time, to
download its 3D engine (Three.js).

| Key | What it does |
| :-- | :----------- |
| Left / Right (or A / D) | Hop between the three lanes. Near a corner, they turn instead. |
| Up (or W, Space) | Jump over logs and streams (and grab the stars above them) |
| Down (or S) | Duck under low branches |
| P | Pause |
| M | All sound on or off |
| N | Music on or off |

On a tablet: swipe left, right, up or down. A tap jumps.

You can't lose. Hitting something makes Walter stumble: he slows down, drops 3 bear
tracks, and blinks for a moment while nothing can trip him again. Missing a turn
bumps him into the bushes, then he turns anyway. At forks, the wrong way has glowing
coyote eyes in the brambles. A clean run takes about 1 minute 35 seconds.

## Friends along the way (in the book's order)

| Who | What happens |
| :-- | :----------- |
| Polly | Swoops in beside Walter, whir-whir-whirs, and tells him to follow the tracks |
| The Great Wolf Owl | Hoots from up ahead, then dives at Walter. "Duck!" flashes on screen. Press Down any time after that and Walter stays crouched until the owl has passed. |
| Major | Stands at the trail's edge waving, hums, and leaves a line of stars |
| The coyote | Chases Walter for a few seconds. A drum joins the music, and Walter runs faster. Then it gives up and howls. |
| The cat | Trots ahead of Walter for a while, then darts back into the woods |
| Polly | Comes back near the end: "I can see your house!" |

Every run is a new route. The best score is saved in the browser.

## Changing things

Everything is in `index.html`. The numbers that set how hard it is are the
KNOBS at the top of the script: speed, jump height, duck time, how many trail
segments a run has, how many tracks a stumble costs, and the chase speed boost.

- `makeRoute()` plans the whole trail: straight segments joined by left and right turns.
- `fillSegment()` decides where the obstacles, bear tracks and stars go. The `gap`
  line sets how close together obstacles are.
- `buildSegment()` builds the 3D world for one segment. Only a few are built at a
  time, just ahead of Walter.
- `CAMEOS` lists when each friend appears and what they say. `ACTORS` says how each
  one moves.
- `MELODY`, `ROOTS` and `CHORDS` are the music, written as note numbers (60 is
  middle C). It's in E minor with a heartbeat and a ticking pulse, for suspense.
  `SFX` holds every sound effect.
- Characters are built from body parts hung on joints (hip, knee, ankle, shoulder,
  elbow). `makePerson()` builds Walter, Mom and Dad; the kid and grown-up versions
  differ in proportions. `poseWalter()` sets his joints for running, jumping,
  ducking and stumbling.
- `lumpy()`, `capsule()` and `lathe()` are the sculpting helpers that turn simple
  shapes into rounded, natural ones.
- `bearPrint()` draws the paw prints, and the sky colors are in the `sky` shader.

## Testing in the Claude browser pane

Use the `walter` server in `.claude/launch.json` and open
`http://localhost:8797/`. The pane's file:// view can't download
Three.js.
