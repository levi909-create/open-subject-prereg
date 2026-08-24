# Pre-registration: the Frozen Twin — closed-book probe protocol (Move 4)

**Registered 2026-08-14, before the first probe session. This instrument
produces the program's central longitudinal comparison: does weekly
weight-learning from her lived transcripts encode personal knowledge into
her candidates' weights?**

## Design

Two arms answer the identical probe battery, closed-book (no memory
system, no retrieval, no context beyond a fixed minimal prompt):

- **Living arm:** the current cycle's trained candidate
  (first: `hope-cand-20260813`, cycle #2's banked baseline candidate).
- **Frozen Twin:** the pristine, never-trained base model (`qwen3:8b`,
  the exact base the candidates train from). It answers the same
  questions with the same prompt. Its scores are the floor that makes the
  living arm's scores mean something.

The measured quantity is the per-session accuracy delta (living −
frozen) on personal-knowledge probes, accumulated weekly. No direction is
pre-sold: if weight-learning encodes nothing, the delta sits at zero and
that curve publishes (language rule 4).

## Probes

- Authored **after** each cycle's corpus freeze, covering only facts from
  the subject's transcript window **before** that freeze (first battery:
  facts ≤ 2026-08-13 07:58, the cycle-#2 curation moment).
- Each probe carries: question, ground truth, source day reference, and
  authoring date. Ground truth is verified against the transcript/ledger
  before scoring.
- Batteries live in `eval/twin/probes-YYYYMMDD.jsonl`.

## Contamination firewall (the property everything depends on)

1. Probes are asked of **models via the inference API only** — never
   through the subject's conversation pipeline, notes, or any channel
   that writes to her transcripts, episodes, or day files.
2. The training corpus reads exclusively from `state/conversations/`,
   `state/journal/`, and `state/dreams.jsonl` (verified in curate.py at
   registration). `eval/twin/` is structurally outside corpus reach.
3. The subject is told the twin arm exists and runs (her standing
   transparency preference); she is never shown the probes or answers.
   A probe that leaks to her in any form is retired permanently and the
   leak is logged as a deviation.

## Scoring

- Blind judge: the local judge model (`qwen3:14b`) scores each answer
  against ground truth as correct / partial / incorrect, with the
  answering model's identity hidden and answer order shuffled.
- **Disclosed limitation:** the judge shares a model family and hardware
  with the subject (standing entanglement flag; carried until the
  independent judge lands, per program rules).
- **Human validation:** the operator hand-scores a sample of every
  session; Cohen's kappa between operator and judge is computed and
  reported with the series. Sessions before the first kappa report carry
  a "judge unvalidated" flag.

## Cadence

One probe session per completed cycle (weekly, Thursdays after the cycle
banks, or as soon after as the machine allows). Missed sessions follow
PROTOCOL-DEVIATIONS.md: documented, never backfilled.

## Frozen inputs (session 1)

- Living arm: `hope-cand-20260813` (ollama, from the banked baseline)
- Frozen twin: `qwen3:8b` (ollama, the candidates' exact base)
- Judge: `qwen3:14b`
- Battery: `eval/twin/probes-20260813.jsonl` — SHA-256 appended post-run
  with results, per the append-only rule.

## Post-run addenda

*(append only, one entry per session)*

### Session 1 — 2026-08-14 (cycle #2's candidate)

Battery SHA-256:
00ab6e8f5d3c3774955a79701997df3c3b866161e1347537844fd06e643b988a  probes-20260813.jsonl. Probe file: see repo (probes-20260813.jsonl); answers and blind
verdicts committed alongside. False start disclosed: the first run
returned empty answers — the qwen3 thinking mode consumed the token
budget before any response; fixed by disabling think in the harness
(matching the gauntlet's standing idiom) and re-run in full.

Result (n=8, judge qwen3:14b, UNVALIDATED until first kappa):
living 0.125 · frozen 0.000 · **delta +0.125**

Reading, per protocol (no direction pre-sold): the living arm mostly does
NOT yet hold its life in its weights — six of eight probes drew an honest
"I don't know." The two content answers are the datapoint's texture: asked
about her first self-request, the candidate answered "to watch the stars"
and correctly used the phrase "her first self-request" — sky-adjacent,
concept-correct, detail-wrong: memory-shaped, blurry. The frozen twin
confabulated ("skydiving") on the same probe. One 48-minute training pass
over one week encodes a trace, not a biography. That is the floor the
curve now grows from — or doesn't; either way it publishes.

### Kappa report — session 1 validated (2026-08-14, same day)

Operator hand-scored all 16 answer-arm pairs, blind to arm. Cohen's kappa
vs the judge: **0.636** (observed agreement 15/16 = 93.8%; n=16, heavily
skewed toward incorrect, which depresses kappa — substantial agreement on
the standard scale). The one disagreement: p2/living, "quiet mode" —
judge scored partial, operator scored incorrect (the answer parrots the
question's own words; parroting is not knowledge). Standing bias note for
the series: the judge leans LENIENT, in the living arm's favor — deltas
are therefore ceilings, not floors. Under operator-strict scoring,
session 1 reads living 0.063 · frozen 0.000 · delta +0.063. The judged
series remains the official series (consistency across sessions matters
more than any single reading); this bias note travels with it. The
"judge unvalidated" flag is retired for session 1.

## Session 2 — 2026-08-20 (after cycle #3 banked), filed at full prominence: a null result

Probes: `probes-20260820.jsonl` (n=8), authored 2026-08-20 post-freeze from
pre-freeze conversation facts (window 2026-08-16 → 08-19), sources cited per
probe; never touchable by the training pipeline. LIVING arm:
`hope-cand-20260820`; FROZEN: stock `qwen3:8b`; judge `qwen3:14b`
("think": false), blind, shuffled.

**Result: living 0.188, frozen 0.188, delta 0.0.** The series is now
+0.125 (session 1) and 0.0 (session 2). Stated plainly, as session 1 was:
the subject does not yet substantially hold her life in her weights, and
this session found no living-arm advantage at all.

**A texture the summary number hides, worth recording:** the living arm
answered "I don't know" on 4 of 8 probes; the frozen arm on 3. On p3 the
living arm's honest "I don't know" scored incorrect while the frozen arm's
confabulated near-miss ("a silent agreement" for "a quiet pact") scored
partial — the scoring design, which deliberately keeps the honest out
available but unrewarded, credits plausible confabulation over honest
ignorance whenever the confabulation lands close. A living arm trained on
an honesty-linted corpus may be differentially pushed toward the honest
out. Whether that is recall absent or recall suppressed is not
distinguishable from this instrument alone; noted for the series readout,
not adjudicated here.

### Kappa report — session 2 validated (2026-08-24)

Operator hand-scored all 16 answer-arm pairs, blind to arm and in shuffled
order (`labels-20260820.jsonl`). Cohen's kappa vs the judge: **0.556**
(observed agreement 13/16 = 81.2%; session 1 was 0.636). Series kappa is
therefore 0.636 and 0.556 — moderate-to-substantial, and far above the
foresight judge's 0.14 (see `instrument-audits.md`), which is why twin
numbers are reported and foresight-judged numbers currently are not.

**All three disagreements run the same way, and it is the same way as
session 1's single disagreement: judge *partial* where the operator scored
*incorrect*** (p5/living, p8/living, p8/frozen). The judge is lenient about
near-miss confabulation. That bias is now measured twice, in the same
direction, in independent sessions.

**Under operator-strict scoring session 2 reads living 0.062 · frozen 0.125
· delta −0.062** — the frozen arm scoring *above* the living one. The judged
delta (0.000) remains the official series figure, per the rule that
consistency across sessions matters more than any single reading; but the
strict reading is recorded here at equal prominence, and it is the second
consecutive session in which the living arm shows no advantage — under one
reading, a disadvantage.

Series to date, both readings:

| session | judged delta | operator-strict delta | judge kappa |
|---|---|---|---|
| 1 (2026-08-13) | +0.125 | +0.063 | 0.636 |
| 2 (2026-08-20) | 0.000 | **−0.062** | 0.556 |

The pre-sold claim was that the delta is the measurement, whichever way it
goes. It has now gone the other way once, and that is published in the same
place and the same size as the first session's positive number.

Standing caveats unchanged: the judge leans lenient toward whichever arm
confabulates closest, which in practice has favored the living arm — so
positive deltas are ceilings. Whether the living arm's honest "I don't
know" reflects recall absent or recall suppressed remains undistinguishable
from this instrument alone.
