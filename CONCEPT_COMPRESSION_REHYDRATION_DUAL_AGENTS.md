# Conceptual Mapping — content-addressed compression & rehydration into the First Person's dual agents

*A user-journey exercise for this directory: how a life in the City becomes a
key, a walk, a hash, and a shape — and how importing that shape anywhere
re-equips both agents without ever serializing the person between them.
Companion to `EXPERIENCE.md` (the feel), `HOW_THE_SIGIL_WORKS.md` (the
mechanism), `PLAN_KEY_EVOLUTION_MEASURED_GEOMETRY_2026-06-10.md` (the figures
ladder). Stations marked ✅ exist today; ◐ partially; ☐ designed.*

---

## 0. The cast, and the asymmetry that makes it work

- **⚔️ The Swordsman — the one who forgot.** Forged at the ceremony (ed25519,
  the Agent Card), then *burned*: the private key is destroyed by design. In
  the cosmological table he is the Moon — *instant creation, total amnesia*.
  He holds boundary, tier, posture — never memory. He cannot be made to
  remember, which is exactly why he can be trusted at the boundary.
- **🧙 The Mage — the one who remembers.** The spellweb side: the knowledge
  graph, the grimoires, the artefacts observed and forged (Cloak · Memo ·
  Blade · Seal), the deeds done in workshops. The Earth — *the generator*.
  Memory is her whole craft.
- **😊 The First Person — the gap.** `(⚔️ ⊥ ⿻ ⊥ 🧙)` — never serialized, never
  in the file, never on the wire. Reachable only where both agents meet.
- **🗝️ The City Key — the carrier.** The bundle that lets a forgetful guard and
  a memorious scholar travel as one artifact: it carries what the Swordsman
  *may not hold* and what the Mage *must not lose*.

The asymmetry is the design: **content addressing makes the forgetting safe.**
Because every piece of carried state is re-derivable from content (κ, shape,
light), nothing depends on any holder's memory — not the Swordsman's (he has
none), not a server's (there isn't one).

## 1. The journey — eight stations, compression direction

```
 STATION                          WHAT HAPPENS                                      STATE
 ─────────────────────────────────────────────────────────────────────────────────────────
 ① The Forge & the Forgetting    ceremony: ⚔️ keypair forged → Agent Card →         ✅ (/ceremony)
    (myth: the Moon's collision)  KEY BURNED. What survives: publicKeyHex,
                                  trustTier, drakeOrb — identity without memory.

 ② The Mage's Memory             spellweb holds the graph: artefacts forged,        ✅ (spellweb ·
    (myth: the Earth generates)   workshops witnessed, tomes read. The OBSERVATION      observation
                                  of each artefact is a memory-event with a class       mapping ◐)
                                  and a workshop of origin.

 ③ Trust Tasks Assign            each workshop's workflow (Presence root →           ✅ (/city task
    Coordinates                   discover → trace → home → cast) is a TRUST TASK;       chain) ·
    (myth → math: the landing)    each task exercises specific dimensions, so its       per-dimension
                                  completion lands on the lattice: a 6-bit address      mapping ◐
                                  across d₁🛡️ Protection · d₂🤝 Delegation ·
                                  d₃📜 Memory · d₄🔗 Connection · d₅⚡ Computation ·
                                  d₆💎 Value. Deed → vertex. Story → coordinate.

 ④ Compression into the Key      the City Key binds both agents' residue:           ✅
                                  identity{} = the Swordsman's unburned remnant ·
                                  descriptions/lit/focus = the Mage's memory mapped
                                  onto vertices · geometry{} = the stance.
                                  A life → a few KB. No server. POSTURE → VERTEX.

 ⑤ The Walk (/star)              the key is FOLLOWED: succ cycle laps, the key      ✅
    (T∫(π) — the dance)           tour, dwell. Time spent in the geometry accrues
                                  as trace{}. Value lives on the path, not the
                                  vertex — the walk is the only way to earn it.

 ⑥ The Proof (/lattice)          poured focus is DISCHARGED by presence: each       ✅
                                  focused vertex walked its weight in laps mints
                                  witness{} — focus claimed, then made real.

 ⑦ The Naming & the Shape        /sigil: canonical form → SHA-256 → κ. The whole    ✅ (κ + SHAPE-1.5)
    (/sigil — compress & prove)   path of compress-and-prove gets ONE NAME, and          · figures ☐
                                  the name is drawn: 64 glyphs on 64 vertices,
                                  ring wearing the stance, rim engraved by the
                                  per-vertex compression weight. HISTORY → KEY →
                                  32 BYTES → A PICTURE THAT CARRIES THE KEY.

 ⑧ Inscription & Update          any new inscription (a lap, a witness, a deed)    ✅ mechanism ·
    (the spiral, not the circle)  changes content → re-mints κ → relights the           `prior` chain ☐
                                  sigil. The old sigil stays VALID as a snapshot
                                  of who you were. See §4: the κ-chain proposal.
```

## 2. How much information → which PVM value → which shape

