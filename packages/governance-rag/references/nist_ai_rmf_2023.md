# NIST 2023 — AI Risk Management Framework (AI RMF 1.0)

**Citation:** National Institute of Standards and Technology. 2023. *Artificial Intelligence Risk
Management Framework (AI RMF 1.0).* NIST AI 100-1. https://doi.org/10.6028/NIST.AI.100-1.
**Analytical level:** Structural + Dynamic
**Most relevant design decisions:** Q1, Q3, Q6, Q7

---

## Q1 — Role Structure

GOVERN 3.2: "Policies and procedures are in place to define and differentiate roles and
responsibilities for human-AI configurations and oversight of AI systems." The framework treats
"the AI system's role" and "the human oversight role" as two roles that must be *separately*
defined, not one role with an implicit human backstop. In Powers terms: when an AI agent holds a
governance role, the human-oversight function should be modeled as its own distinct role with its
own `allowedRole`-gated mandates (a veto/pause capability, a review mandate), not assumed to exist
informally because "someone is presumably watching the agent." If a constitution cannot point to
a specific mandate that a specific human-eligible role can invoke to intervene, the oversight
function does not actually exist regardless of stated intent.

GOVERN 2.1: "Roles and responsibilities and lines of communication... are documented and are
clear to individuals and teams throughout the organization." Applied to a constitution: every
mandate's `allowedRole` should be traceable to a documented rationale for why that role — not just
which role — holds it, and the chain of accountability for a given action (who proposed, who
could have vetoed, who executed) should be reconstructable from the mandate structure alone
without needing external documentation. This is a completeness check distinct from the Ostrom
design-principle checklist already in the source library: it asks whether the role structure is
*legible* to an outside reviewer, not just whether it is functionally complete.

---

## Q3 — Mandate Selection

GOVERN 6: "Policies and procedures are in place to address AI risks and benefits arising from
third-party software and data and other supply chain issues," including "contingency processes...
to handle failures or incidents in third-party data or AI systems deemed to be high-risk." Any
Powers mandate that depends on an external contract or oracle (`ExternalAction_Simple`,
`CheckExternalActionState`, `ChainlinkFunctions_Open`, a validation registry as in
`erc_8004_2025.md`) has effectively taken on a third-party dependency in the NIST RMF sense. A
mandate design that only specifies the "happy path" (external check passes, execution proceeds)
without a contingency path for "the external dependency is unavailable, compromised, or
persistently failing" leaves the constitution with no governed response to an external-dependency
failure — it will either silently stall (a mandate that can never satisfy `needFulfilled`) or
require an ungoverned emergency workaround. Pair every external-dependency mandate with an
explicit contingency mandate (a fallback path reachable via `Adopt_Mandates`, or a
`PauseMandates`-scoped bypass) decided in advance, not improvised after the dependency fails.

---

## Q6 — Adaptive Capacity and Reform

GOVERN 1.7: "Processes and procedures are in place for decommissioning and phasing out AI systems
safely and in a manner that does not increase risks or decrease the organization's
trustworthiness." This is a distinct requirement from ordinary role revocation
(`RevokeAccountsRoleId`) or renunciation (`RenounceRole`): decommissioning an AI-agent role
requires actively unwinding what the role was doing — in-flight actions, dependent mandates that
assumed the role would keep acting, any external contracts the agent was authorized to call — not
merely cutting off future access. A Powers constitution granting an agent a role with ongoing
responsibilities (e.g., a recurring `SafeAllowance_PresetTransfer` payment, a periodic
`BespokeAction_Simple` call) should design the decommissioning path *at the same time* as the
role is created: what happens to pending obligations, what other mandates have a
`needFulfilled`/`needNotFulfilled` dependency on this role's continued existence, and who is
responsible for confirming the wind-down is complete. Treat "how does this role end safely" as a
first-class design question alongside "how does this role start."

GOVERN 5.1–5.2: external feedback must not just be collected but "adjudicated" and then "regularly
incorporate[d]... into system design and implementation" — a closed loop from complaint to
decision to reform, on a defined cadence, rather than an open-ended inbox. This sharpens the
complaint-channel gap already identified in `fli_ai_act_overview_2024.md` (Q7): recording
third-party complaints via a low-barrier `StatementOfIntent` mandate is necessary but not
sufficient — pair it with a scheduled review mandate (a periodic `BespokeAction_Simple` or
governance-triggered `Adopt_Mandates` review point) that forces the collected feedback to actually
be considered for reform, rather than accumulating unreviewed.

---

## Q7 — Accountability and Monitoring

§3 (trustworthiness characteristics, general framing): "trustworthiness is... only as strong as
its weakest characteristic," and the seven characteristics (valid/reliable, safe, secure/
resilient, accountable/transparent, explainable/interpretable, privacy-enhanced, fair) actively
trade off against one another — optimizing one in isolation (e.g., maximal transparency) can
degrade another (e.g., privacy). Applied to accountability-chain design: a chain that logs *only*
whether a rule was satisfied (a binary pass/fail, satisfying "accountable") without logging *why*
a decision was made (satisfying "explainable") is a weaker accountability mechanism than one that
captures both, even though both technically produce an on-chain record. Prefer `StatementOfIntent`
configurations whose `inputParams` capture a stated rationale, not just a vote tally — a
constitution that can show *what happened* but not *why* has a harder time distinguishing a
good-faith judgment call from a violation after the fact.

§3.4 (Accountable and Transparent): "Meaningful transparency provides access to appropriate
levels of information based on the stage of the AI lifecycle and tailored to the role or knowledge
of AI actors." Not all audiences need the same information at the same time: a role-holder voting
on a proposal needs different information than a third party later auditing why a decision was
made. Powers' on-chain records are uniformly public by default, which satisfies transparency but
not necessarily this framework's stronger notion of *tailored* transparency — consider whether a
constitution needs a documentation layer (off-chain, referenced from `StatementOfIntent`
descriptions) that explains decisions in role-appropriate terms, since raw on-chain calldata is
legible to auditors but not to affected non-technical third parties.

---

## What to skip

The MAP, MEASURE, and MANAGE functions (the bulk of the document past the material extracted
above) describe internal AI-development-team processes — model testing, evaluation methodologies
(TEVV), bias measurement techniques, and risk-tracking documentation practices used *before* an AI
system is deployed. These are software-engineering and ML-evaluation practices for the team
building an AI system, not governance-structure design decisions for the Powers constitution that
later grants that system a role; they matter to whoever configures an agent's underlying model but
have no mandate-level analogue. The detailed sub-definitions of validity, robustness, and fairness
(§3.1, §3.7) are useful vocabulary for describing an AI system's technical quality but do not by
themselves change a mandate or parameter choice.

---

## Mandate implications

- Model human oversight of an AI-agent-held role as its own distinct role with its own
  `allowedRole`-gated intervention mandate (veto, pause, review) — do not treat oversight as
  implicit just because a human role technically exists elsewhere in the constitution.
- Pair every mandate with an external-contract/oracle dependency with an explicit contingency
  mandate for when that dependency fails or becomes unavailable, decided at design time rather
  than improvised during an incident.
- Design the decommissioning path for an agent-held role (unwinding in-flight obligations,
  dependent mandates, external authorizations) at the same time the role is created, not only
  when revocation becomes necessary.
- Pair any low-barrier complaint-recording mandate with a scheduled review mandate that forces
  accumulated feedback to be actually considered for reform on a defined cadence.
- Prefer accountability mandate configurations that capture stated rationale (`inputParams`
  carrying a "why"), not just a binary outcome, so the record can distinguish good-faith judgment
  calls from violations after the fact.
