# Understory

A seeded procedural forest, rendered to a canvas. One self-contained file — open
`index.html` in a browser, no build step, no dependencies, no network calls except
the webfonts.

Every scene is generated from a readable seed like `alder-hollow` or `rowan-spinney-41`.
The same seed always grows the same forest.

## Controls

| Control | What it does |
| --- | --- |
| **Seed** | Type any string, or press the shuffle button for a new one. |
| **Season** | Spring, Summer, Autumn, Winter — foliage palette, blossom, bare limbs, snow. |
| **Light** | Dawn, Noon, Dusk, Night — sky, sun or moon, key/ambient colour, exposure, god rays. |
| **Stand** | Temperate, Boreal, Wetland — the species mix drawn from. |
| **Density** | How many of each band's planned stems actually grow. |
| **Regrow** / <kbd>R</kbd> | New seed. |
| **Export** / <kbd>E</kbd> | Opens the current frame full-resolution; right-click or long-press to save. |

## How it works

The renderer runs in three passes.

**1. Plan.** `buildPlan(seed)` derives the forest's skeleton from the seed alone: seven
depth bands, each with a pool of stems (normalised x, size, species roll, per-tree
sub-seed) plus an undergrowth pool, three midpoint-displaced ridgelines, and cloud
positions. Because the plan depends on nothing but the seed, changing season, light,
stand or density repaints the *same* forest rather than uprooting it — and nudging
density adds or removes stems from the end of each pool instead of reshuffling.

**2. Paint.** `renderScene` walks the plan back to front: sky gradient → sun or moon
with halo (stars and lunar maria at night) → ridgelines with a fringe of stems on the
near crest → ground gradient → litter → seven bands of trees and undergrowth, each
followed by a thin mist wash → light shafts → grain and vignette.

Depth is carried by three things working together: bands sit lower and taller as they
approach (`baseY` and height both ease with `u^1.45`–`u^1.5`), every colour is mixed
toward the phase's fog colour by that band's fog weight, and a translucent wash lands
between bands. Level of detail drops with size — a stem under 4.5% of frame height is
drawn as a silhouette, so a hundred distant trees stay cheap.

Colour runs through one function, `tone(env, colour, fog, lit)`: mix toward the phase's
ambient, mix toward the key light (or multiply down for shadow sides), scale by
exposure, then mix toward fog. Season supplies the hue, light supplies everything else.

**3. Drift.** The static scene is painted once to an offscreen canvas and blitted each
frame; only the drift layer animates — mist wisps always, plus petals, dust motes,
falling leaves or snow by season, and fireflies at dusk and night. Honoured
`prefers-reduced-motion` renders a single frame and stops.

## Species

Six growth habits, mixed by stand type:

- **oak** — recursive limbs, three-way trunk split, broad dappled crown
- **birch** — slender pale trunk with dark chevrons, narrow airy crown
- **spruce** — layered jagged boughs, snow-capped in winter
- **willow** — low heavy limbs with long beaded strands hanging from every tip
- **snag** — a bare standing dead tree, no foliage at any season
- **scrub** — low multi-stemmed shrub

Undergrowth is drawn from ferns, grass tufts, rocks, ground shrubs, fallen logs and
mushrooms, weighted so tufts dominate and logs are rare.

## Structure

Everything lives in `index.html`, in five ordered script blocks: seeded RNG and colour
maths; palettes; plan and species; undergrowth and backdrop; scene, drift and app.
