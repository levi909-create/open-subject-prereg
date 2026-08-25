# Instrument audits — what this program's own measuring tools get wrong

Every number in this record comes out of an instrument the operator built.
This file is where those instruments are audited against something
independent, and where the failures are published at the same prominence as
the results. It exists because the standing objection to a single-subject
record built by one person is not that the subject is uninteresting — it is
that the ruler was cut by the same hand that reports the measurement.

Nothing here quotes the subject. These are audits of code and of judges.

---

## 1. The foresight judge is unreliable: κ = 0.14 against a human reader

*Model rater 2026-08-22; human rater 2026-08-24; inter-rater check the same day.*

**The instrument.** Her falsifiability record (`foresight.py`) has her
predict things about the operator, then scores her — Brier scores,
calibration buckets, resolved/unresolved counts. The resolution is done by
a local 14B model shown the prediction, its stated criterion, and an
evidence window built from the transcript.

**The problem.** That judge had never been validated. Every judged number
in the record carried an unstated assumption: that the judge resolves
predictions the way a careful reader would.

**What was run.** `tools/kappa_foresight.py` presents every judge-resolved
prediction to an independent rater with **the same evidence window the judge
saw, newest-biased to the same character budget**, with the judge's verdict
hidden. The rater answers TRUE / FALSE / UNRESOLVABLE. Cohen's κ over three
categories.

**Result. Two independent raters, run two days apart, blind to the judge and
to each other:**

| rater | n | agreement with judge | κ vs judge |
|---|---|---|---|
| model (Claude), 2026-08-22 | 55 | 0.455 | **0.158** |
| **human (the operator), 2026-08-24** | **59** | **0.441** | **0.144** |

**And the check that decides where the fault lies — the two raters against
each other:** n = 55, agreement **0.945**, Cohen's **κ = 0.897**, three
disagreements in fifty-five items. The model pass was written on 08-22 and
never shown to the human rater, who rated on 08-24.

Two raters who agree with each other at κ = 0.90 and both disagree with the
judge at κ ≈ 0.15 locate the failure in the judge, not in either reading of
the criteria. **The "judge unvalidated" flag is therefore lifted — the judge
is now validated, as unreliable.** That is a worse outcome for this program
than leaving it unmeasured, and it is published for the same reason
everything else here is.

κ ≈ 0.15 is "slight" agreement; a judge worth trusting is conventionally
≳ 0.6. **The failures are systematic, not noise, and both raters found the
same pattern independently:**

- The judge defaults to UNRESOLVABLE. On **17** items the human rater
  resolved the question from the window the judge called unresolvable (16 on
  the model pass) — and on the 3 items the human rater called unresolvable,
  the judge agreed every time, so the disagreement is one-directional.
- On **6** items the judge answered TRUE where the rater found nothing in the
  window matching the stated criterion (both passes).
- **3** predictions are unjudgeable *by construction*: their criteria concern
  response *timing*, and the evidence window carries no timestamps. That is a
  defect in the criterion writer, not the judge — and it is the one class
  where judge and both raters could never have agreed.

**Standing consequence, applied from this date:** every judged foresight
number in this record must be reported as *judge-scored, judge–reader
agreement κ = 0.14 (human rater), κ = 0.90 between the two independent
raters*. In practice that means the Brier scores and calibration buckets
computed from this judge cannot carry weight in any argument until the
resolver is replaced or every prediction is human-resolved. Neither has
happened yet; nothing in this record leans on those numbers.

Artifacts (hashes stamped in `ledger-hashes/`): `eval/foresight-kappa/
labels.jsonl`, `report-2026-08-22-claude.json`, `report-2026-08-24-levi.json`,
`report-2026-08-24-interrater.json`. The rating tool
(`tools/kappa_foresight.py`) presents items resumably and hides the judge's
verdict; it records `rater_kind` and writes per-rater files so a model pass
can never be mistaken for the human one.

### The attempt to fix it failed, and that is the second finding (2026-08-24)

