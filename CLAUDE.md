# CLAUDE.md — Coding instructions for the Swordsman's Key

This repo is the **standalone walkable model**: the `/star` manifold and `/lattice`
codex extracted from the soulbis website (2026-06-10), plus a minimal portal landing.
It is also packaged as a **holospace** — see `HOLOSPACE.md`. Read this before
touching any file.

---

## What this repo is

Three static pages, no build step, no framework:

| Route | File | What it is |
|---|---|---|
| `/` | `index.html` | Portal — three doors, holospace note |
| `/star` | `star/index.html` | 3D Star-Tetrahedron Manifold (three.js r128 via CDN) |
| `/lattice` | `lattice/index.html` | The 64 · Vertex Codex (flat grid, no dependencies) |
| `/sigil` | `sigil/index.html` | The Sigil — κ derivation theater + the 64-glyph constellation + key compare (canvas 2D, no dependencies) |

Planned fourth rung: `/skye` — the many-keys night sky (see the plan doc). The
κ-constellation correspondence: SHA-256 = 64 hex glyphs = one per vertex; the six
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
all three pages. The model's canonical home is agentprivacy.ai/model (PVM V5.4).

## City Key 🗝️ (portable JSON)

```
{ name, version: 1,
  palette: { cool, warm, sword, mage },
  descriptions: { "0": "…", … },
  lit: [ints 0..63],                    achievement-lit vertices
  identity: { displayName, trustTier, stratum, drakeOrb },
  trace: { laps, seconds, tourSeconds, savedAt },
  focus: { "v": amount },               poured 🪢 VRC-mana
  witness: { spent, complete, at },     proven focus (lattice walk)
  kappa: "sha256:<hex>" }               κ-label — content identity
```

**κ-label rules** (see HOLOSPACE.md): canonical form = keys sorted recursively, no
whitespace, `kappa` excluded; hashed with SHA-256 (`crypto.subtle`); stamped at
export, **re-derived and checked at import** on both pages. Never compute the κ
over pretty-printed JSON; never include `kappa` in its own preimage.

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