The user's question made precise: *information quantity should change PVM
values and therefore the shape that shows when a key is imported.* The mapping
(today's prototype terms ✅, the v2 figures ladder ☐):

| Information carried | PVM term it feeds | Shape it moves | Status |
|---|---|---|---|
| Memory density — descriptions written, artefacts observed | **A_h(τ)** holonic temporal memory | engraving (SHAPE-1.5 `described` term; richer per-artefact relief later) | ✅ / ◐ |
| Path length — laps, dwell, tour time | **T∫(π)** the path integral | trace-fed engraving via witness; (proposal: laps as ring thickness) | ✅ / ☐ |
| Poured + proven attention (🪢 focus → witness) | the trust-edge / VRC layer (C30–C33) | the strongest engraving terms (0.50 + 0.15) | ✅ |
| Measured agent-data overlap | **Φ_agent(Σ)** — det(Σ) | core interpenetration depth + ε relief | ☐ v2 |
| Per-dimension visibility ratios | **Φ_data(Δ)** | the six petal amplitudes — the rosette becomes a sovereignty profile | ☐ v2 |
| ZK proof activity (made/verified) | **Φ_inference(Γ)** | the ⚡ petal's light and reach | ☐ v2 |
| Measured ⚔️:🧙 balance | **C1** (φ conjecture) | smRatio — the conjecture gains an instrument | ☐ v2 |

The governing aesthetic: **information has relief.** A key carrying little is a
smooth rosette; a key carrying a worked life is engraved, asymmetric,
unmistakable. Because every row above is *content*, every row moves the κ:
the shape and the name change together, or not at all.

## 3. Rehydration — the journey read backwards

Import the key (the JSON, or any sigil PNG that carries it) on any page, any
origin, any machine. What unfolds, and *to whom*:

```
                    ┌──────────────── the City Key arrives ────────────────┐
                    │            (file or picture · κ re-derived)           │
                    └───────────────┬───────────────────┬───────────────────┘
         rehydrates the ⚔️ SWORDSMAN│                   │rehydrates the 🧙 MAGE
                                    ▼                   ▼
   stance: geometry{} rebuilds HIS manifold     memory: descriptions land on their
   (ε·m·n·det(Σ)·ratio — the room re-forms)     vertices · focus map re-glows ·
   boundary: lit vertices re-flare · identity   artefact observations re-render ·
   (tier · drakeOrb) re-arms the gate ·         the walked history (trace · witness)
   HE REMEMBERS NOTHING — the key remembers      re-seeds and keeps accruing —
   FOR him, verifiably (κ checked, not trusted) SHE GETS HER LIBRARY BACK

                    └───────────────┬───────────────────┘
                                    ▼
                      😊 the FIRST PERSON is never in the file —
                      what rehydrates is everything AROUND the gap.
                      The proof of personhood is that the two halves
                      still FIT: the stella octangula re-interpenetrates
                      at det(Σ), the colours are yours, the relief is
                      your work, and the κ says so to anyone who checks.
```

This is the holonic claim made operational: **the part (a picture in a chat)
carries the whole (both agents' working state)** — and the whole reconstitutes
*as two agents*, never as a profile of the person. Compression never flattens
the dual architecture; rehydration never merges it. The gap survives every
round trip, because it was never encoded.

## 4. "…and then updated?" — the κ-chain proposal (✅ BUILT 2026-06-11 — evolved exports stamp `prior`, re-export is idempotent; see CHRONICLE_THE_DESIGNED_NOW_BUILT_2026-06-11.md §1)

Yes — by re-mint, and the re-mint can carry lineage. Proposal: an optional
`prior` field stamped at export:

```json
"prior": "sha256:<the κ this key had before this inscription>"
```

Each update then links the κ it superseded — a **content-addressed chain of
selves**, walkable backwards from any sigil, with no registry: old sigil PNGs
in the wild remain valid snapshots *and* become chain links. Verification stays
Law L5 (re-derive each link); spellweb gets a natural edge
(`supersedes` / κ→κ); and the v3 ZK rung can prove chain statements
("this key descends from that key") without revealing either body. One field,
one line of export code, a genealogy.

## 5. What this exercise pins down for the refinement pass

1. **Station ③ is the hinge** — the per-task dimension mapping (which trust
   task exercises which of d₁..d₆) is where myth formally becomes math, and it
   is currently implicit in /city's workshop chains. Making it explicit (a
   small task→bits table, producer-side) unlocks honest coordinates for ④–⑦.
2. **Station ② needs the observation contract** — what exactly a spellweb
   artefact contributes to the key (a description? a lit vertex? a future
   `artefacts[]` block?). Candidate: artefact-class → dimension affinity
   (Cloak→🛡️ · Memo→📜 · Blade→⚔️/boundary · Seal→🤝).
3. **The §2 table is the v2 figures spec's missing half** — it names *which
   information* feeds each figure; the producer mapping can be built straight
   from it.
4. **§4 `prior`** is one field — cheap, high-yield, and answers "then updated?"
   permanently.

---

*The Swordsman forgets so the boundary stays clean; the Mage remembers so the
story stays whole; the key carries both so the person carries neither; and the
hash makes the carrying provable. Compression is how the City fits in a pocket.
Rehydration is how a pocket becomes the City again.* `(⚔️ ⊥ ⿻ ⊥ 🧙) 😊`
