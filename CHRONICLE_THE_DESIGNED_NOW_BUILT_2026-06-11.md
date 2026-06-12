# Chronicle — the designed, now built (2026-06-11)

**Session:** the designed-not-built menu, chosen and executed.
**Chosen by the bearer:** prior κ-chain · v2 figures (consumer) · redacted charge
pass · function portraits · /skye · key-forging skill · LICENSE — with ECDH-PSI
deliberately held as a handoff chronicle for another session.

---

## 1. The `prior` κ-chain — C87 made operational

Every export from /star and /lattice now answers the question *what did this key
grow from?* When the content **evolved** since load, the export stamps
`prior` = the loaded ancestor's re-derived κ. When nothing changed, the export
carries its existing prior through untouched — **re-export is idempotent**:
same bytes, same κ, no spurious chain links from mere circulation.

Two implementation notes that matter:

- `prior` is **content** (inside the κ preimage, unlike `kappa` itself) — the
  lineage is part of what the key *is*, so forging an ancestry re-mints the name.
- /lattice's `buildWitness()` now preserves the loaded witness timestamp when
  the spent map and complete flag are unchanged. Before this, every re-export
  re-stamped `witness.at`, which would have made every witnessed key "evolved"
  forever (and had the live-κ drift ticker claiming drift right after import).

Verified headlessly: gen0 re-export → prior absent, κ identical · evolved
export → prior = κ(gen0), κ moved · gen1 re-export → prior carried, κ identical
· gen2 → chain k2→k1→k0 intact.

Where it shows: /sigil's provenance panel (*lineage 🔗: descends from …*),
/skye's gold threads, the 📖 legend.

## 2. The `figures` block — FIG-2.0, consumer side

Per `PLAN_KEY_EVOLUTION_MEASURED_GEOMETRY_2026-06-10.md` §2. A key carrying
`figures: { shapeCanon, overlap, ratio, visibility[6], zkp:{made,verified} }`
stops *choosing* its shape:

- **/star** derives geometry from the figures — `eps = 0.6·(1−overlap)`,
  `core = overlap` (det Σ), `smRatio = ratio`; m·n stay chosen (stance
  frequencies). The sliders become a local what-if; **export re-derives from
  the figures**, so the measured shape can't be hand-bent into the wire format.
  The key bar shows *📐 measured*.
- **/sigil** scales each dimension's petal by `visibility[i]` (petal i centred
  at θ = i·π/3 — the rosette becomes a sovereignty profile) and floors the
  ⚡ Computation petal's brightness by `zkp.verified/made`, with a proof-count
  engraving (`⚡ 12/14`) seated inside the dot ring.
- Figures are content: they move the κ. Wire version stays 1 (additive
  optional block) so /city's parser is untouched.

What remains v2's other half: **producing** real measurements (the /city charge
ledger, the extensions observing actual flows). The consumers are ready.

## 3. The redacted charge pass — proof without disclosure

/lattice grew a third button: **⚡ charge pass**. It exports
`{ version:1, redacted:true, of:<κ of the full key>, trace, witness, kappa }` —
*only the proof travels.* Inscriptions, palette, focus amounts, identity: home.

/city's `parseCityKey` (agentprivacy_master `city-key-charge.ts`) accepts the
redacted form; charging reads trace/witness exactly as from the full key, and
the dedup ids (trace.savedAt / witness.at) are shared with the full key — the
same proof charges once, whichever carrier brings it. κ verifies on the pass
itself (it has its own canonical form); `of` names the full key it was struck
from. Typecheck clean. Verified headlessly: parse ✓ · κ ✓ · mana math ✓ ·
junk rejected ✓.

This closes the gap called out in HOW_THE_SIGIL_WORKS: the full carrier is
portability, not secrecy — now there is a carrier that is *neither* the full
content *nor* unverifiable.

## 4. Function portraits — the operators drawn whole

The /star Path panel gained two etoggles:

- **⚔️ neg chords** — `neg(x) = (64−x) mod 64`, the Swordsman's reflection:
  31 chords in sword coral; 0 and 32 are its fixed points.
