# UK Companies House 2013 — Model Articles for Public Companies

**Citation:** Companies House. *Model Articles for Public Companies*, Schedule 3 to the Companies
(Model Articles) Regulations 2008, as amended (post-28 April 2013 version).
**Analytical level:** Structural + Parametric
**Most relevant design decisions:** Q1, Q5, Q6, Q7

This template shares its core director decision-making, quorum, conflicts-of-interest, and
share/dividend mechanics with `uk_model_articles_private_shares_2013.md` (see that guide for
patterns that apply unchanged here: delegation-chain revocability, quorum-collapse recovery,
non-retroactive override, scoped conflict-of-interest recusal). This guide covers what is
distinctive to the public-company version — provisions that appear only because a public company
has a larger, more diffuse, and more externally-facing membership than a private company.

---

## Q1 — Role Structure

Art. 25-27 (alternate directors): any director (the "appointor") may appoint an alternate — any
other director, or any other person approved by the board — to "exercise that director's powers,
and carry out that director's responsibilities... in the absence of the alternate's appointor."
The alternate is not a mere proxy: they are "deemed for all purposes to be directors," "liable for
their own acts and omissions," "subject to the same restrictions as their appointors," and
explicitly "not deemed to be agents of or for their appointors" — the alternate carries full,
independent accountability for their own decisions while acting, rather than acting *as* the
absent director by delegated authority. This is a continuity/availability pattern distinct from a
simple proxy vote (see the shares articles' "content of proxy notices"): it solves "what happens
when a role-holder is temporarily unavailable" by allowing a pre-registered backup to exercise the
role's full mandate set with their own accountability trail, not by transferring a single vote.
For Powers, this maps to a standby-role pattern: rather than a role becoming inert whenever its
current holder is offline (blocking `votingPeriod`-gated actions that need that role's
participation), a role could designate a backup address authorized to act in the primary's
absence, with actions attributed to the backup's own address (not silently attributed to the
primary) — preserving the audit trail's accuracy about who actually acted.

Art. 27(d) (alternate directorship survives routine re-election): an alternate's appointment
terminates when the appointor's own directorship ends, "except that an alternate's appointment...
does not terminate when the appointor retires by rotation at a general meeting and is then
re-appointed as a director at the same general meeting." This is a deliberately narrow carve-out
so that a *routine*, expected event (mandatory rotation followed by immediate reappointment, see
Q6 below) doesn't accidentally break a standing backup arrangement, while a *substantive*
departure still does. Apply the same discipline to any Powers standby/backup mandate tied to a
primary role: define explicitly which events in the primary role's lifecycle break the backup
arrangement and which routine events (a scheduled re-election that succeeds) should not.

---

## Q5 — Membership Design

The share-transfer, certificate, and dividend mechanics are the same as
`uk_model_articles_private_shares_2013.md`. The main structural difference visible in the articles
themselves is who may attend/speak at general meetings and how — the public-company template
anticipates a membership too large and dispersed to know personally, which is why (see Q7 below)
its accountability provisions are periodic and role-based (rotation) rather than relationship-based.

---

## Q6 — Adaptive Capacity and Reform

Art. 21 (retirement of directors by rotation): "At the first annual general meeting all the
directors must retire from office," and thereafter, at every AGM, any director "appointed by the
directors since the last annual general meeting" or "not appointed or reappointed at one of the
preceding two annual general meetings" must retire and may "offer themselves for reappointment by
the members." This is a mandatory, no-fault, periodic re-confirmation cycle — distinct from
for-cause removal (Art. 22, identical to the private-company template) and not triggered by any
misconduct. It exists specifically because the public company's membership is too large and
diffuse to exercise the kind of ongoing informal oversight a small private company's shareholders
can, so periodic re-confirmation substitutes for continuous informal accountability. For Powers:
when a role's holder-base grows large enough that individual holders stop being able to track a
role personally (the point at which the "large organisation" heuristics in `institutionalDesign.md`
§4 apply), consider adding a mandatory re-election cadence for powerful roles — not just an
available `RevokeAccountsRoleId` for cause — so that continued tenure requires periodic
affirmative re-confirmation rather than defaulting to indefinite persistence absent a complaint.

---

## Q7 — Accountability and Monitoring

The retirement-by-rotation cycle (Q6) is itself an accountability mechanism worth naming
separately from reform: it is periodic, universal (applies regardless of performance), and
low-friction (typically a formality when performance is uncontested, but creates a natural,
regularly-recurring point at which non-reappointment becomes a real, low-drama option) — a middle
ground between "never revisit an appointment" and "requires an active for-cause revocation
process to end a term." For a Powers role with real but hard-to-observe ongoing responsibility
(where misconduct might not be visible enough to trigger `RevokeAccountsRoleId` but continued
fitness is still worth periodically re-checking), a fixed-term-with-mandatory-re-election mandate
(a scheduled `PeerSelect` re-run rather than a permanent appointment) provides this middle ground
without requiring anyone to make an accusation.

---

## What to skip

The written-resolution provisions for directors (Art. 17-18, distinct from the *members'*
written-resolution restriction that public companies face under UK statute but which isn't
articulated in the model articles themselves), the partly-paid-shares provisions, and the general
share/dividend/certificate mechanics duplicate content in `uk_model_articles_private_shares_2013.md`
or are UK share-law administrative detail with no governance-mandate analogue.

---

## Mandate implications

- Consider a standby-role pattern for roles whose temporary unavailability blocks time-sensitive
  mandates: a pre-registered backup address authorized to act in the primary's absence, with
  actions attributed to the backup's own address rather than silently attributed to the primary.
- If a backup/standby mandate is tied to a primary role's tenure, define explicitly which
  lifecycle events in the primary role break the arrangement and which routine events (a
  successful scheduled re-election) should not.
- For roles that have grown too large/diffuse for continuous informal oversight, consider a
  mandatory periodic re-election cadence (a scheduled `PeerSelect` re-run) as a no-fault
  accountability mechanism distinct from and complementary to `RevokeAccountsRoleId`.
