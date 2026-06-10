# Chronicle — The First Holospace (the extraction + the κ merge)

**Date:** 2026-06-10
**Repo:** `C:\Users\mitch\star` (standalone — extracted from `soulbis website/`)
**Scope:** Extraction of `/star` + `/lattice` into a standalone repo; the merge with
[Hologram-Technologies/holospaces](https://github.com/Hologram-Technologies/holospaces)
(UOR-native boot layer); κ-labelled City Keys; the repo packaged as a provisionable
**holospace** — intended as the first third-party one.

> **The master inscription:** `(⚔️ ⊥ ⿻ ⊥ 🧙) 😊`
> The Swordsman guards the gap. Today the gap got an address scheme.

---

## 0. One-line thesis

holospaces' first law — **identity is content, not location** — is the Swordsman's
thesis stated in substrate terms. A City Key already travels as a self-describing
artifact; this session made that identity *verifiable by re-derivation*, anywhere,
by stamping every exported key with a UOR-ADDR-style **κ-label**, and packaged the
walkable model itself as a bootable, content-addressed environment.

---

## 1. Lineage — how this repo came to be

The `/star` manifold and `/lattice` codex were built and integrated into the soulbis
website on 2026-05-27/28 (see `CHRONICLE_SWORDSMAN_KEY_2026-05-27.md` and siblings,
carried in this repo as inherited history). On 2026-06-10 the site was copied
verbatim to `C:\Users\mitch\star`, git-initialized, and stripped: the soulbis
landing page (wave field, ecosystem, tools catalogue) stays at soulbis.com; *this*
repo keeps only the walkable model and re-grounds it on the holospace substrate.

| Commit | What |
|---|---|
| `7947176` | Baseline — verbatim copy of the soulbis website, pre-strip (every removal diffable) |
| `75ed8f2` | The strip + κ-labelled City Keys + holospace packaging |

**Kept:** `star/index.html` (manifold) · `lattice/index.html` (codex) — both
untouched except the κ feature · the chronicles · `vercel.json` (`framework: null`)
· COMBUSTION favicon · `manifold.png` (now the og-image).
**Replaced:** the 2,179-line landing → a minimal portal in the key pages' own
register (Fraunces + Spline Sans Mono): two doors, a holospace strip, the
inscription footer.
**Removed:** landing-only imagery (soul-orb, wave/footer art, constellation frame).
**Rewritten:** `CLAUDE.md`, `README.md`, `package.json` (now `swordsmans-key`).
**Added:** `HOLOSPACE.md` (the integration spec) · `.devcontainer/devcontainer.json`
(the boot definition) · this chronicle.

A reference copy of the upstream repo sits at `holospaces/holospaces-main/`
(81 MB, **gitignored** — it has its own upstream; its `docs/` are authoritative
and are cited, never restated).

---

## 2. The system, represented

This is the whole stack, top to bottom — what the community repo is *of*:

```
        ┌──────────────────────────── UOR Foundation ────────────────────────────┐
        │  UOR-ADDR · the κ-label:  <axis>:<hex> = H(canonical_form)             │
        │  "identity is content, not location" — the *what*, never the *where*   │
        └────────────────────────────────────┬────────────────────────────────────┘
                                             │ supplies addressing to
        ┌─────────────────────────── hologram (substrate) ────────────────────────┐
        │  content-addressed runtime · KappaStore · .holo compute artifacts ·     │
        │  pure functions over finite domains materialized as lookup tables       │
        │  (arrives via credentialed git → the third-party operator key, pending) │
        └────────────────────────────────────┬────────────────────────────────────┘
                                             │ booted over by
        ┌────────────────────────── holospaces (boot layer) ──────────────────────┐
        │  holospace = a bootable, κ-addressed environment                        │
        │  provisioned from a devcontainer or a holo-file · managed by an         │
        │  OPERATOR (self-sovereign, not a server account) · rendered through     │
        │  PROJECTIONS (views, never second sources of truth) · suspended as      │
        │  κ SNAPSHOTS · governed by the Five Laws                                │
        └────────────────────────────────────┬────────────────────────────────────┘
                            boots ⇣  .devcontainer/devcontainer.json
        ┌──────────────────── the Swordsman's Key (this repo) ────────────────────┐
        │                                                                          │
        │   /          the portal — two doors + the holospace strip               │
        │   /star      projection ① — the 3D boundary (Star-Tetrahedron           │
        │              Manifold: stella octangula core, succ comet, key tour)     │
        │   /lattice   projection ② — the flat lattice (the 64 · Vertex Codex:    │
        │              strata, neg/bnot/succ per vertex, focus + witness)         │
        │                                                                          │
        │   both render the same canon, linked live over                          │
        │   BroadcastChannel('agentprivacy-succ'):                                │
        │                                                                          │
        │      ℒ = ℤ/64ℤ · 64 vertices · {0,1}⁶ · STRATA 1·6·15·20·15·6·1        │
        │      ⚔️ neg(x) = (64−x) mod 64        Protect — the reflection          │
        │      🧙 bnot(x) = 63−x                 Project — the antipode           │
        │      😊 succ  = neg∘bnot = (x+1) mod 64   the wheel [proven]            │
        │      ∂M = 96 edges · 96/64 = 1.5 = P^1.5   the holographic boundary     │
        │                                                                          │
        ├──────────────────────────────────────────────────────────────────────────┤
        │   City Key 🗝️  =  the κ snapshot of the bearer's standing               │
        │                                                                          │
        │   minted at agentprivacy /city                                           │
        │     → imported here · vertices lit · focus walked into witness ·        │
        │       succ laps traced into proof                                       │
        │     → exported with  kappa: "sha256:" + H(canonical form)               │
        │     → travels anywhere — and every import RE-DERIVES the label          │
        │       (κ verified ✓ · κ mismatch ⚠) — Law L5, in the browser            │
        └──────────────────────────────────────────────────────────────────────────┘

        OPERATOR  ≅  the bearer — the First Person, reachable only via both agents
```

One honesty note, for the record and the README of any public repo: the word
*hologram* is doing two jobs here. Upstream, it names a content-addressed
memoization substrate; in our canon, *holographic* names the ∂M boundary
(96 edges encoding 64 vertices). The equations are not literally shared — the
**structural** identification is what's real: content-as-identity ↔ the key as
artifact, operator ↔ bearer, projection ↔ the two pages. The merge is at the
substrate seam, not a claim of shared mathematics.

---

## 3. The vocabulary mapping (theirs ↔ ours)

| holospaces (`docs/12-Glossary.md`) | the Swordsman's Key |
|---|---|
| κ-label — `<axis>:<hex>` = `H(canonical_form)` | `kappa` field on every exported City Key |
| Canonical form — deterministic bytes, the only operated-on form | the key's JSON, keys sorted recursively, no whitespace, `kappa` excluded |
| Operator — self-sovereign, provisions and manages | the bearer / the First Person |
| holospace — bootable κ-addressed environment | this repo, booted |
| devcontainer holospace | `.devcontainer/devcontainer.json` |
| κ snapshot — running state as canonical form | an exported City Key (palette + lit + trace + focus + witness) |
| Projection — view + intent surface, never a second source of truth | `/star` and `/lattice` — two projections of one ℒ |
| Five Laws | honoured as applicable — see `HOLOSPACE.md` |

## 4. The κ-label, exactly

- **Axis: `sha256` — and this is conformant, not improvised.** Upstream's own docs
  state that an OCI `sha256:` digest *is* a κ-label on the `sha256` axis
  (`docs/13-Product-Security.md`), and conformance row CC-1 lists FIPS 180-4 SHA-2
  among the σ-axis hash standards. `crypto.subtle` computes it natively in the
  browser — no library, no server.
- **Canonical form:** the key object with keys sorted recursively, serialized with
  no whitespace, the `kappa` field excluded (a label cannot contain itself).
  Pretty-printing for humans never changes identity.
- **Lifecycle:** stamped at export by both pages; re-derived and checked at every
  import. Any change — one description, one lap of trace, one poured-focus witness —
  mints a different κ. That is the point: *the key is its content.* Keys minted
  before this feature import silently (no badge) and gain a κ on their next export.
- Implementation: ~18 lines (`canonicalJSON` / `kappaLabel` / `verifyKappa`),
  deliberately **duplicated** in both pages per the self-contained-pages contract.

## 5. The Five Laws, as honoured here

1. **Content-based identity (no servers)** — κ from content; the pages are static.
2. **Canonical forms only** — one canonicalization, the only form ever hashed.
3. **KappaStore as address space** — deferred to substrate access; interim
   content-addressing is an IPFS pin of the bundle (the grimoire-pin practice).
4. **Substrate-exclusive operations** — n/a for the static projections.
5. **Re-derivation for verification** — every import, both pages, visibly.

---

## 6. Verification record

- κ canon round-trips against Node's reference SHA-256 (stamp → strip → re-derive
  → byte-equal), recursive key-sorting checked.
