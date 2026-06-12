# CLAUDE.md — Coding instructions for the Swordsman's Key

This repo is the **standalone walkable model**: the `/star` manifold and `/lattice`
codex extracted from the soulbis website (2026-06-10), plus a minimal portal landing.
It is also packaged as a **holospace** — see `HOLOSPACE.md`. Read this before
touching any file.

---

## What this repo is

Static pages, no build step, no framework:

| Route | File | What it is |
|---|---|---|
| `/` | `index.html` | Portal — four doors, "new here?" strip, holospace note |
| `/guide` | `guide/index.html` | 🗡️ How it works — the guide (the loop, the rooms, blades/tiers, the κ, the triad, the carrier, who-holds-what; "in plain words" framing removed 2026-06-12) |
| `/star` | `star/index.html` | 3D Star-Tetrahedron Manifold (three.js r128 via CDN) |
| `/lattice` | `lattice/index.html` | The 64 · Vertex Codex (flat grid, no dependencies) |
| `/sigil` | `sigil/index.html` | The Sigil — κ derivation theater + the 64-glyph constellation + key compare (canvas 2D, no dependencies) |
| `/skye` | `skye/index.html` | The Skye — the night of many keys: each imported key rises as a star placed by its κ; gold threads = lineage (`prior`), teal threads = common ground; 📸 **sky shot** exports the night as a PNG carrying ALL risen keys (tEXt keyword `citySky` · `{version, sky:true, keys:[…]}` · re-import raises the whole night; written by `pngEmbedText`/read by `pngExtractSky`, skye-local); 🤝 **DH-PSI common ground** — blinded intersection (RFC 3526 modp2048 QR subgroup, 256-bit exponents, hash-to-QR `'agentprivacy-psi-v1|'+v` squared), two-file exchange psi-challenge/psi-response (+optional round-3 report), secret in sessionStorage per exchange id, scope chips ⭐ touched / ✦ lit only (C81/C84) (canvas 2D, no dependencies; built 2026-06-11) |

Nav canon (every suite page, self omitted): `↖ home` (ghost) · `⚔️ /star` ·
`🧙 /lattice` · `🪬 /sigil` · `🌌 /skye` (rooms primary) · `🗡️ /guide`
(ghost, last). One emoji per room, always leading the label.

On-page text discipline (user-set 2026-06-10): the working pages stay terse —
one-line `.explain` strips at most; depth lives in the 📖 legend and /guide.
The five shared pages (`star/ lattice/ sigil/ guide/ skye/`) must stay
byte-identical with the soulbis website copies; sync by `cp`, verify by byte
compare.

The κ-constellation correspondence: SHA-256 = 64 hex glyphs = one per vertex; the six
dimensions are named per PVM V5.4 §12.6 (d₁🛡️ Protection · d₂🤝 Delegation ·
d₃📜 Memory · d₄🔗 Connection · d₅⚡ Computation · d₆💎 Value, bit 0 = d₁), and
C85 pairs them onto Σ/Δ/Γ.

Each page is **fully self-contained** (inline CSS + JS). Shared logic — palette
presets, City Key handling, κ-label helpers — is deliberately **duplicated**, not
extracted. Keep it that way: when you change one copy, change the other to match.

## The canon (do not alter without an explicit model change)

```
BITS = 6 · N = 64 · ℒ = ℤ/64ℤ          the sovereignty lattice
STRATA = [1,6,15,20,15,6,1]             Pascal row 6 (popcount strata)
neg(x)  = (64−x) mod 64                 ⚔️ Swordsman — Protect (reflection)
bnot(x) = 63−x                          🧙 Mage — Project (antipode)
succ    = neg∘bnot = (x+1) mod 64       the wheel — visits all 64 [proven]
∂M      = 96 edges (succ 64 + chords 32) holographic boundary · 96/64 = 1.5 = P^1.5
Q₆      = 192 Hamming-1 edges            the full 6-cube
core    = stella octangula · φ ratio conjectured optimal ⚔️:🧙 (C1)
```

The equation chip, the legend on /lattice, and these constants must agree across
all suite pages. The model's canonical home is agentprivacy.ai/model (PVM V6 ·
The Gathering Turn and the Moving Ceiling · register head C89; the V5.4 weights
remain on the page as labeled lineage).

