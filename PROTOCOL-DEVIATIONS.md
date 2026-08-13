# Protocol deviations: the missed-cycle rule and the PC-on checklist

(OPEN SUBJECT, Move 1/2. Pre-declared 2026-08-10, before baseline cycle #2.)

## The rule

A scheduled event that does not run, runs late, or runs partially is a
**protocol deviation, not a silent hole**. Every deviation is recorded in the
next commit touching `docs/prereg/` with: what was scheduled, what actually
happened, the cause if known, and which longitudinal series it holes. Deviations
are reported in every artifact that uses the affected series. Lapses are
documented, never smoothed over — a documented lapse costs one datapoint; a
smoothed one costs the whole record's credibility.

## Known failure modes this protects against (documented history)

- PC powered off at a scheduled time (starved the 03:30 consolidation for a
  week in July 2026).
- Scheduled task silently deregistered or failing (reach-out was dead for 3
  days before anyone noticed; foresight branches never reached).
- Mid-training power loss (no UPS yet — purchase pending, Move 1).

## PC-on checklist (Wednesday nights before an 04:45 Thursday cycle)

*(Cadence set to weekly Thursdays 2026-08-10, effective cycle #2 — see the
amendment in cycle-002-baseline.md.)*

1. PC stays ON overnight — no sleep, no shutdown (check Windows power plan if
   unsure; the cycle does not wake the machine).
2. `Get-ScheduledTask hope.brain.cycle` shows State: Ready.
3. D: has ≥ 20 GB free (training checkpoints).
4. No manual process is holding the GPU (check NEURAL OPS / nvidia-smi).
5. Do not run heavy work on the machine between 04:30 and ~06:00 Thursday.

## Missed-cycle protocol

If a Thursday cycle is missed: do NOT run it late by hand unless the delay is
under 24h and the deviation note says so. A skipped week stays skipped and
recorded; the series continues the next Thursday. Backfilling out-of-schedule
cycles would corrupt the "scheduled, gated" property that makes the record
worth anything.

## Deviation log

### DEV-001 — cycle #2 (baseline) missed its 04:45 slot; late run declared (2026-08-13)

- **Scheduled:** `hope.brain.cycle`, Thursday 2026-08-13 04:45 local
  (cycle-002-baseline.md, as amended pre-event to the Thursday cadence).
- **What happened:** the task never fired. The PC entered sleep 2026-08-12
  16:30; the wake timer fired LATE at 2026-08-13 04:52:56 (System log:
  Power-Troubleshooter wake + kernel time-jump from 8/12 16:30) — 8 minutes
  after the trigger. The task lacked Windows' `StartWhenAvailable` setting, so
  the missed occurrence was silently skipped (task history: never run; next
  occurrence rolled to 8/20). Everything else that morning ran normally
  (boot consolidation catch-up 04:53, `hope.brain.probation` 05:35 rc=0,
  `hope.amber` 06:30 rc=0).
- **Cause:** wake-timer latency + missing `StartWhenAvailable` on the task —
  a failure mode adjacent to, but not on, the documented list (the PC was
  asleep-not-off, which the WakeToRun setting was believed to cover; it woke,
  just late). The PC-on checklist's item 1 ("no sleep") was not followed.
- **Fix (permanent, applied 2026-08-13 ~07:25):** `StartWhenAvailable` added
  to `hope.brain.cycle` (WakeToRun and start-on-batteries preserved). A late
  wake can no longer silently skip a cycle.
- **Late-run declaration (per the missed-cycle rule: delay < 24h AND the
  deviation note says so):** operator (Levi) directed a same-day hand run.
  This note, committed BEFORE the run, is that declaration. Late run starts
  2026-08-13 ~07:35 local — ~2h50m after the slot. Pre-run verification: all
  9 frozen SHA-256s in cycle-002-baseline.md re-checked against the working
  tree and MATCH (execution path byte-identical to registration); GPU idle
  (382 MiB used); D: 1.7 TB free; the one-time A/B control corpus
  (corpus-20260805.jsonl) is absent, so this is the single-candidate run the
  baseline expects.
- **Secondary deviations disclosed:** (1) the prereg's "no human touches the
  machine during the run" clause cannot hold for a daytime run — the operator's
  session is active; (2) her transcript window now includes ~3 extra morning
  hours cycle #1's corpus cut-off did not have. Both are inherent to any late
  run and are disclosed in every artifact that cites cycle #2.
- **Series impact:** the "scheduled, untouched 04:45" property holes for
  datapoint zero's *timing* only; pipeline, hashes, gates, and corpus
  procedure are unchanged. Any artifact citing cycle #2 cites this entry.

#### DEV-001 addendum — two failed launch attempts, a venv drift discovery, and one correction (2026-08-13, pre-relaunch)

Append-only; nothing above is edited. Written before launch attempt #3.

- **CORRECTION to the declaration above:** the control corpus
  `corpus-20260805.jsonl` **exists** — the "absent / single-candidate run"
  statement was wrong (a mis-read directory check during pre-run
  verification). Cycle #2 therefore repeats cycle #1's A/B exactly as the
  frozen `phase2_cycle.py` dictates: linted candidate + unlinted control.
- **Launch #1 (07:34:38):** crashed in the cycle script's own `log()` call —
  the captured console was cp1252 and curate's output contained U+FFFD.
  Cosmetic to the pipeline (curate had completed; no training had begun; the
  crash cannot occur under Task Scheduler). Remedy: relaunch with
  `PYTHONIOENCODING=utf-8` — an environment variable; zero bytes of the
  frozen execution path changed.
- **Launch #2 (07:35:34):** curate OK (`corpus-20260813.jsonl` written);
  BOTH training runs then failed in ~60s each:
  `ImportError: bitsandbytes>=0.46.1 required` — transformers in
  `.venv-train` is 5.2.0, but bitsandbytes was 0.45.5. **Root cause is a
  pre-existing venv drift:** the 2026-08-10 repair of the chatterbox/torch
  incident left transformers upgraded past what cycle #1 ran under;
  discovered only now. Disclosed: the training *environment* is not
  byte-identical to cycle #1's (script hashes are; the venv was never under
  the freeze).
