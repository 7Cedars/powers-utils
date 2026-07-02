# Switzerland SME Portal 2023 — The General Partnership

**Citation:** State Secretariat for Economic Affairs (SECO), Swiss SME Portal. 2023. "Legal Form:
The General Partnership" (Art. 552–593 Swiss Code of Obligations). Last modified 11.01.2023.
**Analytical level:** Structural + Parametric
**Most relevant design decisions:** Q1, Q4, Q5

---

## Q1 — Role Structure

§22 (Management and representation): "The management function of the general partnership is the
responsibility of all partners, provided it is not governed differently according to a decision
of the partners" (Art. 563 CO) — the statutory default is full-participatory management, and
narrowing it to a subset requires an affirmative decision, not the other way round. This is a
concrete legal instance of Ostrom's default-condition principle (`ostrom_2005.md` Q1/Q5: "anyone
can hold this position" is the default absent a specifying rule) — useful as a worked example when
explaining to a designer why a Powers constitution's setup mandate must *explicitly* narrow
`allowedRole` on executive mandates, since an unconfigured default in Powers (no mandate exists)
behaves oppositely to this statutory default (nothing is possible until a mandate grants it) —
worth flagging this inversion explicitly to designers coming from a traditional-company-law
background, since their intuition about "default = open" does not transfer to Powers.

---

## Q4 — Dependency Chains

§17 (Allocation of profits/liability for losses): "when losses have reduced part of the company
assets, the partners maintain their right to payment of fees and interest for their reduced
share, but may not withdraw profits before their share has been reconstituted." This is a
concrete loss-recovery-before-distribution sequencing rule: a distribution mandate is gated on an
implicit precondition (accumulated losses replenished) before it can fire, not merely on having a
positive balance at the moment of the vote. Map this onto a Powers treasury design as an explicit
`needFulfilled`-style precondition on any profit/surplus-distribution mandate: check that
historical losses have been recovered (a running reserve/deficit tracker) before allowing a
distribution, rather than checking only the current balance, which could mask an unreplenished
prior deficit.

§15 (Liability): company assets answer for obligations "in the first instance (primarily)";
partners' personal assets answer only "in the second instance (on a subsidiary basis)." This is a
liability-waterfall pattern: exhaust the organisation's own treasury before any secondary/backup
resource (a guarantor, an insurance mandate, a bonded reserve) is touched. Apply the same ordering
discipline to any Powers design with a fallback funding source — the mandate authorizing access to
the fallback source should have a `needFulfilled` dependency on the primary treasury being
demonstrably insufficient, not run in parallel with it.

---

## Q5 — Membership Design

§23 (Termination/transfer): "A general partnership may not be transferred by one partner without
the consent of the other partners" (Art. 557, 542 CO). This is a peer-consent-gated exit/transfer
pattern — reinforces the CIC model-articles "non-transferable membership with no secondary-market
exit" pattern already in this library (see `reading_guide.md` Q5 Quaternary entries) with an
independent, non-CIC statutory example: transferring a partnership stake is not a unilateral
`RenounceRole`-then-reassign action but requires the equivalent of a `PeerSelect`-style consent
step from remaining members, since incoming partners inherit joint liability exposure that
existing partners did not choose to share with a stranger.

---

## What to skip

The company-naming rules (§7), tax comparison tables (§20), and jurisdictional/nationality
requirements (§24) are Swiss administrative and tax-law specifics with no governance-design
content. The accounting-obligation thresholds (§19) duplicate the audit-scaling content already
extracted in `switzerland_legal_forms_overview_2023.md` Q7.

---

## Mandate implications

- When explaining Powers' `allowedRole` design to someone from a traditional-company-law
  background, flag explicitly that Powers' unconfigured default (nothing possible until a mandate
  grants it) is the *inverse* of the general-partnership default (everything possible to every
  partner until narrowed) — their intuitions will point the wrong way otherwise.
- Gate profit/surplus-distribution mandates on a loss-recovery precondition (accumulated deficit
  reconciled to zero), not merely a positive current balance.
- Order fallback-funding-source mandates with a `needFulfilled` dependency on the primary
  treasury being demonstrably insufficient, rather than running both in parallel.
- Gate membership-stake transfer on a peer-consent step (`PeerSelect`-equivalent) rather than
  treating it as a unilateral action, whenever incoming members inherit shared exposure.
