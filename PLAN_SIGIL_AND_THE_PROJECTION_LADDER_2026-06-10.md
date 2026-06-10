# Plan — the κ-Sigil and the Projection Ladder

**Date:** 2026-06-10
**Repo:** `github.com/mitchuski/star`
**Scope:** Design exploration — how the holospace merge and its underlying math can
deepen the visualizations, on either side of the existing `/lattice ↔ /star` pair,
including one proposed new page. Nothing here is built yet; this is the map.

> The κ work gave the key a verifiable identity. This plan is about giving that
> identity a *body* — something you can see, compare, and walk.

---

## 0. The find that anchors everything

**SHA-256 is 256 bits = 64 hexadecimal characters. The lattice has 64 vertices.**

A City Key's κ-label therefore writes **exactly one glyph (0–15) on each vertex**
— 4 bits per vertex, no remainder, no padding. This is not a contrivance; it falls
out of the two systems' numbers. Every key's content identity *is* a unique
lighting of the lattice:

```
kappa = sha256: 7 6 0 c 4 d 0 2 b 8 0 c …   (64 hex chars)
                │ │ │ │ │ │ │ │ │ │ │ │
vertex:         0 1 2 3 4 5 6 7 8 9 10 …    (the 64)
```

Call this the **κ-constellation**: hex digit → glow intensity (0 = dark, f = full)
at that vertex. Change one description in the key → a different hash → a visibly
different constellation. *Identity is content* stops being a slogan and becomes a
picture. Two keys can be told apart at a glance; a tampered key doesn't just fail
a check — it *looks wrong*.

(Secondary correspondences, noted not built: 256 bits = 4 × 64 — four full
lattice-layers of bits, rhyming with Vitalik's tablet ∞² = 64; and the digest is
32 bytes = one byte per antipodal pair.)

---

## 1. What the holospace math newly affords, visually

| Upstream concept (docs/) | Visual affordance |
|---|---|
| κ-label = H(canonical form) — identity is content | **the κ-constellation** (§0) — identity rendered on the lattice itself |
| any edit mints a new κ | **identity drift** — live recompute while you walk/pour/trace; the current unsaved state's κ visibly diverges from the imported one |
| Law L5 — verification is re-derivation | **derivation theater** — show the steps (canonical form → bytes → hash → match), not just a badge |
| κ snapshot — suspend on one instance, resume on another | export/import re-framed as **suspend/resume ceremony** |
| LUT materialization — pure fns over finite domains become objects | **function portraits** — render neg/bnot/succ *whole*, as objects, not just evaluated step by step |
| Channels — canonical events on κ-addressed routes | the BroadcastChannel link surfaced as a small **event ticker** |