## City Key 🗝️ (portable JSON)

```
{ name, version: 1,
  palette: { cool, warm, sword, mage },
  descriptions: { "0": "…", … },
  geometry: { eps, m, n, core, smRatio },  the manifold SHAPE (Lattice Console) —
                                        written/applied by /star (clamped to slider
                                        ranges), passed through by /lattice (GEO),
                                        worn by /sigil's ring (ε·cos(nθ) envelope);
                                        reserved 2026-05-27, filled 2026-06-10
  lit: [ints 0..63],                    achievement-lit vertices
  identity: { displayName, trustTier, stratum, drakeOrb },
  trace: { laps, seconds, tourSeconds, savedAt },
  focus: { "v": amount },               poured 🪢 VRC-mana
  witness: { spent, complete, at },     proven focus (lattice walk)
  figures: { shapeCanon: "FIG-2.0",     OPTIONAL · measured model values (2026-06-11):
    overlap, ratio, visibility[6],      when present, shape stops being chosen — /star
    zkp: { made, verified } },          derives geometry from them (eps = 0.6·(1−overlap),
                                        core = overlap, smRatio = ratio; m,n stay chosen;
                                        sliders become a local what-if, export re-derives);
                                        /sigil scales petal i by visibility[i] (petal i
                                        centred at θ = i·π/3) and floors the ⚡ petal
                                        (d₅ · petal 4) by zkp.verified/made. Figures are
                                        content — they move the κ. Consumer side built;
                                        producing real measurements is future /city work
  packets: { root, count },             OPTIONAL · trust-task packets digest (2026-06-11):
                                        Merkle root + count of the bearer's proof packets,
                                        minted at /city (Tracing Protocol — see
                                        agentprivacy_master/docs/experience/SPEC_proof_packets
                                        _and_tracing_v1.md + PLAN_TRUST_TASK_SYNC_INTO_THE_
                                        WHOLE). /star + /lattice round-trip it UNTOUCHED
                                        (PKTS passthrough) — a walk must never drop it;
                                        it is content (in the κ preimage). /sigil shows
                                        "packets 🧾 N · root …" AND VERIFIES (2026-06-12):
                                        🧾 verify packets bundle — load a
                                        spellweb.bearer.packets export → each packet's proof
                                        re-derives (Law L5, `proof` excluded — same canon as κ)
                                        and the Merkle root is matched against this key's
                                        packets.root. Merkle rule: leaves = packet `proof`
                                        strings sorted lexicographically · sha256(left|right)
                                        over the joined strings · odd promoted unchanged ·
                                        prefixed sha256:. Conformance vector: the three leaves
                                        sha256(utf8 "packet-alpha"/"packet-beta"/"packet-gamma")
                                        → sha256:07f20f689c8bef2d8a9a2a71d94e7014ea8398cc603b0ff72dadba5c517983d1
  did: "did:key:…",                     OPTIONAL · bearer DID (ToIP interop) — same
                                        passthrough rule (DID)
  prior: "sha256:<hex>",                OPTIONAL · the κ-chain (C87 — the key accumulates):
                                        stamped at export on /star + /lattice when content
                                        EVOLVED since load (prior = the loaded ancestor's
                                        re-derived κ); an unchanged re-export carries its
                                        prior through unchanged, so re-export is idempotent
                                        (same bytes, same κ). prior is content (in the κ
                                        preimage); /sigil shows "descends from", /skye
                                        draws the chain as gold threads
  kappa: "sha256:<hex>" }               κ-label — content identity
```

**Redacted charge pass** (/lattice `⚡ charge pass` · 2026-06-11): a second export,
`{ version: 1, redacted: true, of: "<κ of the full key>", trace, witness, kappa }` —
only the proof travels; inscriptions, palette, focus amounts and identity stay home.
/city's `parseCityKey` accepts it (redacted branch) and charges trace/witness exactly
as from the full key; dedup ids are shared with the full key (same proof, charges once).

