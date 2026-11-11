# Project Sleepwalk

A 2000s internet detective simulator — *Her Story* meets GeoCities, with the
melancholy of an archive. You are a private investigator, not a moderator.
Your only weapon is the search bar and your understanding of the people
behind the pixels.

## Vertical slice — Case 1: "The Quiet Room"

Live at **https://xerohour.github.io/sleepwalk/**

- 1 zone (Goodtime Valley), 1 case, 20 pages
- Client: `marbles_4ever`, 19. Her sister Dani's memorial page
  (`angelfeathers`) has vanished. Find out who took it down.
- The slice has to answer three questions:
  1. Does the tune-as-evidence mechanic read without a hint?
  2. Do players find the webring without Search Assist?
  3. What did 20 pages cost? (Ledger is in the in-game Case File.)

## How it works

- `index.html` — the Somnius OS: draggable windows (Browser, Mail, Notepad,
  Case File, File Report), taskbar, Start menu. Progress saves to
  localStorage; "Reset case" in the Start menu clears it (two-step: click
  twice within 5 seconds — no native dialog, so automated browsers can use
  it too). `?reset=1` on the URL wipes the save before it loads, for a
  guaranteed fresh playtest.
- `pages.js` — the page CMS. Every page is a data object: `id, title,
  author, zone, tags, type (stub|standard|hub), costMin, hidden, dir,
  people, links, body`. Hidden pages are unlisted: reachable only via
  links, never via search or the directory.

## Design decisions (locked 2026-11-11)

- Names: **Somnius** (platform) / **Somnius Labs** (original startup) /
  **Hollowell Media Group** (conglomerate acquirer). No shared prefixes.
- Stuck player: 3 diegetic tiers on a no-new-page timer — Tier 1 client
  follow-up email, Tier 2 Search Assist surfacing one unvisited page,
  Tier 3 Notepad auto-pins the relevant URL. Hints cost nothing.
- Answer checking: no free text. Structured report slots with pickers over
  encountered people / history pages / handles. Reference equality,
  multiple accepted answers, partial credit per slot.
- Page cost: stub ~30 min, standard ~90 min, hub ~3 hrs. Case 1's 20 pages
  estimate at 29.5 hrs — which trips the 25-hour gate, so the target drops
  from 300 pages to 200 unless the measured number says otherwise.
- Page Builder cut from launch. Tune Sequencer stays — in Case 1, a tune is
  literally evidence.
