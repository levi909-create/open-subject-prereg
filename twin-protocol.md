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
