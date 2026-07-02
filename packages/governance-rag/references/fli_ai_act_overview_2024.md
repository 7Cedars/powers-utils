# Future of Life Institute 2024 — High-Level Summary of the EU AI Act

**Citation:** Future of Life Institute. 2024. "High-Level Summary of the AI Act." *EU AI Act
Explorer*, artificialintelligenceact.eu, 30 May 2024.
**Analytical level:** Structural + Dynamic
**Most relevant design decisions:** Q1, Q3, Q6, Q7

---

## Q1 — Role Structure

"The majority of obligations fall on providers (developers)... Deployers... have some
obligations, though less than providers." The Act splits accountability across an AI system's
lifecycle by *function*, not by organisation: whoever designs/configures the system (provider)
carries the heavier documentation, risk-management, and design-for-oversight obligations, while
whoever operates it in a live context (deployer) carries lighter, operational obligations. This
maps directly onto a distinction Powers constitutions should make explicit but often don't: the
party who *authors or configures* a mandate (e.g., builds a `MandatePackage` or a
`BespokeAction_Advanced` config for an agent-held role) is a different accountability locus than
the party who later *operates* that role day-to-day. When a governance template is built by one
team and deployed/operated by another organisation, allocate responsibility explicitly — the
authoring party should bear obligations analogous to the Act's "provider" (documentation of what
the mandate does and doesn't do, why it was configured this way), and the operating party
obligations analogous to "deployer" (day-to-day oversight, monitoring for misuse within the given
configuration).

---

## Q3 — Mandate Selection

"Four-point summary": AI systems are classified into unacceptable risk (prohibited outright),
high risk (heavily regulated with lifecycle obligations), limited risk (light transparency-only
obligations), and minimal risk (unregulated). This is a clean four-tier mandate-selection
framework, independently corroborating the tiered-trust-model principle already drawn from
`erc_8004_2025.md` (Q3): oversight intensity should scale with risk tier, not be applied
uniformly. The Act adds a tier that ERC-8004 does not have — **prohibited outright** — which is
missing from the existing Powers mandate catalogue's framing: some actions should not be
reachable by *any* configuration of `allowedRole`/`votingPeriod`, no matter how strict, because no
amount of governance process makes them acceptable (the Act's examples: social scoring,
manipulative/subliminal techniques). When drafting a constitution, identify this "unacceptable"
tier explicitly and enforce it by *omission* (no mandate exists that could ever produce the
effect) rather than by a votable restriction, since anything gated only by a vote can in principle
be voted away.

"Requirements for providers of high-risk AI systems" (Art. 8-17): high-risk systems must have "a
risk management system throughout the... lifecycle," "record-keeping to enable it to
automatically record events relevant for identifying... risks," and be "design[ed]... to allow
deployers to implement human oversight." The third point is the sharpest and most transferable:
oversight capability must be a *design property of the execution mechanism itself*, not merely a
downstream accountability chain that fires after the fact. For a Powers mandate that an AI-agent
role can trigger with high-stakes effects, this means building an intervention point *into the
execution path* — a mandatory `timelock` window paired with a `PauseMandates` instance scoped to
that specific flow position — rather than relying solely on `RevokeAccountsRoleId` after damage is
already done. Reactive accountability and designed-in interruptibility are different design
requirements; high-stakes agent-triggered mandates need both.

---

## Q6 — Adaptive Capacity and Reform