- Inline scripts of both pages parse clean; `npm run build` (verify-static) OK.
- Served locally: `/`, `/star`, `/lattice` all HTTP 200.
- Manual browser pass of the import/export badge flow: **pending** (test recipe in
  the session log: export → re-import → *κ verified*; tamper one byte → *⚠ κ
  mismatch*; cross-tab BroadcastChannel mirror still live).

## 7. Toward the community repo

What a public repo of this work should ship and show:

- **Ships:** the three pages · `HOLOSPACE.md` · `CLAUDE.md` + `README.md` ·
  `.devcontainer/` · `vercel.json` · the chronicles (they *are* the
  documentation-of-record; the suite's repos are public in this voice already) ·
  this file as the front-door explainer of the system diagram (§2).
- **Excluded by `.gitignore`:** `holospaces/` (point to upstream instead) ·
  `node_modules/`.
- **Open decisions (flagged, not resolved):**
  1. **License.** This repo carries none yet; upstream holospaces is MIT. Decide
     before publishing (MIT would match the seam being courted).
  2. **Name.** `swordsmans-key` (package name) vs `star` (directory) vs something
     that names the holospace claim.
  3. **Deploy target.** Routes are root-relative (`/star`, `/lattice`) — works on
     any domain or subdomain as-is; pick before the og/canonical URLs are set.
  4. **Upstream contact.** The repo is positioned as *the first third-party
     holospace*; an issue/PR introducing it to Hologram-Technologies is the natural
     next move once public — and the route to the operator key.

## 8. Status — the rungs

- [x] Rung 0 — extraction · baseline · strip (`7947176` → `75ed8f2`)
- [x] Rung 1 — κ-labelled City Keys, export-stamped + import-verified, both pages
- [x] Rung 1.5 — devcontainer boot definition + `HOLOSPACE.md`
- [ ] IPFS pin of the bundle (interim content addressing)
- [ ] Public repo (license → name → push → introduce upstream)
- [ ] Provision via Platform Manager — **blocked on the third-party operator key**
- [ ] `.holo` of the lattice canon — neg/bnot/succ over ℤ/64ℤ are pure functions
      over a 64-point domain: precisely the substrate's LUT-materialization case.
      The endgame: a holospace whose *content is the sovereignty lattice itself*.

---

*Chronicle written 2026-06-10 — the key learned to say what it is, wherever it goes.* `(⚔️ ⊥ ⿻ ⊥ 🧙) 😊`
