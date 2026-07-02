# UK Companies House 2013 — Model Articles for Private Companies Limited by Guarantee

**Citation:** Companies House. *Model Articles for Private Companies Limited by Guarantee*,
Schedule 2 to the Companies (Model Articles) Regulations 2008, as amended (post-28 April 2013
version).
**Analytical level:** Structural
**Most relevant design decisions:** Q5

This is the base statutory template the UK CIC guarantee-based model articles already covered
extensively in this library (`cic_model_articles_guarantee_small.md`, `cic_model_articles_
guarantee_large.md`) are built on top of. Nearly all of its director decision-making, quorum,
conflict-of-interest, and voting mechanics are identical to
`uk_model_articles_private_shares_2013.md` (see that guide for the delegation-chain,
quorum-collapse-recovery, non-retroactive-override, and scoped-recusal patterns, all of which
apply here unchanged) and to the CIC guides already in this library for the closed-membership
patterns. The one point not already captured elsewhere is below.

---

## Q5 — Membership Design

Art. 21-22 (applications for membership / termination): "No person shall become a member of the
company unless... that person has completed an application for membership in a form approved by
the directors, and the directors have approved the application" — a two-part gate (a defined
application format, plus discretionary board approval) rather than either open entry or a purely
objective eligibility test. Combined with "membership is not transferable" and automatic
termination "when that person dies or ceases to exist," this is the same closed-membership,
board-gatekept pattern already extracted from the CIC model articles (`reading_guide.md` Q5,
Quaternary entries) — restated here as confirmation that it originates in the base statutory
template, not as a CIC-specific addition. The one detail worth adding: the application *format*
is separately controlled by the directors from the approval *decision* itself — a designer could
map this to a two-stage `PeerSelect`-style entry mandate where the eligibility criteria/form
(what must be submitted) and the admission decision (whether to admit) are two distinct,
independently-adjustable parameters, rather than a single opaque "the board decides" gate.

---

## What to skip

All director decision-making mechanics (delegation, collective decisions, quorum, conflicts of
interest, records) and general-meeting/voting mechanics are identical or near-identical to
`uk_model_articles_private_shares_2013.md` — see that guide. The administrative provisions
(company seals, means of communication, indemnity/insurance) are legal-formality content with no
governance-design analogue.

---

## Mandate implications

- When designing a board-gatekept membership-entry mandate, separate the eligibility
  criteria/application format (an adjustable parameter) from the admission decision itself (a
  discretionary `PeerSelect`-style vote), so each can be reviewed and reformed independently.
