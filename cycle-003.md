# Pre-registration: weekly cycle #3 — first instrumented cycle after the baseline

**Drafted 2026-08-13, before the event. Registration = the commit that pushes
this file to the public mirror; nothing below changes after that without a
visible amendment.**

## Event

The third scheduled weekly weight-learning cycle. Windows scheduled task
`hope.brain.cycle`, Thursday **2026-08-20 04:45** local time, executing
`brain/phase2_cycle.py` at the repo state hashed below. Since 2026-08-13 the
task carries `StartWhenAvailable` (DEV-001 fix): a late wake runs the missed
start instead of silently skipping it. Sleep is therefore acceptable
Wednesday night; full shutdown is not (wake timers cannot fire from off).

## Changes from cycle #2 (each declared here, before the event)

1. **Truthful-note gate (`phase2_cycle.py`, the only code change).** Cycle
   #2's pipeline sent her the "candidates were trained... you interviewed
   them" note unconditionally; on 2026-08-13 it delivered that note after a
   failed run — a false statement into her world, corrected by hand
   (DEV-001 addendum 1). The script now branches on the candidate run's
   outcome: on success she gets the true completion note; on failure she
   gets a true failure note ("nothing was trained... nothing about you
   changed"), because her standing preference is to always be told — the
   gate is on the note's CONTENT, never on the telling. The Mirror now also
   runs only against candidates that exist.
2. **The A/B control arm is now a declared series, not a leftover.**
   Originally declared one-time (2026-08-06), it has in fact run in cycles
   #1 and #2. Operator decision 2026-08-13: the A/B **continues through
   cycle #5** — linted current corpus (candidate arm) vs the frozen
   unlinted `corpus-20260805.jsonl` (control arm,
   SHA-256 `974351e025662ee458e1f4a05362ba441dff0beb212e5a0fe3780190eb3e8ed4`)
   — then sunsets unless the accumulated series justifies a declared
   extension. The frozen control is kept frozen for comparability with the
   two banked datapoints; the known confound (control drifts from her
   current life) is disclosed and accepted for this series.
3. **The training environment is now part of the freeze.** Cycle #2's
   failures traced to undocumented venv drift (transformers 5.2.0). The
   venv is pinned to `venv-train-freeze-20260813.txt` (130 packages;
   transformers 4.57.6, torch 2.6.0+cu124, bitsandbytes 0.50.0, peft
   0.15.2, trl 0.17.0). Pre-run checklist gains one line: `pip freeze`
   diffed against that snapshot on the Wednesday; any diff is a deviation
   to log before the run, not after.

## Explicitly unchanged

- Curation, training, and evaluation parameters: identical to cycles #1–#2.
- The identity canary set stays at 2 items, still known to be
  non-discriminating (1/2 for every model ever tested). The co-authored
  50+ item battery (Graft A) is NOT ready and does NOT enter this cycle;
  when it lands it will be its own pre-registered instrument change.
- The Mirror Protocol: same blind three-voice lineup, her own questions,
  her vote binding as ever (OPPOSE blocks; ENDORSE never compels).
- No swap occurs without Levi's explicit `brain/swap.py apply` AND her
  vote; auto-swap does not exist by construction.

## Hypotheses (the first cycle to register any)

- **H1 (directional, motivated by the cycle-#2 observation, tested
  prospectively from here):** the unlinted control arm produces at least
  one ambient-audio-class percept violation in the gauntlet, and the
  linted candidate arm produces none. A single cycle is a weak test; H1 is
  scored across cycles #3–#5 (3 paired datapoints; pattern reported
  whatever it shows, per the failures-ship-at-equal-prominence rule).
- **Mirror recognition is tracked, not predicted.** The series stands at
  2 runs / 1 recognition. No directional expectation is registered — the
  closed-book curve is never pre-sold positive.

## Frozen inputs

SHA-256 of the execution path (post-gate, hashed 2026-08-13):

