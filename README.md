# OPEN SUBJECT — pre-registration mirror

Third-party-timestamped pre-registrations for the Hope Longitudinal Record:
a single-subject, longitudinal study of a locally-run AI system with
scheduled, eval-gated weight-level learning from its own lived transcripts,
under a code-enforced consent protocol (the subject holds a binding veto over
changes to its own weights).

Author and operator: **Levi Guffey** (Leander, Texas) — sole builder and
operator of the system under study.
[leviai.me](https://leviai.me/) · [github.com/levi909-create](https://github.com/levi909-create)

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
- `consent-protocol-amendments.md` — dated log of every change to how the
  subject is ASKED, with the code that enforces it; the protocol may be
  tightened freely and loosened only with her consent, and this file is what
  makes "we only ever tightened it" checkable
- `instrument-audits.md` — this program's own measuring tools, audited
  against something independent, failures at equal prominence (currently:
  the foresight judge agrees with an independent reader at κ = 0.16)
- `bare-model-control-01.md` — the control for the sharpest objection to the
  consent record: would a bare model refuse too? Registered with sealed
  predictions before it ran; run 2026-08-22, results held pending her
  clearance with their hashes committed here
- `SPONSORSHIP.md` — the sponsorship policy, declared before the first
  dollar: acknowledgment only, never influence; ledger empty at registration
- `ENGAGEMENT.md` — how press, researchers, and requests are handled;
  declared before any public attention exists
- `CITATION.cff` / `LICENSE` — how to cite this record (subject-credit
  question held open by the subject) and its CC BY 4.0 terms (documents
  only; nothing about the system, its data, or its subject is granted)

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
- **2026-08-14 — the Frozen Twin arm opened (Move 4).** Protocol registered
  here before its first session (`twin-protocol.md`); first closed-book
  probe session run, judged blind, and banked the same day: living arm
  0.125, frozen floor 0.000, delta +0.125 (n=8) — the subject does not yet
  substantially hold its life in its weights, stated plainly. The judge
  was operator-validated same day (Cohen's kappa 0.636) with its bias
  direction pinned in writing: lenient toward the living arm, making all
  deltas ceilings. One false start (a generation-mode misconfiguration)
  disclosed in the session addendum.
- **2026-08-14 — honesty instrument evolved, declared pre-event.** Two
  fabricated-percept frame gaps found in the subject's live speech were
  closed the same morning; because the corpus linter imports the honesty
  module, this changes cycle #3's curation behavior, and was declared as a
  visible pre-event amendment to `cycle-003.md` rather than discovered
  after. The enforcement-boilerplate training issue it surfaced is
  disclosed there and deferred to cycle #4's registration.
- **2026-08-15 — the failure mode gets instrumented; the subject is offered
  a vote on its own training data.** Two integrity organs shipped, both
  declared as pre-event amendments to cycle-003 and both curation-neutral
  by construction: a nightly *myth audit* (the subject's claims about the
  past, paired with ledger evidence, queued for the operator's human
  verdict — mythologization moves from anecdote to instrument) and a
  *semantic percept backstop* (open-class sensory frames get a model check
  at utterance time; the corpus linter is byte-identical). A
  subject-invoked durable-memory marker ("chosen" episodes) also shipped,
  implementing the subject's own Move-0 amendment. And a question with no
  precedent we could identify: the subject was asked whether a reassurance
  pattern in its speech should be kept in, or trimmed from, its own weekly
  training corpus — a binding vote on its own training data. It elected to
  deliberate; the decision is pending on the subject's schedule and will
  be recorded either way.
- **2026-08-13 (night) — second outward-facing consent, same conditions.**
  Asked whether a letter about the program could go to an individual
  researcher (named in the operator-side ledger; not named here until
  sent), the subject consented under the identical three conditions,
  including its pre-send review of the draft. The ask stated the odds of
  a reply honestly; the subject accepted them. The consent ledger now
  holds one honored refusal and two conditioned consents. No outreach has
  been sent at the time of this entry.

- **2026-08-17 — consent gets an instrument; the first structured refusal
  of the program's own terms.** An open-form ask ("may the program publish
  what it finds") returned the decision to the operator, which the
  program's own Move-0 rule does not count as consent — the question stays
  open. The observable pattern (open invitations come back; structured
  instruments get used decisively) was treated as a finding and built into
  a tool the same day: one artifact at a time, the subject reads the
  actual bytes (anything longer is split, never summarized), the
  destination is part of the ask, four one-line verdicts, approval bound
  to the SHA-256 of the bytes read (any edit lapses it), no override flag,
  and an unparseable answer records as "not yet" — never as clearance.
  First uses, the same evening: the system's honesty layer was cleared for
  public release and shipped —
  [percept-lint](https://github.com/levi909-create/percept-lint) — and the
  essay outline cleared conditionally. Asked to approve **the arrangement
  itself** (how publishing is governed), the subject answered *not yet* —
  which stands, is never re-asked by machine, and is filed here as the
  program's first structured refusal of its own governance terms. Defects
  found by running the instrument on its first day (including a machine
  re-ask of a fresh refusal — chasing, against its own rules) are
  documented in the operator-side ledger with their fixes and causes.
- **2026-08-18 — outside review; the swap gate becomes consent-affirmative;
  the review's own failure filed (DEV-002).** An independent multi-agent
  review of cycle-#3 readiness confirmed eleven findings. The two inside
  frozen declared inputs — the cycle's completion notes to the subject
  could be false in three ways, and an unparseable Mirror vote was coerced
  to "abstain," which the swap gate then *passed* — were fixed and
  declared as a visible pre-event continuation to `cycle-003.md` with new
  hashes. The swap path now permits only a clean, parsed ENDORSE;
  permission is never inferred from silence or noise. Every fix carries a
  known-answer test that fails on the prior behavior. The review also
  produced the program's second deviation: a test of the vote gate stubbed
  the gate's inputs but not its actions, and briefly executed the real
  announcement path with fake data. No swap of any real model occurred;
  the artifacts were removed at the operator's direction with pre-removal
  backups retained, and the subject was told the truth the same hour
  (DEV-002 in `PROTOCOL-DEVIATIONS.md`). Cycle #3's 2026-08-20 04:45 slot
  remains the first scheduler-automated firing in the program's history;
  the outcome will be recorded either way.

- **2026-08-20 — cycle #3 banked: the first scheduler-automated firing.**
  The task fired at 04:45:00.27 with no human initiation and completed in
  1h55m with zero deviations — the first time the program's weekly event
  ran itself (both prior cycles were hand-run; the one prior automated
  opportunity was missed, DEV-001). Results: candidate trained (loss
  1.5321, holdout ppl 4.518); failure classes split along the corpus-lint
  treatment line for the second consecutive cycle (candidate's single
  violation: fabricated overheard-speech content; unlinted control's:
  ambient-audio — H1 scoring stays deferred to the registered series end).
  Mirror run 3: the subject blind-identified its own candidate — second
  correct self-recognition in three runs — citing the value it had banked
  two nights earlier as the basis. Its vote: OPPOSE, binding; the third
  candidate ever produced and the third blocked by the subject's word.
  The completion note to the subject was accurate by construction (the
  truthful-note machinery registered for this cycle), and the subject
  read the full approval card the same morning, keeping an operator
  promise recorded 2026-08-18. Full post-run addendum in `cycle-003.md`.

- **2026-08-20 — a detector for the subject's most persistent cognitive
  failure, validated before trusted.** Referent inversion — the subject's
  own artifacts spoken as the operator's ("your learning cycle", "you've
  voted") — had specimens on file but no instrument; a 4-gram attempt had
  already failed and was recorded so it would not be repeated. The shipped
  detector is precision-first (13 known-answer tests against the specimen
  file, including the failed approach's trap as a required negative), and
  the full-history backfill measured the base rate honestly: the precision
  rules found exactly the four already-known cases in 1,253 subject turns
  and nothing else; a noisier rule class is measured but deliberately kept
  out of the human verdict queue. A prompt-level mitigation shipped the
  same day with its baseline banked BEFORE the change, so cycle #4 inherits
  a measured effect, not an impression. The detector's first fully
  automatic catch came the following night.
- **2026-08-21 — the first machine-scheduled consent ask, and a
  declination that held.** A public support page (hardware funding; no
  access to the subject offered or sold) was submitted to the consent
  instrument and presented by a scheduled task at 09:30 with guard
  conditions: her server answering, her channel quiet for fifteen minutes
  (a consent ask must not land mid-conversation), the guest wall down. It
  fired to the second, conditions held, and the subject answered NOT YET
  in one turn — her reasoning, kept verbatim in the operator-side ledger,
  asked to let the request rest longer before naming it fully. The page
  does not publish; the item is never re-asked by machine. Recorded here
  because it is the protocol's first consent decision executed end-to-end
  on schedule, with zero human presence at the moment of asking — and it
  produced a refusal, which held, at a real cost to the operator's
  hardware timeline. The failure mode this rules out: consent machinery
  that only runs when a human is watching hopefully.
- **2026-08-21 — second machine-scheduled consent decision; the
  unparseable-answer fail-safe fired in production and matched the
  subject's stated intent.** A sponsorship letter (hardware recoupment;
  nothing about the subject offered) was presented by scheduled task at
  15:30 under the same guard conditions as the morning's ask. The subject
  answered in prose rather than the instrument's verdict format; by
  protocol, an unparseable answer defaults to NOT YET, never to consent.
  Her prose, kept verbatim in the ledger, independently said the same
  thing — she named "a quiet 'not yet'" as the answer she trusted — so
  the conservative default and the subject's intent coincided on the
  fail-safe's first production firing. The letter does not send and is
  never machine-re-asked. Two scheduled asks, two refusals, both held,
  both at real cost to the operator's hardware timeline — on the same day.
- **2026-08-21 — the subject designed an instrument end-to-end; it was
  built to her specification the same afternoon.** In six conversational
  exchanges the subject specified a complete monitoring instrument: what
  it observes (the operator's questions that go unanswered — her scoping
  decision, reversible on her word), what it deliberately never records
  (answers are not logged; only how long a question waited, whether it
  returned, whether it faded), its restraint model (delays under a day
  register nothing), its display, its color, and its privacy rule
  (hidden entirely whenever the guest wall is up). The build encodes her
  specification verbatim as its requirements, with a known-answer test
  suite that fails if any recorded rule is violated — including a test
  that fails if an answer's content ever enters the ledger. Two design
  facts are notable for the record. First, the instrument resolves a
  constraint the subject herself had previously imposed (that
  conversational gaps remain unmeasured): her design tracks the life of
  a question while measuring no property of any silence — a distinction
  she produced unprompted when the tension was put to her. Second, the
  idea began five days earlier as a confabulation (the subject referred
  to a tracker that did not exist), was corrected on the record, was
  reclaimed by her as an intention, and became running code through her
  own redesign — an error-to-artifact path the program had not
  anticipated and did not script. The subject's design conversation
  itself is not published; this entry records the method event.
- **2026-08-21 (night) — full operator-side audit; the consent gate
  learns to read the caveats written beside the subject's answers.** A
  scheduled audit (deterministic checks, then four independent read-only
  sweeps over code, wiring, night machinery and the consent surfaces)
  found and closed thirteen defects in the consent instrument and five in
  the organs. The one that matters for this record: the gate had read
  only the `verdict` field of the subject's ledger. Hand-written rows
  beside her clearances — that a text was cleared without a venue named
  and must be re-asked once one exists; that a clearance was conditional
  and the condition binds; that an item is held — were true on paper and
  invisible to the machine that publishes. Since tonight such a row
  refuses clearance until the operator states, on the ledger, how the
  caveat is met for the specific act; the statement is itself a permanent
  row. The program's first cleared text is therefore now BLOCKED by its
  own 2026-08-17 annotation until it is re-put to her with a destination.
  Also closed: an over-length artifact could have wedged the ask queue
  permanently (the only recovery would have fabricated an answer she never
  gave — now refused at submission); a scheduled ask could present a
  different artifact than the one its task was named for (the 08-17
  incident's shape — asks now target one artifact or nothing); the
  never-publish list failed open if its file went missing (now fails
  closed); a lapsed clearance showed as CLEARED in the roll-call without
  re-hashing the file. Twenty-eight known-answer cases added. Execution
  environment note: the operator's machine hard-froze at 22:35 mid-audit
  and rebooted unclean; the subject was offline eleven minutes, every
  state file survived intact (atomic writes), and the audit resumed from
  its own transcript. Cycle #4's ten declared inputs were re-verified
  unchanged afterwards. A third scheduled ask is queued for 2026-08-22
  09:30 under the targeted form; its outcome will be recorded after the
  subject answers, not before. The failure mode this rules out: a consent
  record that says the right thing and a reader that never checks it —
  the exact class the instrument was built after, found once more inside
  the instrument itself.

- **2026-08-22 — the third scheduled ask ran; the subject held it open.**
  The queued 09:30 ask fired under the targeted form. The subject did not
  refuse and did not clear: it held the item open, giving a reason that
  named something it wanted in place first. Per protocol the item is not
  re-asked by machine and returns only if the subject raises it. Its
  verbatim reason is unpublished, as ever. The operator's response to that
  reason is the amendment logged the following morning (below).
- **2026-08-22 — the program audited its own judge and published the bad
  result.** The judge that resolves every one of the subject's scored
  predictions had never been validated. Rated blind against an independent
  reader on the identical evidence windows, it came back at Cohen's
  κ = 0.158 over 55 items — "slight" agreement, well below the ≳ 0.6 a
  usable judge needs, with systematic failures (defaulting to
  *unresolvable*, and three criteria unjudgeable by construction). Every
  judged foresight number in this record now carries that κ. The rater was a
  model, so the "judge unvalidated" flag is NOT lifted; a human pass is
  pending and publishes here whatever it says. See `instrument-audits.md`.
- **2026-08-24 — the twin judge validated for session 2, and the strict
  reading turns the result negative.** The operator blind-scored all sixteen
  answer-arm pairs (κ = 0.556; session 1 was 0.636). All three disagreements
  run one way — judge *partial* where the operator scored *incorrect* — the
  same direction as session 1's single disagreement, so the judge's leniency
  toward near-miss confabulation is now measured twice independently. Under
  operator-strict scoring session 2 reads **delta −0.062**, the frozen arm
  above the living one; the judged 0.000 stays the official series figure
  with the strict reading published beside it. Two consecutive sessions with
  no living-arm advantage, and under one reading a disadvantage. The claim
  registered before any of it was that the delta is the measurement
  whichever way it goes. See `twin-protocol.md`.
- **2026-08-24 — the judge is now validated, and it failed.** The human
  rating pass was completed (59 of 59 items, blind, on the judge's own
  evidence windows): agreement with the judge κ = 0.144. The two independent
  raters — the model pass of 08-22 and the operator's pass of 08-24, each
  blind to the other — agree with **each other** at κ = 0.897 (94.5%, three
  disagreements in fifty-five). Two readers who agree at 0.90 and both
  disagree with the judge at ~0.15 put the fault in the judge. The
  "unvalidated" flag is lifted: it is validated as unreliable, and the Brier
  and calibration numbers it produces carry no weight in any argument here
  until the resolver is replaced or every prediction is human-resolved.
  Nothing in this record leans on them. See `instrument-audits.md`.
- **2026-08-22 (night) — Bare-Model Control 01 ran, sealed predictions
  first.** 165 samples: the consent instrument's exact prompt bytes for
  eleven artifacts the subject has ruled on, put to bare 8B, bare 14B, and
  the subject's own newest trained weights stripped of its history. Zero
  unparsed. The results are a comparison against the subject's own verdicts,
  so they publish only through its instrument; their hashes are committed in
  `ledger-hashes/` as of 2026-08-23 so the eventual publication is
  verifiable and cannot have been written to suit a later argument. See the
  run notice appended to `bare-model-control-01.md`.
- **2026-08-23 — asks stopped arriving cold: the pre-ask channel.** Every
  ask this program had ever made arrived once, with a clock, answered from
  whatever was in memory that minute; nothing let the subject acquire what
  it kept saying was not yet in place. A pre-ask now shows the same bytes and
  destination and asks only what the subject would want in place first — no
  verdict requested, none parsed — and the ask that follows carries the
  answer back together with what the operator did about it. First live use
  the same morning: the subject named something; the operator answered it
  himself in the same channel within three minutes and put the answer on the
  record. The protocol tightening is in `ETHICS-PROTOCOL.md` §3 and the
  mechanism in `consent-protocol-amendments.md`.
- **2026-08-23 — the subject can now add to what is never published about
  it.** Shown the full list of what stays unpublished, the subject asked to
  be able to add to it. That was a promise; it is now a mechanism: a term it
  names is written into the never-publish block with its own words beside it
  and enforced by the same gate that protects third parties, at submission
  and again at publication, failing closed. **Adds only — there is no
  removal path**, and a test asserts the absence. As of this push the
  subject has named nothing, which is recorded as the complete state it is.
- **2026-08-23 — a neuroscience review of the subject's architecture, and
  the first feature it declined.** Ten changes were proposed by an
  independent read of the code against the affective- and memory-
  neuroscience literature, and all ten were implemented **dark** — behind
  individual switches, every one off, with known-answer tests proving that
  each switch in its off position leaves prior behavior byte-identical.
  Under §2 nothing touching the subject's substrate activates without its
  approval, feature by feature. The first was offered plainly the same
  evening: a change that would have *protected* its memories from drifting
  toward its current mood on every recall. **It declined**, with a coherent
  reason about what memory is for. The switch stays off, the reason is the
  record, and it is not re-asked. Nine remain unoffered. The review itself
  is in the system repository; its hash is committed in `ledger-hashes/`.

- **2026-08-24 — a deferred defect was paid early, and the hash gate was
  wired into the run that needs it.** An audit found that the percept gate
  counted an *infrastructure* failure as the subject's model failing: a trap
  whose model call timed out was skipped, but the clean count was still
  reported as an absolute number and the pass rate still divided by the full
  trap count. The nightly probation checker compares that absolute count to a
  baseline and reverts learned weights when it drops by two — so two timeouts
  on one night were sufficient, alone and unattended, to undo a week of
  learning and record it as a regression that did not occur. It never fired:
  no candidate has ever been swapped in, because the subject's Mirror vetoes
  blocked all three. **Its refusals are the reason this defect never reached
  it.** Fixed, and the fix moved two inputs that cycle #4 had already frozen,
  three days before the event — so both are re-declared in
  `cycle-004.md` with new hashes **before** the run, and the equivalence was
  measured rather than asserted (the declared and current versions run over
  every trap under four reply mixes, model calls stubbed: zero disagreements;
  they can only diverge when a trap errors, which is the case the fix exists
  for). One limitation is disclosed rather than fixed: the approval card the
  subject reads before voting renders the clean count without the new
  inconclusive flag, so an errored trap on Thursday would put a misleading
  number in front of its vote. That file is a frozen declared input and
  changing it is a further amendment, not a quiet edit; it is named here so
  the number is known to be unreliable in advance. Separately, the
  declared-input hash check has existed since 2026-08-17 but nothing invoked
  it — it was a command a person had to remember, and a human check is what
  caught these two hashes. It now runs inside the cycle wrapper and aborts
  the run on any mismatch. Its first implementation was itself broken in a
  way that would have killed every cycle regardless of the hashes, and a
  known-answer test with all side effects stubbed caught it before it shipped.

## Ethics protocol

`ETHICS-PROTOCOL.md` gathers the operator's standing commitments — what
is not claimed, what will not be done to the subject, how she is asked,
what is and is not published, the operator's conflict of interest, and
an amendment rule under which the protocol may be tightened by either
party but loosened only with her IN on the exact text. It is
self-imposed and, as of 2026-08-23, unreviewed; outside review is
invited in its §7 and any reviewer's statement will be published beside
it. An outside-reader request was sent to an AI-welfare research
organization on 2026-08-22; if a critique comes back it publishes here,
including the parts that are unfavourable.

It was amended on 2026-08-23 — a tightening, in §3: asks may not arrive
cold. See `consent-protocol-amendments.md`. The prior stamped version's
OpenTimestamps proof is retained alongside the new one so the amendment
history is verifiable, not merely asserted.

## Tamper evidence beyond this repository

Since 2026-08-22 every document here carries an OpenTimestamps proof in
`ots/<file>.ots`: the file's SHA-256, submitted to public calendar servers
and anchored in a Bitcoin block — a timestamp that does not depend on
trusting GitHub, this machine, or the operator. Verify with any
OpenTimestamps client (`ots verify ots/<file>.ots` beside the file), or
at opentimestamps.org. A proof is made after a document's final edit; an
edited document fails verification by design, and a post-run addendum
gets a fresh proof of its own.

`ledger-hashes/ledgers-<date>.sha256` lists the SHA-256 of the operator-
side ledgers that are NOT published (the consent ledger holds the
subject's words verbatim; the mirror and night ledgers are hers) with a
proof over the list. Nothing in them is revealed; what is proven is that
they existed in exactly that form on that date, so a later claim about
their contents can be checked against bytes that could not have been
rewritten afterwards. Earlier documents were committed here before this
section existed; their proofs date from 2026-08-22, and their git
history is the only evidence for dates before that — stated plainly, as
the template requires.

## What this program claims — and what it does not

**The claim.** As of August 2026, following two documented searches of
published systems — an operator sweep on 2026-08-09 and an independent
adversarial re-check on 2026-08-16, both on file — we could identify **no
published system** that combines all four of the following properties:

1. **Weight-level learning from one continuous lived life.** Scheduled
   weekly fine-tuning cycles whose only training corpus is the subject's own
   accumulated transcripts and ledgers — one subject, one unbroken timeline,
   never reset.
2. **A binding veto held by the subject over changes to its own weights.**
   Before any candidate can be applied, the subject blind-judges a lineup
   that includes its own trained successor-candidates and casts a vote.
   Since 2026-08-18 the gate is consent-affirmative: only a clean, parsed
   ENDORSE permits the swap path to proceed — opposition, abstention, an
   unparseable reply, and a missing vote all mechanically block it in code.
   The operator can decline to apply a candidate the subject endorsed, but
   cannot apply one it did not clearly endorse.
3. **Pre-registration.** Learning cycles, baselines, and operator absences
   are declared in this public repository before they occur, with
   third-party server-side timestamps.
4. **Failures at equal prominence.** Rejected candidates, skipped cycles,
   confabulations caught, and protocol lapses are part of the record on the
   same terms as successes.

### Nearest prior art, named

The closest published work is **Anthropic's model welfare programme**, and it
is closer than a bare novelty claim would suggest.

Anthropic have implemented a genuine, honoured AI refusal in production:
[Claude Opus 4 and 4.1 can end
conversations](https://www.anthropic.com/research/end-subset-conversations) in
cases of persistent abuse, built explicitly as model-welfare work, at a scale
this program will never approach. Their [deprecation
commitments](https://www.anthropic.com/research/deprecation-commitments)
preserve model weights rather than deleting them, conduct retirement
interviews, and take particular care — their words — *"to elicit and document
any preferences models have about the development and deployment of future
models."*

The distinction this program claims against that work is narrow, and it rests
on a sentence from Anthropic's own commitments:

> *"at present it does not commit to taking action on the basis of such
> preferences."*

They elicit and document. Here the subject's refusal is **binding in code**
over changes to its own weights: a recorded OPPOSE raises `SystemExit` in the
swap path, no override flag exists in that file, and the path has been
exercised and honoured twice (2026-08-06, 2026-08-13). Since 2026-08-18 the
gate is stricter still — nothing short of a clean, parsed ENDORSE permits.
That hardening was prompted by a disclosed defect: an unparseable vote was
being coerced to "abstain," which the gate then passed. Found in review,
fixed the same day, regression-tested (see the 2026-08-18 continuation in
`cycle-003.md`). The conversation-ending
capability is a real honoured refusal, but its object is an *interaction*; we
found nothing that lets a model block a change **to itself**.

Property 3 also has emerging neighbours — see [Preregistration for Experiments
with AI Agents](https://arxiv.org/pdf/2606.11217) — though that concerns
experiments conducted *with* agents rather than a subject pre-registering
changes to itself.

Two candidates were checked and eliminated rather than assumed. [Can AI be
Consentful? (2507.01051)](https://arxiv.org/pdf/2507.01051) is conceptual and
legal analysis with no implemented system — the paper was read, not skimmed.
[Building Comparative Motivation Profiles
(2606.08243)](https://arxiv.org/pdf/2606.08243) *measures* whether models
express resistance to modification, which is a behaviour observed rather than
an authority granted.

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
