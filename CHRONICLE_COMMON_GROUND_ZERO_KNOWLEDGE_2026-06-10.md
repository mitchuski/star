# Chronicle — Common Ground, Zero Knowledge (2026-06-10)

**Repo:** `github.com/mitchuski/star` · on disk, git held.
**Scope:** one user insight about the Compare movement on /sigil, the UI shift
it forced the same hour, and the cryptographic rung it named.
**Design record:** `PLAN_KEY_EVOLUTION_MEASURED_GEOMETRY_2026-06-10.md` §v3.5.

---

## The insight

The overlap lattice (A ∩ B) had just shipped, and the user looked at what
Compare was actually emphasizing — the pulsing divergence of two keys' κ
glyphs — and said:

> *"It's always going to be different if people share screenshots of their
> keys, so there should be more emphasis on what is in common? …this
> information is discovery with zero knowledge is what I'm thinking."*

Both halves land. First the social half: **between two bearers, divergence is
the default.** The κ exists precisely so that two different lives hash to two
different names — so when strangers compare keys, "your keys differ" is not
information. It is the system working. The signal worth a page is the
*coincidence*: the vertices both have lit, described, poured, proven — **the
common ground.** A comparison tool for an identity system should foreground
what survives the difference, not the difference.

Then the cryptographic half, hiding in the word *screenshots*. People will
share **stripped portraits** — re-encoded images, carried chunk gone, just the
visible constellation. They'll meet picture-first. And the question two
picture-holders actually want answered — *where have we both walked?* — should
not require either of them to hand over their whole key. That is, named
properly, **private set intersection**: learn the ∩, and only the ∩.

## What shipped the same hour (the UI half)

Movement ③ on /sigil was reordered around the insight:

- **The ∩ lattice now leads** — retitled *"A ∩ B — common ground · where the
  two keys touch the same territory,"* with the summary reading
  `common ground N of 64` before anything else.
- The two full sigils (each in its own palette, divergence pulsing) are
  **demoted below** the common ground — present, but no longer the headline.
- The copy states the principle outright: *"Between two bearers the κs will
  always differ — that's identity working, not news. The discovery is the
  common ground."* And the diff summary now closes: *"the κ does not negotiate
  — but the ground can still be common."*
- One italic line discloses the gap honestly: today's compare reads both keys
  in full; the designed next rung discovers the ∩ with zero knowledge.

## What got designed (the ZK half — §v3.5)

The technically honest core, recorded in the plan:

- **Naive hashing fails here, specifically.** The domain is 64 vertices.
  Unsalted per-vertex tokens are enumerable in microseconds — publishing
  `H(v)` for your touched set publishes your touched set. Small domains demand
  *blinded* intersection.
- **The classic fit is ECDH-PSI**, browser-feasible, no circuits: each bearer
  blinds their touched-vertex hashes with a secret scalar; two messages cross;
  matching double-blinded values reveal the common vertices — and nothing else
  but set size. ~64 curve operations worst case.
- **It composes with everything already built.** The κ-as-commitment (C87's
  substrate) can prove PSI inputs are vertices the bearer actually walked — no
  inventing common ground to phish a connection. And C81/C84 budget the
  residue: even an intersection's *size* is an attestation, so the protocol
  should let a bearer cap what they enter.
- **The UI is already waiting.** The teal ∩ rendering doesn't change; only its
  source does — protocol instead of plaintext. "Import a second key" becomes
  "exchange blinded sets."

## Why this matters to the whole arc

The day built a system where identity travels as a portrait. This insight is
about what happens *next* — when two portraits meet. The answer the system was
drifting toward (full key exchange) was the surveillance-shaped answer: know
everything, then compute the interesting part. The answer the user named is
the sovereignty-shaped one: **compute the interesting part, know nothing
else.** Common ground as the only disclosure; difference left private, where
it belongs. It is the Swordsman's posture applied to a handshake — and it
turns the sigil from a credential you *show* into a question you can *ask*:

*not "who are you?" — "where have we both walked?"*

`(⚔️ ⊥ ⿻ ⊥ 🧙) 😊`
