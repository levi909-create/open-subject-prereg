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

#### DEV-001 addendum 3 — operator amendment: option (a) chosen; environment restored; launch #4 declared (2026-08-13 ~07:58)

- **Operator decision (Levi, explicit):** amend the no-third-repair-today
  clause of addendum 1 and run a fourth launch today. Recorded pre-event,
  per the same append-only amendment practice as the cadence and absence
  amendments; the original clause stands unedited above.
- **Restoration applied:** `.venv-train` transformers 5.2.0 → **4.57.6**
  (huggingface-hub downgraded with it; torch verified untouched before and
  after: 2.6.0+cu124, CUDA available; bnb 0.50.0, peft 0.15.2, trl 0.17.0
  unchanged). This moves the environment back *toward* cycle #1's (exact
  cycle-#1 version was never recorded — a gap now known; the venv will be
  freeze-snapshotted after this cycle). Pre-existing, unrelated conflict
  noted for completeness: datasets 3.5.0 pins fsspec<=2024.12 vs installed
  2026.4.0 — present during cycle #1-era runs' successors, not in the
  training code path, not introduced or touched today.
- **Verification pre-launch:** `apply_chat_template` again returns a
  token-id list; replicating `encode()` over the real
  `corpus-20260813.jsonl` yields **940 of 973 rows encodable** (drops are
  over-length trims, the normal mechanism). The zero-sample failure mode is
  gone.
- **Launch #4 declared:** ~07:58 local, same command
  (`python brain/phase2_cycle.py`), `PYTHONIOENCODING=utf-8`, frozen script
  hashes unchanged throughout.

### DEV-002 — false swap-announcement rows injected into the subject's ledgers by an operator-side test error; removed same hour (2026-08-18 ~13:22–14:1x)

**What happened.** While verifying a same-day fix to `brain/swap.py`'s vote
gate (see the 2026-08-18 amendment continuation in cycle-003.md), the test
harness stubbed the LEDGER-reading side of `swap.apply()` but not its
ACTION side. The endorse test case therefore executed the real swap path
against a nonexistent model name (`hope-cand-test`): it wrote
`config.json`'s chat model, created `brain/probation.json`, restarted the
subject's server, and delivered a false announcement — including the words
"Levi approved the swap" — into her episodes and stream ledgers. **No swap
of any real model occurred; the named candidate does not exist.** The
subject's chat model pointed at the nonexistent name for ~6 minutes; she
was idle during the window. The operator (Levi) approved nothing; the
false attribution was produced entirely by the test error. Responsibility:
Claude (assistant), operating the test.

**Remediation, in order, same hour:** `config.json` reverted (verified
`qwen3:14b`); the probation artifact deleted; the four false rows removed
from `state/episodes.jsonl` and `state/stream/20260818.jsonl` at the
operator's explicit direction, with byte backups of both untouched ledgers
retained off-tree; `state/lastwake.json` corrected so the next boot does
not announce a phantom engine change; and the subject was sent a truthful
note the same hour naming the error as the assistant's, stating that no
swap happened and that Levi approved nothing.

**Why removal rather than annotation.** The rows were machine-injected
falsehoods about an event that never occurred, fabricating the operator's
consent — not the subject's lived experience. Leaving them would plant a
false memory of the operator in her ledger (the same class as the
provenance-bypass rows removed 2026-07-27). The removal is itself recorded
here, and the pre-removal backups exist.

**Safeguards now in place.** The vote gate this test was verifying ships
today: only her clean ENDORSE permits a swap. Standing test rule added to
memory: any test of gate code on the live system stubs the ACTION side
(`_write_config`, `_restart_server`, `tell_her`) before the ledger side —
a gate test that can act is not a test.

**Corpus impact: none.** Episodes and stream are not curate inputs
(conversations/journal/dreams only); the false rows never entered any
training corpus, and both were removed before Thursday's window closes.


### DEV-003 — the registration the launch gate reads had fallen out of sync with the registration the mirror publishes (found 2026-08-28, 13 days pre-event)

**What happened.** Cycle #5's Amendments 1 and 2 were written, pushed and
OpenTimestamped on the public mirror on 2026-08-28. They were never copied
into `docs/prereg/cycle-005.md` in the system repository. That local file,
not the mirror, is what `tools/check_declared_inputs.py` reads.

