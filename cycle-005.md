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
