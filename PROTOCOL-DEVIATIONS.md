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
