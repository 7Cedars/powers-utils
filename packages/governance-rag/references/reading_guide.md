# Reference Reading Guide — Powers Protocol Governance Design

This file is the index layer. Use it to decide which source to consult for a given design
question. Each entry summarises what a source contributes and which design decisions it covers
most directly. Full guides are in the individual source files listed below.

---

## Source files

| File | Citation | Analytical level |
|---|---|---|
| [`podger_2020.md`](podger_2020.md) | Podger, Su, Wanna & Chan (eds.), 2020. *Designing Governance Structures for Performance and Accountability.* ANU Press. | Structural + Parametric |
| [`carlisle_gruby_2019.md`](carlisle_gruby_2019.md) | Carlisle & Gruby, 2019. "Polycentric Systems of Governance: A Theoretical Model for the Commons." *Policy Studies Journal* 47(4): 927–952. | Structural + Dynamic |
| [`hynes_oecd_2020.md`](hynes_oecd_2020.md) | Hynes, Lees & Müller (eds.), 2020. *Systemic Thinking for Policy Making.* OECD/IIASA. | Dynamic |
| [`ostrom_2009.md`](ostrom_2009.md) | Ostrom, Elinor. 2010. "Beyond Markets and States: Polycentric Governance of Complex Economic Systems." Nobel Prize Lecture, Dec 8, 2009. *American Economic Review* 100(3): 641–672. | Structural + Dynamic |
| [`ostrom_2011.md`](ostrom_2011.md) | Ostrom, Elinor. 2011. "Background on the Institutional Analysis and Development Framework." *Policy Studies Journal* 39(1): 7–27. | Structural + Parametric |
| [`ostrom_2005.md`](ostrom_2005.md) | Ostrom, Elinor. 2005. *Understanding Institutional Diversity.* Princeton University Press. | Structural + Parametric + Dynamic |

### UK Community Interest Company (CIC) sources

A family of real-world legal-governance templates and regulatory documents. Treated as a single
analytical "tier" below (cited as Quaternary) because they post-date and supplement the academic
core sources rather than replacing them — they contribute concrete, statutorily-validated
calibration points and a genuinely novel external-oversight mechanism not found in the academic
sources.

| File | Citation | Analytical level |
|---|---|---|
| [`cic_model_articles_guarantee_small.md`](cic_model_articles_guarantee_small.md) | UK CIC Model Articles of Association, Limited by Guarantee, Small Membership, Companies House template. | Structural + Parametric |
| [`cic_model_articles_guarantee_large.md`](cic_model_articles_guarantee_large.md) | UK CIC Model Articles of Association, Limited by Guarantee, Large Membership, Companies House template. | Structural + Parametric |
| [`cic_model_articles_shares_sch2_small.md`](cic_model_articles_shares_sch2_small.md) | UK CIC Model Articles of Association, Limited by Shares (Schedule 2 — no private distribution), Small Membership, Companies House template. | Structural + Parametric |
| [`cic_model_articles_shares_sch2_large.md`](cic_model_articles_shares_sch2_large.md) | UK CIC Model Articles of Association, Limited by Shares (Schedule 2 — no private distribution), Large Membership, Companies House template. | Structural + Parametric |
| [`cic_model_articles_shares_sch3_small.md`](cic_model_articles_shares_sch3_small.md) | UK CIC Model Articles of Association, Limited by Shares (Schedule 3 — capped distribution permitted), Small Membership, Companies House template. | Structural + Parametric |
| [`cic_model_articles_shares_sch3_large.md`](cic_model_articles_shares_sch3_large.md) | UK CIC Model Articles of Association, Limited by Shares (Schedule 3 — capped distribution permitted), Large Membership, Companies House template. | Structural + Parametric |
| [`cic_memorandum_guarantee.md`](cic_memorandum_guarantee.md) | UK CIC Model Memorandum of Association, Limited by Guarantee, Companies Act 2006 template. | Structural (minimal) |
| [`cic_memorandum_shares.md`](cic_memorandum_shares.md) | UK CIC Model Memorandum of Association, Limited by Shares, Companies Act 2006 template. | Structural (minimal) |
| [`cic_regulations_2005.md`](cic_regulations_2005.md) | The Community Interest Company Regulations 2005, SI 2005/1788. | Structural + Parametric + Dynamic |
| [`cic_guidance_govuk.md`](cic_guidance_govuk.md) | UK Dept for Business and Trade / CIC Regulator, 2025. *Community Interest Companies Guidance.* GOV.UK. | Structural + Parametric + Dynamic |
| [`cic_model_articles_intro_govuk.md`](cic_model_articles_intro_govuk.md) | UK Dept for Business and Trade / CIC Regulator, 2025. *CIC model Articles of Association: introduction.* GOV.UK. | Structural |
| [`cic_plinth_guide.md`](cic_plinth_guide.md) | Plinth Team, 2026. *What is a Community Interest Company (CIC)? Complete Guide.* | Structural (comparative framing) |
| [`cic_wikipedia.md`](cic_wikipedia.md) | Wikipedia contributors. "Community interest company." *Wikipedia.* | Structural |
| [`cic_annual_report_2024_2025.md`](cic_annual_report_2024_2025.md) | Office of the Regulator of Community Interest Companies. *Annual Report 2024 to 2025.* | Dynamic (empirical) |

### AI agent governance and standards sources (Quinary)

Technical standards and policy frameworks for governing AI agents as autonomous or semi-autonomous
actors. Treated as a distinct "Quinary" tier because they address a structurally new problem the
academic core and CIC sources do not: how to grant governance authority (a role, a mandate) to an
actor whose internal reasoning is not fully auditable and whose behaviour can be adversarially
manipulated. Cross-reference these sources whenever a constitution grants any `allowedRole` to an
AI agent, not only for AI-specific governance questions.

| File | Citation | Analytical level |
|---|---|---|
| [`erc_8004_2025.md`](erc_8004_2025.md) | De Rossi, Crapis, Ellis & Reppel, 2025. "ERC-8004: Trustless Agents." *Ethereum Improvement Proposals*, no. 8004 (Draft). | Structural + Dynamic |
| [`erc_4337_2021.md`](erc_4337_2021.md) | Buterin et al., 2021. "ERC-4337: Account Abstraction Using Alt Mempool." *Ethereum Improvement Proposals*, no. 4337. | Structural + Parametric |
| [`erc_6900_2023.md`](erc_6900_2023.md) | Egyed et al., 2023. "ERC-6900: Modular Smart Contract Accounts." *Ethereum Improvement Proposals*, no. 6900 (Draft). | Structural |
| [`fli_ai_act_overview_2024.md`](fli_ai_act_overview_2024.md) | Future of Life Institute, 2024. "High-Level Summary of the AI Act." artificialintelligenceact.eu. | Structural + Dynamic |
| [`nist_ai_rmf_2023.md`](nist_ai_rmf_2023.md) | NIST, 2023. *Artificial Intelligence Risk Management Framework (AI RMF 1.0).* NIST AI 100-1. | Structural + Dynamic |
| [`nist_ai_600-1_2024.md`](nist_ai_600-1_2024.md) | NIST, 2024. *AI RMF: Generative Artificial Intelligence Profile.* NIST AI 600-1. | Structural + Dynamic |