**κ-label rules** (see HOLOSPACE.md): canonical form = keys sorted recursively, no
whitespace, `kappa` excluded; hashed with SHA-256 (`crypto.subtle`); stamped at
export, **re-derived and checked at import** on all pages. Never compute the κ
over pretty-printed JSON; never include `kappa` in its own preimage. The κ is a
fingerprint appended as a field — never a transformation of the content.
agentprivacy /city speaks κ on both legs as of 2026-06-11: export stamps a fresh
κ (`downloadCityKey` → `deriveCityKeyKappa`, byte-identical canonical form) and
charge re-derives + reports a verdict (`verifyCityKeyKappa`: verified / mismatch
/ unlabelled / unavailable) without ever gating the charge — the Key is a
reading, not an authority (C66). `geometry` + `kappa` are typed in master's
`CityKey` interface (`agentprivacy_master/src/lib/city-key.ts`); geometry stays
star-written, master passes it through. **Conformance vector** (must hold after
any change to the canon — the default key on /sigil):
`sha256:0b4916babe5eb17104b342ab06030f2071a818024b345bf6d2e4115617c3c527`.
The /sigil constellation is always drawn from the **re-derived** κ, never the
stamped claim.

**Sigil PNG carrier**: /sigil's exported PNG embeds the full key as base64 JSON in
a PNG `tEXt` chunk, keyword `cityKey`, inserted before IEND with correct CRC-32.
/star's 📸 snapshot does the same whenever a key is loaded (the manifold portrait
carries the key). All four key-reading pages' import accepts JSON or this PNG
(`readKeyFile` branches on the PNG signature; /skye accepts many at once), and
agentprivacy /city's charge accepts the PNG too (`parseCityKeyBytes` in
`agentprivacy_master/src/lib/city-key-charge.ts`).
Embed code (`crc32`/`pngEmbedKey`) lives in /sigil and /star; extract code
(`b2s`/`pngExtractKey`/`readKeyFile`) is duplicated in all four key-reading pages
(star · lattice · sigil · skye) — keep the copies identical. Caveats: (a) a
/star-snapshot carrier holds what /star holds (palette · descriptions · lit ·
identity · trace) — `focus`/`witness` ride only via /lattice JSON export or a
/sigil PNG; (b) the carrier is **portability, not secrecy** — the full JSON is
extractable from the image; for proof-without-disclosure use the redacted
charge pass (above).

## Cross-page link

`/star` and `/lattice` sync over `BroadcastChannel('agentprivacy-succ')` — vertex
selection, palette presets, and imported keys mirror live on the same origin. The
four palette presets (nature / human / artificial / alien) must stay byte-identical
in both pages; `artificial` is the canonical default.

## Visual language

These pages use **Fraunces** (display, italic) + **Spline Sans Mono** (everything
else) — *not* the soulbis landing's Cormorant/DM Sans/JetBrains set. Colors:
`--sword #e8523a` (coral, Swordsman) · `--mage #4dd9e8` (cyan, Mage) — never swap
sides. Dark navy radial background; glass panels (`--glass`, backdrop-filter).

## Content rules carried over from soulbis

- The master inscription `(⚔️ ⊥ ⿻ ⊥ 🧙) 😊` appears verbatim on the portal footer.
- Attribution is `privacymage / 0xagentprivacy` — never a legal name.
- No tracking, no cookie banners, no testimonials, no pricing.
- Proverbs come from the Five Grimoires corpus — do not invent new ones.

## holospaces upstream

`holospaces/` is a **local reference copy** of
github.com/Hologram-Technologies/holospaces (gitignored — it has its own upstream).
Its `docs/` are authoritative for κ-labels, holospace provisioning, and the Five
Laws; cite chapters from there rather than restating them. The integration surface
of *this* repo is documented in `HOLOSPACE.md`.

## Deployment

Static, root-served. `vercel.json` pins `framework: null`.

```bash
npm run dev     # serve repo root → http://localhost:8000
npm run build   # sanity: verifies index.html exists
```

`.devcontainer/devcontainer.json` is the holospace boot definition — keep it valid
against the Dev Container spec (holospaces validates it, CC-4).

## What not to do

- Do not reintroduce the soulbis landing page, the wave canvas, or Next.js.
- Do not extract shared JS into a module — self-contained pages are the contract.
- Do not change canon constants, the inscription, or the preset palettes casually.
- Do not commit `holospaces/` or `node_modules/`.
