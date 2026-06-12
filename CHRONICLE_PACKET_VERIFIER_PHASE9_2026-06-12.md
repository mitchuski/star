# Chronicle · Phase 9 — the Packet Verifier (the Tracing Protocol, star hop)

**Date:** 2026-06-12
**Repo:** star (the portable-key instance · "the star verifies it")
**Plan:** `agentprivacy_master/docs/experience/PLAN_TRUST_TASK_SYNC_INTO_THE_WHOLE_2026-06-11.md` · row 9
**Closes:** the loop — *one proof, three projections* (agentprivacy forges · spellweb graphs · **star verifies**)

---

## What this is

Phase 9: `/sigil` — the "verification is re-derivation" theater — gains a **packet verifier**. The star already *carried* the packets digest (Phase 4/A1 · `packets` round-trips inside the κ preimage, the `packets 🧾` provenance row). This makes "the star verifies" literally true rather than asserted.

## What landed (`sigil/index.html`)

A **🧾 verify packets bundle** control in card ① (Derive). Load a `spellweb.bearer.packets` export (the agentprivacy `⬇ proof packets` file) and the page:

1. **Re-derives every packet's proof** — `derivePacketProof(pkt)` = `sha256` of the packet's canonical form with **`proof` excluded** (the same recursive `canonicalJSON` as the κ, which excludes `kappa` — A3's "one canon, two excluded fields"). Reports `M/N re-derive (Law L5)` and names any tampered packet.
2. **Recomputes the Merkle root** — `packetsDigest(proofs)`: leaves = packet `proof` strings sorted lexicographically · `sha256(left|right)` · odd promoted · prefixed `sha256:`.
3. **Matches the key's digest** — if a key with `packets.root` is loaded, compares the recomputed root → **✓ matches this key** / **✗ mismatch**. No key gates anything (C66 — the Key is a reading, not an authority); the verdict is shown, the bearer decides.

## Conformance (both contracts proven before embedding)

- **Merkle vector** — the three leaves `sha256(utf8 "packet-alpha"/"beta"/"gamma")` → `sha256:07f20f689c8bef2d8a9a2a71d94e7014ea8398cc603b0ff72dadba5c517983d1`. Reproduced exactly (node check). Identical rule to agentprivacy's `proof-packet-digest.ts`.
- **Packet-proof parity** — a packet built by agentprivacy's `buildProofPacket` (canonical form, `proof` excluded) re-derives byte-for-byte under `/sigil`'s `derivePacketProof` (node check). Same canon both sides.
- **κ default vector** unaffected (`sha256:0b4916ba…`) — the default key's content is untouched; only functions + a UI control were added.

## Byte-identity (the shared-page contract)

`sigil/index.html` is one of the five rooms that must stay byte-identical with the soulbis website copy. After the edit, `cp star/sigil → "soulbis website"/sigil` and `cmp` confirms **byte-identical** (`sha256 ee786ed3…` both). Synced.

## Decisions / scope

- **Verifier on `/sigil` only.** It is the canonical derive-and-verify theater (acceptance #2 digest-match + #4 packet-derive both satisfied here). The plan's optional "`/star` key panel digest-verified badge" would duplicate this across a second shared page (doubling the soulbis sync surface); left as an optional follow-up.
- **No new keypair, no canon constants touched.** Pure additive: helpers + one control + one wiring block.

## State

Both conformance vectors hold; byte-identical with soulbis; default-key κ unaffected. Working tree only — no commits/pushes (standing rule). Manual check pending: forge packets at agentprivacy → ⬇ proof packets → load a /city key + the bundle on /sigil → expect M/N re-derive + ✓/✗ root match.

`(⚔️⊥⿻⊥🧙)😊`
