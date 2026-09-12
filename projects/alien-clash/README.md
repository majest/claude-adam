# Alien Clash

A card game for 2 to 4 players sharing one screen. Every alien is invented the
second you flip it, so nobody has seen your cards before you do.

## How to play

1. Choose how many of you are playing, and a **Quick** game (5 cards each) or a
   **Long** one (10 cards each). Every card in the deck is then shown to you.
2. The screen says whose turn it is. That player looks at their top card and
   everyone else looks away.
3. That player picks a power: **Power**, **Speed**, **Brains** or **Armour**.
4. Everyone's top card flips over at once. The biggest number in that power wins
   every card on the table.
5. Two players tie on the same number? Those cards wait in the middle, and
   whoever wins the next round takes those as well.
6. Run out of cards and you are out. The player with the biggest pile at the end
   wins.

The 🔊 button in the corner turns the noises on and off.

## What is in a card

Each card is built from a number called its seed. The same seed always makes the
same alien, which is why the artwork and the name and the stats always match.

- **Three families.** Slimes are wobbly blobs with drips and eyes on stalks.
  Mechs are metal plates with a visor, a grille and antennae. Bugs have a
  segmented shell, jointed legs, mandibles and see-through wings.
- **Nothing is a picture file.** Every alien is drawn with code onto a canvas,
  along with its own starfield and nebula. That is why the game weighs almost
  nothing and works with no internet.
- **Rarity** runs Common, Rare, Epic, Legendary. Rarer cards get a bigger pile
  of points to share between their four powers, and Epic and above shimmer.
- **One boss** hides in every single deck. Gold frame, scary name, huge numbers.
  You will know when it turns up.

## The noises

There are no sound files, because a project here cannot fetch anything from the
internet. Every noise is built in code with the Web Audio API: slimes squelch
(a sine wave falling from 430 Hz to 80 Hz with a burst of filtered noise), mechs
beep two square notes, bugs chirp three rising ticks, and the boss growls a low
sawtooth. Winning plays a little arpeggio.

## Still to decide

Adam asked for a Hearthstone-style version. Two questions were open when the
last session ended, and the answers change what gets built, so nothing has been
started:

1. **Keep this game and add the new one beside it, or replace this one?**
   Adding is safer. Nothing that already works gets lost, and the title screen
   picks which to play.
2. **Two computers, or one screen?** Two computers is possible now. The move
   service in `BUILDING.md` is turn-based, which suits a card game, and it has
   been checked from a cloud session. One screen is simpler and needs no
   internet at all.

A Hearthstone-style game means cards held in a hand, a mana cost that grows
each turn, creatures placed on a board that fight, and a health total that ends
the game when it reaches zero. That is a new game rather than a change to this
one, which is why it would live alongside.

Also waiting: the painted portraits in `art/PROMPTS.md`. They need a session on
Artur's own computer, because the machine that paints them is not reachable
from anywhere else, and Artur has to agree to the size first.

## Seeing every card

After the cards are dealt the whole deck is laid out, boss first, so you can see
what is in play before anyone takes a turn. Tap **Start playing** to begin.

## Painted portraits from the AI machine

Aliens are drawn in code, which is why they are cartoons rather than paintings.
If the machine at home paints real portraits into `art/` with an `index.json`
listing them, each card shows a painting instead and falls back to the drawn
alien for any family that has none. The full spec and the prompts are in
`art/PROMPTS.md`.

## Extra words from the AI machine

The game is complete as it stands and needs nothing else. But if a file called
`aliens.json` is sitting next to `index.html` when the page is served, the game
will read it once and use the words inside it instead of its built-in lists:

```json
{
  "names":     ["Zorblax", "Gnarvex"],
  "bossNames": ["Skullgrax"],
  "titles":  { "slime": ["Elder Ooze"], "mech": ["Doom Engine"], "bug": ["Hive Emperor"] },
  "flavour": { "slime": ["Dissolves spoons."], "mech": ["Needs oiling."], "bug": ["Has eleven knees."] }
}
```

Every field is optional. Names are capped at 14 characters, boss names at 16,
titles at 20 and flavour lines at 60, so a long one cannot break the card
layout. Anything that is not a list of text is ignored.

There is a word-making model that runs in the browser, and this project
deliberately does not use it. It is 81 MB and it rambles, which is fine for a
silly sentence and wrong for a card that has to read well every time. Names and
flavour lines are better made once, in advance, and kept.

This is the only place the project expects help from a model, and it happens
**ahead of time, somewhere else**. The page itself never calls a server: it
reads a plain file that is already there. Opened by double-clicking, the page
skips the read entirely and plays with its built-in words.
