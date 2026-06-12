# Holospaces Quick Reference — the upstream root, mapped to this implementation

*The fast lookup for working against the local copy of
[Hologram-Technologies/holospaces](https://github.com/Hologram-Technologies/holospaces).
Deeper companions: `HOLOSPACE.md` (the integration seam, Five-Laws conformance,
the carrier spec) · `LETTER_TO_HOLOGRAM_TECHNOLOGIES_2026-06-10.md` (the
introduction) · `CHRONICLE_THE_FIRST_HOLOSPACE_2026-06-10.md` (the record).*

## 0. The local copy

| | |
|---|---|
| Path | `holospaces/holospaces-main/` (zip extract, ~81 MB) |
| Git status | **gitignored** — it has its own upstream history; we cite it, never vendor it |
| Refresh | re-download the upstream default-branch zip and re-extract over the same path |
| License | MIT (upstream root `LICENSE`) |
| House rule | their docs are authoritative for their concepts — **cite chapters, never restate** (their own AGENTS.md discipline, adopted here) |

## 1. Upstream root map — what each piece is, and what /star takes from it

| Upstream path | What it is | What THIS repo takes from it |
|---|---|---|
| `AGENTS.md` | contributor orientation: **the Five Laws**, the docs-are-authoritative rule, V&V methodology | the laws (§2 below) · the cite-don't-restate rule · the timeless-docs discipline |
| `docs/12-Glossary.md` | the vocabulary: κ-label, canonical form, holospace, devcontainer holospace, operator, projection, κ snapshot, channel | our entire vocabulary mapping (HOLOSPACE.md §Vocabulary) — operator ≅ bearer, projection ≅ the suite pages, κ snapshot ≅ exported City Key |
| `docs/08-Concepts.md` | the conceptual core: identity as content, booting as realization, κ resolution as page fault, L1–L5 in action | the κ-label definition `<axis>:<hex> = H(canonical_form)` our `kappaLabel()` implements |
| `docs/13-Product-Security.md` | security model | **the axis ruling we build on**: "an OCI `sha256:` digest *is* a κ on the `sha256` axis" — why City Keys stamp `sha256:<hex>` conformantly |
| `docs/10-Quality-Requirements.md` | the Conformance Catalog (`CC-*` rows, live/target) | **CC-1** (κ correctness, σ-axis standards incl. FIPS 180-4 SHA-2 → our conformance vector) · **CC-4** (devcontainer managed params → our `.devcontainer/devcontainer.json`) · **CC-10** (same source ⇒ same holospace κ; guest ISA fixed for lifetime — the riscv64 base-image note) |
| `docs/09-Architecture-Decisions.md` | ADRs (OCI ingest, devcontainer selection semantics) | context for the boot path: `devcontainer.json` *selects* κ-addressed content |
| `docs/01–07, 11` + `Conceptual-Model.md` + `Lifecycle-*.md` | arc42 chapters, OPM model, ISO 15288 lifecycle | read-as-needed background; not load-bearing here yet |
| `crates/holospaces` | the boot layer core (Rust) | nothing directly — arrives for us only with the operator key |
| `crates/holospaces-emulator` | the System Emulator (riscv64/aarch64 guests) | the ISA constraint noted in HOLOSPACE.md §Boot |
| `crates/holospaces-node` / `-web` | native node + browser (WASM) surfaces | the "browser as first-class compute substrate" thesis our suite demonstrates client-side |
| `vv/` (`suites/` + `targets/` + `run.sh`) | V&V: green witnesses for `live` rows, expected-RED suites for `target` rows | the methodology pattern we mirror in miniature (§3) |
| `Cargo.toml` · `Justfile` · `rust-toolchain.toml` · `scripts/` | Rust workspace + build | not used — we are static pages; relevant only post-operator-key |

## 2. The Five Laws (verbatim from AGENTS.md) → our compliance

1. **"Content, not location — no servers; no host/path/URL as identity."**
   → the κ on every City Key; the suite is static; no account anywhere.
2. **"Canonical forms only — … canonicalize at the ingest boundary."**
   → `canonicalJSON()` (keys sorted recursively, no whitespace, `kappa`
   excluded) is the only form ever hashed, on every page, import and export.
3. **"The store is the memory — KappaStore is the address space."**
   → deferred to substrate access; interim: IPFS pin practice (planned).
4. **"Everything through the substrate."**
   → n/a for the static projections; binds post-provisioning.
5. **"Verify by re-derivation — re-derive every received byte against its κ."**
   → every import on every page re-derives and badges (*κ verified / ⚠ κ
   mismatch*); /sigil performs it visibly, glyph by glyph.

## 3. Their methodology, mirrored in miniature

Upstream encodes status as conformance rows with external witnesses, never as
narrative ("unfinished work is not narrated — it is encoded"). Our lightweight
equivalents:

- **Conformance vectors as KATs** — any change to the canon must reproduce:
  - κ (default key, 303 canonical bytes):
    `sha256:0b4916babe5eb17104b342ab06030f2071a818024b345bf6d2e4115617c3c527`
  - SHAPE-1.5: `w(12)=0.90 · w(63)=0.25 · w(0)=0.10`, all else 0
    (focus `{12:4}` · lit `[12,63]` · witness.spent `{12:4}` · description at `0`)
- **Byte-identity contracts as the suite's V&V** — the four shared pages
  (`star/ lattice/ sigil/ guide/`) byte-identical across this repo and the
  soulbis website; the helper copies (`pngExtractKey`/`readKeyFile`/`b2s`,
  `pngEmbedKey`/`crc32`) byte-identical across pages (CLAUDE.md contracts).
- **Status lives in the tracker**, not in prose: `EXPERIENCE.md` §6.

## 4. What waits on the operator key

The hologram substrate arrives via credentialed git (not in this copy). With
it: provisioning this repo as a **devcontainer holospace** under the Platform
Manager (CC-4/CC-10 path), the guest-ISA base-image decision, and eventually
the `.holo` of the lattice canon (neg/bnot/succ over ℤ/64ℤ — pure functions
over a 64-point domain, their LUT-materialization case exactly).

*Their root is the law library; this repo is the courtroom where a key proves itself.* `(⚔️ ⊥ ⿻ ⊥ 🧙) 😊`