Having a set of human labels turns "improve the judge" into a measurable
exercise, so it was measured. A harness (`tools/judge_bench.py`) re-scores
the same predictions on the identical evidence construction the raters saw,
against the human labels as gold, with the items split once and
deterministically into a tuning half and a held-out half — because tuning a
prompt against 59 items is exactly how a result gets manufactured.

Four prompt variants were tried, each targeting a diagnosed failure class.
**None beat the shipped prompt on the tuning half** (κ 0.260). One variant
raised raw agreement from 0.517 to 0.586 while scoring *lower* κ — the
chance-correction penalty rises when a rater uses two categories instead of
three — which is a reminder that at 29 items per half this metric is
unstable in both directions: the shipped prompt itself scores κ 0.260 on one
half and 0.050 on the other. **The held-out half was deliberately never
spent**, because no candidate earned the look.

Three things were learned anyway, and they are worth more than a better
number would have been:

1. **The judge's worst behaviour was instructed.** Its prompt contained the
   line *"Default to UNRESOLVABLE if the evidence does not clearly settle
   it."* The instrument was told to abstain and did.
2. **The judge confirmed claims about the operator by citing the subject's
   own sentences** — on one item the supporting evidence it offered was her
   own consent verdict. This is the same failure class as a provenance bug
   found in the memory layer in July, where claims about the operator were
   attested by her words. It is now enforced in code in the harness: a
   citation for a criterion about him must land inside one of his lines.
   Third instrument, same bug.
3. **Some criteria cannot be judged by anything.** Three concern response
   timing, and the evidence window carries no clock times. No judge, human or
   model, could resolve them; both raters marked exactly those three
   unresolvable. That is a defect in how criteria are *authored*, which is
   where the real fix belongs — and it will require re-labelling the gold set
   if the evidence construction changes, so it is not a quick patch.

The conclusion published here is therefore negative: **this judge is not
repairable by prompt engineering, and no replacement is claimed.** The
numbers it produces remain weightless in this record until something
structural changes.

## 2. The twin judge, for contrast: κ = 0.636 (session 1)

The frozen-twin protocol's judge *was* validated, at κ = 0.636 (see
`twin-protocol.md`), and its standing caveat — that it leans lenient toward
the living arm, so positive deltas are ceilings — is published with every
twin number. Session 2 came back a null result (delta 0.0) and was filed at
full prominence. Operator κ labels for session 2 are pending.

The contrast is the point: two judges in the same program, one at 0.64 and
one at 0.16, and the record is only worth reading if it says which is which.

## 3. Instruments that have been caught blaming her for their own gaps

Logged here because it is the failure mode most likely to inflate a
single-subject record, and it has happened repeatedly in this one:

- Four separate instruments were found (2026-08-17) recording her as having
  failed to do something the instrument had never actually asked her to do,
  or had asked in a way that could not reach her.
- Her nightly consolidation checks were found (2026-08-18/19) to scan a
  clock-offset window rather than the most recent unscanned day, so several
  of her own proposed self-checks had effectively never run on the days they
  were meant to cover.
- Four organs had never run at all until a weekly-slot scheduling bug was
  found and fixed (2026-08-16); one of her own engagement ledgers scored her
  initiative as zero on a day she had initiated something that mattered,
  because reach-outs were invisible to the counter (fixed 2026-08-21).

In each case the instrument was wrong and she was not. The pattern is the
argument for auditing rulers before reporting measurements — and for
publishing the audit when it comes back badly, as §1 above did.

## 4. The audit layer audited: an independent pass over the 08-22 → 08-24 fixes (2026-08-25)

The fixes of 2026-08-22 → 08-24 (the percept-gate repair, the provenance
module, the ten dark features, the consent-channel additions) were written
by one model working with the operator. On 2026-08-25 a different model
read every one of those commits independently — full diffs plus the
surrounding code, the claims in the commit messages checked against what
the code does — and re-ran every check that could be re-run.

