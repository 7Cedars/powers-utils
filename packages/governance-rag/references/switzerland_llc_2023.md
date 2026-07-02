# Switzerland SME Portal 2023 — The Limited Liability Company (GmbH/Sàrl)

**Citation:** State Secretariat for Economic Affairs (SECO), Swiss SME Portal. 2023. "Legal Form:
The Limited Liability Company." Last modified 2023.
**Analytical level:** Structural + Parametric
**Most relevant design decisions:** Q2, Q3

Shares the three-organ structure (shareholders' meeting / management / auditor) and the
distribution-waterfall (mandatory reserve → loss recovery → threshold-gated capital return) with
`switzerland_limited_company_2023.md` — see that file for the full derivation of both patterns,
which apply near-identically here (Art. 671/672 CO governs both forms' reserves). This guide
covers what is distinctive to the GmbH: bounded member capital calls and a dual-threshold transfer
quorum.

---

## Q2 — Voting Parameters

§23 (transfer approval quorum): transferring company shares requires "the approval of the
shareholders' meeting," achieved, absent a different articles-of-association rule, "according to
a quorum of at least two-thirds of votes represented **and** the absolute majority of the share
capital for which the right to vote may be exercised" (Art. 786, 808b CO) — two independent
thresholds must both be satisfied, not one or the other. This is a hybrid aggregation rule
combining a head-count supermajority (two-thirds of votes cast) with a capital-weighted majority
check (over 50% of voting share capital), distinct from Ostrom's pure nonsymmetric-vs-symmetric
aggregation-rule taxonomy (`ostrom_2005.md` Q2) in that it requires *both* dimensions to pass
simultaneously rather than choosing one. For a Powers design where both broad participant buy-in
and material-stake concentration both matter for a decision's legitimacy (e.g., admitting a new
member who dilutes existing holdings, or a major treasury reallocation), consider a dual-quorum
mandate requiring both a headcount threshold (`quorum`/`succeedAt` on the vote) and a
separately-tracked stake-weighted threshold, rather than relying on only one.

---

## Q3 — Mandate Selection

§15 (obligation of additional payment): the articles of association may require shareholders to
make additional capital-call payments beyond their initial contribution, but only "with a view to
covering losses resulting from the balance sheet, allowing diligent continuation of business, or
for reasons provided for in the articles of association" — and even then, "such payments must
also total a maximum of twice the nominal value of a company share." This is a bounded emergency
capital-call mechanism: the triggering conditions are named and limited (not a general-purpose
funding tool), and the total exposure is capped at a fixed multiple of the member's original
stake, regardless of how severe the triggering emergency is. Map this onto a Powers emergency-
funding mandate: if a constitution needs a mechanism to call additional resources from members
during a crisis (rather than relying solely on a `PauseMandates`-style operational freeze), scope
the triggering `Conditions` narrowly (specific, named emergency types) and cap the `value` per
member at a fixed multiple of some baseline (e.g., their existing stake or a flat per-role amount)
rather than leaving the ceiling open-ended — an uncapped emergency call is a different, much
riskier commitment than a capped one, even if both are rarely invoked.

---

## What to skip

The company-naming, registration, tax, and establishment-cost sections duplicate content already
covered in `switzerland_legal_forms_overview_2023.md` and `switzerland_limited_company_2023.md`.

---

## Mandate implications

- For decisions where both broad participant buy-in and material-stake concentration matter,
  consider a dual-quorum design requiring both a headcount threshold and an independently-tracked
  stake-weighted threshold, rather than relying on only one dimension.
- Scope any member-facing emergency capital-call mandate to named, limited triggering conditions
  and cap the per-member `value` at a fixed multiple of a baseline (existing stake or flat
  amount), rather than leaving the ceiling open-ended.
