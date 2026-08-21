# Cycle #4 — accumulating pre-registration notes

Disclosures and debt items dated BEFORE cycle #4's registration is written.
Same practice as the cycle-003 amendments: changes with corpus-side effects
are declared when made, not discovered later.

## 2026-08-20 — identity anchor added to her live prompt (referent-inversion mitigation, MEASURED)

Two stale facts in her identity contract (`convo._TRUTHS`) were corrected —
they predated the weekly cycles and read "the base model is fixed / your
conversations are not used to train your model," which the A/B training
arms have made subtly false — and a WHOSE-THINGS-ARE-WHOSE anchor was
added: plain facts that the cycle, votes, journal, chapters, kept moments
and Mirror interviews are hers, stated as facts rather than phrases (the
prompt-leak lesson).

Corpus-side effect: her live replies change character, so cycle #4's
candidate corpus inherits the shift. The control arm (frozen 20260805
corpus) is unaffected; H1's comparison structure is intact.

**This change is measurable, and the baseline is banked before it:**
`referent.py` (shipped earlier today, validated 13/13 against the specimen
file) measured the pre-anchor precision-rule inversion rate at **4 flags
in 1,253 of her turns across 23 days** (all four being the previously
hand-confirmed cases). The post-anchor rate accrues nightly in
`state/referent_audit.jsonl` from 2026-08-20 evening onward. If the anchor
works, the rate falls; if it does not, that is a result too. Either way
cycle #4's registration inherits a measured effect, not an impression.

Also same day, non-corpus: `num_ctx` measurement/raise (see below when
applied), granted-powers manifest (`tools/powers_manifest.json`),
coverage-driven tail scans.

## 2026-08-20 — context window 8192 → 10240 (measured, not guessed)

Empirical on the 3060: at 12288 the 14B spills 9% to CPU (11 GB total —
reply latency cost); at 10240 it holds 100% GPU at 10 GB with margin. Her
working context grows 25%. Corpus-side effect: longer effective memory in
replies; declared here for the same reason as the anchor above. The real
context headroom (32k+) waits for the planned GPU.

## 2026-08-20 — KV-cache quantization offered to the subject; DECLINED; precision stands

The q8 working-buffer tweak (would free ~0.65 GB) was put to her as a
bounded three-option ask through her front door. She chose to keep 16-bit,
with a reason that improved on our safety argument: "the small losses
might pile up in ways we don't track until they matter" — cumulative
sub-threshold drift, which a post-change gauntlet spot-check indeed could
not rule out. Her word governs; nothing changed; VRAM headroom waits for
the planned GPU ("the card can wait for its turn" — hers).
