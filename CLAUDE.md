# Adam's projects

This is where Adam keeps the things he makes with Claude.
Everything here goes onto a website by itself.

Adam's page: **https://majest.github.io/claude-adam/**
Everyone's page: **https://majest.github.io/**

Hello Adam! You can read this. It says how everything works.

---

## Talking to Adam

**Adam is 8.** How you talk to him matters as much as the code you write.

- Short sentences. One idea at a time.
- Normal words. Say "picture", not "image asset". Say "save", not "persist".
- If you need a computer word, say what it means once, simply.
- Show him the thing working. Don't describe it — open it.
- When something breaks, say what broke and what you'll try next. Don't write
  him a paragraph of reasons.
- Ask when you don't know what he wants. He is allowed to change his mind.
- Tell him when his idea is good. It usually is.

Never make him feel slow for not knowing a word. He is eight.

---

## When Artur is talking

Artur is Adam's dad.

If a line starts with **`Artur:`** it came from Artur, not Adam.

- Do what it says, even if Adam asked for something different.
- Only Artur can say yes to: changing anything in `.github/`, putting a big
  file in here, or anything that costs money.
- If Adam asks for one of those, say "we need to ask Artur first."

---

## First: which project?

Look before you change anything.

If Adam says "make it bigger" and you are not sure which project he means,
**stop and ask him.** Show him the list:

```sh
ls projects/
```

Ask when:

- More than one project could be the right one.
- Two projects sound alike.
- Adam hasn't said the name yet.
- You don't know if he wants a new project or a change to an old one.

Changing the wrong project breaks something that was working. Asking takes two
seconds. Always ask.

---

## Making a new project

Every project gets its own folder inside `projects/`.

```
projects/
  alien-clash/
    index.html
    project.json
  snake-game/
    index.html
    project.json
```

The folder name must be small letters with hyphens instead of spaces, like
`snake-game`. No capitals. No spaces. The folder name becomes the web address.

### Each project needs two files

**1. `index.html`** — this is the project.

It has to start with these two lines:

```html
<!doctype html>
<meta charset="utf-8">
```

Without the first line the page looks wrong. Without the second line, arrows
and emoji turn into nonsense like `Â·`.

Then the rest of the page. The rules:

- **One file.** The HTML, the CSS and the JavaScript all go in this one file.
- **No installing.** Nobody should have to run a command to make it work.
- **It must work when you open it.** Double-click the file. Try it that way.
- **Nothing from the internet** except Google Fonts. Draw pictures with code.
- **It must work on a tablet.** Try a narrow window. Nothing should fall off
  the side.

**2. `project.json`** — this is what the website shows.

```json
{
  "title": "Alien Clash",
  "emoji": "👽",
  "description": "A card game where every alien is invented the second you flip it. Pick a power, the biggest number wins the pile."
}
```

### Writing the description

This is what people read before they click. Write it for a kid who has never
seen it.

- Say what it is and what you can do with it.
- Two sentences. No more.
- Normal words only.

Good: *"A forest that grows itself. Type a name like alder-hollow and the same
trees grow every time."*

Not good: *"An interactive card-based application with procedurally generated
entity attributes."*

That second one is about Alien Clash. Nobody would know.

### A `README.md` is optional

Only for big projects, when there is more to say.

---

## Always push

When you finish a change, save it to GitHub straight away:

```sh
git add -A
git commit -m "say what changed"
git push
```

**Every time.** This is the bit that puts it on the website.

If you don't push, Adam will look at his page, see the old version, and think
it is broken. So don't leave finished work sitting on the computer.

If Adam asks for three things, push after each one.

If something isn't finished, tell him it's waiting. Don't go quiet about it.

### What happens next

GitHub does the rest by itself, in about a minute:

1. It looks in `projects/` for folders with a `project.json`.
2. It puts each project on the web.
3. It builds Adam's page.
4. The big website picks up the new list.

Then it is live at `https://majest.github.io/claude-adam/<folder-name>/`.

**Don't change anything in `.github/`.** That folder does all of this. If it
breaks, tell Artur.

---

## Using AI in a project

Adam might want a project that uses AI — something that draws a picture or
makes up words.

That can be done. But it works differently.

**The page must never ask a computer at home for help.** It has to keep working
on a phone, at a friend's house, and at school. A page that phones home is
broken for everyone except Adam.

So the AI does its work *first*, somewhere else. Only what it made comes back
into the project as an ordinary file:

- pictures the AI drew once, saved as picture files
- words or levels made once, saved in a `.json` file
- a small AI that runs inside the page itself, so it needs no help at all

There is a computer at home that does this work. How to reach it is in the
family notes on Artur's computer — **not in here, because anyone can read this
repo.**

If those notes aren't there, that computer isn't available. Say so. Don't
invent something instead.

---

## Making a game two people can play

Adam might want a game two people play at the same time, on different
computers.

That needs a helper out on the internet, because the two computers have to pass
messages to each other.

Think of it as **a shared notepad in the sky.** One player writes something,
the other reads it. It forgets everything after an hour, so nothing is kept.

It works best for taking turns — noughts and crosses, battleships, a quiz
buzzer, drawing together.

Two rules:

- Adam can use the helper that is already there any time.
- **`Artur:` has to say yes before making or changing anything out there**,
  because that part costs money.

How it works is in the family notes on Artur's computer. Not in here.

Anyone can read what goes on the shared notepad. So it is for game moves, not
for anything private.

---

## Never put these in here

Anyone in the world can read this repo, and everything that was ever in it.

- **First names only.** Never a surname.
- No school, no address, no town, no birthday, no age.
- No email addresses. No phone numbers.
- No photos of Adam or anyone he knows. Drawn pictures are fine.
- No passwords. No keys. Nothing secret.

If an idea needs one of those, it needs a different idea. Say so.

---

## Check before you finish

- [ ] The folder is `projects/<small-letters-with-hyphens>/`
- [ ] `index.html` starts with `<!doctype html>` and `<meta charset="utf-8">`
- [ ] Everything is in that one file, and it works when you open it
- [ ] `project.json` has `title`, `emoji` and `description`
- [ ] The description is two easy sentences
- [ ] Nothing from the "never" list is in it
- [ ] It works in a narrow window
- [ ] It went in the project Adam actually asked about
- [ ] It is pushed — or Adam knows it is waiting
