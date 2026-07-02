# Switzerland SME Portal 2023 — Comparison of Legal Forms

**Citation:** State Secretariat for Economic Affairs (SECO), Swiss SME Portal. 2023. "Comparison
of Legal Forms" (sole proprietorship, general partnership, GmbH/Sàrl, AG/SA). Last updated
January 2023.
**Analytical level:** Structural
**Most relevant design decisions:** Q3, Q6, Q7

This is a side-by-side factsheet comparing four Swiss legal forms across liability, capital,
governance, and audit requirements. It is best read as a summary map before the individual-form
guides (`switzerland_general_partnership_2023.md`, `switzerland_llc_2023.md`,
`switzerland_limited_company_2023.md`, `switzerland_limited_partnership_2023.md`), which contain
the detailed statutory content.

---

## Q3 — Mandate Selection

The four forms scale formality (minimum capital, mandatory audit, registration procedure) to the
stakes and external-trust needs of the organisation: no minimum capital and no audit for a
partnership vs. CHF 100,000 minimum capital and (above threshold) mandatory ordinary audit for an
AG, explicitly justified by "a high degree of reliability among creditors, suppliers and
customers" for the more capital-intensive form. This is a reusable heuristic distinct from the
existing organisation-size-based `votingPeriod`/quorum table in `institutionalDesign.md` §4:
scale a constitution's formality (documentation requirements, treasury lock-up, mandatory
external-facing accountability mandates) not just to organisation size but to how much *external*
trust the organisation needs from counterparties it hasn't yet built a relationship with — an
internally-trusted, purely member-serving organisation needs less of this than one seeking grants,
contracts, or external partnerships.

---

## Q6 — Adaptive Capacity and Reform

A GmbH "may be transformed into an AG without prior dissolution" — Swiss law provides an explicit
upgrade path between legal forms that preserves the organisation's continuity rather than
requiring a full dissolution and refounding. This is a directly transferable pattern for Powers
constitutions expected to grow in formality over time: design the reform path from a lightweight
starting constitution to a heavier, more externally-legible one as an in-place `Adopt_Mandates`/
`MandatePackage` upgrade (swapping mandate sets while roles and treasury persist) rather than
assuming a growing organisation will eventually need to redeploy entirely. Decide this upgrade
path at initial design time, even if it isn't exercised for years — retrofitting it after the fact
is harder than building it in from the start.

---

## Q7 — Accountability and Monitoring

Audit obligation scales in two independent steps: a "limited audit" becomes compulsory above ten
employees, and a full "ordinary audit" becomes compulsory only once two of three thresholds are
crossed (CHF 20M balance sheet, CHF 40M turnover, 250 FTEs) — the same two-step scaling appears in
`switzerland_llc_2023.md` and `switzerland_limited_company_2023.md`. This is a real-world
instantiation of proportional oversight (cross-cutting rule 11) independent of the AI-governance
family sources that rule was drawn from: a small organisation should face a lighter accountability
mandate (informal monitoring, no dedicated audit-equivalent mandate) than a large one, with the
threshold for escalation defined by concrete, checkable metrics rather than a subjective judgment
call.

---

## What to skip

The tax-comparison tables and worked examples (comparing tax burden across legal forms for a
hypothetical business) are Swiss tax-law specifics with no governance-design content. The company
naming rules (Art. 944-951 CO) are administrative/registration formalities.

---

## Mandate implications

- Scale constitutional formality to the organisation's need for *external* trust from
  counterparties, not only to internal organisation size.
- Design an in-place upgrade path (via `Adopt_Mandates`/`MandatePackage`) from a lightweight
  starting constitution to a heavier one at initial design time, so growth doesn't require a full
  redeployment.
- Define accountability/audit-equivalent-mandate escalation thresholds using concrete, checkable
  metrics (treasury size, membership count) rather than subjective size judgments.
