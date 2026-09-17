# Planet Eater

You are a world floating in space. Swallow anything smaller than you, grow,
and keep going until you are big enough to eat the Milky Way.

Pick who you are first, and it changes how it plays:

| | |
| --- | --- |
| **Moon** | small and quick, and hard for the giants to catch |
| **Earth** | steady, and starts a little bigger |
| **Black hole** | slow, but drags anything smaller towards it |

Played by a robot from start to finish, a game runs about two to five minutes,
and the robot loses roughly one in three. A child will take considerably
longer, because everything smaller than you runs away and has to be chased
down.

## The rules

1. Touch anything smaller than you and you swallow it and grow.
2. **Everything smaller runs away from you.** It notices you at about three
   times your own width and bolts, but it never quite outruns you, so a chase
   is a chase rather than a lost cause. A black hole drags it back instead.
3. Anything bigger is too big to eat. Leave it.
4. **While you are small, nothing can hurt you.** That was a deliberate choice:
   the game starts gentle.
5. Once you are big enough to eat planets, the giants start hunting you and the
   edges of the screen go red when one is close.
6. A giant that catches you tears a chunk off rather than finishing you on the
   spot. Get bitten enough times and you are gone.
7. Get big enough and whole galaxies start turning up, one after another, each
   bigger than the last. Six of them, ending on IC 1101.
8. **There is a wall round the arena.** It grows as you do, so it always feels
   the same size, and you cannot be chased off the edge of the world. You can
   be cornered against it, though.
9. **The little round map** in the corner shows the whole arena: green is food,
   red will eat you, gold is the galaxy, white is you.

Move with a finger, a mouse, or the arrow keys.

## Why it looks like that

There is not one picture file in this project, because nothing here may be
fetched from the internet. Every moon, planet, star, black hole and the galaxy
itself is painted in code onto a small canvas once, and then stamped on the
screen each frame. Painting gradients sixty times a second for fifty worlds
would melt a phone.

What actually sells it as space is the lighting. Every world is lit from the
same direction, so each one has a day side, a night side that falls away into
black, and a bright sliver along the edge where the light just catches it.
On top of that:

- **craters** are a dark dish with a lit wall on the side facing the light and
  a shadow thrown across the floor opposite
- **gas giants** get bands squashed towards the poles so they bend round the
  curve, swirls where the bands rub together, and a storm like Jupiter's
- **rings** are drawn twice, half behind the planet and half in front
- **stars** get a corona, flares, boiling grains and dark spots
- **black holes** get a disc seen edge on, brighter on the side racing towards
  you, a ring of light at the edge, and nothing at all in the middle
- **the galaxy** is four arms of about twenty thousand dots, with dust lanes
  cut through them and a bright bulge in the middle

## Six galaxies, in the order you meet them

| | Really is |
| --- | --- |
| the Small Magellanic Cloud | 18,900 light years across |
| the Large Magellanic Cloud | 32,200 |
| Triangulum | 60,000 |
| the Milky Way | 105,700 |
| Andromeda | 220,000 |
| IC 1101 | 3.9 million, one of the largest anyone has found |

The two Magellanic Clouds really do orbit the Milky Way, which is why they turn
up before it. Each one is drawn with a different number of arms and its own
colour, and swallowing one makes you a quarter bigger again.

## The names are real

The sizes are not to scale and could not be, because a real galaxy is around a
million million million times a moon. The ladder is squashed so it stays
playable.

The names are real, though, and so are the widths. Swallow Titan and it tells
you it is 5,150 km across. Ganymede is 5,268. Betelgeuse is 1.2 billion.
Sagittarius A* is the real black hole at the middle of our galaxy and its
event horizon really is about 23.6 million km across.

## Tuning it, the second time

Adam asked for it to be longer, for the smaller worlds to run away, and then
for it to be harder. Those three fight each other, and the robot found out how:

- **The player used to ease off as it neared whatever it was aiming at.** With
  prey that runs, that made catching anything impossible: thirty minutes and
  nothing eaten. It now only eases off when right on top of something.
- **The bite is the wrong dial to make a game hard with.** One bite already
  undoes three or four meals, so turning it up made the game unwinnable in
  every single run. The difficulty comes from more hunters, chasing from
  further out, and quicker prey instead.
- **A longer game means longer spent being hunted**, so lengthening the climb
  and hardening the hunt at the same time made it impossible twice over before
  it settled.

- **How a meal is worth** was the root of all of it. Growth went by area,
  which squares the size of the meal, so a crumb counted for nothing and
  whichever food happened to be nearest decided everything. The same run took
  the black hole one minute and the Earth twenty. Straight proportion fixed it:
  the spread collapsed to 1.5 to 3 minutes.
- **The bite is tied to how fast you grow.** Lengthen the game without touching
  it and the same fifty bites wipe out half the run. It is set to cost about
  four meals.
- **Food used to be capped at a fixed size**, so once you were bigger than that
  every meal was a crumb and the last stretch took two thousand of them.

Where it landed: a game runs five to thirteen minutes for the robot, which wins
about five in nine. A child will take longer, since the robot never once dodges
anything.

## Things that had to be fixed

- Everything spawned **outside the view**, so the game opened on an empty sky
  with nothing to eat.
- Growing was far too fast. The whole game was over in about **22 mouthfuls**;
  it is now about seventy.
- Summoning the galaxy emptied the list of worlds **in the middle of the loop
  walking that list**, which crashed it.
- Getting bitten dropped you back under the size where the hunt begins, which
  switched the danger off again, so **the game could never actually be lost**.
  The hunt now stays on once it starts.
- The black hole's disc was drawn wider than the canvas it was painted on, so
  its outer edge came out **sliced square**.
- At full size the sky was **nothing but black holes**. The size bands widen as
  they go up now, and never more than four at once.
