# Painted alien portraits

These exist now. All 48 are in this folder, and the game uses them.

The game does not depend on them. Every alien is still drawn in code, and that
drawing is what you see for any family whose list is empty.

## What is here

```
art/
  slime-01.webp  …  slime-16.webp
  mech-01.webp   …  mech-16.webp
  bug-01.webp    …  bug-16.webp
  index.json
```

They are `.webp` rather than `.png`. The same picture as a PNG is about ten
times bigger, and this repo is cloned by the web build on every push. All 48
together come to 1.2 MB, and the largest single file is 42 KB.

`index.json` is written by the machine, not by hand. It lists what actually
exists, so a half-finished set still works:

```json
{ "kind": "images",
  "generated": "…",
  "items":  [ { "id": "slime-01", "file": "slime-01.webp" } ],
  "groups": { "slime": ["slime-01.webp"], "mech": [], "bug": [] } }
```

The page reads the three lists out of `groups`, picks one picture per card from
that card's family, and keeps the code-drawn alien for any family with an empty
list. It also accepts the three lists at the top level, so an index written by
hand still works. Filenames must be letters, digits and hyphens with a `.png`,
`.jpg`, `.jpeg` or `.webp` ending, or they are ignored.

## The request

`../ai/request.json` is what the machine reads. It holds all 48 prompts, one
per picture, with a fixed seed each — so running it again makes the same
pictures rather than new ones. Delete a file and ask again to replace just that
one.

Two things in it are worth knowing before editing a prompt.

- **Prompts have to be short.** The picture maker stops reading after about 60
  words and silently ignores the rest. The first set was written long, and the
  words naming the background fell off the end, so half the aliens came out
  standing in a desert instead of in space. Every prompt is now checked to fit.
- **`guidance` is not zero.** Zero is the usual setting here, but it switches
  the "don't draw this" list off completely, and the paintings came back with a
  painted signature scrawled in the corner. A little guidance turns that list
  back on. Much more than a little makes the paintings flat and harsh.

## What to put in a prompt

Say the creature, then say how this one differs from the others in its family,
then the style. The style ending used for all 48:

> full body, centred, dark starfield background, rich colour, clean silhouette,
> creature concept art, digital painting

Do not write "no text" into the prompt itself. It does not work that way round
and tends to produce text. Text goes on the "don't draw this" list instead.

## What these have to look like

- **Square, 512 x 512.** The card crops to fill, centred, so keep the creature
  inside the middle 80% and nothing important in the corners.
- **Under 150 KB each**, and the whole set under about 5 MB.
- **One creature, centred, facing the viewer**, full body or head and shoulders.
- **Dark space background** with stars or a distant planet. The card frame is
  dark purple, so a dark backdrop blends; a white or bright background looks
  like a sticker stuck on.
- **No text, no logos, no watermarks, no borders.** The card draws its own name
  and numbers over the top.
- **Nothing frightening.** These are for a child. Bold, characterful, a bit
  silly. No blood, no gore, no body horror, no realistic human faces, and
  nobody holding a weapon.

## Not perfect

A few of the mechs have a faint scribble along the very bottom edge, where the
picture maker has imitated an artist signing their work. It is a few pixels
tall, it is not readable, and the card crops most of it away — but it is there,
and the rule above says there should be no text at all.

Getting rid of it by trying different seeds does not work: a new seed drops one
scribble and adds another somewhere else, and twice it produced a robot holding
a gun, which is worse. The reliable fix is to trim a few percent off every edge
after the picture is made, which is a change to the machine rather than to this
game. That is Artur's to decide.

## Checking the result

Serve the project over http, not by double-clicking, or the lookup is skipped
on purpose:

```sh
python3 -m http.server 8000
```

If a card still shows a drawn alien, that family's list in `index.json` is
empty or a filename is misspelt.
