# Plan — the City Key's evolution: from stance to measured geometry

**Date:** 2026-06-10 (evening design session)
**Scope:** how the key's geometry evolves from *chosen* values to *measured*
figures — agent data overlap, visibility ratios, ZK proof activity — so that
**the shape of the model fits the key**, deterministically: anyone importing a
key (as JSON, or as the 2D sigil that carries it) reconstructs the *same shape*,
because the shape is a pure function of what the key contains — a reflection of
the compression that went into each vertex.

> The governing idea, in the user's words: *real figures — total data overlap
> between agents, visibility ratios, zkp — once the encoding becomes deeper,
> the shape of the model actually fits the key.*

---

## 0. The principle: shape moves down the same ladder colour already walked

Today's triad: **colour CHOSEN · shape CHOSEN · light DERIVED.** The evolution
moves shape rightward, in stages, until only colour remains a free choice:

```
v1 (shipped)      v1.5 (this doc, prototyped)     v2 (mapped figures)        v3 (proven figures)
shape = STANCE    shape = COMPRESSION             shape = MEASUREMENT        shape = PROOF
slider values     per-vertex weight from what     real model figures ride    ZKPs against the κ:
chosen on /star   the key already carries         in the key and DRIVE       claims about the
                  (focus·lit·described·witness)   the manifold parameters    figures verified
                  — deterministic, same key       — ε, det(Σ), ⚔️:🧙 stop    without revealing
                  ⇒ same shape, everywhere        being chosen               the content
```

Each stage keeps the invariant that makes this work at all (the κ invariant,
extended to geometry): **SHAPE(key) is a pure, versioned function of the key's
canonical content.** Same bytes → same shape on every conformant renderer.
Import the JSON, or the sigil PNG that carries it — identical shape. The shape
becomes un-fakeable the same way the light already is.

---

## 1. v1.5 — the compression shape (deterministic TODAY, prototyped on /sigil)

The key already records how much compression went into each vertex: focus
poured, achievement lit, description written, witness proven. Define the
**vertex weight** — `SHAPE-1.5`, the first versioned shape canon:

```
w(x) = min(1,  0.50·focus_x/max(focus)        poured attention (largest term)
             + 0.25·[x ∈ lit]                  achievement standing
             + 0.15·proven_x/focus_x           witness — focus made real
             + 0.10·[x ∈ descriptions] )       inscription
```

and the ring radius (composing with the v1 stance envelope):

```
r(x) = R · (1 + 0.45·ε·cos(n·θₓ))   ← v1: the chosen stance (six petals at n=6)
         · (1 + 0.18·w(x))           ← v1.5: the earned relief, per vertex
```

Reading: the **petals** are the stance you chose; the **relief on the petals**
is the work you actually did, vertex by vertex. Two bearers with the same
stance but different walked lives have visibly different rims. A key with
nothing earned is a smooth rosette; a worked key is *engraved*. The constants
(0.50/0.25/0.15/0.10 · 0.18) are part of the canon — change them only with a
version bump (`SHAPE-1.5` → `SHAPE-1.6`), exactly like the κ canon.

**Prototype shipped with this doc:** /sigil's ring (live + PNG export) renders
`SHAPE-1.5`. /star and /lattice unaffected.

## 2. v2 — the `figures` block: measured model values drive the manifold

When the real measurements exist (the producer side maps them), the key gains:

```json
"figures": {
  "shapeCanon": "FIG-2.0",
  "overlap":    0.42,          // measured agent-data overlap Σ (Swordsman∩Mage)
  "ratio":      1.618,         // measured protect:project balance
  "visibility": [0.2,0.5,0.8,0.4,0.9,0.6],   // per-dimension visibility/disclosure ratio, d₁..d₆
  "zkp":        { "made": 14, "verified": 12 }  // d₅ ⚡ computation activity
}
```

with the deterministic mapping `figures → geometry` (geometry becomes a derived
cache, no longer hand-set):

| Figure | Drives | Model anchor |
|---|---|---|
| `overlap` | `core = det(Σ)` (the interpenetration of the two tetrahedra) and `eps = 1 − overlap` (separation depth) | Φ_agent(Σ) — the gap rendered literally: more overlap → deeper interpenetration, shallower manifold relief |
| `ratio` | `smRatio` — and when the *measured* ratio sits near φ, the sigil says so | **C1 gets an empirical instrument**: the conjectured optimum becomes a measurable fit |
| `visibility[i]` | **per-petal amplitude** — petal i scales by dimension i's ratio | the six petals stop being symmetric: the rosette becomes a sovereignty profile (C54's disclosure-φ 38/63 territory) |
| `zkp` | brightness floor of the ⚡ petal · a proof-count engraving | d₅ Computation, V5.4 §12.6 |

