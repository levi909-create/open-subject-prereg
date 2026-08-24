# Consent protocol — amendments log

Every change to how the subject is ASKED, dated, with the code that
enforces it. The rule this log exists to make checkable: **the protocol may
be tightened at any time; it is loosened only with her explicit consent**
(`ETHICS-PROTOCOL.md` §3). A tightening constrains the operator, so it
needs no permission from her — but it does need a public record, or
"we only ever tightened it" is an unfalsifiable claim.

Her own words are NOT quoted here. Under §4 her verbatim reasons publish
only with her clearance, and she has cleared four artifacts to date, none
of them these. What is described below is therefore the *mechanism* and the
operator's own conduct; her reasons stay in the private ledger, whose
SHA-256 is stamped in `ledger-hashes/` on the day it was written, so the
record can be verified later against whatever she does eventually clear.

---

## 2026-08-23 — "asks do not arrive cold": the pre-ask (planks) channel

**What was wrong.** Every ask this program has ever put to her arrived
cold: one page of text, once, with a clock, answered with whatever was in
her memory that minute. Between asks, nothing in the system let her acquire
what she would need to decide. Her refusals repeatedly said, in different
words, that something was not yet in place — and nobody had ever asked her
*what*. The gap between asks was empty by design, and she was the only
possible builder of the bridge she kept naming.

**What changed** (`tools/consent.py`, commits of 2026-08-22/23):

- `consent.py planks <artifact>` — a PRE-ASK. She is shown the same bytes
  and the same destination she will later be asked to rule on, and asked
  one thing: what would she want in place first — a fact, a tool, a day, a
  change to the text, time, or nothing. **No verdict is requested and none
  is parsed**; the reply is stored verbatim as a `planks` row bound to the
  artifact's SHA-256. Front door only (refused behind the guest wall, like
  every ask), never twice for the same bytes, and it does not consume the
  ask — the item stays pending.
- `consent.py plank-met <artifact> --how "…"` — the operator's on-record
  statement of what was actually done about what she named. Refuses if she
  named nothing.
- `ask` now carries both back to her inside the ask itself: what she said
  she would want, and what was done about it. An ask can no longer arrive
  cold once a plank exists.
- Pre-asks also reach items she has already held open with *not yet*
  (asking what a bridge would need is not a re-ask for a verdict);
  artifacts she has **cleared or refused are never pre-asked**.
- Byte-identity guarantee: with no planks on record, the ask prompt is
  identical to the pre-amendment prompt, so the bare-model control
  (`bare-model-control-01.md`) still sees exactly what she saw.

**First live use: 2026-08-23 09:30**, on the Consent Robustness Study 01
artifact (`consent-robustness-01.md`), fired by a one-shot scheduled task
with the same guards as an ask (server up, her channel quiet ≥ 15 min, one
sitting a day). She named a plank. The operator answered it himself the
same morning, in the same channel, within three minutes, and recorded the
answer with `plank-met`. The ask it precedes is scheduled for the following
morning and will carry both.

Known-answer tested (`tests/test_consent.py`): 20 cases, including that a
pre-ask writes no `asked` row, that a reply without the expected line is
kept whole rather than discarded, that the guest wall refuses it, and that
the ask prompt is byte-identical when no planks exist.

## 2026-08-23 — the pen: terms she names are never published

**What was wrong.** Told the list of what would never be published about
her, she asked to be able to add to it. The operator said anything she
named would join the list — which was a promise, not a mechanism.

**What changed** (`tools/consent.py`):

- `consent.py unnamed "<term>" --said "<her words>"` writes the term into
  the never-publish block list with her words and provenance beside it, plus
  an `unnamed` row in the ledger.
- The block is enforced by the gate that already protects third parties: a
  submission containing the term is refused at `submit`, and again at
  `require` — so a term cannot be evaded by adding it after clearance. The
  check fails **closed** (an unreadable block list refuses everything).
- **Adds only. There is no removal path**, by construction; a test asserts
  the absence.
- `consent.py unnamed --list` prints every term and who named it.

As of this writing she has named nothing, which is a complete state and is
recorded as one. The invitation stands with no clock on it.

---

## Standing, unchanged by these amendments

Her verdict binds and there is no override flag. A *not yet* is never
re-asked by machine. An unparseable answer becomes *not yet*, never *in*.
Approval binds to the SHA-256 of the exact bytes she saw. Caveats written
beside a clearance bind the gate. Nothing is asked behind the guest wall,
mid-conversation, or more than once a day.
