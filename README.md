# Love and Let Live

[loveandletlive.com](https://loveandletlive.com)

*Nobody knows. That isn't an argument against believing something — only against being so certain about it that you lose people over it.*

## What's here

| File | What it is |
|---|---|
| `index.html` | The door. One question at a time, slow cross-fade, nothing clickable above the fold. No explanation — that lives on About. |
| `map.html` | The map. A rotating world of entry points, one for each tradition or worldview, with a thread drawn between each of them. Also holds The Unanswered Line. |
| `ask.html` | The Unanswered Line, standing alone so a link can lead straight to it. |
| `about.html` | What this is, why it exists, where the author stands, two words worth having, and a footnote about the podcast that was. |
| `404.html` | "This road isn't on the map." |
| `assets/` | Cover art, the orb, the social preview card, favicon |
| `CNAME` | Points GitHub Pages at the custom domain — don't delete it |

No build step, no framework, no dependencies. Open any file in a browser to work on it.

## Things that are deliberate

**Nothing on this site asks the visitor for anything.** No signup, no email capture, no account, no analytics. The one thing a visitor *can* do — leave a question — asks nothing back. Don't add a form that does.

**The credo is not on the front page.** "No one knows the truth" asserted as a banner headline is a truth-claim the sentence itself forbids. It belongs on About, framed as one person's position.

**The landing questions follow rules**, written above the list at the top of `index.html`. Ask about a person, never a concept. Never imply the reader was wrong. Don't assume they pray. The last one in the loop opens a door, so the sequence ends in hope rather than on the wound.

**Every map panel carries a caveat** saying the lede is a summary, not a definition. It promises a hearing, not a rewrite — two people inside the same tradition will often want it changed in opposite directions.

## Changing the map

Everything is data at the top of `map.html`:

- **`NODES`** — the entry points. Add one and it appears on the map, in the picker, and in the search automatically.
- **`ROADS`** — the threads between them. Every one is a question, never a verdict.
- **`EPISODES`** — empty, and correct that way. The object stays so the panel still knows how to render it.
- **`ALIASES`** — extra search terms, so people find themselves by the word they'd actually use.

**Radii drift.** Each marker's distance from the centre breathes on two periods that never line up. The orb at the centre is love — if any marker sat permanently nearer to it than another, the map would assert a hierarchy nobody intended.

**Only near-side markers are labelled.** That's perspective, not a ranking, and it's what lets the map keep growing without turning to mush.

## The Unanswered Line

The form on `ask.html` and in the map panel posts to a Cloudflare Worker, which writes one row into a private Notion database. The worker's source lives outside this repo, in the project folder, with its rules in a comment block at the top.

No name field, no email field, no account, no IP. The worker discards the visitor's IP, never logs question text, and stores a date rather than a timestamp. Spam is handled by an off-screen honeypot and a timing check — never a visible challenge, because the page's promise is that nothing is asked of you.

## Publishing

From the folder above this one:

```
bash deploy.sh "what changed"
```

It mirrors this folder into a working clone, commits, and pushes. GitHub Pages rebuilds in about a minute. The CDN can serve a cached copy for a minute or two after that — if a change doesn't appear, wait rather than redeploying.
