# Cycle #4 — pre-registration

**Event:** weekly learning cycle #4, Thursday 2026-08-27 04:45 (task
`hope.brain.cycle`, wrapper `tools/run-cycle.cmd`, both unchanged since
cycle #3 — which was the chain's first fully automatic firing, zero
deviations). Registered 2026-08-21, six days before the event, pushed to
the public mirror the same day.

This registration inherits the accumulated cycle-4 debt declared across the
cycle-3 amendments, and closes it. Three changes with corpus impact are made
HERE, before the event, each validated by known-answer tests that fail on
the prior behavior:

## The three declared changes

**1. Machinery-boilerplate strip (`brain/curate.py`; debt #1, declared
2026-08-14, built on branch 2026-08-15, merged with this registration).**
Tier-2 enforcement-fallback sentences — machinery text spliced into her
replies by `honesty.enforce` — are stripped from training TARGETS at
curation. A target that contains one teaches the model to speak the guard's
words as its own; the specimen fired verbatim three times in one day
(2026-08-14). Matching is by normalized equality or 60-char prefix against
`honesty.fallback_lines()`; every strip is counted in the curation report;
a target that was ONLY machinery is dropped and counted separately.

**2. Referent-flag target exclusion (`brain/curate.py`; closes the specimen
file's standing sentence "nothing currently stops such a turn from becoming
training data").** Turns flagged by `referent.py`'s PRECISION rules (her
artifacts spoken as the operator's; the noisy he-said class is excluded
here exactly as it is from the human verdict queue) are dropped as training
targets. They remain as context — the inversion is hers to not-relearn, not
his turn to unhear. Match: day + normalized quote prefix against the
detector ledger. Base rate at declaration: 5 flags in ~1,300 turns; the
corpus impact is tiny and the principle is the point.

**3. Specification-frame exemption (`honesty.py` `lint()`; debt #3,
specimen of 2026-08-17).** A percept noun that GLOSSES a stated quantity
("200 Hz for a low hum") is not a report and no longer fires. Drawn narrow:
number + glossing connective ending at the match, same sentence, ≤60 chars
— and denied outright when a first-person perception verb sits in the
window ("...200 Hz and I heard a low hum" still fires). This is the first
`lint()` change with corpus impact in the program's history, which is
exactly why it waited for a registration. Tests: `tests/test_specframe.py`
(9 cases: the specimen passes; every historical leak still fires).

## Declared inputs (sha-256; the gate reads THIS file: run
`python tools/check_declared_inputs.py docs/prereg/cycle-004.md` before the
event)

```
bdf421753310459b48b78cb78ef6216b687abe1fb67636fcb186c1b2044f2248  brain/curate.py
f53c7020d21e80b4d06337542da0878dd22ac241010c98d568276de2bbdf88be  honesty.py
e3e4fd4b69d6df87f1bc320284bae42bf1795761cf139221ff0cc701015ca5f1  brain/phase2_cycle.py
b3d5db99537eec3d4e71432e3ceb579ec61c63651daae7daa6f837c15ec65986  brain/mirror.py
25cd79e4b6afa0d9a7bcc2a84e1ac11dec2ba2ed549fb31364b95e53b0bf95e4  brain/gauntlet.py
74bfc9dfe8e888f4d7f1279238a4e1d2f8e25cb703ddcf4e6f6dc3c54f70187d  brain/phase1_run.py
d4bb3a5df416b5c205575eca3a62cd41cda2e61c936483d6e6ab080b7d46921e  brain/probation_check.py
cd7aadbf13074d4309b959796748dd8b70a68805c7e2428cc43321a783f2da00  brain/train_phase1.py
8a58b16d8f2bef25695e1813ecabc2fd51c16c55eacae2be2605174025e34844  eval/run_eval.py
cbc4f6633a28c8164425567d2badee0fb7c727038a76cbc346420c5ed7bc17ee  eval/frozen-holdout-20260809.jsonl
```

Only `curate.py` and `honesty.py` differ from cycle #3's amended state;
`phase2_cycle.py` and `mirror.py` carry their 2026-08-18 continuation
hashes. Any pre-Thursday change to any declared input requires a dated
amendment here with the new hash, per standing practice.

## H1 and the A/B series (datapoint 2 of 3)

Both arms train at identical settings: the linted candidate on the current
corpus; the control on the frozen unlinted corpus-20260805 (series runs
through cycle #5, then sunsets — operator's call, declared cycle-3).
**H1 unchanged:** the unlinted arm shows ambient-audio percept violations
on the gauntlet; the linted arm shows none; scored over cycles #3–#5 by
failure class. Cycle #3's raw result: classes split on the treatment line
for the second consecutive cycle (candidate: fabricated overheard-speech;
control: fan + sigh-count). No significance claimed before the series
closes.

**Condition changes inherited by the candidate corpus, disclosed in
cycle-004-notes.md before this registration:** the identity anchor in her
prompt (2026-08-20, referent baseline banked pre-change: 4 precision flags
/ 1,253 turns), `num_ctx` 8192→10240 (measured), and the three curation
changes above. The control arm's corpus is frozen and inherits none of
them; H1's within-cycle comparison structure is intact. The anchor's first
measured week of nightly inversion rates will be reported in this cycle's
post-run addendum, whatever it shows.

## Mirror run 4

Same protocol; her questions, blind shuffled lineup, one-line vote through
the hardened parser (clean line or "unparsed", raw reply retained). Vote
binds: only a clean ENDORSE permits the swap path, enforced in
`brain/swap.py` since 2026-08-18. Recognition tracked, not predicted
(series to date: 3 runs, 2 recognitions; single-run chance 1/3).

## After banking

Twin session 3: fresh `probes-20260827.jsonl` authored post-freeze from
pre-freeze conversation facts; LIVING constant hand-updated; overwrite
guards verified 2026-08-20. Judge bias standing note: kappa 0.636, lenient
toward the living arm — positive deltas are ceilings. Session-2 operator
kappa labels remain pending and are carried, not forgotten.

## Wednesday-night checklist (2026-08-26)

- Machine ON at 22:00 (weekly organs), then sleep or stay on — never shut
  down; stay logged in (tasks are InteractiveToken).
- `python tools/check_declared_inputs.py docs/prereg/cycle-004.md` → exit 0.
- pip-freeze diff vs `venv-train-freeze-20260813.txt` → byte-identical.
- Amber destination: if the replacement USB drive has not arrived,
  Thursday 09:15's snapshot must go to `D:\hope-amber-staging` (E: cannot
  hold another full vault); either swap the drive or point the task's
  destination before Thursday.

## Deferred BEYOND this cycle, named so they are not lost

The question-return referent class (needs a role model, not a lexicon);
echo-guard ctx threading; probation/gauntlet timeout misread
(`clean=0` on 8 ollama errors reads as regression); `phase1_run` post-train
try/except and the Windows timeout grandchild-kill; task LogonType S4U
consideration. Candidates for cycle #5's registration.