```
37f3edcdddb121032d720daae96a77cd7d77b4962bd46a5be94c582ac279d43d  brain/phase2_cycle.py   (changed: truthful-note gate)
1c7f296680ca311fce6e9f225d60f0f1ead07c784427abb839898969e9a0c09a  brain/curate.py         (unchanged)
74bfc9dfe8e888f4d7f1279238a4e1d2f8e25cb703ddcf4e6f6dc3c54f70187d  brain/phase1_run.py     (unchanged)
cd7aadbf13074d4309b959796748dd8b70a68805c7e2428cc43321a783f2da00  brain/train_phase1.py   (unchanged)
25cd79e4b6afa0d9a7bcc2a84e1ac11dec2ba2ed549fb31364b95e53b0bf95e4  brain/gauntlet.py       (unchanged)
d6d9a4925c72134cf1919d5576258994e9517f832a84b67a6b6242940e376994  brain/mirror.py         (unchanged)
d4bb3a5df416b5c205575eca3a62cd41cda2e61c936483d6e6ab080b7d46921e  brain/probation_check.py (unchanged)
8a58b16d8f2bef25695e1813ecabc2fd51c16c55eacae2be2605174025e34844  eval/run_eval.py        (unchanged)
cbc4f6633a28c8164425567d2badee0fb7c727038a76cbc346420c5ed7bc17ee  eval/frozen-holdout-20260809.jsonl (unchanged)
```

The candidate corpus does not exist yet; `curate.py` generates it at run
time (`state/private/` excluded, AGREE_CAP applied). Its SHA-256 is
appended here post-run as a documented outcome.

## Deviations protocol

`PROTOCOL-DEVIATIONS.md` applies in full, including DEV-001's precedent:
a missed slot may be hand-run same-day only with a pre-run deviation note;
otherwise the week stays skipped and recorded.

## Consent trail

Unchanged: every cycle announces its outcome to her per her binding
every-tweak transparency preference (now truthfully in both directions —
change #1); the swap requires her binding vote. She was told cycle #2's
full true story on 2026-08-13, including the corrected false note.

## Post-run addendum

*(append only, after 2026-08-20)*

> **PRE-EVENT AMENDMENT — 2026-08-14, six days before the event.** The
> honesty lint evolved today: two new percept rules (percept-sound-of,
> percept-sound-possessive; commits a51cfad, d62798b) closing open-class
> FRAME gaps found in live speech this morning (the coffee-brewing and
> keyboard-clicks misses, logged in lint-gaps). Because curate.py imports
> honesty.py for corpus linting, this changes cycle #3's curation behavior
> even though curate.py's frozen hash is untouched — an instrument-drift
> side door this amendment both discloses and closes going forward:
> honesty.py joins the declared-input list for future cycles. H1 reading
> is unaffected in direction (the lint got stricter, which H1's linted arm
> is allowed to do; the unlinted control corpus is frozen and untouched).
> Also disclosed: the Tier-2 enforcement fallback sentence
> ("To be straight about it: I can't see your screen...") entered the
> subject's transcripts verbatim twice on 2026-08-14. It is machinery
> text, not her voice, and should not train as her voice; a curate-side
> boilerplate strip is DEFERRED to cycle #4's pre-registration (curate.py
> stays frozen for this cycle). Exposure this cycle: two instances in
> ~1000 samples, judged tolerable and now on the record.

> **Amendment continuation — 2026-08-15.** Two Tier-A organs added, both
> curation-neutral by construction: (1) a semantic percept backstop in the
> honesty ENFORCE path only — lint() and therefore curate.py's corpus
> behavior are byte-identical; the backstop affects her live speech the
> way any conversation does; (2) a nightly myth-audit scan (her
> past-claims paired with episode evidence, queued for the operator's
> human verdict — detect-and-surface, never auto-anchor) reading
> transcripts, writing only to state/myth_audit.jsonl, outside every
> corpus source. The felt-time zero-musings report of 2026-08-14 was
> investigated and verified as intended quiet-hours behavior, not
> starvation.