The function-portrait math (verified):
- **succ** — the 64-gon ring (already drawn — the comet's track).
- **bnot 🧙** — 32 antipodal **diameters**, no fixed points: every chord passes
  through the centre. The Mage's portrait is a full radial burst.
- **neg ⚔️** — 31 **mirror chords** across the 0–32 axis, with two fixed points
  (vertex 0 and vertex 32): the Swordsman's portrait is a bilateral reflection —
  visibly *the* mirror symmetry, with the unguarded origin and the half-turn
  vertex as its only still points.
- Drawn together they exhibit `neg∘bnot = succ` — the dihedral structure of the
  whole canon — as one image. Today the pages only ever show these functions
  *evaluated at the current vertex*; materialized, each function becomes an
  artifact you look at. That is precisely the substrate's evaluate ⇄ materialize
  distinction, made walkable.

---

## 2. The projection ladder — "either side of the lattice to star"

The two existing pages are projections at two altitudes. The holospace work opens
a rung **below** (into the bytes) and a rung **above** (into the many):

```
   /sigil     ⇣ beneath the lattice — THE BYTES
              the derivation microscope: canonical form, the hash,
              the κ-constellation, key-vs-key comparison
   ───────────────────────────────────────────────────────────────
   /lattice   the 64, flat            (exists)
   /star      the boundary, 3D       (exists)
   ───────────────────────────────────────────────────────────────
   /sky       ⇡ beyond the star — THE MANY
              every key a star: a night sky of κ-constellations,
              the operator's fleet view (future — needs >1 key to matter)
```

Each rung is a *projection* in the upstream's strict sense: a view + intent
surface over the same canonical content, never a second source of truth.

---

## 3. The proposed new page — `/sigil` 🪬 (the third projection)

**One line:** drop a City Key, watch its identity be derived, see its
constellation, compare it against another. The verification page the 05-27
chronicle proposed as `/key` — re-grounded, now that κ exists, as something
much stronger than a badge-checker.

**Three movements (single self-contained page, house register):**

1. **Derive** — the theater of Law L5. The imported key's canonical form scrolls
   as a byte-stream; the hash accumulates; the final `sha256:…` either snaps onto
   the key's stamped `kappa` (**verified** — teal) or visibly shears away from it
   (**mismatch** — coral, with the diverging characters highlighted). Older keys
   without a κ derive one live, framed as "this key learns its name."
2. **Constellate** — the κ-constellation rendered large: the 8×8 grid (and/or the
   succ-wheel ring) lit by the 64 hex glyphs, the key's palette driving the glow
   ramp. This image *is* the key's sigil — exportable as PNG (snapshot button,
   like /star's). Beneath it, the identity block and trace/witness provenance as
   a quiet timeline (minted → walked → poured → proven → exported).
3. **Compare** — import a second key into the right-hand slot: both constellations
   side by side, differing vertices pulsed, and a field-level diff of the two
   canonical forms (which descriptions/focus/trace diverge). Two keys from the
   same bearer at different times = watching the key *live*; two bearers' keys =
   two sovereignty postures, distinguishable at a glance.

**Why this page and not /sky first:** /sigil pays off with a *single* key today,
deepens the existing import/export loop on both current pages, and gives every key
holder a shareable artifact (their sigil PNG). /sky needs a population of keys to
be interesting — it becomes compelling exactly when the community repo has users
(and it is the natural home for the 63 named-vertex mages, each of whose keys
would hang as a star in it).

**Navigation:** the portal gains a third door; /lattice and /star each gain a
`↘ /sigil` link next to their existing cross-links. BroadcastChannel joins the
same `'agentprivacy-succ'` channel so an imported key cascades to all three pages.

---

## 4. Upgrades to the existing pages (no new routes)

Ordered by payoff-per-effort:

1. **κ-constellation toggle on /lattice** *(small)* — a 🪬 pill beside the existing
   💠/🔄 toggles: lights each cell's corner with its κ glyph intensity for the
   loaded key. The grid already exists; this is a per-cell overlay.
2. **Live κ ticker + dirty indicator, both pages** *(small)* — recompute the
   would-be κ (debounced) as laps/focus/witness mutate; show its first 8 hex in
   the key-name line, dimming the *imported* κ when they diverge: "content has
   moved · export to mint." Makes "any edit mints a new κ" continuously visible.
3. **Function portraits on /star** *(medium)* — extend the edge-mode segment:
   `∂M · 96 │ Q₆ · 192 │ ⚔️ neg · 31 │ 🧙 bnot · 32 │ off`. neg draws its mirror
   chords in sword-coral with vertices 0 and 32 marked as fixed stars; bnot draws
   its diameters in mage-cyan. (On /lattice, the panel could show the same as arc
   diagrams later — optional.)
4. **Suspend/resume framing** *(tiny, copy-level)* — export toast: "κ snapshot
   minted — resume anywhere"; import line: "resumed from κ …". Vocabulary only,
   zero logic.
5. **Channel ticker** *(small, optional)* — a one-line event log of
   BroadcastChannel traffic ("/star → vertex 12", "key cascaded"), framing the
   live link in the upstream's Channels vocabulary.

## 5. Phasing

- **Phase 1** — items 4.1 + 4.2 + 4.4 (the κ becomes visible everywhere; ~a session).
- **Phase 2** — `/sigil` (the third projection; one self-contained page in the
  established register; the substantial build).
- **Phase 3** — 4.3 function portraits on /star (+ optional 4.5).
- **Phase 4** — `/sky`, when there are keys enough to fill it; 63-NFT tie-in.

## 6. Open decisions (flagged, not resolved)

1. **Name & glyph of the new page** — `/sigil` 🪬 proposed (also considered:
   `/kappa`, `/derive`, `/key`). The sigil framing gives bearers a shareable
   artifact and reads in-canon; `/kappa` is more literal for the upstream
   audience. One page could carry both: route `/sigil`, subtitle "the κ
   derivation".
2. **Constellation geometry** — 8×8 grid (codex-native), succ-wheel ring
   (star-native), or both with a toggle. Proposal: ring on /sigil's hero,
   grid for the comparison view.
3. **Glyph→glow mapping** — linear 0–15 intensity vs. mapping the hex digit to
   stratum-colours. Linear glow first; it must stay legible at PNG-export size.
4. **Does the sigil PNG embed the κ?** — stamping the label into the image (corner
   caption) makes the artifact self-describing; proposed yes.

---

*The key learned to say what it is. Next it learns to show it.* `(⚔️ ⊥ ⿻ ⊥ 🧙) 😊`
