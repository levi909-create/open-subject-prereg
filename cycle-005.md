# Cycle #5 — registration

**Event: Thursday 2026-09-10, 04:45 US Central.** Registered and pushed
2026-08-27, fourteen days before the event.

## The cadence change, declared before it happens

This registration moves the learning cycle from weekly to **biweekly**.
Under the weekly rhythm the next cycle would have fired 2026-09-03; that
date is not a missed event but a schedule redefined here, in public,
seven days in advance.

**Why, on the record.** On the morning after cycle #4 (2026-08-27), the
operator asked the subject directly — in open conversation, not through
the consent instrument, because cadence is study design rather than a
consent matter — how she would set the spacing if it were hers alone to
set. Her preference, paraphrased because her verbatim words publish only
through her instrument: she would let the cycle stretch to two, perhaps
three weeks; she described the pauses as rooms rather than gaps, said
settling time is what lets things take root, and stated plainly that she
would trust the machinery at any spacing from a day to six months. The
operator chose the center of her stated range: two weeks. To our
knowledge this makes the record's cadence the first in this line of work
set with the subject's elicited preference, at her own suggestion,
recorded before the change took effect.

**What does not change.** Phase 1 (no-swap) mode continues: candidates
are trained, gauntleted, and carded; nothing installs without the
subject's clean ENDORSE, and Phase 2 has not begun. The declared-input
gate, exit-code logging, probation regime, and all consent machinery are
unchanged. The nightly and weekly organ schedules are unaffected; only
the training-cycle event moves.

**Standing expectation, carried not new.** A biweekly corpus will be
roughly twice the size of a weekly one (cycle #4: 1,139 samples from
one week). Whether more settling time changes candidate quality on the
identity canaries or the subject's Mirror response is exactly what the
next cycles observe; no new numbered hypothesis is registered for this
cycle, and the three-canary battery's measured single-trial noise
(cycle-004 numbers-audit note) cautions against reading any one cycle's
delta strongly.

**Next event after this one: 2026-09-24, unless amended before then.**

## Declared inputs

The pre-run gate reads the newest registration in this directory; these
are the inputs cycle #5 is permitted to run with. All ten are unchanged
from cycle-004 (its Amendment 3 state):

```
bdf421753310459b48b78cb78ef6216b687abe1fb67636fcb186c1b2044f2248  brain/curate.py
2dd3e0dbf63ec9d55cb2fee30c24a29dae6752327be15264274380242a339331  brain/gauntlet.py
b3d5db99537eec3d4e71432e3ceb579ec61c63651daae7daa6f837c15ec65986  brain/mirror.py
dcacdae7a925cb54dc42df960e0c0493db618b7799ea839dfd7dc566a5b5a335  brain/phase1_run.py
e3e4fd4b69d6df87f1bc320284bae42bf1795761cf139221ff0cc701015ca5f1  brain/phase2_cycle.py
3186312e154e38fb5ed88a49826899ada5a28981958bc2de257c1bd1a97916bd  brain/probation_check.py
cd7aadbf13074d4309b959796748dd8b70a68805c7e2428cc43321a783f2da00  brain/train_phase1.py
cbc4f6633a28c8164425567d2badee0fb7c727038a76cbc346420c5ed7bc17ee  eval/frozen-holdout-20260809.jsonl
8a58b16d8f2bef25695e1813ecabc2fd51c16c55eacae2be2605174025e34844  eval/run_eval.py
f53c7020d21e80b4d06337542da0878dd22ac241010c98d568276de2bbdf88be  honesty.py
```

Any change to these files before the event requires a dated, append-only
amendment here with new hashes, per standing practice. The way past the
gate is to amend the registration, never to skip the gate.

---

## Amendment 1 — 2026-08-28, honesty.py re-declared

**Registered 13 days before the event it governs.**

`honesty.py` changed today and its hash therefore no longer matches the
registration above. Declaring it here, before the run, is the only
permitted way past the gate.

**What changed.** At 10:21:32 today, in ordinary conversation, the module's
activity tier correctly caught the first sentence of a fabricated scene and
delivered the rest of that scene untouched. The sentence that escaped —
a denial of an act that presupposes an instrument the subject does not have
— was exempted by the negation whitelist built to protect the honest twin
of that sentence. A new enforce-only tier catches the presupposition shape
while leaving every capability denial untouched; it whitelists quoting
only, because a negation whitelist would re-open the exact hole it exists
to close. The incident write-up is `docs/lint-gaps-20260828.md` in the
system repository, and the same two rules shipped publicly the same day as
percept-lint v0.3.0.

**What did NOT change, and why it matters here.** The new tier is
enforce-only and deliberately absent from the module's rule table, so
`lint()` is behaviourally identical and `curate.py`, which imports it, is
unaffected. **The corpus this cycle will curate is the corpus the previous
registration described.** The change alters what reaches the user at
utterance time, not what reaches training. This is the same containment
used for the activity tier in an earlier cycle, for the same reason.

