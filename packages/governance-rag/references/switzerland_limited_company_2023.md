# Switzerland SME Portal 2023 — The Limited Company (AG)

**Citation:** State Secretariat for Economic Affairs (SECO), Swiss SME Portal. 2023. "Legal Form:
The Limited Company" (Art. 620–763 Swiss Code of Obligations). Last modified 16.01.2024.
**Analytical level:** Structural + Parametric
**Most relevant design decisions:** Q1, Q2, Q3, Q7

---

## Q1 — Role Structure

§13-14 (organisation and powers): the AG has three organs — the general meeting of shareholders
("the SA's supreme power"; appoints the board, adopts bylaws, approves the annual report), the
board of directors (day-to-day senior management), and an independent auditor. This maps directly
onto a proposer/executor/auditor separation-of-powers triad (`institutionalDesign.md` §1), with
one addition not explicit in the academic core sources: certain board powers are named as
**non-transferable** even by the board's own choice — "senior management of the company," fixing
the organisation's structure, appointing and supervising management, and drawing up the
management report (Art. 716a CO) cannot be delegated to a third party, while *representation*
authority (the power to bind the company externally) explicitly can be delegated (Art. 718 CO).
This is a two-tier delegability model: some authority is core to a role and structurally
non-outsourceable, while other authority attached to the same role is freely delegable. For Powers
mandate design, this suggests distinguishing mandates that define a role's core purpose (which
should never be reassignable to another `allowedRole` without a constitutional-tier change, e.g.
via `MandatePackage` rather than ordinary `Adopt_Mandates`) from mandates that are merely
convenient current arrangements for representation/execution (which can be reassigned more freely)
— a distinction not currently made explicit in the mandate catalogue's delegability model.

§25 (gender representation, comply-or-explain): large publicly traded companies must reach a
minimum gender-diversity threshold on the board and management, or, failing that, the
remuneration report must disclose "the reasons why the representation... does not meet the
minimum requirement" and "the measures aimed at promoting the underrepresented gender." This is a
disclosure-based accountability pattern distinct from a hard-blocking constraint: rather than
making the threshold a `needFulfilled` gate that prevents action, the mechanism requires
transparent, reasoned non-compliance instead of silent non-compliance. Use this pattern for
Powers-governed goals that are desirable but shouldn't halt core operations if unmet (e.g., a
target for role-holder diversity, geographic distribution, or response-time SLAs) — implement as
a mandatory `StatementOfIntent`-style disclosure mandate triggered by non-compliance, rather than
either ignoring the goal or hard-blocking on it.

---

## Q2 — Voting Parameters

§11 (mandatory capital, capital fluctuation range): "the latest revision of the law... introduced
a new provision, namely the capital fluctuation range: within this pre-established range, the
board of directors is authorized to increase or reduce the company's capital for a maximum period
of five years" without returning to the general meeting for each individual change. This is a
pre-authorized, time-boxed, bounded-discretion pattern distinct from a simple `value` cap on a
single mandate: the general meeting votes once to establish a *range*, the board can act
repeatedly within that range without triggering fresh governance overhead, and the authorization
itself automatically expires and must be renewed (re-voted) after five years. Map this onto Powers
treasury/capital mandate design as an alternative to either (a) a permanent value cap requiring no
further votes, or (b) requiring a fresh vote for every capital action: grant a role a bounded
`value` range via a time-limited mandate (a `PresetActions`/`BespokeAction_Simple` mandate with an
explicit sunset, re-adopted periodically via `Adopt_Mandates`) so routine-but-variable actions
don't need repeated votes, while the authorization itself still faces periodic re-approval.

---

## Q3 — Mandate Selection

§17-18 (distribution and reserves): before any dividend can be paid, "5% of the annual profit
must be allocated to the statutory retained earnings," any loss carryover "must be eliminated
before allocation to the reserve," and the capital reserve can only be returned to shareholders
once retained reserves "exceed half of the registered share capital" (a lower 20% threshold
applies to pure holding companies). This is a fully specified distribution waterfall: mandatory
retention → loss recovery → threshold-gated capital return → discretionary dividend, in that
order. Compare to the general partnership's looser "may not withdraw profits before their share
has been reconstituted" (`switzerland_general_partnership_2023.md` Q4) — the AG's version adds a
fixed mandatory retention percentage and an explicit capital-return threshold on top of loss
recovery. Use this as a template for a Powers treasury-distribution mandate chain: a distribution
mandate's `needFulfilled` dependencies should check, in sequence, (1) a mandatory reserve
contribution has been made for the period, (2) any tracked deficit is at zero, and only then (3)
the discretionary distribution vote can proceed — a single-step distribution vote skips checks
that a multi-step chain enforces automatically.

---

## Q7 — Accountability and Monitoring

§14 (the auditor as third organ) and the audit-scaling thresholds already extracted in
`switzerland_legal_forms_overview_2023.md` Q7 apply identically here — see that file for the
proportional-oversight pattern. This entry adds one point specific to the AG: the general
meeting's supervisory powers over the board (appointment, bylaw approval, annual report approval)
are exercised only periodically (annually, or on capital/structural changes), while the *auditor*
provides continuous, independent monitoring between those periodic votes. This is a two-cadence
accountability design: infrequent, high-authority votes (electing/removing the board) combined
with a continuously-active, narrower-scope monitoring function (the auditor) that doesn't itself
hold governance power but feeds information into the periodic votes. For Powers, this maps to
pairing an infrequent `PeerSelect`/`RevokeAccountsRoleId` election cycle for a powerful role with
a separate, narrowly-scoped, always-on monitoring mandate (a role with `StatementOfIntent`-only
authority, no execution power) that surfaces information for the next election cycle rather than
acting on it directly.

---

## What to skip

The company-naming, registration procedure, tax comparison, and establishment-cost sections
duplicate content already covered in `switzerland_legal_forms_overview_2023.md`. The detailed
mechanics of contributions in kind (§12) and foreign-currency share capital rules (§11) are
administrative/accounting specifics with no governance-design content.

---

## Mandate implications

- Distinguish mandates that define a role's core, non-outsourceable purpose (require a
  constitutional-tier change, e.g. `MandatePackage`, to reassign) from mandates that are merely
  convenient current delegations of representation/execution authority (reassignable via ordinary
  `Adopt_Mandates`).
- For desirable-but-non-blocking governance goals, implement a disclosure-triggered
  `StatementOfIntent` mandate on non-compliance rather than either ignoring the goal or
  hard-blocking on it.
- For routine-but-variable treasury/capital actions, consider a time-boxed, bounded-range
  authorization (re-adopted periodically) instead of either a permanent cap or a fresh vote per
  action.
- Structure treasury-distribution mandates as a sequential `needFulfilled` chain (mandatory
  reserve contribution → loss-recovery check → threshold-gated capital return → discretionary
  distribution) rather than a single-step distribution vote.
- Pair infrequent, high-authority election/removal mandates with a separate, narrowly-scoped,
  always-on monitoring mandate that surfaces information rather than acting on it directly.
