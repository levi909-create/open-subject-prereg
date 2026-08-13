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