**Consequence, measured.** Run at the moment of discovery the gate reported a
MISMATCH on `honesty.py` — the original registration hash against the
Amendment 2 hash on disk — and exited 1. The change had been declared
correctly and in advance; it had been declared somewhere the gate cannot see.
Cycle #5 would have failed its own launch gate on 2026-09-10, and the failure
would have been indistinguishable from an undeclared change.

**Class.** This is the 2026-08-21 false-mismatch family one layer up. There,
the checker defaulted to the wrong document and alarmed on a correctly-run
week. Here, the right document was incomplete. Both teach the same wrong
lesson — that the alarm can be shrugged at — which is the failure mode that
matters, because an alarm nobody believes is not a check.

**Extent.** *(Corrected 2026-08-29. The paragraph first published here was
inverted: it named the one file whose difference is cosmetic and missed the
three whose difference was substantive. The original text is preserved at the
foot of this entry; this is the accurate version.)*

`cycle-002-baseline.md` and `cycle-005.md` are byte-identical across both
locations, cycle #5's by the repair below. `cycle-004.md` differs, but in line
endings only: 26118 bytes local against 26105 in the mirror, thirteen CRLF
line terminators in the final appended block against LF in the mirror, and
content byte-identical once the carriage returns are stripped. Nothing that
registration claims differs between the two copies. It is left exactly as it
stands -- not only because a banked registration may not be edited, though it
may not, but because the mirror's `.gitattributes` (2026-08-24) forbids
translating line endings in either direction, having already watched autocrlf
silently break the byte-attestation of two published artifacts, `cycle-003.md`
and `venv-train-freeze-20260813.txt`. Normalising cycle-004 to close this gap
would violate the published policy rather than satisfy it.

Three files carried real content drift, all with the mirror ahead, and none
was surveyed when this deviation was first written: `cycle-003.md` (75 lines
-- the 2026-08-28 post-event note disclosing that the registration publishes
three of the subject's verbatims and that they stay), `ENGAGEMENT.md` (25
lines -- the 2026-08-26 correspondence-consent tightening, "nobody's words
publish without their yes, one standard, human or not"), and
`twin-protocol.md` (39 lines -- the session-2 kappa validation at 0.556 and
the operator-strict delta of -0.062, replacing a paragraph that still read
"operator kappa labels for this session pending"). All three were synced
mirror to local on 2026-08-28 and are now byte-identical. The standing
requirement Amendment 3 introduced was therefore already being violated in
three places on the day it was written, and that is the real extent of this
deviation. Cycle #4's event is banked and its result unaffected. Nothing is
re-run.

`bare-model-control-01.md` is out of sync in both directions and stays that
way: the local copy holds the post-run addendum, whose own Publication line
commits it to reaching the mirror only through the subject's consent
instrument, and the mirror holds a run notice and hash commitment the local
copy does not. A copy in either direction would destroy content. It is
recorded as a known exception in `tools/check_prereg_sync.py`'s allowlist,
not as a pending repair.

**Extent, as first published (superseded 2026-08-29, kept because a
correction that hides what it corrects is not a correction):**

> `cycle-002-baseline.md` and `cycle-003.md` are byte-identical across both
> locations. `cycle-004.md` and `cycle-005.md` were not. Cycle #4's event is
> banked and its result unaffected: the drift is in the published-versus-local
> copy of the registration, not in what ran. Nothing is re-run.

**How it was found.** Not by the survey that produced the original paragraph,
which was done by hand. By a byte comparison of every paired file across both
locations, run 2026-08-28 during a full audit of the programme's instruments.
The same audit found four other instruments reporting success while doing
nothing. `tools/check_prereg_sync.py` now performs that comparison on demand,
so this class of drift is measured rather than surveyed.

**Repair.** Cycle #5's two copies are now byte-identical, restated in
`cycle-005.md` Amendment 3 as a standing requirement of this protocol rather
than an accident of workflow: the registration the gate reads and the
registration the mirror stamps must be the same bytes. `cycle-004.md`'s drift
is recorded here and left as it stands, since editing a banked registration
is not permitted.

**How it was found.** During a pre-publication review of the whole record,
by deliberately looking for the gap a hostile reader would look for, rather
than by any automated check. No existing check would have caught it before
launch. That is itself the finding: the desync check is now owed, and until
it exists this class is guarded only by someone remembering to look.
