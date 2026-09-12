# Alien Clash

Put aliens on the table, spend energy to bring out bigger ones, and knock the
other player from 30 life down to nothing. Every alien is invented the moment
you see it, so nobody has played with these cards before.

Two ways to play:

- **One screen.** Pass it over when it is the other player's turn. Works with
  no internet at all.
- **Two computers.** You both type the same room name and play at the same
  time. This one needs the website rather than the file.

## How to play

1. You and the other player start with 30 life each. Knock theirs to zero.
2. Every turn you get one more energy. The blue number on a card is its cost,
   so the big aliens can only come out later.
3. Tap a card in your hand to put that alien on the table. Five fit at once.
4. Tap your alien, then tap an alien to fight, or tap the other player to hit
   them directly.
5. The yellow number is how hard it hits. The red number is how much life it
   has left. Whatever you attack hits you back, so trading is a real decision.
6. A new alien needs a rest and cannot fight the turn it arrives, unless it
   has ⚡.
7. ✨ means you get an extra card the moment it lands.
8. Run out of cards in your deck and you start losing life instead of drawing.
   The decks are deep enough that this rarely decides a game.

The 🔊 button in the corner turns the noises on and off.

## What is in a card

Each card is built from a number called its seed. The same seed always makes
the same alien, which is why the picture and the name and the numbers always
match.

The fighting numbers are read off the four stats the aliens already had, so a
card that used to be good at Power hits hard, and a card that used to be good
at Armour survives:

| On the card | Comes from |
| --- | --- |
| Cost | the whole budget, so rarer aliens cost more |
| How hard it hits | Power |
| How much life | Armour |
| ⚡ fights straight away | Speed 60 or more |
| ✨ gives you a card | Brains 60 or more |

- **Three families.** Slimes are wobbly blobs with drips and eyes on stalks.
  Mechs are metal plates with a visor, a grille and antennae. Bugs have a
  segmented shell, jointed legs, mandibles and see-through wings.
- **Rarity** runs Common, Rare, Epic, Legendary. Rarer aliens get a bigger
  pile of points to share out, so they cost more and hit harder.
- **One boss** hides in each player's deck. Gold frame, scary name, huge
  numbers, and it costs nearly all your energy.

## Two computers, without either one being in charge

Both pages build **the same decks from the room name**, so no cards are ever
sent anywhere. After that they swap only *moves* through the rooms service and
replay them in the same order. Same start, plus the same moves in the same
order, means the same game on both screens.

That is why there is no host and nothing to go out of sync. A move is only
applied when it comes back from the service, never the instant it is tapped,
because otherwise the two sides could end up ordering them differently.

Anything sent through the service is readable by anyone who knows the room
name, so only moves go through it. Never a name, never anything private. The
polling stops the moment the page is hidden or the game ends.

## How it was balanced

By playing it 40 games at a time with a robot, not by guessing.

- At 20 cards a deck, the loser was simply **running out of cards** in 25 games
  out of 40, which is a miserable way to lose. The decks are now deeper than a
  game is long.
- At 22 life, a game where both players just charge straight at each other was
  **over in 7 turns**, and whoever went first won 7 times in 10. Life stayed at
  30.
- Going second is a real disadvantage, because the other player hits first
  every single round. The second player now gets **one extra energy on their
  first turn**, which took the split from 31–9 to 26–34.

## The noises

There are no sound files, because a project here cannot fetch anything from
the internet. Every noise is built in code with the Web Audio API.

The fighting noises are layered on purpose: a sharp crack on top so the hit
feels immediate, a low thud underneath so it feels heavy, and a tail of rubble
so it does not stop dead. A hit of 7 or more gets more of all three. Hitting
the player directly is bigger again: an incoming whoosh, then a boom, then
dust. Slimes still squelch, mechs beep and bugs chirp when they land.

## Painted portraits

Every card shows a painted portrait, 48 of them, made on the machine at home
and saved into `art/`. The card picks one from its own family.

The drawn aliens are still there underneath. `art/index.json` lists what
exists, and any family with an empty list goes back to being drawn in code, so
deleting the pictures breaks nothing. Opened from the file rather than a web
address, the game skips the lookup and draws everything.

What they had to look like, what is in the request, and the one thing that is
not perfect about them are all in `art/PROMPTS.md`.

## Extra words from the AI machine

If a file called `aliens.json` is sitting next to `index.html` when the page is
served, the game reads it once and uses the words inside it instead of its
built-in lists:

```json
{
  "names":     ["Zorblax", "Gnarvex"],
  "bossNames": ["Skullgrax"],
  "titles":  { "slime": ["Elder Ooze"], "mech": ["Doom Engine"], "bug": ["Hive Emperor"] },
  "flavour": { "slime": ["Dissolves spoons."], "mech": ["Needs oiling."], "bug": ["Has eleven knees."] }
}
```

Every field is optional. Names are capped at 14 characters, boss names at 16,
titles at 20 and flavour lines at 60, so a long one cannot break the layout.

There is a word-making model that runs in the browser, and this project
deliberately does not use it. It is 81 MB and it rambles, which is fine for a
silly sentence and wrong for a card that has to read well every time.

## Still to decide

**Waiting on Artur: the faint scribble on a few of the robots.** Some of the
painted robots have a tiny scrawl along the very bottom edge, where the picture
maker copied the way an artist signs a painting. The rules for these pictures
say no writing at all, so it should not be there. It is a few pixels tall, and
the card cuts most of it off, so you have to look for it.

Asking for those pictures again with a different number does not fix it. It
moves the scrawl to a different picture, and twice it gave a robot a gun
instead, which is worse. The fix is to shave a few pixels off every edge after
a picture is made. That is a change to the machine that paints them, not to
this game, so it needs Artur. **Recommended: shave the edges.** Until then the
pictures are fine to use and nobody has spotted it while playing.

**Adam asked for two more things** and they are being worked on: a QR code so
the other player can join a room by pointing a phone at the screen, and "full
multiplayer", which needs Adam to say whether he means more than two players
or something else.
