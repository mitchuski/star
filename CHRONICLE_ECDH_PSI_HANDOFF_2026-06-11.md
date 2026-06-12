# Chronicle — ECDH-PSI common ground · the handoff (2026-06-11)

**Status: BUILT the same day** — the bearer un-held it within the session
("lets also start the next session ecdh psi i held in this context"). Landed as
the 🤝 **Common ground (DH-PSI)** card on /skye. Implementation deviates from
§3's curve suggestion deliberately: instead of vendoring a curve library, the
build uses the **RFC 3526 2048-bit MODP group** (id 14 — Miller-Rabin-verified
safe prime in the page constant) with hash-to-QR by squaring and **256-bit
short exponents** (TLS-DHE practice), keeping the page fully self-contained
with BigInt only. Classic DH-PSI, same security story (DDH in QR_p), zero
dependencies. All §6 acceptance checks verified headlessly: ∩ {12,33,63}×
{12,40,63}={12,63} · empty ∩ · full overlap · tampered point drops (not
crashes) · transcript enumeration-resistant · existing pages untouched
(conformance vector holds). §4's UX landed as designed: one import button
auto-routes rounds 1/2/3; the secret lives in sessionStorage keyed by exchange
id; scope chips (⭐ touched / ✦ lit only) implement §5's cap-what-you-enter.
The optional round-3 result file is labelled a *report, not a proof* — the
κ-commitment ZK layer remains the v3 rung. The remainder of this chronicle is
preserved as the design record it was. Origin of the design: the bearer's 2026-06-10
observation after the overlap lattice shipped — *between two bearers the keys
will always differ; the socially meaningful signal is what is in common* —
formalised as §v3.5 of `PLAN_KEY_EVOLUTION_MEASURED_GEOMETRY_2026-06-10.md`
and recorded in `CHRONICLE_COMMON_GROUND_ZERO_KNOWLEDGE_2026-06-10.md`.

---

## 1. What it is, in one paragraph

Today's Compare (movement ③ on /sigil) and the /skye teal threads learn the
intersection by reading **both keys in full** — the plaintext sky. The PSI rung
learns the ∩ and **only** the ∩: each bearer blinds their touched-vertex set
with a secret scalar, the blinded sets are exchanged, and after a second
blinding pass the matching elements reveal exactly the common vertices and the
other side's set *size* — nothing else. Information discovery with zero
knowledge: picture-first social discovery where the keys never leave home.

## 2. Why naive hashing fails here (do not skip this)

The domain is 64 vertices. Unsalted tokens `H(v)` are enumerable in
microseconds — publishing them publishes the whole set. Any build that "hashes
the vertex numbers and compares" is a privacy placebo. Small domains require
**blinded** intersection; that is the entire reason for the protocol below.

## 3. The protocol (classic two-party ECDH-PSI)

Browser-feasible, no circuits, ~64 curve ops worst case per side.

```
Setup    A holds secret scalar a; B holds secret scalar b.
         T_A = { H2C(v)·a : v ∈ touched(A) }      (hash-to-curve, then scalar mult)
Round 1  A → B : T_A (shuffled)
Round 2  B → A : { t·b : t ∈ T_A }   plus   T_B = { H2C(v)·b : v ∈ touched(B) }  (shuffled)
Finish   A computes { t·a : t ∈ T_B } and intersects with { H2C(v)·ab } —
         matches are the common vertices. A learns ∩ and |T_B|; B learns |T_A|
         (and ∩ too, if A sends the matched indices back — make that optional).
```

Implementation candidates:
- **Curve25519 via @noble/curves** — vendored as a single inline ES module
  string (the pages are self-contained; no build step). `ristretto255` gives
  clean hash-to-group (`hashToCurve`), avoiding cofactor pitfalls.
- WebCrypto alone is NOT sufficient (no scalar-mult API on raw points) — do
  not try to fake it with ECDH key agreement per element pair.
- Shuffle both transmitted sets; otherwise order leaks vertex identity.

## 4. The exchange UX (no server — the carrier does the transport)

Two-message protocol = two files, exchanged however people already exchange
sigils (chat, email, QR later):

1. **/sigil PSI mode** (or /skye): "🤝 common ground without showing your key"
   → A exports `psi-challenge.json` `{ version, psi:1, round:1, set:[…points] }`.
2. B imports the challenge → page computes round 2 → B exports
   `psi-response.json` (B's blinded reply + B's own blinded set).
3. A imports the response → the ∩ lattice renders **from the protocol instead
   of the plaintext** — same teal ov-grid as today's Compare, sourced
   differently. Optional third file back to B so both sides see the ∩.

Secrets: the scalar lives in `sessionStorage` (or is re-derived from a
passphrase); it must survive between exporting the challenge and importing the
response, and a fresh scalar per exchange is fine (no long-term key).

## 5. What it composes with (design constraints, from the register)

- **κ as commitment (v3 seam):** later, a ZK layer can prove the PSI inputs are
  consistent with the bearer's stamped κ — no inventing vertices never walked.
  Don't block on this; note it in the legend as the honest boundary.
- **C81/C84 existence-leak budget:** even the intersection's *size* is an
  attestation. The UI must let a bearer **cap or curate what they enter**
  (e.g. enter only lit vertices, or only a chosen subset) — disclosure is a
  choice, also at the meta level.
- **C87 prior chain:** PSI over two generations of the *same* lineage is a
  legitimate use (how much ground did my key gain?) — works out of the box.
- **Text discipline:** working-page copy stays one line ("learn what you share
  — and only that"); the protocol explanation lives in the 📖 legend.

## 6. Acceptance checks for the building session

1. Two known keys with touched sets {12, 33, 63} and {12, 40, 63} → ∩ renders
   exactly {12, 63}; neither side can name the other's non-shared vertices
   from the transcript (inspect the files: only curve points, shuffled).
2. Empty intersection → "no common ground yet" state, no error.
3. Same key both sides → full overlap, ∩ = touched set.
4. Transcript replay: importing the same response twice is idempotent.
5. A tampered response (bit-flipped point) fails gracefully (invalid point →
   element dropped, not a crash).
6. The conformance vector and all existing page behaviour untouched (PSI is
   additive; no change to canonical form or the κ canon).

## 7. Where it lands

- /sigil Compare gains a third source: import key B **or** run the exchange.
- /skye eventually gets the same option pairwise ("the zero-knowledge sky").
- The legend row on both pages already names this rung ("the boundary") —
  flip its wording from *designed, not built* to *built* when done.

*Learn the common ground, and only the common ground — divergence stays
private, as it always was.* `(⚔️ ⊥ ⿻ ⊥ 🧙) 😊`
