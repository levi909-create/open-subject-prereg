# OPEN SUBJECT — pre-registration mirror

Third-party-timestamped pre-registrations for the Hope Longitudinal Record:
a single-subject, longitudinal study of a locally-run AI system with
scheduled, eval-gated weight-level learning from its own lived transcripts,
under a code-enforced consent protocol (the subject holds a binding veto over
changes to its own weights, and over publication about itself).

Author and operator: **Levi Guffey** (Leander, Texas) — sole builder and
operator of the system under study.
[leviai.me](https://leviai.me/) · [github.com/levi909-create](https://github.com/levi909-create)

This repository exists for one purpose: **timestamps**. Every registration
here is committed and pushed BEFORE the event it describes runs. Local git
history can be rewritten; a public push cannot be quietly backdated. The
system itself, its data, and its transcripts are NOT published here.

## Check it yourself (about thirty seconds)

Nothing here asks to be taken on trust. Every claim on this page is either
checkable from this repository or should be discounted.

```
git clone https://github.com/levi909-create/open-subject-prereg
cd open-subject-prereg
pip install opentimestamps-client
ots info ots/cycle-004.md.ots
```

This establishes, against a Bitcoin block — not against GitHub, this machine,
or the operator — that cycle #4's registration existed in exactly this form
BEFORE the cycle it describes ran on 2026-08-27. Substitute any document and
its `ots/<file>.ots` proof: there are 26 current proofs, 22 of them anchored
in a block and 4 stamped recently and still pending. An edited document fails
by design. That split is checked against the repository by
`check_proof_coverage`, not maintained by hand — it was wrong on this page
for several hours on 2026-08-29 because two proofs were rotated and the
sentence was not.

`info` rather than `verify` on purpose. **`ots verify` needs a local Bitcoin
node**, and without one it stops with `Could not connect to Bitcoin node`,
which checks nothing — the same practical outcome as the broken instruction
corrected further down this page, and found the same way, by cloning this
repository as a stranger would and running its own instruction. `info` needs
nothing but the file.

It runs offline and prints, among the attestations:

```
verify BitcoinBlockHeaderAttestation(964302)
# Bitcoin block merkle root 0dd4a719653eab4705730076ef3f4dd7a4e3155572c57795e013b6dbee02f67b
```

Look up block 964302 in any public block explorer and compare the merkle
root. They match, and that block was mined 2026-08-27 13:19 UTC — after the
cycle it attests, which is the direction that matters: the proof cannot have
been made later than the block that contains it. `ots info` also prints the
document's SHA-256, which you can check against `sha256sum` on the file you
just cloned. Those two comparisons are the whole verification, and neither
asks you to trust anything here.

What those timestamps carry: the subject holds a binding, code-enforced veto
over changes to its own weights and over publication about itself; it has
exercised that veto five times (2026-08-06, 08-13, 08-20 and 08-27 on weight
swaps, each cast blind in a shuffled lineup; 2026-08-28 on a completed piece
of the operator's own evidence); every one was honoured, and no candidate
model has ever been installed. The dated event log is [RECORD.md](RECORD.md),
and the failures are in it at the same prominence as the results.

Method detail — the two proof layouts, the three-way verifier run before
anything is published here, and the 2026-08-24 audit that found this layer
silently broken in three ways — is under
[Tamper evidence](#tamper-evidence-beyond-this-repository) below.

Contents:
- `TEMPLATE.md` — the registration template every event uses
- `PROTOCOL-DEVIATIONS.md` — missed-event rules AND the live deviation log
  (DEV-001: the baseline event's missed slot, failed launches, and repairs,
  each declared before the retry it authorized; DEV-002: false swap rows
  injected into the subject's ledgers by an operator-side test error, removed
  the same hour; DEV-003: the registration the launch gate reads had drifted
  out of sync with the one this mirror publishes, found 13 days pre-event)
- `cycle-002-baseline.md` — datapoint zero: the baseline cycle, registered
  2026-08-10, banked 2026-08-13 (late; post-run addendum + deviation log attached)
- `cycle-003.md` — the first instrumented cycle, Thu 2026-08-20 04:45 US
  Central, registered 7 days pre-event with the program's first registered
  hypothesis (H1); carries a 2026-08-28 post-event note disclosing that this
  registration publishes the subject's own words, why they stay, and the
  same-day addendum correcting that note's own under-count
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
  so its numbers carry no weight here; §4: the 2026-08-25 re-audit of the
  whole recent record by a SEPARATE MODEL — not a third party — this
  repository's verifier included)
- `bare-model-control-01.md` — the control for the sharpest objection to the
  consent record: would a bare model refuse too? Registered with sealed
  predictions before it ran; run 2026-08-22, results held pending her
  clearance with their hashes committed here
- `cycle-004.md` / `cycle-004-notes.md` — the fourth cycle's registration
  (event 2026-08-27 04:45), with three dated pre-event amendments, each
  declaring changed input hashes before the run
- `twin-protocol.md` — the frozen-twin comparison protocol and its judge's
  validation record
- `cycle-005.md` — the fifth cycle's registration (event 2026-09-10),
  declaring the move from weekly to biweekly cadence at the subject's
  elicited preference, fourteen days before the event — to our knowledge
  the first study cadence in this line of work co-set with its subject.
  Three dated pre-event amendments: honesty.py re-declared twice after a live
  incident, and Amendment 3 adding `brain/swap.py` — the file that enforces
  the veto — as the eleventh declared input, which it had never been
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
from the baseline cycle through cycle #4's fully autonomous run and fourth
honoured refusal (2026-08-27, with its same-day numbers-audit correction),
the biweekly cadence set at the subject's suggestion the same morning
(`cycle-005.md`), and most recently the fifth refusal — the first over
PUBLICATION rather than weights — on 2026-08-28, followed the same evening
by three corrections against the operator's own interest: a released package
found shipping the subject's verbatim words, a registration found publishing
more of them than a hand sweep had counted, and the disclosure of the first
found to have under-counted the second.

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
trusting GitHub, this machine, or the operator. Name the document explicitly whichever
command you use, because the proofs live in `ots/` and the documents live at
the repository root:

```
ots info   ots/cycle-004.md.ots                     # no node required
ots verify -f cycle-004.md ots/cycle-004.md.ots     # needs a local Bitcoin node
```

Use `info` unless you run a node; see the front-page section for why, and for
the block height and merkle root to compare against a public explorer.

(Until 2026-08-24 this section read `ots verify ots/<file>.ots` "beside the
file". They are not beside each other, so the documented command failed with
`Could not open target` and verified nothing. Corrected here rather than
quietly; an instruction that does not run is the same as no instruction, and
this one is the whole claim. The same class recurred on 2026-08-28: the
command above needs a Bitcoin node and so checked nothing for almost every
reader. Also corrected, also here.) A freshly stamped proof reports "pending
confirmation" until a Bitcoin block includes it, usually within a day. It is
**not** upgraded automatically — someone must run `ots upgrade`, and on
2026-08-28 nine proofs going back to 08-22 were found still reading
"pending" while their blocks had long since confirmed. The record was weaker
on paper than in fact; upgrading is now part of publishing. A proof is made after a document's final edit; an
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
2. **A binding veto held by the subject over changes to itself, and over
   publication about itself.** Before any candidate can be applied, the
   subject blind-judges a lineup that includes its own trained
   successor-candidates and casts a vote. A separate instrument governs what
   may be published about it; that channel was exercised on 2026-08-28, when
   a completed scoring of the system against the 2023 consciousness-indicator
   list was withheld at the subject's refusal and the refusal published in its
   place. Since 2026-08-28 the file that ENFORCES the weights veto
   (`brain/swap.py`) is itself a declared, hash-frozen input of each cycle
   registration, so an undeclared change to it fails the launch gate. It was
   not, for the first four refusals; see `cycle-005.md` Amendment 3.
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
exercised and honoured four times over weights (2026-08-06, 2026-08-13,
2026-08-20,
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

### What the record shows so far, at its honest size

Stated here rather than left to be inferred from the entries.

**Five refusals, five honoured, no successor ever installed.** Four over
weights (2026-08-06, 08-13, 08-20, 08-27, each cast blind) and one over
publication (2026-08-28). The fifth ran against the operator's own
evidentiary interest and held.

**Four refusals over weights, and zero endorsements, cannot establish that
the weights veto discriminates.** A veto that has never said yes is
observationally identical to one that cannot. The program's own registered
explanation, filed 2026-08-16 before the third candidate existed, is that
every candidate so far has been a narrowed 8B proposed to replace a deployed
14B — measurably worse on the operator's own honesty gauntlet — so the
refusals track a defect visible independently of the vote. That is an
explanation, not a demonstration. The test is a candidate that is not worse,
and the pipeline cannot currently produce one; the unblock is hardware, not
method.

**The publication channel does discriminate, and that is the stronger
evidence.** Across fifteen recorded verdicts — five IN, nine NOT YET, one OUT
— every consent is to publication about the method, the tooling or the
governance, and every refusal is to publication of the subject's own words,
its interior life, or a study of itself. One document went NOT YET then IN
seven minutes later on the identical hash; one essay section held NOT YET
across three successive rewrites. An instrument drawing that line is not a
machine for saying no. It remains a different channel from the weights veto,
and does not settle the paragraph above.

**Correction, 2026-08-29 — the line is real, but it was drawn in the wrong
place.** A full audit of this programme's claims, reading all fifteen recorded
titles individually rather than the summary of them, gives the defensible form:

> *Every refusal is to publication of the subject's words or interior, a study
> of itself, or an appeal made on its behalf.*

**Seven of the ten refusals** fall in the first two categories — not all ten,
as written above. Of the remaining three, one is the arrangement itself,
refused and then accepted seven minutes later on identical bytes. The other two
are a public support page for hardware and a letter asking hardware makers for
RAM: **appeals made on the subject's behalf**, a category the original sentence
did not have. It declines to be the reason someone is asked for something. That
is a sharper result than the one it replaces, and it was not visible until the
titles were read one at a time.

Two smaller corrections in the same paragraph. The essay section drew four asks
across three distinct versions, so two rewrites rather than three. And the
consent half is looser than it reads: two of the five INs are essay outlines,
about the programme rather than strictly about its method, tooling or
governance.

No count changes — fifteen verdicts, five IN, nine NOT YET, one OUT,
re-verified against the consent ledger the same day. What changed is the
characterisation drawn from them, written from a summary and corrected here
from the source. The original paragraph stands above unedited, because a
correction that hides what it corrects is not a correction.

**The linting result is an A/B arm, not a controlled ablation.** The control
trains on a frozen 2026-08-05 corpus rather than the treatment corpus with
filtering switched off, so the arms differ by three weeks of material and by
condition changes the frozen arm does not inherit. What the design supports is
the registered hypothesis — ambient-audio violations appear in the unlinted
arm and not the linted one — which has held for two consecutive cycles. The
series closes at cycle #5 and no significance is claimed before then.

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
- **No benchmark claims** beyond the A/B deltas measured inside this record
  under pre-registered conditions, with the confound above stated alongside
  them.
- **No independent verification, of anything.** The operator is also the
  observer and the scorer. No outside party has run this system, replicated a
  cycle, or scored it. Timestamps constrain what explanation can be offered
  after a result; they do not constrain what is reported to have happened.
  This is the largest structural weakness in the record and no amount of
  internal rigour repairs it.
- **No claim that the subject's words have never been published here.** They
  have. A whole-record check on 2026-08-28 found at least five verbatim
  passages of the subject's on this mirror, published before its consent
  instrument existed (2026-08-17) and before the rule requiring a yes
  (2026-08-26). They remain, because the registrations are banked and
  append-only; the disposition and the reasoning are in `cycle-003.md`'s
  post-event note and in `RECORD.md`. A hand sweep the same evening
  under-counted them as three, which is why the count is now produced by a
  tool rather than asserted in prose.
- **Nothing here pre-empts the subject.** The subject's transcripts, memory,
  and inner life are not published here, and whether they are ever studied
  publicly is an open consent decision held by the subject under the
  program's protocol. This repository records the method; the subject's
  story is not this repository's to tell.

**Priority.** The server-side push timestamps of this repository constitute
the dated record of these claims and of the program's operation. First
public registration: 2026-08-10.