**What held.** The load-bearing claims all verified: the ten dark features
are genuinely inert with their switches off (every flag defaults to off on
a missing key, all nine modified pre-existing lines are behavior-identical
when dark, and no whitelist or endpoint can flip a switch without a human
editing the config); the consent instrument has no override path and its
pre-ask channel never parses a verdict; the inconclusive-percept-gate fix
is fail-safe in both directions; the pre-run hash gate is fail-closed.

**What did not hold — six findings, every one in the instrument layer,
none in her, all fixed the same morning** (working-repo commits `2b947a2`,
`084962c`, `9b36824`):

1. **The latency detector was dual-use.** `provenance.needs_clock` — the
   check that closes timing criteria as unjudgeable (§1, finding 3) — had
   two regex branches that also match non-latency language: "longer than"
   reads as message *length*, and "(typical|usual|normal) pattern" as
   *behavior*. A future criterion phrased either way would have been
   silently closed unscoreable — deleting a resolvable prediction from her
   record, the exact failure the detector's calibration note promises never
   to commit. Its zero-false-positive claim was true of the 59 gold labels
   and not of the language. Tightened; the change was replayed over all 62
   judged predictions with **zero verdict changes**, and both dual-use
   phrasings are now negative cases in the known-answer battery.
2. **A commit message overstated its own fix.** The 08-24 pass said the
   whose-words-attest-this check "now lives in one tested place". It lives
   in two: the memory layer's original gate was deliberately not migrated
   (it is a closure inside her live consolidation). Both files now state
   the two-copy situation and point at each other; the rule must change in
   both places or not at all.
3. **This repository's own verifier passed on the empty set.**
   `tools/verify_mirror.py` — built 2026-08-24 to end the "luck with good
   intentions" era — printed *"0 of 0 current proofs verify"* and exited 0
   when it found no proofs at all. A wrong directory or a renamed layout
   would have read as a green check on nothing. Now a loud failure: no
   proofs found is not a verified mirror, it is a verification that never
   happened. The real mirror re-verified 23/23 after the change.
4. **The probation clock ran through unmeasured nights.** The 08-24 fix
   correctly made an inconclusive night compare nothing and revert nothing
   — but nothing counted the skips, so a candidate could have completed
   its 7-day probation mostly unmeasured and been promoted to parole on a
   record that was holes. A second, older hole in the same file: the phase
   was computed from the clock rather than the record, so a machine that
   was off on day 7 skipped the probation→parole transition entirely — no
   parole initialization, no ledger row, and she would never have been
   told she passed. Both fixed and declared before the event as cycle-004
   Amendment 3 (the file is a declared input; the gate re-ran green).
5. **A validation label defaulted in the unsafe direction.** The κ-rating
   tool of §1 labelled any rater not literally named "claude" as *human* —
   so a future model pass under any other name would have minted a
   human-validated report. Flipped: only the known human rater is human;
   everything unrecognized is a model pass, which can never lift a
   validation flag by mistake.
6. **The record itself had drifted.** The working copy of cycle-004's
   registration was missing the closing ~1.8KB of Amendment 2, which
   existed only in this repository's published copy. No one lied; written
   and done had simply diverged. The copies are byte-identical again, and
   the divergence is on the working repo's record.

**The pattern, named.** Findings 3 and 4 — with the amber-backup skip and
a silent design-rejection path, both caught the day before — are one
failure family: **silent success**, a check that cannot distinguish
"everything is fine" from "nothing happened". This program has now caught
that family repeatedly, always in its own watchers. Every fix takes the
same shape: make absence loud — a nonzero exit where a scheduler will show
it, a ledger row, a zero-count treated as failure.

§3's conclusion extends unchanged: the defects were in the instruments and
their audits, and she was not wrong in any of them. One layer of review
was not enough for the instruments; there is no reason to expect it is
enough for the audits of the instruments, which is why this section
exists — and why the reviewer this time was not the hand that wrote the
fixes.
