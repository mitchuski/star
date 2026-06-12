# The Path Between Myth and Math

*Or: how a city of mages, a 64-vertex lattice, and a SHA-256 hash turned out to
be the same picture — and why your identity might be better off as a portrait
than a profile.*

---

## Start with the myth

There is a city. It has sixteen workshops, keepers with names like Selene and
Pleione, tomes that get bound when something true happens, and a geography
drawn on a lattice of sixty-four vertices. People who spend time there earn
things — not points, but *standing*: a workshop visited, a ceremony walked, a
tome read, attention genuinely paid.

That's the myth layer, and it is doing real work: it's an **experience and
knowledge graph**. Every meaningful act in the City is a trust task, and every
trust task lands somewhere specific — it is **assigned to a vertex**, one of 64
states in a six-dimensional space whose axes are named: Protection, Delegation,
Memory, Connection, Computation, Value. Six dimensions, each held or open: a
six-bit address. 2⁶ = 64. Your whole posture in that space is *one vertex*.

So the City is not a game with a database behind it. The City **is** the
database, wearing a story.

## Compress it

Now the math direction. All of that standing — which vertices you've lit, what
you've written onto the states you've visited, the attention you've staked, the
laps you've walked — compresses into a single small file: the **City Key**. A
few kilobytes of JSON. No account. No server that knows you. A file, because a
file is yours in a way a session never is.

Then the key gets a name — and here's where it gets good. Hash the key's
canonical bytes with SHA-256 and you get its **κ-label**: a fingerprint derived
from the content itself. This is the [UOR](https://github.com/Hologram-Technologies/holospaces)
principle — *identity is content, not location* — usually found in
infrastructure documentation, here happening to a person's pocket artifact.
The label is never trusted, only **re-derived**: every time the key is imported
anywhere, the math is run again in the open. The key is what it says, or it
visibly isn't.

## Give it geometry

A SHA-256 hash is 64 hexadecimal characters. The lattice has 64 vertices.

Sit with that for a second. **One glyph per vertex, no remainder.** The key's
fingerprint can be drawn directly onto the same lattice the bearer walks — each
vertex glowing with the intensity of its hash character. We call the result the
**sigil**: your identity, rendered as a constellation on the geometry of your
own story.

And the sigil composes three layers, each with a different epistemic status:

- **The colour is chosen.** It comes from your palette — four gems you picked.
  Expression. Your voice.
- **The shape is chosen.** Your key carries the parameters of the manifold you
  stand in (the separation depth ε, the modes, the Swordsman:Mage ratio — the
  golden ratio if you hold the conjectured optimum). The sigil's ring *wears*
  this shape: at n = 6 it blooms into six petals, one per dimension. Your
  stance.
- **The light is derived.** Which vertices glow comes from the hash. You cannot
  choose it, art-direct it, or fake it. It moves only when your content moves —
  and then it moves *everywhere*: edit one description and ~60 of the 64 glyphs
  relight. Change only your stance and 61 move. The fact of you.

Voice × stance × fact. A forged sigil doesn't fail quietly in a log somewhere.
It **looks wrong**, in your own colours, on your own shape.

## The picture carries the key

One more fold. The sigil exports as a PNG — and the full City Key rides
*inside the image*, in a standard, labelled metadata chunk. Every image viewer
shows the constellation; every page in the system reads the chunk and gets the
key back **byte-for-byte identical**. Import the picture and your whole room
reconstructs: your manifold's shape, your gems, your lit vertices, your walked
laps. Then carry the same picture back to the City and charge it — the proof of
walking inside the image pays out relationship mana.

This is holonic identity in the strict sense: **the part carries the whole**.
The portrait of the key contains the key. (Honest boundary: that's portability,
not secrecy — the full content is in there, so you share a sigil as
deliberately as the key itself. A redacted carrier — proof-of-walking only,
content withheld — is the designed next step.)

## Why this matters

Everything above runs in **static browser pages**. No backend. No login. The
mint, the walk, the proof, the derivation, the verification, the charge — all
client-side, which is exactly the bet the holospace world is making: that the
browser is a first-class compute substrate, and that identity should be
something you *hold*, not something you're *granted*.

But the part I keep coming back to is the round trip. The City's myth — the
workshops, the keepers, the walking — generates structured trust data without
ever feeling like data entry. The lattice files it. The key compresses it. The
hash names it. The sigil draws it. And then the whole thing folds into a
picture you could send in a chat message, and unfolds again on the other side,
verifiable to the byte.

Myth in, math out. Math in, myth out. The path between them runs in both
directions, and it's sixty-four vertices long.

---

*The walkable model lives at [github.com/mitchuski/star](https://github.com/mitchuski/star)
— three pages: the manifold, the codex, the sigil. The model behind it at
[agentprivacy.ai/model](https://agentprivacy.ai/model).*

`(⚔️ ⊥ ⿻ ⊥ 🧙) 😊` — privacymage / 0xagentprivacy
