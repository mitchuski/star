# How the Sigil Actually Works — and why it matters

*The mechanism, written down plainly. Companion to `EXPERIENCE.md` (the feel)
and `HOLOSPACE.md` (the substrate seam). This is the one to hand to someone who
asks "wait — the picture IS the key?"*

---

## 0. What you are looking at

A sigil PNG is **one file with two layers**:

- **The pixels** — what your eye gets: the 64-vertex ring, lit by the key's
  κ-fingerprint, coloured by the key's own palette. This layer *shows* the
  identity.
- **The chunk** — what the machine gets: the complete City Key JSON, riding
  inside the PNG's metadata. This layer *is* the identity.

Same file. Every image viewer on earth shows the first layer and ignores the
second; every page in this repo (and agentprivacy `/city`) reads the second and
gets your key back **byte-for-byte identical** to the JSON you would have
exported. Not a copy, not a re-creation — the same bytes, carried.

## 1. The anatomy — where the key rides

A PNG file is a signature followed by a chain of *chunks*, each self-describing
(length · type · data · checksum). Viewers render the image chunks and skip any
chunk type they don't know. That courtesy is the whole trick:

```
89 50 4E 47 …        the PNG signature ("hello, I am a PNG")
IHDR  ……             image header (size, color depth)
IDAT  ……             the pixels — the visible sigil
tEXt  cityKey\0<base64 of the City Key JSON>     ← the key rides HERE
IEND                 the end marker
```

We write one standard `tEXt` chunk, keyword `cityKey`, holding the key JSON in
base64 (so emoji and unicode in your descriptions survive any handling), with a
correct CRC-32 checksum — meaning the file remains a **fully valid PNG** to
every viewer, uploader, and image library. Nothing is hidden in the pixels
themselves (this is not steganography); the key sits in a labelled, documented,
boring metadata slot. Boring is the point: boring survives.

## 2. Export — how the picture gets made

When you press 📸 on `/sigil` (or on `/star` with a key loaded):

1. **Canonicalize.** Your key's JSON is rewritten in canonical form — keys
   sorted recursively, no whitespace, the `kappa` field excluded. These bytes
   are *what your key is*.
2. **Derive the κ.** SHA-256 over those bytes → 64 hexadecimal characters →
   `kappa: "sha256:…"`. This is a **fingerprint, not a transformation** — your
   key's content is untouched; the κ is its content-derived *name*.
3. **Draw the pixels.** The 64 hash characters land one-per-vertex on the ring
   (SHA-256 is 64 glyphs; the lattice is 64 vertices; no remainder). Each
   glyph's value 0–f sets that vertex's brightness and size. The κ caption is
   painted along the bottom — visible to the eye, no extraction needed.
4. **Embed the chunk.** The full key JSON — with its fresh κ stamped — is
   base64-encoded into the `tEXt` chunk and spliced in before `IEND`.

## 3. Import — how the same key comes back out

