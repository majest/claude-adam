# Painted alien portraits

The game does not need these. It draws every alien in code and works fine that
way. This folder is for when the machine at home paints proper portraits, which
the cards will then use instead.

## What to produce

48 images, 16 per family, into this folder:

```
art/
  slime-01.png  …  slime-16.png
  mech-01.png   …  mech-16.png
  bug-01.png    …  bug-16.png
  index.json
```

`index.json` lists what actually exists, so a half-finished set still works:

```json
{
  "slime": ["slime-01.png", "slime-02.png"],
  "mech":  ["mech-01.png"],
  "bug":   []
}
```

The page reads `index.json` once when it is served over the web, then picks a
portrait per card from its family's list. A family with an empty list keeps the
code-drawn alien. Filenames must be letters, digits, hyphens and a
`.png`, `.jpg`, `.jpeg` or `.webp` ending, or they are ignored.

## Image requirements

- **Square, 512 x 512.** The card crops to fill, centred, so keep the creature
  inside the middle 80% and do not put anything important in the corners.
- **Under 150 KB each.** WebP at quality 80 gets there easily. All 48 together
  should stay under about 5 MB, because this repo is cloned by a web build on
  every push.
- **One creature, centred, facing the viewer**, full body or head and shoulders.
- **Dark space background** with stars or a distant planet. The card frame is
  dark purple, so a dark backdrop blends; a white or bright background will look
  like a sticker stuck on.
- **No text, no logos, no watermarks, no borders.** The card draws its own name
  and numbers over the top.
- **Nothing frightening.** These are for a child. Aim for the feel of a
  creature-collecting game: bold, characterful, a bit silly. No blood, no gore,
  no body horror, no realistic human faces.

## Prompts

Append this to every prompt:

> digital painting, creature concept art, centred full-body portrait, dramatic
> rim lighting, dark starfield background, rich colour, clean silhouette,
> trading-card art, highly detailed, no text, no watermark

### slime-01 … slime-16

> A friendly gelatinous alien blob creature, translucent wobbling body with
> light glowing through it, several large cartoon eyes at different heights,
> dripping goo, wide grin

Vary between images: colour (lime, teal, violet, amber, coral), one eye versus
five, eyes on stalks versus on the body, tall and thin versus wide and squat,
smooth versus bubbly.

### mech-01 … mech-16

> A boxy alien robot with heavy bevelled metal armour plates, a dark glowing
> visor across its face, a vent grille for a mouth, antennae, rivets, scratched
> and weathered paint

Vary: one lens versus three, brushed steel versus rusty orange versus white
enamel, chunky and heavy versus tall and thin, one antenna versus a cluster.

### bug-01 … bug-16

> A large alien beetle creature, iridescent segmented shell, jointed armoured
> legs, mandibles, compound eyes, translucent wings folded on its back

Vary: shell colour and iridescence (emerald, bronze, violet, ice blue), wings
open versus folded versus none, spikes along the back, long feelers versus short.

## Checking the result

Serve the project over http, not by double-clicking, or the lookup is skipped
on purpose. The browser console logs nothing on success; if a card still shows
a drawn alien, the family's list in `index.json` is empty or a filename is
misspelt.
