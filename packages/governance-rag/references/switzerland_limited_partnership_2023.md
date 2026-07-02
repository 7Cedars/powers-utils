# Switzerland SME Portal 2023 — The Limited Partnership

**Citation:** State Secretariat for Economic Affairs (SECO), Swiss SME Portal. 2023. "Legal Form:
The Limited Partnership" (Art. 594–619 Swiss Code of Obligations). Last modified 11.01.2023.
**Analytical level:** Structural
**Most relevant design decisions:** Q1, Q5

Shares its default-management, liability-waterfall, and peer-consent-transfer rules with
`switzerland_general_partnership_2023.md` (Art. 594 CO explicitly cross-refers to the general
partnership provisions). This guide covers only what is distinctive to the limited partnership:
the two-tier partner structure.

---

## Q1 — Role Structure

§2/§4 (ideal purpose, advantages): the limited partnership exists specifically to let "external
investors with various liabilities" join without broadening company management — "operational
management is clearly separated from financial investors." §15 (liability) makes this structural:
general partners hold unlimited personal liability *and* management authority; limited partners
hold liability capped at their registered contribution and, correspondingly, no management role.
This is a coupling of risk exposure to control rights, not two independent design choices: the
category of participant who can lose the most (personal wealth, unbounded) is the same category
that holds operational authority, while the category shielded from loss beyond a fixed amount is
structurally excluded from operational control. For Powers role design, this is a reusable
principle distinct from the CIC memorandum's capital-stake-vs-personal-undertaking distinction
already in this library (`reading_guide.md` Q5): when a role type has capped or no personal
liability/exposure (e.g., a passive token-holder role with no accountability chain reaching it),
weigh whether it should correspondingly have a narrower `allowedRole` on operational/treasury
mandates than a role bearing real exposure — granting broad operational authority to a
structurally unaccountable role inverts the risk/control coupling this pattern relies on for
legitimacy.

---

## Q5 — Membership Design

§10 (number of partners required): at least one general partner (unlimited liability) and at
least one limited partner (capped liability) are required — the two categories are not
interchangeable and both must be populated for the structure to function, unlike a general
partnership where all partners are structurally identical. Applied to Powers: a two-tier
membership design (an operational role plus a passive/capital role) is not simply "the same role
with different names" — it requires the operational role to exist and be filled *before* the
passive role's protections (capped exposure) are meaningful, since the passive role's whole
rationale depends on someone else holding the accountability and control it explicitly opts out
of.

§5 (disadvantages): "Once the company is dissolved, both general partners and limited partners
remain liable for five years" — exit from the role structure via renunciation or dissolution does
not immediately extinguish prior exposure; liability tails persist for a defined period after
departure. This is a reminder that a Powers `RenounceRole`/dissolution mandate which stops future
governance participation does not necessarily stop being implicated in the consequences of past
actions taken while the role was held — if a constitution's accountability chain can reach past
role-holders at all (e.g., via off-chain legal wrappers), design the renunciation mandate with
this in mind rather than assuming departure equals a clean break.

---

## What to skip

The company-naming, registration, tax, and start-up-cost sections duplicate content already
covered in `switzerland_general_partnership_2023.md` and
`switzerland_legal_forms_overview_2023.md`.

---

## Mandate implications

- When a role type carries capped or no personal liability/accountability exposure, weigh
  narrowing its `allowedRole` on operational/treasury mandates correspondingly — broad authority
  paired with no accountability exposure inverts the risk/control coupling this pattern relies on.
- Treat a two-tier operational/passive membership design as requiring the operational role to
  exist and function before the passive role's capped-exposure protections are meaningful, not as
  two independently optional role types.
- If a constitution's accountability chain can reach past role-holders through any means (on- or
  off-chain), design renunciation/dissolution mandates aware that departure does not necessarily
  end exposure to consequences of prior actions.