"Classification rules for high-risk AI systems" (Art. 6): the Commission can add, modify, or
delete high-risk classification conditions "through delegated acts if there is concrete evidence"
that a use case does or doesn't pose significant risk — an explicit, bounded reform mechanism for
adjusting the regulation's own scope over time without a full legislative rewrite. Separately,
the systemic-risk threshold for general-purpose AI models is an objective, checkable number
(10^25 FLOPS of training compute), but is paired with *two* independent override paths: a
provider "may present arguments that, despite meeting the criteria, their model does not present
systemic risks," and conversely the Commission "may decide on its own, or via a qualified alert
from the scientific panel of independent experts, that a model has high impact capabilities,"
classifying it as systemic even without crossing the numeric threshold. Two actionable patterns
for Powers reform design: (1) keep a narrow, well-scoped `Adopt_Mandates`/`MandatePackage` path
for adjusting classification-style thresholds (e.g., what counts as a "high-value" treasury
mandate requiring extra oversight) without requiring a full constitutional rewrite; (2) pair any
hard-coded numeric threshold (`needFulfilled` gates keyed to a `value` cutoff, a quorum
percentage) with *both* an appeal path (the affected role-holder can contest an automatic
classification) and a discretionary escalation path (governance can vote to apply high-oversight
treatment to a specific action even when it falls under the numeric threshold) — a pure
hard-coded cutoff with no override in either direction will eventually misclassify an edge case in
both directions.

---

## Q7 — Accountability and Monitoring

"Governance" (Chapter VI): "Downstream providers can lodge a complaint regarding the upstream
provider's infringement to the AI Office" — a complaint/redress channel available to a party who
is affected by an AI system's operation but has no formal vote or role in governing it. This is a
gap not addressed by any other source in this library, which otherwise focus on accountability
*among role-holders*. For Powers constitutions where an agent-held role can affect non-role-holder
third parties (e.g., a governance-controlled service whose users are not themselves members), add
an explicit, low-`allowedRole`-bar `StatementOfIntent` mandate for recording third-party
complaints, feeding into the same accountability chain that role-holder-originated
`StatementOfIntent` reports feed into (see `erc_8004_2025.md` Q4/Q7) — do not assume that only
role-holders will ever need a channel to flag misbehaviour.

"Requirements for providers" (data governance, Art. 8-17): training/validation/testing datasets
must be "relevant, sufficiently representative and... free of errors and complete according to
the intended purpose" — an input-quality obligation distinct from output monitoring. For an
AI-agent role in Powers, this suggests an accountability dimension not covered by feedback/
validation registries (`erc_8004_2025.md`): auditing what the agent was configured or trained on
in the first place, not just what it subsequently does. This has no direct on-chain mandate
equivalent but is worth flagging as a documentation requirement alongside the mandate
configuration when an agent role is first granted (`PresetActions` setup step), analogous to how
setup mandates already document *why* a role exists.

---

## What to skip

The detailed prohibited-use-case enumeration (Art. 5: social scoring, biometric categorisation,
emotion inference, remote biometric identification exceptions) and the full Annex III sectoral
list (education, employment, law enforcement, migration, justice) are domain-specific legal
classifications with no generalisable mandate-design content beyond the "some things should be
categorically prohibited" principle already extracted above. The specific compliance-deadline
timeline (6/12/24/36 months) and the codes-of-practice drafting process (Art. 56) are EU
regulatory-process mechanics, not governance-design patterns.

---

## Mandate implications

- Enforce a "categorically prohibited" tier by omission (no mandate configuration can produce the
  effect) rather than by a votable restriction, for any action a constitution should never permit
  regardless of process — a purely vote-gated restriction can always in principle be voted away.
- For high-stakes agent-triggered mandates, design in an interruption point (`timelock` +
  scoped `PauseMandates`) as part of the execution path itself, not only a downstream
  accountability chain that fires after the action has already taken effect.
- Pair hard-coded numeric classification thresholds (`value` cutoffs, quorum percentages
  triggering extra oversight) with both an appeal path for the affected role-holder and a
  discretionary escalation path for governance to apply stricter treatment to an edge case that
  the threshold missed.
- Provide a low-barrier complaint-recording mandate for non-role-holder third parties affected by
  agent-triggered actions, feeding into the same accountability chain used for role-holder
  reports — accountability channels should not assume the affected party always has a vote.
- When authoring a governance template (`MandatePackage`) intended for use by a different
  operating organisation, document the authoring party's design obligations separately from the
  operating party's day-to-day oversight obligations.
