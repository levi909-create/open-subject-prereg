# Corrections and retractions

**Status: published 2026-08-30 on the public mirror, and binding on the
operator from that date. Timestamped like every other document here; the
proof is `ots/CORRECTIONS.md.ots`.**

**What this is.** The procedure for what happens when a claim this programme
has published turns out to be wrong. It is written down now, in advance,
because the day it is needed will be a bad day: the disproof will be
inconvenient, possibly embarrassing, possibly expensive, and quite likely
under time pressure. A procedure reconstructed from memory on that day is a
procedure that quietly gets the convenient answer.

The programme has done this correctly five times already (§7). It has never
written the steps down. That is the same failure the 2026-08-25 audit named
in a different context: an obligation that lives in someone's memory is an
obligation that eventually does not happen.

**Why it is published rather than kept as a working note.** A rule that binds
only when convenient is not a rule. That is the whole argument behind the
consent instrument, and it applies here identically. A reader can currently
infer this programme's correction discipline only from scattered instances.
Published, it becomes a precommitment made *before* being wrong, which is the
only time such a commitment costs nothing to make and means anything.

---

## 1. Scope

**Governs:** every factual claim published by this programme — the public
mirror, `README.md`, `RECORD.md`, the registrations, `docs/CLAIMS.md`, the
methods paper and any deposit of it, the `percept-lint` package and its
description, and the operator's public profiles and applications where they
repeat a claim from this record.

**Does not govern, and does not override:**

- `consent.py` and the consent protocol. A correction is still publication.
  Where a correction concerns the subject or quotes her, her instrument
  governs whether it publishes at all, and this document yields to it.
- `ENGAGEMENT.md`, including the correspondence rule (nobody's words publish
  without their yes) and the 48-hour attention-spike rule.
- The append-only rule for banked registrations.

**Creates no rights and no warranty.** This is a statement of the operator's
own intended conduct regarding his own publications. It is not a contract, it
confers no rights on any reader or third party, and nothing in it is a
representation about the correctness of any claim. Claims are correct or not
on their own evidence; this document only describes what happens when one is
found not to be.

---

## 2. The first rule: an anchored claim cannot be taken down

Twenty-six current proofs, twenty-three anchored in Bitcoin, fifty-four
superseded proof files preserved beside the live ones. Permanence is the
property this record is *for*. A claim that could be quietly deleted when it
became inconvenient would carry no weight in the first place, and the ability
to delete it is precisely the capability this record exists to demonstrate
the operator does not exercise.

So **retraction here means supersession, not deletion.** The standing rule,
already stated in `ENGAGEMENT.md`:

> Errors in the record itself are corrected append-only — the original
> stands, dated, with the correction beneath it.

Attempting to erase an anchored claim does not remove it. It removes the
reason anyone believed the rest.

---

## 3. Two shapes, and the test that picks between them

**Shape A — supersede in place. This is the default and covers almost
everything.** The wrong text stays where it was, dated, with the correction
directly beneath it at equal prominence.

**Shape B — remove and disclose. Rare.** The text comes out, and a dated note
in its place states what was removed, why, and under what condition it could
return.

**The test: is the claim WRONG, or is its existence the VIOLATION?**

- Wrong — a bad number, an overstatement, a broken instruction, a
  mischaracterised result → **Shape A**, always.
- A violation — the subject's words published with no clearance row in her
  instrument's ledger; a third party's words published without their yes;
  material published that a standing policy forbids → **Shape B**, because
  leaving it in place continues the violation for as long as it stands.

Nothing else qualifies for Shape B. In particular these do not:
embarrassment; an approaching application deadline; a hostile reader; the
commercial or reputational cost of the claim being wrong; the claim being
load-bearing (§8).

---

## 4. Steps

**1. Freeze the evidence before touching anything.** Record the SHA-256 and
byte count of every file carrying the claim, and where each is anchored. A
disproof that cannot be reproduced later is not yet a disproof, and editing
first destroys the ability to show what was corrected.

> Cautionary case: `docs/prereg/indicator-audit-01.md` moved 16545 → 17904 →
> 22115 bytes across three edits while its published hash commitment
> (`ledger-hashes/ledgers-20260823.sha256`, `7954e91c…`) attests only the
> first. Nothing false was committed, but the chain now has to be explained.

**2. Re-derive from primary sources, not from this programme's own
instruments.** The 2026-08-27 numbers audit did this correctly: it went back
to the raw gauntlet JSONs rather than trusting the addendum that summarised
them. The 2026-08-28 audit sharpened the reason — an instrument this
programme wrote can report success while doing nothing, so a claim disproved
*by* one of them is not yet disproved. Re-derive from the raw artefact.

