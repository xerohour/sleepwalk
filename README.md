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

## Vertical slice — Case 2: "The Girl Who Drew the Stars"

Live at **https://xerohour.github.io/sleepwalk/?case=2**

- 1 new zone (Teentopia), 1 case, 20 pages
- Client: `lunar_latte`, 15. Her webcomic "Comet Cat" is being reposted
  as someone else's work by `starfactory` — a Hollowell Media Group
  content farm.
- New tests: multi-zone search, visual evidence (zoom-to-reveal hidden
  signature), pattern discovery via a second victim, and the corporation
  as a report answer.
- Case switcher lives in the in-game Case File; progress saves per case.
  In the full game Case 2 unlocks by closing Case 1 — in the slice both
  cases are open for playtesting. `?case=2` opens straight into Case 2.

## Vertical slice — Case 3: "The 3y3 of the Storm"

Live at **https://xerohour.github.io/sleepwalk/?case=3**

- 1 new zone (gamerZone), 1 case, 20 pages
- Client: `pixelpete_99`, 14. His older brother `DoomDealer` was banned
  from gamerZone for uploading a cracked game. Pete thinks he was framed.
  He is wrong about that — and right about something else.
- New tests: a tool-gated case (`3y3.exe`, a decryptor the player
  downloads from a fake banner ad), a two-layer decryption (one file needs
  the audio key — Skullcrusher's theme, fingerprint QR-9931), a client who
  is wrong, and an ethical choice at the end of the report (four actions,
  four epilogues — no right answer, only the one you can live with).
- The Null Sector webring is the hidden ring: black pages, green
  monospace, ASCII eye. Entry is the eye icon on DoomDealer's locked page
  or the banner ad on The Cheat Vault. `?case=3` opens straight into
  Case 3.

## How it works

- `index.html` — the Somnius OS: draggable windows (Browser, Mail, Notepad,
  Case File, File Report), taskbar, Start menu. Progress saves to
  localStorage, one sub-state per case; "Reset case" in the Start menu
  clears it (two-step: click twice within 5 seconds — no native dialog, so
  automated browsers can use it too). `?reset=1` on the URL wipes the save
  before it loads, for a guaranteed fresh playtest. `?case=2` opens
  straight into Case 2.
- `pages.js` / `pages2.js` / `pages3.js` — the page CMS. Every page is a data object:
  `id, title, author, zone, tags, type (stub|standard|hub), costMin,
  hidden, dir, people, links, body`. Hidden pages are unlisted: reachable
  only via links, never via search or the directory. Each case also
  registers its people, identity evidence, and mail in the same file.
  Case 3 additionally registers `SLEEPWALK_FILES3` — the encrypted .nfo
  files 3y3.exe decrypts (each maps to one evidence item; one needs the
  audio key).

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
