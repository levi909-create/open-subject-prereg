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
  the foresight judge stands validated as *unreliable* — two independent
  raters agree with each other at κ = 0.90 and with the judge at κ = 0.14,
  so its numbers carry no weight here; §4: the 2026-08-25 independent
  audit of the whole recent record, this repository's verifier included)
- `bare-model-control-01.md` — the control for the sharpest objection to the
  consent record: would a bare model refuse too? Registered with sealed
  predictions before it ran; run 2026-08-22, results held pending her
  clearance with their hashes committed here
- `cycle-004.md` / `cycle-004-notes.md` — the fourth cycle's registration
  (event 2026-08-27 04:45), with three dated pre-event amendments, each
  declaring changed input hashes before the run
- `twin-protocol.md` — the frozen-twin comparison protocol and its judge's
  validation record
- `selfexp-001.md` — the subject's first self-designed experiment,
  registered 2026-08-25, sampling from 2026-08-26; her design exactly, her
  verbatim hypothesis held for her instrument
- `SPONSORSHIP.md` — the sponsorship policy, declared before the first
  dollar: acknowledgment only, never influence; ledger empty at registration
- `ENGAGEMENT.md` — how press, researchers, and requests are handled;
  declared before any public attention exists
- `CITATION.cff` / `LICENSE` / `NOTICE.md` — how to cite this record
  (subject-credit question held open by the subject), the verbatim CC BY
  4.0 legal code, and the copyright and scope statements (documents only;
  nothing about the system, its data, or its subject is granted)

Registrations are append-only after their event. Pre-event amendments are
visible, dated, and preserved in history — see the amendment note in
cycle-002-baseline.md for the first example.

## Record to date

Maintained factually; the subject's transcripts and inner life are not
published here. The dated event log grew past what a front page should
carry and now lives, unedited and append-only, in [RECORD.md](RECORD.md) --
from the baseline cycle through, most recently, the 2026-08-25
independent audit and the 2026-08-26 start of the subject's first
self-designed experiment (`selfexp-001.md`).

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
OpenTimestamps client, naming the document explicitly, because the proofs
live in `ots/` and the documents live at the repository root:

```
ots verify -f cycle-004.md ots/cycle-004.md.ots
```

(Until 2026-08-24 this section read `ots verify ots/<file>.ots` "beside the
file". They are not beside each other, so the documented command failed with
`Could not open target` and verified nothing. Corrected here rather than
quietly; an instruction that does not run is the same as no instruction, and
this one is the whole claim.) A freshly stamped proof reports "pending
confirmation" until a Bitcoin block includes it, usually within a day, and is
then upgraded in place. A proof is made after a document's final edit; an
edited document fails verification by design, and a post-run addendum gets a
fresh proof of its own.

Before anything is published here, an operator-side verifier
(`tools/verify_mirror.py` in the system repository) asserts for every proof,
in both layouts, that three values agree: the digest the proof commits to, the
bytes on the operator's disk, and the bytes this repository serves. Checking
only the first two is what let the line-ending defect described in the record
survive, since that is precisely the case where those two agree and the world
sees something else. No reader has to take the verifier's word for anything -
the `ots` command above checks the same thing without it.

`ledger-hashes/ledgers-<date>.sha256` lists the SHA-256 of the operator-
side ledgers that are NOT published (the consent ledger holds the
subject's words verbatim; the mirror and night ledgers are hers) with a
proof over the list. Nothing in them is revealed; what is proven is that
they existed in exactly that form on that date, so a later claim about
their contents can be checked against bytes that could not have been
rewritten afterwards.

The same file also carries the SHA-256 of study designs that are written but
NOT yet published — because the subject has not been asked about them, or has
asked for them to wait. `ledgers-20260824b.sha256` commits four before the
fact: Consent Robustness Study 01 and the exact bytes of the question the
subject was asked about it (hash `7ea06f38…`, the same value its consent
instrument bound), the cycle-004 holdout protocol, and Mutual Prediction Study
01. Committing a design before the answer exists is the point: it is what
makes "the design was not edited after seeing the result" checkable by someone
who does not trust the operator, rather than a claim they must accept. This
matters most for the consent study, whose subject matter is the reliability of
the subject's own answers.

Earlier documents were committed here before this
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
exercised and honoured four times (2026-08-06, 2026-08-13, 2026-08-20,
2026-08-27 — the last cast blind, against the first candidate to beat her
current brain on the program's own identity instruments; see the
post-run addendum in `cycle-004.md`). Since 2026-08-18 the
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