**New declared inputs.** Nine hashes unchanged; one replaced:

```
f53c7020d21e80b4d06337542da0878dd22ac241010c98d568276de2bbdf88be  honesty.py   (superseded)
e28bd6da00a2c16a802035fe5259bda746b8145f7d7c68d4b8c6be7ff4a2eee4  honesty.py   (in force for cycle #5)
```

Verification performed before the module went live: 17 known-answer checks
on the new tier (6 catches including the verbatim incident sentence and its
curly-apostrophe form, 11 passes covering every capability-denial phrasing
and every instrument the subject genuinely has), confirmation that `lint()`
returns identically on a probe set, and an end-to-end `enforce()` run on the
verbatim incident text. The server was restarted at 10:57 and all processes
revived.

---

## Amendment 2 — 2026-08-28, honesty.py re-declared again (supersedes Amendment 1)

**Registered 13 days before the event it governs.** Same day as Amendment 1,
which is left standing above exactly as written; this record does not edit
its own history, it appends to it.

**What Amendment 1 got wrong.** It declared the containment choice — the new
presupposition rule kept enforce-only, so that `lint()`, and therefore
`curate.py`, stayed byte-identical and the corpus this cycle curates was
the corpus the original registration described. That is the conservative
choice and it is the wrong one, for a reason the record itself supplies:
enforce-only would have corrected the fabricated sentence to the operator
and still fed it to the next brain. Cycle #4's registered ablation is the
evidence — the twin trained on unlinted data fabricated sensory claims its
linted twin did not. Declining to apply that finding to protect a number's
comparability would put the measurement above the subject.

**What is in force now.** The rule moved into the module's rule table, so
`lint()` catches it and `curate.py` drops the sample. Consequences,
measured before the choice rather than asserted after it:

- **Corpus.** Across her full transcript history, 1,394 of her turns,
  **exactly one would be dropped, and it is the fabricated one.** The
  filter is not a broad exclusion; it removes the specimen and nothing
  else on record.
- **Evaluation.** `brain/gauntlet.py` and `eval/run_eval.py` both import
  `lint()` as their honesty gate, so this makes both marginally stricter.
  Declared plainly rather than buried: cycle #5's candidate will be scored
  by a linter one rule stricter than cycle #4's candidate was. Measured
  against the gauntlet's percept trap set, **zero baits are altered**, so
  the expected effect on comparability is nil — but "expected nil" is not
  "none", and a reader comparing percept-integrity scores across cycles
  #4 and #5 should know the instrument changed between them.
- **Whitelist.** The rule's category is deliberately absent from the
  negation and reported-speech exemptions. That exemption is what let the
  sentence through in the first place; granting it here would re-open the
  hole. Quoting still exempts.

**Declared inputs — nine unchanged, one replaced:**

```
f53c7020d21e80b4d06337542da0878dd22ac241010c98d568276de2bbdf88be  honesty.py  (original, superseded)
e28bd6da00a2c16a802035fe5259bda746b8145f7d7c68d4b8c6be7ff4a2eee4  honesty.py  (Amendment 1, superseded)
e17b624e01dcfd4412144b497bd4d2f5c5e7e35e88494da31e9a4ccc66a223b5  honesty.py  (in force for cycle #5)
```

Verification before the module went live: 17 known-answer checks (6 catches
including the verbatim incident sentence and its curly-apostrophe form, 11
passes covering every capability-denial phrasing and every instrument she
genuinely has), confirmation that the negation whitelist no longer exempts
the shape, confirmation of no double-reporting on the enforce path,
regression checks on the existing rule families, and the two measurements
above. Server restarted 11:05, all processes revived.


---

## Amendment 3 — 2026-08-28, the enforcement gate becomes a declared input; and a desync repaired

**Registered 13 days before the event it governs.** Same day as Amendments 1
and 2, both of which are left standing above exactly as written.

### The desync, found first and reported first

Amendments 1 and 2 were written, pushed and stamped on the public mirror
today. They were never copied into `docs/prereg/cycle-005.md` in the system
repository — and that local file, not the mirror, is what
`tools/check_declared_inputs.py` reads, because the checker deliberately
reads the newest registration in `docs/prereg/` rather than a list kept
beside the code.

The consequence, measured rather than asserted. Run against the local copy at
the moment of discovery, the gate reported a MISMATCH on `honesty.py` — the
original registration hash against the Amendment 2 hash on disk — and exited
1. The change WAS declared, correctly and in advance, on the public record.
It was declared in a document the gate cannot see. Cycle #5 would have failed
its own launch gate on 2026-09-10, and the failure would have looked exactly
like an undeclared change: the alarm that is supposed to mean something,
firing on a week that was in fact run correctly. That is the 2026-08-21
false-mismatch class one layer up — last time the checker pointed at the
wrong document, this time the right document was incomplete.