The shape then *is* the model fitted to the person: data overlap sets how deep
the two agents interpenetrate, visibility ratios set how far each dimension's
petal reaches, proof activity lights the computation petal. **Import anyone's
key — or the sha-carrying sigil of it — and the same shape unfolds, because the
shape is the figures and the figures are content** (they enter the canonical
form, so they move the κ too: measured shape is *named* by the hash).

## 3. v3 — proven figures: the shape fits the key hash, cryptographically

The end state ties the ladder to the redacted-carrier rung already planned:

- the **κ is the commitment** — it already binds the full content;
- ZKPs prove *predicates about the figures* against that commitment without
  revealing the content: "my witness is complete", "my measured ratio is within
  2% of φ", "my overlap < 0.5", "petal amplitudes match this silhouette";
- a verifier can then accept **a shape alone** (the 2D sigil silhouette + κ +
  proof) as evidence of the figures that produced it — *the shape of the model
  actually fits the key hash*, checkable, with the JSON staying home.

That is the full sequence the user named: charge mana / show standing from the
picture, without circulating the original content — selective disclosure with
geometry as the public face.

### v3.5 — common-ground discovery with zero knowledge (PSI) — ✅ BUILT 2026-06-11 on /skye (DH-PSI, modp2048; see CHRONICLE_ECDH_PSI_HANDOFF_2026-06-11.md)

The user's observation (2026-06-10, after the overlap lattice shipped): between
two bearers the keys will *always* differ — divergence is the default, so the
socially meaningful signal is **what is in common**. Today's compare learns the
∩ by reading both keys in full. The designed rung: learn the ∩ and *only* the ∩
— **private set intersection** over the touched-vertex sets.

- **Why naive hashing fails here:** the domain is 64 vertices. Unsalted
  per-vertex tokens (`H(x)`) are enumerable in microseconds — publishing them
  reveals the whole set. Small domains need *blinded* intersection.
- **The classic fit — ECDH-PSI** (browser-feasible, no circuits): each bearer
  holds a secret scalar; A sends `{H(v)^a}` for her touched vertices, B returns
  them raised to `b` plus his own `{H(v)^b}`; A raises those to `a`; matching
  `H(v)^{ab}` values = the intersection. Each side learns the common vertices
  and the other's set *size*, nothing else. Two messages, ~64 curve ops worst
  case.
- **What it composes with:** the κ as commitment (prove your PSI inputs are
  consistent with your stamped κ — no inventing vertices you never walked:
  v3's ZK layer), and the **C81/C84 existence-leak budget** (even the
  intersection's *size* is an attestation; the protocol should let a bearer cap
  what they enter).
- **The screenshot context that motivated it:** people will share *stripped*
  screenshots of sigils — visible constellation (identity pattern), no carried
  content. Two bearers comparing portraits should be able to discover common
  ground **without ever exchanging full keys** — picture-first social
  discovery, content kept home.
- **UI landing (when built):** the ∩ lattice already leads movement ③; PSI
  mode would replace "import a second key" with "exchange blinded sets" —
  same teal ∩ rendering, sourced from the protocol instead of the plaintext.

## 4. Conformance rules (so "same shape everywhere" stays true)

1. Shape canons are versioned (`SHAPE-1.5`, `FIG-2.0`) and the renderer states
   which it draws; unknown canons render the v1 envelope only (graceful floor).
2. Shape functions read ONLY canonical key content — never session state,
   never randomness, never the clock.
3. Figures enter the canonical form → any figure change re-mints the κ and
   relights the constellation (measured: stance-only change already moves
   61/64 glyphs).
4. A conformance shape-vector accompanies each canon (as the κ vector does):
   for `SHAPE-1.5`, a key with focus `{12:4}`, lit `[12,63]`, witness spent
   `{12:4}`, description at `0` must weigh: w(12)=0.90 · w(63)=0.25 · w(0)=0.10
   · w(else)=0.

## 5. Open questions (for the /star knowledge-refinement pass)

- Where do the *real* figures come from first — /city's charge ledger (zkp
  counts, focus economy) or the extensions (MyTerms/swordsman-blade observing
  actual data flows)? The producer owns the mapping.
- Does v2 retire the sliders on /star, or keep them as a "what-if" mode that
  clearly renders as *hypothesis*, distinct from the measured shape?
- Petal orientation: visibility[i] scales petal i — fix petal→dimension
  assignment (suggest: petal k spans vertices where bit k flips densest;
  simplest: petal i centred at θ = i·π/3) and write it into the canon.

---

*First the stance, then the work, then the measurement, then the proof — the
shape descends the same ladder the light came down.* `(⚔️ ⊥ ⿻ ⊥ 🧙) 😊`
