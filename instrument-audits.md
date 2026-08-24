# Instrument audits — what this program's own measuring tools get wrong

Every number in this record comes out of an instrument the operator built.
This file is where those instruments are audited against something
independent, and where the failures are published at the same prominence as
the results. It exists because the standing objection to a single-subject
record built by one person is not that the subject is uninteresting — it is
that the ruler was cut by the same hand that reports the measurement.

Nothing here quotes the subject. These are audits of code and of judges.

---

## 1. The foresight judge is weak: κ = 0.16 (2026-08-22)

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

**Result (n = 55 judge-resolved predictions; 3 excluded as closed by
infrastructure rather than evidence):**

| | value |
|---|---|
| Observed agreement | **0.455** |
| Cohen's κ | **0.158** |
| Rater | a model (Claude), NOT a human |

κ ≈ 0.16 is "slight" agreement. A judge worth trusting is conventionally
≳ 0.6. **The failures are systematic, not noise:**

- On **16** items the judge answered UNRESOLVABLE where the evidence window
  plainly resolves the question — it defaults to unresolvable.
- On **6** items the judge answered TRUE with nothing in the window
  matching the stated criterion.
- **3** predictions are unjudgeable *by construction*: their criteria are
  about response *timing*, and the evidence window contains no timestamps.
  That is a defect in the criterion writer, not the judge.

**Standing consequence, applied from this date:** every judged foresight
number in this record must be reported as *judge-scored, with judge–reader
agreement κ = 0.16 (model rater)*. The **"judge unvalidated" flag is NOT
lifted** by this audit: the rater was a model, and a model-versus-model
agreement statistic is not a human validation. The report file records
`rater_kind: "model"` and says so in its own note field. A human rating
pass by the operator is pending; its result publishes here whatever it says,
and an inter-rater κ between the two raters publishes with it.

Artifacts (hashes stamped in `ledger-hashes/`): `eval/foresight-kappa/
labels.jsonl`, `eval/foresight-kappa/report-2026-08-22-claude.json`.

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