### Organisational resilience and sector-practice sources (Senary)

Empirical studies from outside governance-theory proper — social movement/repression research and
cultural-sector management research — mined for organisational-design lessons under adversarial
pressure or operational crisis. Fit with the Q1-Q7 framework is markedly weaker and more indirect
than the other source families; several of these entries are thin, single-point contributions
rather than broad frameworks (see each file's "Note on fit").

| File | Citation | Analytical level |
|---|---|---|
| [`honari_2018.md`](honari_2018.md) | Honari, A., 2018. "From 'The Effect of Repression' Toward 'The Response to Repression.'" *Current Sociology Review* 66(6): 950–973. | Structural + Dynamic |
| [`durrer_gilmore_stevenson_2019.md`](durrer_gilmore_stevenson_2019.md) | Durrer, Gilmore & Stevenson, 2019. "Arts Councils, Policy-Making and 'The Local.'" *Cultural Trends* 28(4): 317–331. | Structural + Dynamic |
| [`meier_pena_nah_2025.md`](meier_pena_nah_2025.md) | Meier, Peña & Nah, 2025. "From Collusion to Autonomy: Patterns of Hybrid Repression and Human Rights Activism." *Government and Opposition* 60: 773–798. | Dynamic (weak fit) |
| [`ellefsen_jamte_2023.md`](ellefsen_jamte_2023.md) | Ellefsen & Jämte, 2023. "The Causes, Content and Consequences of Repression." *Social Movement Studies* 22(4): 567–582. | Dynamic (weak fit) |
| [`bennett_kottasz_yuan_2025.md`](bennett_kottasz_yuan_2025.md) | Bennett, Kottasz & Yuan, 2025. "The Mediating Role of Digital Innovation Capability..." *Cogent Business & Management* 12(1). | Dynamic (very weak fit) |

**Removed as not actionable:** a 2026 crypto-philanthropy fundraising report (pure donation-volume
marketing statistics, no governance content) was reviewed and its source PDF and reference guide
were removed from the library rather than kept as dead weight.

### Comparative company law sources (Septenary)

Statutory/regulatory company-law material from Switzerland, the UAE, the UK (general, non-CIC),
and the US (Delaware), gathered to compare how different real-world legal regimes solve the same
governance-design problems as the academic core and CIC sources, independent of blockchain or
DAO context. `delaware_dgcl_title8.md` (the Delaware General Corporation Law) is the single
richest source in this entire library — treat it as a first-stop reference alongside the academic
core for Q1, Q2, Q4, and Q7. The UAE and introductory UK/Delaware entries are administrative-
procedure pages with thin governance content (see each file's "Note on fit").

| File | Citation | Analytical level |
|---|---|---|
| [`delaware_dgcl_title8.md`](delaware_dgcl_title8.md) | State of Delaware. *Delaware Code Title 8 — Corporations* (General Corporation Law). | Structural + Parametric + Dynamic |
| [`switzerland_limited_company_2023.md`](switzerland_limited_company_2023.md) | SECO, Swiss SME Portal, 2023. "Legal Form: The Limited Company" (Art. 620-763 CO). | Structural + Parametric |
| [`switzerland_llc_2023.md`](switzerland_llc_2023.md) | SECO, Swiss SME Portal, 2023. "Legal Form: The Limited Liability Company (GmbH/Sàrl)." | Structural + Parametric |
| [`switzerland_general_partnership_2023.md`](switzerland_general_partnership_2023.md) | SECO, Swiss SME Portal, 2023. "Legal Form: The General Partnership" (Art. 552-593 CO). | Structural + Parametric |
| [`switzerland_limited_partnership_2023.md`](switzerland_limited_partnership_2023.md) | SECO, Swiss SME Portal, 2023. "Legal Form: The Limited Partnership" (Art. 594-619 CO). | Structural |
| [`switzerland_legal_forms_overview_2023.md`](switzerland_legal_forms_overview_2023.md) | SECO, Swiss SME Portal, 2023. "Comparison of Legal Forms." | Structural |
| [`uk_model_articles_public_2013.md`](uk_model_articles_public_2013.md) | Companies House. *Model Articles for Public Companies*, Sch. 3 (post-2013). | Structural + Parametric |
| [`uk_model_articles_private_shares_2013.md`](uk_model_articles_private_shares_2013.md) | Companies House. *Model Articles for Private Companies Limited by Shares*, Sch. 1 (post-2013). | Structural + Parametric |
| [`uk_model_articles_private_guarantee_2013.md`](uk_model_articles_private_guarantee_2013.md) | Companies House. *Model Articles for Private Companies Limited by Guarantee*, Sch. 2 (post-2013). | Structural |
| [`uk_companies_house_guidance_overview.md`](uk_companies_house_guidance_overview.md) | Companies House. "Guidance for Limited Companies, Partnerships and Other Company Types." | Structural + Dynamic |
| [`uk_model_articles_overview_gov_uk.md`](uk_model_articles_overview_gov_uk.md) | Companies House. "Model Articles of Association for Limited Companies" (overview). | Structural (thin) |
| [`delaware_business_structure_table_2020.md`](delaware_business_structure_table_2020.md) | Delaware Division of Revenue, 2020. *Legal Business Structures Table.* | Structural (thin) |
| [`delaware_how_to_form_business_entity.md`](delaware_how_to_form_business_entity.md) | Delaware Division of Corporations. "How to Form a New Business Entity." | Structural (very weak) |
| [`uae_free_zones_establishing_business.md`](uae_free_zones_establishing_business.md) | UAE Ministry of Economy & Tourism. "Establishing Business in Free Zones." | Structural (weak) |
| [`uae_licensing_advantages_mainland_vs_freezone.md`](uae_licensing_advantages_mainland_vs_freezone.md) | UAE Ministry of Economy & Tourism. "The Advantages of Licensing..." | Structural (weak) |

**Removed:** a UAE tax/compliance blog source whose PDF extraction failed (captured only page
navigation, no article content) and the 39-page HMRC Cryptoassets Manual (individual UK tax
compliance guidance — no governance content at any Q1-Q7 dimension) were both reviewed and
removed, source PDFs and reference guides, rather than kept as dead weight in the library.

---

## Which source to read for which design question

### Q1 — Role structure and separation of powers

**Primary:** `podger_2020.md`
The book provides the most actionable typology for role design: a spectrum from high-political-
control (departments) to high-independence (judicial bodies), with each point on the spectrum
mapping to specific mandate type and appointment mechanism choices. Use it when the core question
is "how much autonomy should this role have, and what mandate type follows from that?"

**Secondary:** `carlisle_gruby_2019.md`
Adds the de facto vs. formal autonomy test: after drafting roles, use this source to verify that
roles with different labels genuinely have different authority scopes and mandate sets, not just
different names.

**Tertiary:** `ostrom_2011.md`
Adds the three-tier IAD structure (operational / collective-choice / constitutional) as a
completeness check: confirm that mandates exist at all three tiers and that the seven rule
types (boundary, position, scope, choice, aggregation, information, payoff) are each addressed
by at least one mandate or parameter. Use it when auditing a completed constitution for gaps.

**Tertiary:** `ostrom_2009.md`
Adds the polycentric independence test: formal independence (different labels) + functional
interdependence (`needFulfilled` chains) must both be present for a structure to be genuinely
polycentric. Also provides the three-mechanism framework for why smaller, specialised roles
outperform large monolithic ones. Use it when choosing between a single broad role and
multiple specialised roles.

**Quaternary:** `cic_model_articles_guarantee_large.md` (representative of the six model-articles
files — see also the small-membership and shares variants)
Adds real statutory precedent for a layered delegation chain (executive role → revocable
committee-equivalent grants) and a dual-track removal design: peer-triggered automatic removal
for disengagement (three consecutive absences) versus member-voted removal for cause with a
mandatory hearing step. Use it when designing `Adopt_Mandates`/`Revoke_Mandates` delegation chains
or calibrating a removal-track split for an executive role.

**Quaternary:** `cic_regulations_2005.md`
Adds the one genuinely external-to-the-organisation oversight role in the library: the CIC
Regulator's power to appoint, pay, and remove a manager over a CIC's property and affairs, plus a
hard cap on how much board control non-members may hold (never a majority). Use it when a
constitution needs an external/funder oversight role with no Powers-native equivalent.

**Quaternary:** `cic_wikipedia.md`
Adds the CIC form's core role-design insight: "can be compensated" and "loses governance control"
are independently decidable, not bundled by default (contra the charity model). Use it when
assigning `allowedRole` to paid operator roles versus deliberation/oversight roles.

**Quaternary:** `cic_model_articles_intro_govuk.md`
Adds the rationale for collapsing a member role and an executive role into one `allowedRole` when
the two sets are coextensive, versus splitting them once membership exceeds the executive set. Use
it as a first-pass check before defining two separate roles: ask whether the stakeholder set and
the decision-making set are actually identical.

**Tertiary:** `ostrom_2005.md`
Adds the ADICO grammar (Attributes-Deontic-Aim-Conditions-OrElse) as a drafting checklist mapping
directly onto mandate design (`allowedRole`/mandate type/target/`votingPeriod`/accountability
mandate), and position-rule cardinality bounds (min/max holders) as the theoretical basis for
`numberToSelect` and `quorum`. Use it when auditing whether a drafted mandate has a real
enforcement path (an OR ELSE) or is a norm dressed up as a rule.

**Quinary:** `erc_8004_2025.md`
Adds the principle that oversight intensity should scale with the *value at risk* of what a role
can trigger, not with role-holder count, plus the warning that an AI agent's on-chain identity
does not guarantee behavioural continuity the way a human role-holder's does. Use it when scoping
`allowedRole`/`target`/`value` bounds for any role held by an AI agent.

**Quinary:** `erc_6900_2023.md`
Adds a field-tested warning that broad-scope permission grants (`allowedRole` = PUBLIC, wide
`target`/`value` ranges) carry root-access-equivalent risk regardless of how narrowly the
mandate's stated purpose sounds. Use it when reviewing any mandate with an unusually wide scope.

**Quinary:** `fli_ai_act_overview_2024.md`
Adds the provider/deployer accountability split: the party who authors or configures a mandate
carries different obligations than the party who later operates it. Use it when a governance
template is built by one team and deployed/operated by another organisation.

**Quinary:** `nist_ai_rmf_2023.md`
Adds the requirement to model human oversight of an AI-agent-held role as its own distinct role
with its own intervention mandate, rather than assuming oversight exists implicitly. Use it
whenever a constitution grants an AI agent a governance role.

**Senary:** `honari_2018.md`
Adds independent, repression-resistance-driven evidence for distributing authority across many
small overlapping roles rather than a few visible, powerful ones — converging with Ostrom's
polycentricity argument via a different mechanism (target-hardening vs. free-rider prevention).
Use it as corroborating evidence when justifying a polycentric role structure to a designer
weighing simplicity against resilience.

**Septenary:** `delaware_dgcl_title8.md`
Adds a precise, enumerated non-delegable-powers model (§141(c)): a board committee may exercise
all board authority except approving matters that legally require full-membership approval or
amending bylaws — map onto a rule that constitutionally-gated mandates can never be reassigned to
a narrower `allowedRole` via ordinary reform, only via a `MandatePackage`-level change. Also adds
that a member-set rule (a bylaw stockholders adopted) can be locked against override by a body
(the board) that would normally have authority to change similar rules (§216) — protection
attaches to *how* a rule was adopted, not to a fixed category — and that differential voting
weight among role-holders is legitimate when fixed at the *selection* stage (§141(d)), consistent
with Powers reserving token-weighting to `DelegateTokenSelect` rather than ongoing votes.

**Septenary:** `switzerland_limited_company_2023.md` / `switzerland_limited_partnership_2023.md`
Add a two-tier delegability model (core/non-outsourceable board powers vs. freely delegable
representation authority) and a risk/control coupling principle (liability exposure and
operational authority should scale together — a role with capped/no exposure warrants a narrower
`allowedRole` on operational mandates). See `delaware_dgcl_title8.md` above for a more precise,
enumerated version of the delegability distinction.

**Septenary:** `switzerland_general_partnership_2023.md`
Adds a default-management inversion warning: unlike Powers (nothing possible until a mandate
grants it), traditional company law defaults to full participatory authority for all role-holders
until narrowed — flag this explicitly when onboarding a designer from a company-law background.

**Septenary:** `uk_model_articles_private_shares_2013.md` / `uk_model_articles_public_2013.md`
Add a delegation-chain-stays-revocable pattern, a sole-holder/degenerate-case simplification
pattern, a quorum-collapse residual-mandate pattern (a role that falls below its own quorum
retains a narrow self-repair mandate rather than deadlocking permanently), and a standby/backup-
role pattern (a role can designate a backup to act in its absence, with the backup's actions
attributed to its own address, not silently to the primary).

**Septenary:** `uk_companies_house_guidance_overview.md`
Adds a live regulatory precedent for identity-verification gates on powerful roles (`ZKPassport_
Check`-equivalent) and a two-tier delegated-verification pattern (an authorized intermediary
performs verification on a central authority's behalf, but is itself individually accountable).

**Septenary:** `delaware_how_to_form_business_entity.md`
Adds the registered-agent requirement as a thin precedent for a stable, discoverable point-of-
contact role that persists across internal role turnover, for constitutions interacting with
off-chain counterparties.

---

### Q2 — Voting parameters

**Primary:** `ostrom_2009.md`
The six microsituational cooperation variables (Section 7C) are the most directly actionable
source on voting design: communication channel (`votingPeriod > 0`), reputation visibility
(on-chain record), marginal per-capita return (role size), exit capability (`SelfSelect`),
time horizon (`votingPeriod` length), and agreed sanctioning (graduated chain design). Use it
when calibrating `votingPeriod` and when choosing between small specialised roles and large
member roles for high-stakes decisions.

**Secondary:** `ostrom_2011.md`
Adds the aggregation rule framework: majority, supermajority, and unanimity rules should be
calibrated to the expected active membership size, not set as absolute values. Also introduces
the cross-type interaction: changing `allowedRole` (boundary rule) may require adjusting
`votingPeriod` (aggregation rule). Use it when a role membership change prompts a review of
voting parameters.

**Quaternary:** `cic_model_articles_guarantee_large.md` (consistent across all six model-articles
files)
Adds concrete, externally-validated calibration anchors: a minimum quorum floor of 2; a hybrid
quorum formula ("2 persons or 10% of total membership, whichever is greater") for roles of
variable size; an automatic quorum-waiver fallback on a failed-quorum adjournment, to prevent
permanent deadlock; a 75%-supermajority / simple-majority two-tier resolution threshold; and a
90%-near-unanimity threshold for bypassing standard notice/deliberation periods. Use these as
ready-made `votingPeriod`/quorum benchmarks when no other calibration source is available.

**Tertiary:** `ostrom_2005.md`
Adds the aggregation-rule taxonomy (nonsymmetric/symmetric/no-agreement rules) and the finding
that the specific *no-agreement* rule (what happens when a vote fails) has a larger effect on
outcomes than the threshold itself. Use it when a `votingPeriod`/quorum design keeps failing to
reach threshold: the fix may be the no-agreement fallback, not a lower threshold.

**Septenary:** `delaware_dgcl_title8.md`
Adds cumulative voting for multi-seat elections (voters pool weight onto fewer candidates,
guaranteeing minority representation — a distinct aggregation rule from any single-decision
threshold already in this library), plurality (not majority) thresholds for multi-candidate
`PeerSelect`-style elections to avoid vote-splitting deadlock, a proportional (⅓) quorum floor as
an alternative to an absolute-number floor, and a stricter-than-normal threshold (full unanimity)
for asynchronous/no-meeting board decisions versus ordinary majority-at-a-meeting decisions.

**Septenary:** `switzerland_llc_2023.md`
Adds a dual-quorum pattern (a headcount supermajority AND an independently-tracked stake-weighted
majority both required) for decisions where both broad buy-in and material-stake concentration
matter.

---

### Q3 — Mandate selection

**Primary:** `carlisle_gruby_2019.md`
The institutional fit framework (Section 4.2) is the most directly applicable tool: it frames
mandate selection as a matching problem between the governance institution and the problem it
addresses. Use it when deciding between mandate types for a specific governance function.

**Secondary:** `podger_2020.md`
Adds the coherence principle: similar functions should use similar mandate types. Use it to check
that the mandate selection across roles is internally consistent.

**Tertiary:** `hynes_oecd_2020.md`
Adds the systemic perspective: mandates for contested or multi-stakeholder domains should include
a `StatementOfIntent` deliberation step; constitutions without reform mandates are structurally
incomplete. Use it when the organisation's governance domain is complex or contested.

**Tertiary:** `ostrom_2009.md`
Adds the four-type goods taxonomy (private / toll-club / public / common-pool resource) as the
mandate selection entry point: identify the good type first, then select the mandate pattern
from the table in `ostrom_2009.md`. Use it when the organisation type is ambiguous or when
the designer is applying a template without checking whether it matches the resource type.

**Tertiary:** `ostrom_2011.md`
Adds the three-tier IAD match: operational mandates for execution, collective-choice mandates
for rule modification, constitutional mandates for wholesale restructuring. Use it to confirm
that the mandate type selected matches the decision tier being addressed.

**Quaternary:** `cic_regulations_2005.md`
Adds the clearest binary mandate-selection fork in the library: choose once, at the
constitutional level, between a treasury mandate with no payout path to role-holders at all
(asset-lock-only) versus one permitting capped distributions. Use it when deciding whether a
treasury should ever pay out to role-holders, and if so, under what hard ceiling.

**Quaternary:** `cic_guidance_govuk.md`
Adds the four-branch transfer-justification gate (full consideration / nominated asset-locked
body / regulator-consented body / community benefit) and the pattern of hard-coding a fixed
distribution-cap percentage rather than leaving it to a discretionary vote each time. Use it when
designing treasury-outflow mandates that must balance flexibility against self-dealing risk.

**Quaternary:** `cic_plinth_guide.md`
Adds an income-model heuristic — ongoing trading/fee revenue favours an asset-locked,
restricted-distribution mandate set; one-off grant/donation revenue favours simpler
grant-compliance/reporting mandates instead. Use it early, before selecting any specific
mandate, to check that an asset-lock-style pattern actually fits the organisation's revenue model.

**Quaternary:** `cic_wikipedia.md`
Adds the hybrid-goods framing: an organisation that behaves like a flexible private enterprise but
must produce a structural public-good commitment needs operational mandates left unconstrained
while treasury/dissolution mandates carry a standing, non-bypassable purpose check. Use it to
distinguish this hybrid pattern from a pure charity-style pattern (which would instead restrict
*who may propose* financial mandates).

**Quinary:** `erc_8004_2025.md`
Adds three pluggable trust models (reputation-gated, validation-gated, staked) as mandate patterns
for gating agent-triggered actions, keyed to the cost of a false positive vs. the cost of latency.
Use it when deciding how much pre-execution scrutiny an AI-agent-triggered mandate needs.

**Quinary:** `erc_4337_2021.md`
Adds the validate-then-execute two-phase pattern (gate expensive/irreversible execution on a
cheap, revertible validation step) as a general design independent of voting, plus a distinction
between stakes meant to deter Sybil/spam entry (no slashing needed) and stakes meant to insure
against misbehaviour (requires slashing). Use it when scoping a stake requirement for role entry.

**Quinary:** `fli_ai_act_overview_2024.md`
Adds a four-tier risk classification (unacceptable/high/limited/minimal) including a
"categorically prohibited" tier enforced by omission rather than by vote — some actions should be
unreachable by any mandate configuration, not merely vote-gated. Use it when identifying actions a
constitution should never permit regardless of process.

**Quinary:** `nist_ai_rmf_2023.md`
Adds the requirement to pair any mandate with an external-contract/oracle dependency with an
explicit contingency mandate for when that dependency fails, decided at design time rather than
improvised during an incident. Use it whenever a mandate depends on `ExternalAction_*`,
`CheckExternalActionState`, or an oracle.

**Quinary:** `nist_ai_600-1_2024.md`
Adds the prompt-injection risk: content an AI agent processes from outside the constitution's own
state is an attack surface, so mandate scope (not agent judgment) should be the actual security
boundary for agent-held roles. Use it when scoping `target`/`value` bounds for a mandate an AI
agent can trigger based on external content.

**Senary:** `durrer_gilmore_stevenson_2019.md`
Adds a documented failure mode: unstructured discretionary resource-allocation mandates
systematically reward already-well-connected recipients even without bad intent. Use it when
choosing between a discretionary treasury/grant mandate and a formula-driven one.

**Septenary:** `delaware_dgcl_title8.md`
Adds two distinct patterns for encoding an organisational mission alongside operational
flexibility: a hard-lock style (a mechanical `needFulfilled`/value-bound constraint, e.g. the CIC
asset lock) versus a balancing-duty style (a role charged with weighing multiple named interests,
reviewed under a deferential good-faith standard rather than blocked mechanically — Delaware's
public benefit corporation model, §365). Choose deliberately based on whether the mission is
reducible to a bright-line check or requires genuine judgment calls; pair the balancing-duty style
with mandatory structured periodic disclosure (see Q7) since it can't be enforced by a mechanical
check alone.

**Septenary:** `switzerland_llc_2023.md`
Adds a bounded emergency-capital-call pattern: named, limited triggering conditions plus a hard
cap on per-member exposure (a fixed multiple of a baseline), rather than an open-ended call power.

**Septenary:** `switzerland_legal_forms_overview_2023.md` / `delaware_business_structure_table_2020.md` / `uae_licensing_advantages_mainland_vs_freezone.md`
Three independent jurisdictions corroborating the same principle: constitutional formality should
scale to how much *external* trust an organisation needs from counterparties it hasn't yet built a
relationship with, not only to internal organisation size.

**Septenary:** `uae_free_zones_establishing_business.md`
Adds a thin portability warning: a governance-template menu (legal forms) is not necessarily
available identically across deployment contexts — verify a target environment supports the same
primitives before reusing a `MandatePackage` template built for a different one.

---

### Q4 — Dependency chains

**Primary:** `hynes_oecd_2020.md`
The cascading failure analysis (Ch 12) is the most specific source on dependency chain risks.
Use it when designing `needFulfilled` chains: it provides the fault-tolerance constraint (max 3
sequential dependencies) and the fat-tailed risk argument for robust emergency paths.

**Secondary:** `carlisle_gruby_2019.md`
Adds the conflict resolution dimension: dependency chains that create winner-take-all competition
need a deliberation step. Also provides the "rapid access" argument for keeping conflict
resolution mandates short in `votingPeriod`.

**Quaternary:** `cic_regulations_2005.md`
Adds the only sourced example of an external-approval dependency: a purpose-change reform has no
legal effect until an outside party approves it, independent of and subsequent to the internal
vote. Use it when a reform mandate must remain verifiably aligned with an outside standard (a
legal wrapper, grant condition, or registry membership) rather than being fully self-amendable.

**Quaternary:** `cic_guidance_govuk.md`
Adds a consult-then-decide-then-appeal chain around the single highest-stakes treasury action
(final asset distribution on wind-up): notify affected parties, allow objection, only then
execute. Use it when designing a dissolution or final-liquidation mandate that should not be a
single-step vote.

**Tertiary:** `ostrom_2005.md`
Adds the OR ELSE requirement from the ADICO grammar (a valid rule needs a collectively-decided,
monitorable consequence) and the choice-rules-vs-scope-rules distinction — constrain *who acts*
via `allowedRole`, or constrain *what outcome* results via `target`/`value` bounds, independent of
who causes it. Use the latter for asset-lock-style protections that must survive role turnover.

**Quinary:** `erc_8004_2025.md`
Adds the progressive-validation pattern (soft finality unlocks a reversible step, hard finality
unlocks the irreversible one) as a template for staged `needFulfilled` gates on agent-triggered
actions with a graduated risk profile.

**Quinary:** `erc_4337_2021.md`
Adds the parallel-nonce-channel pattern: an emergency/administrative flow should have an
independent path to execution that does not share a `needFulfilled` dependency with the normal
flow it is meant to interrupt. Use it when adding a `PauseMandates` instance.

**Quinary:** `erc_6900_2023.md`
Adds a canonical-ordering discipline for stacked checks (most-specific veto has priority,
document precedence explicitly) so that adding a new accountability mandate via `Adopt_Mandates`
doesn't silently change which check wins when two mandates disagree.

**Septenary:** `delaware_dgcl_title8.md`
Adds a stall-recovery escalation pattern generalized to the whole-organisation level: a lapsed
mandatory periodic cycle (e.g. election) gets, after a grace period, an escalation path with its
own deliberately relaxed quorum — since normal quorum requirements may be exactly what's broken.
Also sharpens the delegation-stays-revocable principle: irrevocable delegation should require the
delegate to hold an independent interest beyond the delegation itself, not be a casual default.

**Septenary:** `uk_model_articles_private_shares_2013.md`
Adds a non-retroactivity rule for override/veto mandates: a membership override that redirects a
role's future actions does not, by default, invalidate or reverse actions already completed under
the prior mandate — override mandates should be understood as forward-looking unless reversal is
built in separately.

---

### Q5 — Membership design

**Primary:** `podger_2020.md`
The most detailed treatment of the formal vs. actual membership distinction. Use it when designing
the combination of open entry (`SelfSelect`) and gatekeeping (`PeerSelect`, `RevokeAccountsRoleId`)
— the key insight is that both layers must be designed, not just the formal rule.

**Secondary:** `carlisle_gruby_2019.md`
Adds the bootstrapping problem (Section 4.1.2): pure `PeerSelect` constitutions can stall if no
seed members exist. Also adds the homophily warning: informal networks without on-chain
deliberation records reduce membership diversity over time.

**Tertiary:** `ostrom_2009.md`
Adds the dual boundary requirement (Design Principles 1A + 1B): user boundaries (`allowedRole`)
and resource boundaries (`target` + `value` limits) must both be designed. A mandate specifying
only one is structurally incomplete. Also provides empirical evidence that no self-organised
institution in the meta-analysis used binary revocation (grim trigger) as its only enforcement
mechanism — use it to justify graduated accountability chains.

**Tertiary:** `ostrom_2011.md`
Adds the three-component boundary design (entry mechanism, eligibility criteria, exit
mechanism) and the rules-in-form vs. rules-in-use gap: informal membership conventions cannot
drift into on-chain constitutions automatically — they must be formally codified via
`Adopt_Mandates`. Use it when auditing whether informal membership practices match the formal
mandate rules.

**Quaternary:** `cic_model_articles_guarantee_small.md` (and the other model-articles files)
Adds concrete closed-membership patterns: gatekept entry requiring approval by the existing
controlling role, non-transferable membership with no secondary-market exit, and automatic
(non-discretionary) termination triggers tied to inactivity or to a member ceasing to exist. Use
it when designing an admission/exit mandate pair that should not rely on a tradeable instrument.

**Quaternary:** `cic_regulations_2005.md` / `cic_guidance_govuk.md` / `cic_wikipedia.md`
Add a third boundary type, distinct from `allowedRole` (who can act): a recipient-class
restriction on `target` — who funds may flow to — that persists independently of current role
membership (the "asset-locked body" concept). Use it when a treasury mandate's destination
restriction needs to survive membership turnover, and to avoid conflating a beneficiary/output
boundary with a governance-participation boundary.

**Quaternary:** `cic_memorandum_guarantee.md` / `cic_memorandum_shares.md`
Add the binary founding choice between capital-stake membership (token-gated `allowedRole`) and
personal-undertaking membership (`SelfSelect`/`PeerSelect` keyed to identity, no balance
requirement) as a one-time, foundational decision UK company law forces explicitly at
incorporation. Use it as the first design question when scoping a new constitution's membership
unit.

**Tertiary:** `ostrom_2005.md`
Adds the most detailed boundary-rule taxonomy in the library: entry is open/invitational/
competitive/compulsory (`SelfSelect`/`PeerSelect`+`Nominate`/election/no clean equivalent); exit
is voluntary/for-cause/term-based (`RenounceRole`/`RevokeAccountsRoleId`/`RevokeInactiveAccounts`).
Entry and exit are independent choices — always specify both. Also adds succession-rule patterns
(civil-service/seniority/patronage) mapped to `RoleByRoles` and its gaps.

**Quinary:** `erc_8004_2025.md`
Adds the discovery-vs-trust boundary distinction: an open registration role proves an agent
*exists*, not that it should be *trusted* — route agents through a second, higher gate before
granting any consequential `allowedRole`. Also flags Sybil vulnerability of open registration
combined with reputation-based trust.

**Quinary:** `erc_4337_2021.md`
Adds the stake-without-slashing pattern as pure Sybil/spam deterrence, distinct from a stake meant
to insure against in-role misbehaviour (which needs a slashing mandate). Use it when deciding
whether a role-entry stake needs a slashing mechanism at all.

**Senary:** `meier_pena_nah_2025.md` / `honari_2018.md`
Add a documented trade-off for organisations under credible adversarial risk: full on-chain
role-holder identity transparency doubles as a targeting surface, so rotating-pseudonym or
non-persistent identity designs may be worth the accountability-continuity cost. Treat as an
explicit, deliberate trade-off, not a default — see each file for the underlying evidence.

**Septenary:** `switzerland_limited_partnership_2023.md`
Adds a risk/control-coupled two-tier membership pattern (an operational role bearing real
exposure plus a passive/capped-exposure role structurally excluded from operational control), and
a liability-tail warning: renouncing/exiting a role does not necessarily end exposure to
consequences of actions taken while the role was held, if the accountability chain can reach past
role-holders at all.

**Septenary:** `switzerland_general_partnership_2023.md`
Adds a peer-consent-gated transfer/exit pattern: transferring a membership stake that carries
shared exposure requires a `PeerSelect`-style consent step from remaining members, not a
unilateral `RenounceRole`-then-reassign action.

**Septenary:** `uk_model_articles_private_guarantee_2013.md`
Adds a two-parameter admission-gate pattern: separate the eligibility criteria/application format
(an adjustable parameter) from the admission decision itself (a discretionary vote), so each can
be reformed independently.

**Septenary:** `uk_companies_house_guidance_overview.md`
Adds a two-tier delegated-verification pattern for scaling identity/eligibility checks: an
authorized intermediary role performs verification on a central authority's behalf, but needs its
own `allowedRole` scoping and accountability chain rather than being an unaccountable bottleneck.

---

### Q6 — Adaptive capacity and reform

**Primary:** `carlisle_gruby_2019.md`
Provides the clearest conceptual distinction between process-level adaptation (`Adopt_Mandates`)
and structural adaptation (`MandatePackage`). Use it when deciding which reform mandate type
fits the scope of the intended change.

**Secondary:** `hynes_oecd_2020.md`
Adds the institutional argument: good governance must be built into the mandate structure, not
depend on individuals. Provides the IRGC 7-step completeness check — does the constitution cover
monitoring and adaptation (step 7), or only execution (steps 1–6)?

**Tertiary:** `ostrom_2009.md`
Adds empirically validated design principles for adaptive capacity: Design Principle 3
(collective-choice arrangements must include affected roles, not only admin) and Principle 8
(nested enterprises for polycentric resilience). Use it when justifying why `Adopt_Mandates`
must be accessible to member roles, not restricted to admin.

**Gap:** `may_2022.md` is expected to be the strongest source for this question but is currently
unreadable. Replacing that file is the highest-priority scholarship gap.

**Quaternary:** `cic_regulations_2005.md`
Adds the clearest example of a reform constraint sitting permanently outside the ordinary
amendment surface: the asset lock cannot be removed by any internal vote, while the
distribution-cap percentage layered on top of it is an ordinary, revocable parameter. Use it when
deciding which parts of a constitution should be excluded from `Adopt_Mandates`/`Revoke_Mandates`
entirely versus left as a votable parameter.

**Quaternary:** `cic_annual_report_2024_2025.md`
Adds real longitudinal data: roughly 78% lifetime attrition among UK CICs registered since 2005,
and a regulatory cost structure that scaled with a 100x population increase over 20 years without
requiring any rule amendment. Use it when deciding whether a constitution needs an explicit,
low-cost wind-down/dissolution mandate path rather than assuming indefinite persistence.

**Tertiary:** `ostrom_2005.md`
Adds five documented threats to institutional sustainability (rapid exogenous change,
transmission failure across generations, blueprint thinking, corruption/rent-seeking around
artificial scarcity, lack of large-scale supportive institutions) and the mechanism by which
transmission failure erodes rules one small self-favouring interpretation at a time. Use it as a
threat checklist alongside the Design Principles when reviewing a constitution's resilience.

**Quinary:** `erc_6900_2023.md`
Adds a warning that mandate re-adoption at a previously-revoked flow position is not guaranteed to
be a clean reset — associated state can persist across a revoke/re-adopt cycle. Treat re-adoption
as requiring an explicit state-audit step.

**Quinary:** `fli_ai_act_overview_2024.md`
Adds the requirement to design an interruption point (`timelock` + scoped `PauseMandates`) into a
high-stakes mandate's execution path itself, not only a downstream accountability chain, plus the
case for a low-barrier complaint channel for non-role-holder third parties affected by a mandate.

**Quinary:** `nist_ai_rmf_2023.md`
Adds the requirement to design a *safe decommissioning* path for an agent-held role (unwinding
in-flight obligations and dependent mandates) at the same time the role is created, and the
principle that accountability records should capture stated rationale, not just a binary outcome.

**Senary:** `honari_2018.md`
Adds that a repression event can itself be used as the trigger for a governed response
(publicising an attack via `StatementOfIntent`), extending the accountability chain's function
beyond internal sanctioning to external legitimacy documentation.

**Septenary:** `uk_model_articles_overview_gov_uk.md`
Adds real-world corroboration (independent of the Federated Sub-org Governance pattern already in
`institutionalDesign.md` §2) that updating a default constitution/template should never
retroactively migrate already-deployed instances — they stay pinned to the version in effect at
their creation, moving to a newer version only via their own explicit governance action.

**Septenary:** `uk_model_articles_public_2013.md`
Adds mandatory periodic re-election (retirement by rotation) as a no-fault accountability
mechanism distinct from `RevokeAccountsRoleId`, appropriate once a role's holder-base grows too
large/diffuse for continuous informal oversight — continued tenure should require periodic
affirmative re-confirmation, not default to indefinite persistence absent a complaint.

**Septenary:** `delaware_dgcl_title8.md`
Adds that a judgment-based mission-balancing duty (see Q3) is itself an adaptive-capacity feature:
because it is a standard rather than a fixed rule, it does not need amending every time
circumstances change the specific trade-off it governs. Weigh this flexibility against the
accountability cost noted in Q7 — a judgment standard is harder to enforce mechanically than a
bright-line constraint.

---

### Q7 — Accountability and monitoring

**Primary:** `hynes_oecd_2020.md`
On-chain attributable accountability is framed here as a structural advantage of Powers vs.
conventional governance — every vote and execution is permanently associated with a specific
account. Use it to argue for broad `allowedRole` on accountability mandates and against
collective-responsibility structures without individual attribution.

**Secondary:** `podger_2020.md`
Adds the upward vs. outward accountability distinction and the graduated vs. binary enforcement
distinction (signal → warn → revoke). Use it when designing the accountability chain for
integrity or veto roles.

**Tertiary:** `carlisle_gruby_2019.md`
Adds the diffuse-accountability warning: shared mandates between multiple roles create shared
(and therefore weakened) accountability. Use it when two roles have overlapping mandate authority.

**Tertiary:** `ostrom_2009.md`
Adds the four empirically validated accountability design principles (4A monitoring users,
4B monitoring resource, 5 graduated sanctions, 6 conflict resolution). These are the most
directly specified accountability requirements in the library — sourced from meta-analysis of
institutions that survived long-term. Use it when designing or reviewing the accountability
chain for any execution or role-assignment mandate.

**Tertiary:** `ostrom_2011.md`
Adds the six evaluative criteria (efficiency, fiscal equivalence, redistribution, accountability,
conformance to values, sustainability) as a post-design review checklist. Also distinguishes
between accountability (attributable, on-chain) and conformance to values (reputation-building
over time). Use it when the designer asks "how do we know the governance is working?"

**Quaternary:** `cic_annual_report_2024_2025.md`
Adds the strongest empirical accountability evidence in the entire library: real complaint and
enforcement statistics from a 37,000-entity population showing the harshest sanction (asset
seizure) was never invoked in a year with multiple financial-mismanagement and governance
complaints logged, and that hard-coded constraints (the asset lock) generated zero disputes while
discretionary judgment calls generated the most. Use it when deciding how aggressively to design
an enforcement/escalation chain — design the harshest sanction as a credible-but-rare backstop,
not the primary mechanism.

**Quaternary:** `cic_regulations_2005.md`
Adds the external-manager-appointment mechanism (no Powers-native equivalent) and the
disclosure-after-vote pattern: a distribution vote alone is not treated as accountability-complete
without a mandatory downstream public report. Use it when a constitution needs an external
oversight role or a mandatory post-distribution reporting mandate.

**Quaternary:** `cic_guidance_govuk.md`
Adds the "excessive role-holder compensation is a disguised asset-lock breach" framing, and the
light-touch/complaint-driven oversight model (most effective oversight here is reactive, not
constantly active). Use it when designing remuneration mandates or scoping how active an
oversight role needs to be.

**Quinary:** `erc_8004_2025.md`
Adds three concrete accountability-record patterns: exclude a role-holder and its known operators
from the `allowedRole` set of any mandate recording accountability signals about that same
role-holder; allow signal *revocation* by the original submitter without allowing signal
*deletion*; and separate the mandate that records a validation/audit result from the mandate that
acts on it, so consequence logic can be reformed independently of the recording mechanism.

**Quinary:** `erc_4337_2021.md`
Adds the principle that every failure path in a multi-step `needFulfilled` chain should be
attributable to the specific mandate/entity responsible, not collapse into an undifferentiated
failure — important once a chain involves an external party. Also suggests automatic graduated
throttling (rather than voted sanctions) for high-frequency, low-stakes infrastructure-adjacent
roles.

**Quinary:** `nist_ai_600-1_2024.md`
Adds a Powers-specific integrity risk: agent-authored on-chain rationale text can be fluent,
specific, and entirely fabricated (confabulation), and once written becomes a permanent part of
an immutable audit trail. Flag agent-authored text as distinct from human-authored text, and
weight ex-ante mandate-scope limits more heavily than ex-post accountability chains for agent-held
roles, since post-hoc fault attribution may be structurally limited by opacity in the agent's
underlying model.

**Senary:** `durrer_gilmore_stevenson_2019.md` / `ellefsen_jamte_2023.md`
Add two related accountability-gaming risks: selecting role-holders/grantees on administrative
legibility rather than underlying performance, and open reputation/complaint channels being
flooded with unverified negative signals by bad-faith external parties to manufacture internal
distrust. Use both when designing signal-source requirements for a `RevokeAccountsRoleId`
threshold.

**Septenary:** `delaware_dgcl_title8.md`
The single richest Q7 source in this library. Adds: three independent safe-harbor validation
paths for conflict-of-interest mandates (a smaller disinterested-role quorum, full-membership
ratification, or an objective fairness check — any one suffices, more flexible than a single fixed
recusal rule); a deferential good-faith-and-informed review standard for judgment-based
balancing-duty mandates (necessary if using the balancing-duty mission pattern from Q3, since
outcome-based review makes every decision endlessly second-guessable); mandatory structured
periodic disclosure (objectives → measurement standard → data → self-assessment) as the primary
accountability mechanism for a duty that resists mechanical pass/fail checks; a minimum-stake
standing threshold for challenging a discretionary judgment call, filtering nuisance challenges
while preserving genuine accountability for major stakeholders (a concrete numeric anchor for the
signal-flooding concern above); an indemnification asymmetry (broader default protection for
good-faith harm to third parties than for harm to the organisation's own treasury/membership); and
a burden-of-proof default placing the justification burden on whichever mandate withholds
information, not on the requester.

**Septenary:** `uk_companies_house_guidance_overview.md`
Adds live regulatory corroboration for identity-verification gates on powerful roles, and a
general commitment to non-arbitrary, principle-bound enforcement, lightly corroborating the
existing graduated-sanctions and hard-coded-constraints cross-cutting rules.

---

## Cross-cutting design rules

Rules 1–8 appear independently in all three core academic sources (Podger, Carlisle, OECD) and
can be treated as well-grounded design constraints. Rules 9–10 are added from the CIC source
family and are well-grounded in statute/regulation and empirical enforcement data rather than
academic meta-analysis, but are corroborated by the academic sources' boundary and sanctions
principles (see cross-references):

1. **Formal ≠ de facto independence.** A role's actual independence is determined by its
   appointment and revocation mechanisms, not only its execution mandate. (Podger Ch 2,
   Carlisle Section 3.1, OECD Ch 13)

2. **Reform mandates are first-class.** A constitution without `Adopt_Mandates` or equivalent
   is structurally incomplete — it cannot adapt, learn, or correct itself. (Podger Ch 2 Weberian
   paradox, Carlisle Section 4.1, OECD IRGC step 7)

3. **Mandate diversity enables resilience.** A constitution that assigns the same mandate type
   to every function has no repertoire to draw on when the normal path fails. (Podger Ch 2
   twin-forces, Carlisle Section 4.1.1, OECD Ch 12 fat-tailed risk)

4. **Broad `allowedRole` on reform and accountability mandates.** Restricting reform or
   censure to an admin-only role concentrates adaptive capacity in a single point of failure
   and weakens outward accountability. (Podger Ch 1, Carlisle Section 4.1, OECD Ch 13)

5. **On-chain vote records are the accountability mechanism.** Mandates with `votingPeriod = 0`
   on treasury or role-assignment actions remove the social decision process that gives the
   constitution its legitimacy claim. (Podger Ch 1, Carlisle Section 4.1.4, OECD Ch 13)

6. **Dual boundary requirement.** Every mandate must specify both user boundaries (`allowedRole`)
   and resource boundaries (`target` + `value` limits). A mandate with only one boundary type
   is structurally incomplete against Ostrom's Design Principle 1A+1B. (Ostrom 2009 Section 4E,
   Ostrom 2011 p. 21, Carlisle Section 4.2)

7. **Graduated sanctions over binary revocation.** No long-surviving self-organised institution
   used binary exclusion as its only enforcement mechanism. The graduated chain
   (`StatementOfIntent` → `PauseMandates` → `RevokeAccountsRoleId`) is the empirically
   supported pattern. (Ostrom 2009 Design Principle 5, Podger Ch 7, Carlisle Section 4.1.5)

8. **Collective-choice reform must include the affected role.** Restricting `Adopt_Mandates`
   to admin violates Ostrom's Design Principle 3, which is associated with institutional failure
   in the empirical record. (Ostrom 2009 Section 4E, Carlisle Section 4.1, OECD Ch 13
   cogeneration principle)

9. **Recipient/output boundaries are a third boundary type, distinct from participant
   boundaries.** A restriction on *who funds may flow to* (`target`) must be designed
   independently of, and can outlive, a restriction on *who may act* (`allowedRole`) — changing
   role membership should never silently change where treasury assets are allowed to go.
   (CIC Regulations 2005 Sched. 1 ¶1, CIC Guidance "Asset Lock" section, Wikipedia "The asset
   lock" section)

10. **Hard-coded constraints prevent more disputes than discretionary review.** Real-world
    enforcement data shows non-discretionary, automatically-checked rules generate far fewer
    disputes than rules that depend on after-the-fact judgment calls about whether discretionary
    behaviour was appropriate. Prefer `needFulfilled`/`needNotFulfilled` checks evaluated
    automatically over relying solely on `StatementOfIntent` deliberation to catch the same
    problem later. (CIC Annual Report 2024–25 §8, reinforcing Cross-cutting rule 6)

Rule 11 is added from the AI agent governance source family, where it appears independently
across three unrelated authors (an Ethereum standards proposal, a national regulatory body, and a
US federal standards agency) converging on the same principle from different angles:

11. **Oversight intensity should scale with value at risk, not with role-holder count or
    organisation size.** Security/oversight proportional to what a mandate can actually do —
    validation gates, `timelock` length, staking requirements — should be calibrated per-mandate
    to the stakes of that specific action, supplementing (not replacing) the size-based
    `votingPeriod`/quorum heuristics in `institutionalDesign.md` §4. A "categorically prohibited"
    tier, enforced by omission rather than by vote, sits below the lowest end of this scale for
    actions no amount of process should legitimise. (ERC-8004 Abstract, FLI AI Act Overview
    four-point summary, NIST AI 600-1 §2.9 on ex-ante scope limits vs. ex-post attribution)

Rule 12 is added from the comparative company-law source family, where it appears independently
across three unrelated legal systems (Swiss, UK, and Delaware corporate law) converging on the
same delegability distinction:

12. **Some authority is structurally non-delegable, distinct from routine delegable authority
    attached to the same role.** A role's core, constitution-defining powers (approving matters
    that legally require full-membership approval, amending the constitution itself) should never
    be reassignable to a narrower `allowedRole` through ordinary reform — reserve that for a
    constitutional-tier change (`MandatePackage`). Routine operational authority attached to the
    same role remains freely delegable. Symmetrically, a rule adopted by the broader membership at
    a high threshold should be protected from reversal by a narrower body that would normally have
    authority to change similar rules — protection attaches to how a rule was adopted, not to a
    fixed category of "important" rules. (Swiss AG Art. 716a CO, Delaware DGCL §141(c)(2) and
    §216, reinforcing Cross-cutting rule 2)
