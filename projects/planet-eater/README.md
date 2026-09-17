# Planet Eater

You are a world floating in space. Swallow anything smaller than you, grow,
and keep going until you are big enough to eat the Milky Way.

Pick who you are first, and it changes how it plays:

| | |
| --- | --- |
| **Moon** | small and quick, and hard for the giants to catch |
| **Earth** | steady, and starts a little bigger |
| **Black hole** | slow, but drags anything smaller towards it |

Played by a robot from start to finish, the three take about 2.5, 3.5 and 5
minutes. The moon was never once caught; the black hole was bitten nineteen
times.

## The rules

1. Touch anything smaller than you and you swallow it and grow.
2. Anything bigger is too big to eat. Leave it.
3. **While you are small, nothing can hurt you.** That was a deliberate choice:
   the game starts gentle.
4. Once you are big enough to eat planets, the giants start hunting you and the
   edges of the screen go red when one is close.
5. A giant that catches you tears a chunk off rather than finishing you on the
   spot. Get bitten enough times and you are gone.
6. Reach the top and the Milky Way itself turns up.

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

## The names are real

The sizes are not to scale and could not be, because a real galaxy is around a
million million million times a moon. The ladder is squashed so it stays
playable.

The names are real, though, and so are the widths. Swallow Titan and it tells
you it is 5,150 km across. Ganymede is 5,268. Betelgeuse is 1.2 billion.
Sagittarius A* is the real black hole at the middle of our galaxy and its
event horizon really is about 23.6 million km across.

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
