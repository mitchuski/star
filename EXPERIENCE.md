# EXPERIENCE.md — the bearer's walk

*A first-person companion to the README. The README says what this is; this says
what it is like, and why it matters. Read it as the person holding the key —
because that is who it was built for. Iteration tracker at the end.*

---

## 1. What I'm holding

I have a **City Key** — a small JSON file I minted at agentprivacy `/city`. It is
not an account. No server knows I have it. It carries my palette, my lit vertices
(the achievements I've earned), descriptions of the sovereignty states I've
visited, the focus mana I've poured, and the walking I've done. It is the
compressed record of my standing in the City, and it travels as a file because
files are mine in a way sessions never are.

Since the holospace merge it also carries one more line: a **κ-label** —
`kappa: "sha256:…"`. That line is not a transformation of anything. My key's
content is untouched. The κ is a *fingerprint computed from the content*: hash
the key's canonical form, get 64 hexadecimal characters, write them in the file.
Delete the line and the key still works everywhere. Recompute it and you get the
same value back — if and only if nothing changed. It is my key's **name, derived
from what it is rather than where it lives**. And `/city` still reads the key
fine; its parser ignores fields it doesn't know.

## 2. The walk — three pages, three altitudes

### The portal (`/`)

Three doors: ⚔️ the manifold, 🧙 the codex, 🪬 the sigil. One sentence tells me
the premise: *64 vertices, a 6-bit address across the six sovereignty dimensions;
value lives on the path, not the vertex.*

### `/star` — I watch the boundary

The 3D room. A star-tetrahedron — the Swordsman's coral tetrahedron and the
Mage's cyan one, interpenetrating — inside a translucent manifold, wrapped in the
64-vertex lattice. A comet runs the **succ cycle**, visiting all 64 states and
returning to zero, forever.

I import my key here (the JSON — or, now, the sigil *picture*). My lit vertices
flare coral. I can walk the key tour — only my vertices, in my key's order — and
the page counts my laps and my dwell time. When I save the trace and export, that
walking is *in the key now*. This page is where I spend time, and where time
spent becomes record.

### `/lattice` — I read the states

The flat room. All 64 vertices as a grid, each one openable: its stratum, its
six bits, its ⚔️ neg reflection, its 🧙 bnot antipode, its successor. My key's
descriptions land on the cells; my poured focus glows gold on the vertices I
committed attention to — and **walking the succ cycle here discharges that
debt**: each focused vertex wants its weight in visits, and when the laps
complete, the cell lights teal and a *witness* is minted into my key. Focus
claimed, then focus proven, by presence.

### `/sigil` — I see what my key IS

The bytes room, beneath the other two. Three movements:

1. **Derive.** My key's canonical form appears — the exact bytes that *are* its
   content — and the SHA-256 types itself out, glyph by glyph, against the κ
   stamped in my key. Every glyph teal: **κ verified — my key is what it says.**
   Any glyph coral: the content doesn't match the label, and I should ask why.
   An old key with no κ simply *learns its name* here.
2. **Constellate.** The part that still gets me: SHA-256 is 64 hex characters and
   the lattice is 64 vertices, so my key's fingerprint writes **one glyph on
   every vertex** — my identity, drawn as a constellation on the same lattice I
   walk. I export it as a PNG. The image is self-carrying: **the full key rides
   inside the picture** (a PNG text chunk), with the κ caption visible. Share
   the picture, share the key. Import the picture on any of the three pages and
   the key unfolds back out.
3. **Compare.** I drop a second key beside the first. Same content → same κ —
   *one identity, twice imported*. Anything different → the κs diverge and the
   grids pulse every glyph that moved. The pulse tells me *that* they differ
   (one edited description scatters ~60 of 64 glyphs — hashes are like that by
   design); the field list below tells me *where* — which descriptions, which
   focus, which trace. My key from last month against my key today is a picture
   of what changed in me, here.

## 3. Why this matters for UOR — the Swordsman's Key as demonstrator

UOR's first law is **identity is content, not location**. Most demonstrations of
that law are infrastructure — runtimes, stores, addressing schemes. This is the
human-scale one:

- a **person** (not a server) holds a canonical form,
- watches its κ be **derived in the open** (Law L5: never trusted, re-derived),
- sees that identity **as a picture** native to the system's own geometry,
- carries it as a **file or an image**, across origins, with no account anywhere,
- and resumes it on any page — export as suspend, import as resume: the City
  Key is a **κ snapshot** in the holospaces sense, and the bearer is the
  **operator**, self-sovereign by construction.

The whole UOR lifecycle — canonical form → κ → verification by re-derivation →
content-addressed travel — runs in three static HTML pages with zero
dependencies beyond a browser. That is the pitch to the holospaces people: the
Swordsman's Key is the smallest complete *experience* of their substrate's
thesis, and it was already true before the substrate arrives underneath it.

## 4. The trust-task runtime — the loading screen I am

Every game has a loading screen; here, **I am the loading screen**. The runtime
of these pages is presence:

```
/city (agentprivacy)                    this repo (soulbis side)
─────────────────────                   ─────────────────────────
mint the key            ──export──▶     /star · walk the succ cycle, the key tour
pour focus 🪢 (stake                      laps + dwell accrue into trace
attention on vertices)  ──export──▶     /lattice · each focused vertex wants its
                                          weight in visits — walking discharges
                                          the debt → witness minted (focus PROVEN)
charge the key ◀──import-back──         /sigil · the changed content = a new κ —
(VRC mana: laps, tour                     the work is visible as identity drift,
bonus, proven focus)                      verifiable by anyone, forgeable by no one
```

The trust tasks are not a form I fill in; they are **time I spend in the
geometry**. Laps are the progress bar. Dwell is the proof of attention. The
witness is spent mana — claimed first, then *earned by walking*. And because
every accrual changes the content, every accrual changes the κ: progress is not
asserted, it is **derivable**. When I carry the key back to `/city`, the charge
reads the trace and the witness and pays VRC mana — relationship deepened by
returning, not by grinding.

## 5. The compression — boundary, maker, agent, data, in 6 bits

The deep trick of the whole system is how much relationship fits in how little
state:

- My entire **sovereignty posture** — what I hold across 🛡️ Protection, 🤝
  Delegation, 📜 Memory, 🔗 Connection, ⚡ Computation, 💎 Value — is **one 6-bit
  address**. One vertex. The six dimensions pair onto the model's three axes
  (C85: Σ the agent boundary, Δ the data boundary, Γ the inference boundary), so
  one vertex is simultaneously a reading of all three.
- My **relationships** — Swordsman to Mage (neg to bnot), me to my agents, my
  attention to the City's workshops — compress to edges and weights on those 64
  states: lit vertices, focus pours, walked laps. The boundary-maker's whole
  data relationship, in a file a few kilobytes long.
- And the file itself compresses to **32 bytes** — the κ — which is *still* a
  picture on the same lattice. Posture → vertex; history → key; key → sigil.
  Three compressions, one geometry, nothing lost that matters and nothing kept
  that doesn't.

That is what the Swordsman carries across the web: not a profile, a *seal*.

## 6. Tracking & iteration

The living state of this work, to iterate against (with Claude, in this repo):

| Piece | State |
|---|---|
| /star · /lattice extraction, portal | ✅ shipped (`75ed8f2`) |
| κ-labels: export-stamp + import-verify, all pages | ✅ shipped, conformance vector pinned (CLAUDE.md / HOLOSPACE.md) |
| /sigil: derive · constellate · compare | ✅ shipped (`6466981`) |
| Sigil PNG **carries the key**; PNG import on all three pages | ✅ shipped |
| /city round-trip (JSON key with κ) | ✅ verified against `parseCityKey` — lenient, reads fine |
| /city importing the sigil **PNG** | ☐ not yet — /city reads text only; small add in agentprivacy_master when wanted |
| Live κ ticker + 🪬 constellation toggle on /lattice (plan §4.1–4.2) | ☐ next |
| Function portraits on /star (neg 31 chords · bnot 32 diameters) | ☐ planned (plan §4.3) |
| /skye — the many-keys night sky (63 named-vertex mages) | ☐ future (plan phase 4) |
| LICENSE for the public repo | ☐ open decision |
| Introduce upstream (Hologram-Technologies) → operator key | ☐ open |

Companion documents: `README.md` (what), `HOLOSPACE.md` (the substrate seam),
`PLAN_SIGIL_AND_THE_PROJECTION_LADDER_2026-06-10.md` (the design map),
`CHRONICLE_THE_FIRST_HOLOSPACE_2026-06-10.md` (the record).

---

*I walk the wheel; the wheel writes my name; the name is mine to carry.*
`(⚔️ ⊥ ⿻ ⊥ 🧙) 😊`