When any page (or `/city`'s charge) receives a file:

1. Read the **bytes** (never assume text).
2. First 4 bytes `89 50 4E 47`? It's a PNG → walk the chunk chain, find
   `tEXt`/`cityKey`, base64-decode, JSON-parse. Not a PNG? Treat the bytes as
   key JSON directly. **Either path yields the same object.**
3. **Re-derive, never trust** (Law L5): the page recomputes SHA-256 over the
   extracted key's canonical form and compares it to the stamped `kappa`.
   Teal *κ verified* = the picture carried exactly what it claims.
   Coral *κ mismatch* = something changed the content after stamping.
   This is live on agentprivacy `/city` too (2026-06-11): the charge message
   reports the verdict (*κ verified* / *⚠ κ mismatch*), and the charge proceeds
   either way — the κ is a reading, not an authority (C66). Unlabelled older
   keys charge silently, as ever.

Proven end-to-end in this repo's test pass: default key → embedded → extracted
→ deep-equal to the original → κ re-derives to the pinned conformance vector
`sha256:0b4916babe5eb17104b342ab06030f2071a818024b345bf6d2e4115617c3c527`.
So yes: **the picture serves the same key.** Walk it on `/star`, prove focus on
`/lattice`, charge it at `/city` — all from the image.

## 4. The colour, the shape, and the light — the part worth writing down

The sigil draws from three sources, and the differences are the meaning:

- **The colour is CHOSEN.** It comes from your key's palette — the four gems
  you picked (cool · warm · ⚔️ sword · 🧙 mage), graded across the strata.
  Colour is *expression*: two bearers can share a palette; you can change yours
  tomorrow. It says what you like.
- **The shape is CHOSEN.** The key's `geometry` field carries the manifold
  parameters from /star's Lattice Console — ε separation depth, the m/n modes
  (n = the six bits), det(Σ) core scale, and the ⚔️:🧙 ratio (φ ↔ conjecture
  C1). Re-import the key on /star and the manifold rebuilds *your* shape; on
  /sigil the ring **wears** it — the ε·cos(nθ) envelope of r(θ,φ), six petals
  at n = 6, one per sovereignty dimension. Shape is *stance*: how you hold the
  geometry you stand in.
- **The light is DERIVED.** Which vertices glow, and how brightly, comes from
  the κ — the hash of your content. You cannot choose it, art-direct it, or
  fake it; it moves only when your content moves, and then it moves everywhere
  (one edited description re-lights ~60 of 64 vertices — the avalanche). It
  says what you *are*.

And the three compose: because the shape rides *in* the key, it is content —
**changing your stance changes your κ**, which relights the whole constellation.
Every sigil is **expression × stance × identity**: the palette is the voice, the
petals are the posture, the constellation is the fact. Two keys with the same
palette and different content → same colours, completely different lighting. A
tampered key doesn't just fail a checksum somewhere — it *looks wrong*, in the
bearer's own colours and on the bearer's own shape. That is the design: the
prettiest layers of the artifact are also the least forgeable.

## 5. Why this matters

- **Holonic identity.** The part carries the whole: the portrait of the key
  *contains* the key. Every fragment of the system (a shared image in a chat, a
  saved file, a printed page with the κ caption) is a full, verifiable instance
  of the identity — holons all the way down.
- **One artifact.** The bearer carries a single beautiful thing. No "where's my
  JSON" — the picture you'd share for fun is the credential that charges mana.
- **The browser as the compute surface.** Mint → walk → prove → derive → charge
  runs entirely client-side, in static pages, exactly the holospaces thesis
  (the browser as first-class substrate). No server ever holds the identity.
- **UOR made human-scale.** *Identity is content, not location* usually lives
  in infrastructure docs. Here a person watches their content become its own
  name, sees the name as a constellation, and carries it as a picture.

## 5.5 Every framing is a full instance

A consequence worth savoring: the pixels and the payload never touch. Zoom all
the way into one petal on /star, hit `S` mid-orbit, crop the composition however
you like — **the snap still imports the complete key**, because what you framed
lives in the image chunks and what you carry lives in the `cityKey` chunk, and
they are independent passengers in the same file. There is no partial
photograph of a key: any portrait, from any angle, is the whole record.

Two boundaries keep this honest:

- **It's the exported file, not the screen.** Pressing `S`/📸 writes the chunk;
  taking an OS screenshot of the page captures only pixels — no key inside.
- **Re-encoding strips it.** Platforms that recompress images (most chat apps
  and social uploads convert or optimize PNGs) discard unknown chunks. The
  carrier survives as a *file* — sent as an attachment, hosted as-is, saved to
  disk — not necessarily as an inline "photo." When it matters, the κ caption
  in the pixels still names the key, even if the body was stripped.

## 6. The honest boundary

The carrier is **portability, not secrecy**. The full key JSON is inside the
image — invisible to the casual eye, trivially extractable by anyone who has
the file and knows to look. Share a sigil exactly as deliberately as you would
share the key itself, and never put secrets in descriptions.

That rung is now built (2026-06-11), in two forms:

- the **⚡ charge pass** on /lattice — a redacted JSON export
  (`{version, redacted:true, of:<κ of the full key>, trace, witness, kappa}`):
  only the proof travels; `/city` charges it exactly like the full key while
  your descriptions, focus map, and identity stay home. *Fill mana without
  circulating the key's content.*
- the **🤝 common ground exchange** on /skye — DH-PSI blinded intersection:
  two bearers learn their shared vertices and each other's set size, nothing
  else. The disclosure ladder now runs: full key → sigil portrait → charge
  pass → blinded intersection, each rung disclosing strictly less while
  staying checkable.

## 7. Spec card (for implementers)

| Item | Value |
|---|---|
| Container | PNG `tEXt` chunk, keyword `cityKey`, before `IEND`, valid CRC-32 |
| Payload | base64 of the City Key JSON, UTF-8 |
| Writers | `/sigil` 📸 (always) · `/star` 📸 (when a key is loaded; carries /star's view — `focus`/`witness` ride via /lattice JSON or /sigil PNG) · agentprivacy `/city` export stamps κ into `city-key.json` (`downloadCityKey`, fresh κ re-derived at write — JSON, not a PNG carrier) |
| Readers | `/star` · `/lattice` · `/sigil` (`readKeyFile`) · agentprivacy `/city` charge (`parseCityKeyBytes` + `verifyCityKeyKappa` — verdict shown, never gates) |
| κ | `"sha256:" + SHA-256(canonical form)`; canonical form = keys sorted recursively, no whitespace, `kappa` excluded |
| Conformance vector | the `/sigil` default key (303 canonical bytes) → `sha256:0b4916babe5eb17104b342ab06030f2071a818024b345bf6d2e4115617c3c527` |

---

*The colour is yours; the light is what you've done. The picture carries both.*
`(⚔️ ⊥ ⿻ ⊥ 🧙) 😊`