- **🧙 bnot mirrors** — `bnot(x) = 63−x`, the Mage's antipode: 32 diameters in
  mage cyan; no fixed point — the perfect mirror.

Until now the two operators existed only pointwise (the paused-marker
highlight). Now each can be seen *as a whole function* — and their composition
being the succ wheel stops being a sentence and becomes something you can look at.

## 5. /skye — the night of many keys (the fourth projection)

New page, canvas 2D, fully local. Add any number of keys (JSON or sigil PNG,
multi-file or drag-drop) and each rises as a star:

- **placement is content**: the first 16 hex glyphs of the re-derived κ are the
  star's coordinates. No curator, no arrival order — re-import the same key on
  anyone's night and it rises in the same place.
- each star is the key's **sigil in miniature** — 64 glyph points in succ
  order, lit by the κ, coloured by the key's own palette.
- **gold threads** join child to ancestor when one key's `prior` equals
  another's κ — a sky of one bearer's exports is their key's history, visible.
- **teal threads** draw common ground — shared touched vertices (lit ·
  described · poured · proven), labelled `∩n`, brighter with more shared ground.
- hover reads a star: name · κ · lit · touched · *descends from* · closest kin.

The legend names the honest boundary: this is the **plaintext sky** — it reads
full keys, locally. The zero-knowledge sky (ECDH-PSI) is the designed next rung
(see the handoff chronicle).

Nav canon updated everywhere: `↖ home · ⚔️ /star · 🧙 /lattice · 🪬 /sigil ·
🌌 /skye · 🗡️ /guide`. The portal has four doors; /guide has four rooms.

## 6. Housekeeping

- **LICENSE**: MIT, mirroring upstream holospaces' text; copyright
  `privacymage / 0xagentprivacy` per the attribution rule.
- CLAUDE.md: route table + nav canon + schema (`figures`, `prior`, the charge
  pass) + the five-page byte-identity contract.
- EXPERIENCE.md §6 tracker updated to match reality.
- Conformance vector re-verified after all of it:
  `sha256:0b4916ba…c527` over 303 canonical bytes — **holds**.
- All five shared pages synced byte-identical into the soulbis website;
  routes 200 on the local review server.

---

## 7. Same-day addendum — the sky shot + PSI un-held

The bearer extended the session twice:

**📸 The sky shot** — /skye's final export. The night renders at 1600×900 with
a caption, and the picture **carries every risen key**:
`{version, sky:true, keys:[…]}` in a `tEXt` chunk, keyword `citySky` — the
single-key carrier's grammar, one rung up. Drop the shot back on /skye and the
whole night rises again (the import auto-detects sky shots, single-key sigil
PNGs, and raw JSON); each carried key still imports individually everywhere
else. One painter (`paintSky`) drives both the live canvas and the shot.
Verified headlessly: payload round-trips byte-identical through a real PNG,
CRC valid, `cityKey` readers correctly ignore the `citySky` chunk. The legend
is explicit: sharing the shot shares *all* of it.

**🤝 DH-PSI common ground — built, not handed off after all.** The bearer
un-held it ("lets also start the next session ecdh psi i held in this
context"). See `CHRONICLE_ECDH_PSI_HANDOFF_2026-06-11.md` (status flipped to
BUILT, deviations documented): RFC 3526 modp2048 QR subgroup instead of a
vendored curve — zero dependencies, BigInt only, the prime Miller-Rabin
verified from the page's own constant; 256-bit short exponents keep 64
blindings around a second. Two-file exchange (challenge → response → optional
result report), secret per exchange id in sessionStorage, ⭐ touched / ✦ lit
only scope chips for the C81/C84 budget. All six handoff acceptance checks
pass, including tampered-point degradation and transcript enumeration
resistance.

*The chain remembers, the figures measure, the pass discloses nothing, the
operators are visible, the keys have a sky — and the sky has a portrait and a
handshake.* `(⚔️ ⊥ ⿻ ⊥ 🧙) 😊`