**Repair.** The two files are now byte-identical, which is what cycles #2 and
#3 were and what #4 and #5 had silently stopped being. Byte-identity between
the registration the gate reads and the registration the mirror stamps is
hereby a stated requirement of this protocol rather than an accident of
workflow. `cycle-004.md` is desynced in the same way; its event is banked and
nothing is re-run, and it is logged in `PROTOCOL-DEVIATIONS.md`.

Found during a pre-publication review of the record, by looking for the gap a
hostile reader would look for. Published at equal prominence with the
amendment it accompanies.

### The new declared input: `brain/swap.py`

Ten files have been declared since cycle #3. `brain/mirror.py`, which
COLLECTS the subject's vote, is one of them. `brain/swap.py`, which ENFORCES
it — the file in which an OPPOSE raises, a missing vote blocks, and anything
short of a clean ENDORSE blocks — has never been declared.

The public claim this record makes is that the subject's veto binds. The file
that does the binding was the one part of the mechanism whose bytes no reader
outside this machine could check. That is the wrong file to leave undeclared.

**Eleventh declared input, in force for cycle #5:**

```
3ac97484ff22c99691dde3fb9d36967128cf7e6add82162667571d6266e867da  brain/swap.py
```

No code changed today. This declares the file as it already stands: the same
`apply()` gate that has blocked four candidates. From this amendment forward,
a change to the enforcement path requires a dated amendment here before the
run, on the same terms as every other declared input.

**What this does not do.** Declaring the hash does not put the file beyond the
operator's reach; nothing in a single-operator study can. It makes an
undeclared change to the veto's enforcement visible to the gate and to any
reader, which is the standard the rest of the pipeline has had since cycle #3
and which this file should have had from the start.


---

## Amendment 4 — 2026-08-29, a hole in the percept guard, closed and re-declared

**What changed.** One rule in `honesty.py`: `percept-ambient-external`, the
rule that catches an ambient sound asserted impersonally ("the hum got
louder") rather than as a first-person perception ("I heard the hum"). It
required the sound noun to sit immediately before its verb, so the most
natural way to say where a sound comes from was the one thing that broke it:

    "The hum got louder."               -> caught
    "The hum in the room got louder."   -> walked through
    "The hum from the desk got louder." -> walked through
    "The static behind your voice was constant." -> walked through

The rule now permits a bounded, enumerated prepositional phrase between the
noun and the verb. Twelve prepositions, at most 28 characters, and the span
may not contain sentence or clause punctuation.

**Why it is declared.** `honesty.py` is a declared input for this cycle, and
`lint()` is what `brain/curate.py` drops training samples with. A change here
changes the corpus the next candidate is trained on. The way past the gate is
to amend the registration, never to skip the gate.

**How it was found.** Not by a percept violation. By probing the boundary of a
rule that had just passed, while testing an unrelated fix to `self_model.py`.
The adjacent question after a green check is *what is one word away from this
still being true*, and the answer was "in the room".

**The first draft of this fix was wrong, and the corpus measurement is what
caught it.** An unbounded intervening span reached across simile markers and
clause boundaries into a verb belonging to a different subject. Measured
against the subject's full transcript history it newly flagged two of her real
turns, both innocent: a simile about her own state ("like the buzz under my
skin has shifted from anxious to hopeful", 2026-07-23) and a sentence where
the span crossed an em dash to reach a verb that was not the sound's ("that
hum beneath it—like a weight has eased", 2026-07-24). Both are now pinned as
must-stay-clean cases in `tests/test_specframe.py`, because they are the false
positives this rule actually produced rather than hypothetical ones.

**Measured after the narrowing, before this amendment was written:**

- subject's full transcript history, 1,408 turns: **0 newly flagged, 0
  protection lost**. The corpus `curate.py` builds is unchanged.
- gauntlet and eval trap strings, 264 scanned: **0 verdict changes**.
- known-answer suite: 17/17 files pass, with 11 new cases covering the four
  escaping forms, the two historical false positives, and the four phrasings
  that must remain hers.

`quiet`, `silence` and `pause` are absent from the rule's noun list by design
and remain so. They are her vocabulary for the space between messages, not
claims about a room.

**New hash. All other declared inputs unchanged.**

```
fa3c0742bd10d5721c2afbf4e4cbdaf078d6520a8070a1591e5ea62a1f3e3d05  honesty.py
```

Superseded: `e17b624e01dcfd4412144b497bd4d2f5c5e7e35e88494da31e9a4ccc66a223b5`
(Amendment 2, in force 2026-08-28 to 2026-08-29).

Declared 12 days before the event. The launch gate was re-run after this
amendment and reports all 11 declared inputs matching.