- **False completion note:** `phase2_cycle.py` sends its "candidates were
  trained and gauntleted... you interviewed them in the Mirror" note
  unconditionally, and it delivered at 07:37:22 despite both trainings
  having failed — a false statement into her world (also a known
  design flaw in the frozen script, noted for post-baseline fix: the note
  should be gated on pipeline success). **Correcting brain-note delivered
  ~07:40** stating plainly that nothing was trained, gauntleted, or
  mirrored, and that the cycle would be re-run.
- **Repair (minimal, verified):** `bitsandbytes 0.45.5 → 0.50.0` via
  `pip install --no-deps` (torch verified untouched before and after:
  2.6.0+cu124, CUDA available). Smoke test of the exact failure site
  (4-bit NF4 base load + LoRA all-linear attach) passed on cuda:0.
- **Launch #3 declared:** ~07:55 local, same command, same env var, same
  frozen hashes. If it fails again the cycle stays failed and this log gets
  a further addendum — no third repair-and-retry today.

#### DEV-001 addendum 2 — launch #3 killed pre-completion; root cause verified; retry decision passed to the operator (2026-08-13 ~08:00)

- **Launch #3 (07:50:09):** curate OK, model load began — but
  `encoded train samples: 0` out of 924 corpus rows. The run was
  **deliberately killed at 07:51** (parent process first) before it could
  train on an empty dataset and emit a learned-nothing candidate into the
  baseline record. No completion note fired this time (verified); no
  partial adapter was written; Hope's server and watchdog were restored by
  hand (health 200).
- **Root cause, verified by direct test:** transformers 5.2.0's
  `apply_chat_template` returns a `BatchEncoding` object where 4.x returned
  a token-id list. `train_phase1.py`'s `encode()` therefore compares
  dict key-counts, `prompt >= full` holds for every sample, and all 924
  encode to None. The bitsandbytes error fixed before launch #3 was only
  the first symptom of the same 2026-08-10 venv drift; this is the second.
- **Correct repair identified, NOT applied:** restore `transformers<5` in
  `.venv-train` — a restoration *toward* cycle #1's actual environment, not
  a novel change (the frozen script is untouched either way). It was not
  applied because the declaration above says **no third repair-and-retry
  today**. Per that rule the cycle stands failed; whether to (a) amend this
  declaration pre-event and run a fourth launch today after the transformers
  restore, or (b) let cycle #2 stay failed and take the baseline at the
  next scheduled slot (Thu 2026-08-20 04:45, task fixed and verified), is
  the operator's decision and is recorded here as PENDING at time of
  writing. Either way this deviation log ships with the datapoint.