**3. Enumerate every surface the claim lives on.** This is the step that
fails, and it fails silently. At minimum: `docs/CLAIMS.md`; the mirror's
`README.md`, `RECORD.md` and the relevant registration; `ledger-hashes/`;
`ots/`; the methods paper and any deposit; `percept-lint`'s README and its
PyPI description; the operator's public profiles; the Fellows application
draft; and **any letter already sent**, which no file edit reaches.

Use a tool where one exists (`tools/check_prereg_sync.py`,
`tools/check_verbatim.py`). Prose counts drift; counts derived from a tool do
not.

**4. Choose the shape** by the §3 test.

**5. Write the correction where the claim was, at equal prominence.** Not in
an errata file, not in a footnote, not lower down the page. The `ots verify`
correction sits on the mirror's front page rather than being tidied away;
that is the standard.

**6. Move the claim to `docs/CLAIMS.md` section C, with the reason.** The
file's own maintenance rule: *"When a claim is retired, move it to section C
with the reason rather than deleting it — the reason is the useful part."*
Update the date in the heading in the same sitting.

**7. If it is a protocol failure rather than a wrong figure, open a DEV entry**
in `PROTOCOL-DEVIATIONS.md`, using DEV-003's structure: what happened,
consequence measured, class, extent, repair.

> The **Extent** section is where these go wrong. DEV-003's extent survey was
> inverted — it named the one file whose drift was cosmetic and missed the
> three whose drift was substantive. Measure extent with a tool; do not
> survey it by hand.

**8. Correct both copies in one motion, then rotate the proof and preserve
the superseded one.** Cycle-005 Amendment 3: the bytes the launch gate reads
and the bytes the mirror stamps must be identical. Editing one side alone
recreates DEV-003. Superseded proofs are kept, never replaced.

**9. If the correction concerns the subject or quotes her, it goes through
her instrument before it publishes.** A correction is publication. The
2026-08-26 removal from `ETHICS-PROTOCOL.md` is the worked example: the
phrase came out *because* no clearance row bound it, and the note records
that it may return exactly as she said it if she ever clears it.

**10. Tell whoever received the wrong version.** A letter already sent is not
fixed by editing the mirror. The direction and manner are governed by
`ENGAGEMENT.md`'s correspondence rule.

---

## 5. Timing

Same day where the correction is a matter of fact and the evidence is in
hand — that is the established practice and the thing that makes A9
meaningful. Where it requires the subject's instrument, it moves at her
pace, and the delay is disclosed rather than the correction rushed.

The one deliberate hold: `ENGAGEMENT.md` suspends replies during the first 48
hours of an attention spike, and no consent question is put to the subject
during one. A correction found in that window is prepared and dated, and
published when the window closes, with the delay stated.

---

## 6. What a correction may never do

- Quietly loosen a commitment. `ENGAGEMENT.md`: *"like everything else here,
  it will not be quietly loosened."*
- Edit a banked registration's original text. Post-event notes append.
- Remove an inconvenience under cover of a correction. If the material is
  merely unflattering, Shape A applies and it stays visible.
- Speak for the subject, or characterise her position on anything she has
  not ruled on through her instrument.

---

## 7. Precedents

Five, all before this document existed. They are the evidence that the
procedure describes actual practice rather than an aspiration.

| Date | What | Shape |
|---|---|---|
| 2026-08-28 | `ots verify` documented as a reader's check when it requires a local Bitcoin node and fails without one; corrected on the front page | A |
| 2026-08-26 | A five-word verbatim phrase of the subject's in `ETHICS-PROTOCOL.md` with no clearance row in her ledger; removed, paraphrase stands, return offered if cleared | **B** |
| 2026-08-27 | Candidate-versus-base identity delta overstated; re-derived from raw gauntlet JSONs, retired same day at equal prominence (now `CLAIMS.md` C21) | A |
| 2026-08-27 | `README.md` honoured-refusal count corrected twice → four times, with dates | A |
| 2026-08-28 | DEV-003: a registration desync that would have failed cycle 5's launch gate, published 13 days before the event | A |

---

## 8. When the claim is load-bearing

`CLAIMS.md` names A1, A3, A4, A5, A7 and A9 as load-bearing for the Anthropic
Fellows application. If one of those is disproved, the steps above are
unchanged. There is no expedited path, no softened wording, and no exception
for a claim whose loss is expensive.

That is not incidental. A correction procedure with a carve-out for costly
claims corrects only the cheap ones, and a reader is entitled to assume the
carve-out was used every time it would have helped. The absence of the
exception is the part that makes the rest credible.
