# Adam's projects 🌲

Things Adam builds with Claude. Every one of them is a single web page that
runs in a browser — no installing, no setting up.

**See them all: https://majest.github.io/claude-adam/**

Part of the family showcase at **https://majest.github.io/**

## What's in here

| Project | What it is |
| --- | --- |
| [Understory](projects/understory/) | A forest that grows itself from a name you type. |

## How it's laid out

```
projects/<name>/index.html     the project
projects/<name>/project.json   its title, emoji and description
projects/<name>/README.md      optional, for the bigger ones
```

`CLAUDE.md` is the instructions Claude follows when Adam asks for a new project.
Adam can read it too.

## How it gets published

Pushing to `main` triggers `.github/workflows/publish.yml`, which runs
`.github/scripts/build.mjs` and deploys the result to this repo's own GitHub
Pages site. It only touches this repo, so it needs no tokens or keys.

To see what it would build, without pushing:

```sh
node .github/scripts/build.mjs
```
