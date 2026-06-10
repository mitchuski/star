# HOLOSPACE.md — the Swordsman's Key as a holospace

This repo is packaged to be provisionable as a **holospace** — a bootable, κ-addressed
environment — over [Hologram-Technologies/holospaces](https://github.com/Hologram-Technologies/holospaces),
the UOR-native boot layer. A local reference copy of the upstream repo lives at
`holospaces/` (gitignored; it has its own upstream history).

The thesis of the integration: holospaces' first law — **identity is content, not
location** — is the Swordsman's thesis stated in substrate terms. A City Key already
travels as a self-describing artifact; the κ-label makes that identity verifiable
by re-derivation, anywhere.

---

## Vocabulary mapping

| holospaces (docs/12-Glossary.md) | the Swordsman's Key |
|---|---|
| **κ-label** — `<axis>:<hex>` = `H(canonical_form)`; identity of every thing (*what*, not *where*) | `kappa` field on every exported City Key — `sha256:<hex>` over the key's canonical form |
| **Canonical form** — deterministic bytes; the only form holospaces operates on | the key's JSON, keys sorted recursively, no whitespace, `kappa` excluded |
| **Operator** — self-sovereign identity that provisions and manages holospaces | the bearer — the First Person, reachable only via both agents |
| **holospace** — bootable κ-addressed environment | this repo booted: the walkable model (/star + /lattice) |
| **devcontainer holospace** — provisioned from a devcontainer | `.devcontainer/devcontainer.json` (this repo's boot definition) |
| **κ snapshot** — running state as κ-addressed canonical form | an exported City Key: palette + descriptions + lit + trace + focus + witness, κ-stamped |
| **Projection** — a view + intent surface, never a second source of truth | /star and /lattice — two projections of one lattice ℒ, linked by BroadcastChannel |

## The Five Laws, as honoured here

1. **Content-based identity (no servers)** — the City Key's `kappa` is derived from
   its content; the pages are static and serverless.
2. **Canonical forms only** — `canonicalJSON()` (sorted keys, no whitespace) is the
   only form hashed; pretty-printing for humans never changes identity.
3. **The KappaStore as address space** — out of scope until substrate access (below);
   interim content addressing is an IPFS pin of the site bundle, matching the
   grimoire-pin practice.
4. **Substrate-exclusive operations** — n/a for the static projection.
5. **Re-derivation for verification** — on every City Key import, both pages
   recompute the κ-label and display `κ verified` / `⚠ κ mismatch`.

## The κ-label on a City Key

- Axis: **`sha256`** — per the upstream spec, a SHA-256 digest *is* a κ-label on the
  `sha256` axis (docs/13-Product-Security.md; CC-1 lists FIPS 180-4 SHA-2 among the
  σ-axis standards). `crypto.subtle` provides it natively in the browser.
- Canonical form: the key object with keys sorted recursively, serialized with no
  whitespace, the `kappa` field excluded (a label can't contain itself).
- Stamped at export by both pages; re-derived at import. Any edit to the key —
  a description, a lap of trace, a poured-focus witness — mints a different κ.
  That is the point: the key *is* its content.

```json
{
  "name": "city key",
  "version": 1,
  "palette": { "cool": "#141a3d", "warm": "#f0eee8", "sword": "#e8523a", "mage": "#4dd9e8" },
  "descriptions": { "0": "…" },
  "kappa": "sha256:…64 hex…"
}
```

## Boot

- **Today (any devcontainer tool / Codespaces):** `.devcontainer/devcontainer.json`
  boots the repo and serves the walkable model on port 8000. holospaces honours the
  same managed parameters (CC-4): `forwardPorts`, lifecycle commands, `containerEnv`,
  `features`.
- **Over holospaces (when operator access arrives):** a devcontainer holospace is
  provisioned from this repo + `devcontainer.json`; the OCI image and repo ingest as
  κ content (CC-10), and **same source ⇒ same holospace κ** — the repo itself becomes
  a content-addressed identity. Note the guest ISA (`riscv64` or `aarch64`) is part
  of that identity and fixed for the holospace's lifetime; the current base image is
  amd64/arm64, so provisioning under the System Emulator may need a riscv64-capable
  base — settle this with the operator key in hand.
- **Later (`.holo` compute artifact):** the lattice canon — `neg`, `bnot`,
  `succ = neg∘bnot` over ℤ/64ℤ — is a family of pure functions over a 64-point
  domain: exactly the shape the hologram substrate materializes into lookup tables.
  A `.holo` of the canon would make the Swordsman's Key a compute artifact, not just
  a site: the first holospace whose content *is* the sovereignty lattice.

## Status

- [x] κ-labelled City Keys (export-stamped, import-verified) — both pages
- [x] Devcontainer boot definition
- [ ] IPFS pin of the stripped site bundle (interim content addressing)
- [ ] Provision as a devcontainer holospace via the Platform Manager — **blocked on
  the third-party operator key** (the hologram substrate arrives via credentialed git)
- [ ] `.holo` artifact of the lattice canon
