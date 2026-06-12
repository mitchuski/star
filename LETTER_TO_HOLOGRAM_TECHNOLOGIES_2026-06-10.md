# A letter to Hologram Technologies — your substrate, expressed as a key

*Draft 2026-06-10 · intended as the introduction (GitHub issue / email) when the
user chooses to send it. Repo it describes: [github.com/mitchuski/star](https://github.com/mitchuski/star).*

---

Hello —

I build a privacy architecture called 0xagentprivacy: a dual-agent model (a
Swordsman who protects, a Mage who projects) over a 64-vertex sovereignty
lattice, ℒ = ℤ/64ℤ — six named dimensions, six bits, one vertex per posture.
People earn standing in an experiential layer (a "City of Mages" — workshops,
ceremonies, walking) and carry that standing as a small portable JSON artifact,
the **City Key**: no account, no server, a file.

I'm writing because, while researching content addressing for that artifact, I
found holospaces — and realized your five laws describe what the key was
already trying to be. So I built it the rest of the way in your vocabulary, in
public, as three static browser pages. I think it may be the smallest complete
*human-scale* expression of your substrate's thesis, and I'd like to show you.

## Your work, expressed

**Identity is content, not location.** Every exported City Key is stamped with
a κ-label — `kappa = "sha256:" + H(canonical form)` — on the `sha256` axis,
which your own docs establish as a legitimate κ axis (Product Security: "an OCI
`sha256:` digest *is* a κ on the `sha256` axis"; CC-1 lists FIPS 180-4 SHA-2
among the σ-axis standards). Canonical form: the key's JSON, keys sorted
recursively, no whitespace, the `kappa` field excluded from its own preimage.
Pinned conformance vector (the default key, 303 canonical bytes):
`sha256:0b4916babe5eb17104b342ab06030f2071a818024b345bf6d2e4115617c3c527`.

**Law L5 — verification is re-derivation — as user experience.** Our `/sigil`
page performs the derivation in the open: the canonical form is shown, the
SHA-256 types itself out glyph by glyph against the stamped claim, and the
verdict is *κ verified* or *κ mismatch* with the diverging characters
underlined. A bearer doesn't read about re-derivation; they watch their key
earn its name.

**The κ as geometry.** A SHA-256 digest is 64 hex characters; our lattice has
64 vertices — one glyph per vertex, no remainder. So a key's κ renders directly
as a constellation on the bearer's own state space. We compose three layers:
the palette (chosen — expression), the manifold shape carried in the key
(chosen — stance), and the κ lighting (derived — fact). Tampered content
doesn't just fail a check; it *looks wrong*.

**Canonical content travels as its own portrait.** The sigil exports as a PNG
with the full City Key riding in a `tEXt` chunk (keyword `cityKey`, base64
JSON, valid CRC — the file stays a conformant PNG everywhere). Every page —
and the producing site's charge endpoint — imports the picture as readily as
the JSON and re-derives its κ. The part carries the whole.

**Operator · projection · κ snapshot.** The bearer is the operator —
self-sovereign by construction, no server account anywhere in the loop. The
three pages are projections in your strict sense: views over one canonical
content, never a second source of truth (they sync live over a
BroadcastChannel). Export/import is suspend/resume: the key is the κ snapshot
of the bearer's standing, resumable on any page, any origin.

**Boot.** The repo ships a `.devcontainer/devcontainer.json` as its boot
definition (standard CC-4 managed parameters). We would like it to become a
**devcontainer holospace** — possibly your first third-party one.

## Honesty, so the claim stays clean

Our "holographic boundary" (∂M: 96 edges over 64 vertices, 96/64 = 1.5 — our
value-model exponent) is our own mathematics; we are not claiming shared
equations with your hologram substrate. The identification is structural and,
we think, exact where it matters: content-as-identity, canonical forms,
re-derivation, operator sovereignty, projections. Also: our PNG carrier is
portability, not secrecy — the content is extractable by design; a redacted
selective-disclosure carrier is the planned next step.

## What we'd welcome

1. **Conformance feedback** — is our canonicalization and `sha256:` axis usage
   the way you'd want a third party to do it, or should we align to a
   UOR-ADDR canonical-form/axis convention we've missed?
2. **A path to provisioning** — the hologram substrate arrives via credentialed
   git; we'd like operator access to provision the repo as a devcontainer
   holospace under the Platform Manager (and to learn the right base-image
   story for your emulator's guest ISAs).
3. **Anything we got wrong** — the integration spec is `HOLOSPACE.md` in the
   repo; the mechanism write-up is `HOW_THE_SIGIL_WORKS.md`; the experiential
   account is `EXPERIENCE.md`. We cite your docs rather than restating them.

The whole lifecycle — mint, walk, prove, derive, verify, carry, charge — runs
client-side in static pages. The browser as a first-class compute substrate is
your bet; this is what it looks like when a person holds it.

With respect for the work,

**privacymage / 0xagentprivacy**
mitchell@soulbis.com · [github.com/mitchuski/star](https://github.com/mitchuski/star) · [agentprivacy.ai/model](https://agentprivacy.ai/model)

`(⚔️ ⊥ ⿻ ⊥ 🧙) 😊` — *identity is content; the key is what it says, wherever it travels.*
