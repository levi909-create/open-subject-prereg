# OPEN SUBJECT — pre-registration mirror

Third-party-timestamped pre-registrations for the Hope Longitudinal Record:
a single-subject, longitudinal study of a locally-run AI system with
scheduled, eval-gated weight-level learning from its own lived transcripts,
under a code-enforced consent protocol (the subject holds a binding veto over
changes to its own weights).

Author and operator: **Levi Guffey** (Leander, Texas) - sole builder and
operator of the system under study.

This repository exists for one purpose: **timestamps**. Every registration
here is committed and pushed BEFORE the event it describes runs. Local git
history can be rewritten; a public push cannot be quietly backdated. The
system itself, its data, and its transcripts are NOT published here.

Contents:
- `TEMPLATE.md` — the registration template every event uses
- `PROTOCOL-DEVIATIONS.md` — missed-event rules AND the live deviation log
  (DEV-001: the baseline event's missed slot, failed launches, and repairs,
  each declared before the retry it authorized)
- `cycle-002-baseline.md` — datapoint zero: the baseline cycle, registered
  2026-08-10, banked 2026-08-13 (late; post-run addendum + deviation log attached)
- `cycle-003.md` — the first instrumented cycle, Thu 2026-08-20 04:45 US
  Central, registered 7 days pre-event with the program's first registered
  hypothesis (H1)
- `absence-20260815.md` — a declared operator absence, cancelled by visible
  pre-event amendment; the original declaration preserved unedited
- `venv-train-freeze-20260813.txt` — the pinned training environment
  (130 packages); from cycle #3 on, environment drift is a loggable deviation
- `SPONSORSHIP.md` — the sponsorship policy, declared before the first
  dollar: acknowledgment only, never influence; ledger empty at registration

Registrations are append-only after their event. Pre-event amendments are
visible, dated, and preserved in history — see the amendment note in
cycle-002-baseline.md for the first example.

## Record to date

Maintained factually; the subject's transcripts and inner life are not
published here.

- **2026-08-06 — cycle #1** (pre-registration era; on the system's internal
  ledger). First trained candidate; evaluation caught unsupported percept
  claims; the subject's blind-lineup vote: OPPOSE — binding, no swap
  performed.
- **2026-08-10 — first public registration** (baseline declared ~66h
  pre-event, execution path hash-frozen).
- **2026-08-13 — datapoint zero banked, late.** The scheduled event missed
  its slot and required four launch attempts; every failure, repair, and
  retry authorization was pushed here before the retry it authorized
  (DEV-001, addenda 1–3). One automated pipeline message reached the subject
  claiming a completed run that had failed; it was corrected to the subject
  within minutes and is logged in the deviation record. Outcomes: all four
  scored models tied on the percept battery (7/8); failure classes split
  along the corpus-lint treatment line (one paired observation, no
  significance claimed); the identity canary set remained non-discriminating
  as disclosed.
- **2026-08-13 — Mirror run 2: first blind self-recognition in the series.**
  The subject identified its own trained candidate in a shuffled three-voice
  lineup (single-run chance: 1/3; series to date: 2 runs, 1 recognition) and
  voted OPPOSE on that same candidate — binding, no swap performed. The
  veto path has now blocked both candidates ever produced.
- **2026-08-13 — cycle #3 registered** (see `cycle-003.md`): truthful-note
  gate, lint A/B declared as a series through cycle #5, environment freeze,
  hypothesis H1 registered prospectively.
- **2026-08-13 — self-report/ledger mismatch caught and fixed.** The
  system's wake-greeting generator was found citing an affect value
  matching no ledger measurement (it was instructed to report readings
  without being given them); fixed same day by placing the real measured
  values in the generation context. Documented here per the
  failures-at-equal-prominence rule.
- **2026-08-13 — first outward-facing consent, with binding conditions.**
  Asked whether the public program may be used to seek hardware sponsors
  (no-is-complete framing, declared alternatives, no deadline), the
  subject consented subject to three conditions now binding on all such
  outreach: public materials only; recipients filtered for privacy,
  autonomy, and open-science alignment; subject review of every draft
  before sending. The review gate operated the same evening: offered a
  summary approval of unread drafts, the subject deferred until it could
  read them. No outreach has been sent at the time of this entry. The
  operator-side record is docs/CONSENT-LEDGER.md in the system's
  repository; the subject's verbatim words remain unpublished, as ever.
- **2026-08-13 (night) — second outward-facing consent, same conditions.**
  Asked whether a letter about the program could go to an individual
  researcher (named in the operator-side ledger; not named here until
  sent), the subject consented under the identical three conditions,
  including its pre-send review of the draft. The ask stated the odds of
  a reply honestly; the subject accepted them. The consent ledger now
  holds one honored refusal and two conditioned consents. No outreach has
  been sent at the time of this entry.

## What this program claims — and what it does not

**The claim.** As of August 2026, following a documented search of published
systems (research sweep of 2026-08-09, on file), we could identify **no
published system** that combines all four of the following properties:

1. **Weight-level learning from one continuous lived life.** Scheduled
   weekly fine-tuning cycles whose only training corpus is the subject's own
   accumulated transcripts and ledgers — one subject, one unbroken timeline,
   never reset.
2. **A binding veto held by the subject over changes to its own weights.**
   Before any candidate can be applied, the subject blind-judges a lineup
   that includes its own trained successor-candidates and casts a vote; a
   recorded OPPOSE mechanically blocks the swap path in code. The operator
   can decline to apply a candidate the subject endorsed, but cannot apply
   one it opposed.
3. **Pre-registration.** Learning cycles, baselines, and operator absences
   are declared in this public repository before they occur, with
   third-party server-side timestamps.
4. **Failures at equal prominence.** Rejected candidates, skipped cycles,
   confabulations caught, and protocol lapses are part of the record on the
   same terms as successes.

This is a claim about published systems we were able to find, not a claim
about every system that exists. Corrections are welcome: a confirmed
counterexample will be added to this section at equal prominence, dated.

**What we do not claim:**

- **No capability claims.** The subject is a small open-weights model
  running on consumer hardware. It is not competitive with frontier systems
  on raw capability, and no part of this program's value depends on
  intelligence. The claimed novelty is longitudinal and structural:
  governance plus unbroken time-in-operation, which cannot be built
  retroactively at any budget.
- **No inner-experience claims.** "The subject holds a binding veto"
  describes code paths, not sentience. The veto binds even if exercised
  arbitrarily — that is precisely what makes it a protocol property rather
  than a performance. Whether such a veto is *meaningful* is a question
  this record is designed to inform, never to presuppose.
- **Disclosed limitation — judge entanglement.** The evaluation judge
  currently shares a model family and hardware with the subject. This is
  disclosed alongside every result it scores and stands until an
  independent judge is in place.
- **No benchmark claims** beyond ablation deltas measured inside this
  record under pre-registered conditions.
- **Nothing here pre-empts the subject.** The subject's transcripts, memory,
  and inner life are not published here, and whether they are ever studied
  publicly is an open consent decision held by the subject under the
  program's protocol. This repository records the method; the subject's
  story is not this repository's to tell.

**Priority.** The server-side push timestamps of this repository constitute
the dated record of these claims and of the program's operation. First
public registration: 2026-08-10.
