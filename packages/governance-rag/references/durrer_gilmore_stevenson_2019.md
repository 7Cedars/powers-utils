# Durrer, Gilmore & Stevenson 2019 — Arts Councils, Policy-Making and "The Local"

**Citation:** Durrer, V., Gilmore, A., & Stevenson, D. 2019. "Arts Councils, Policy-Making and
'The Local.'" *Cultural Trends* 28(4): 317–331. https://doi.org/10.1080/09548963.2019.1644795
**Analytical level:** Structural + Dynamic
**Most relevant design decisions:** Q3, Q6, Q7

This is a comparative case study of three UK national arts-funding bodies (Creative Scotland,
Arts Council England, Arts Council Northern Ireland) and how they distribute authority and
resources to numerous smaller, dispersed local recipients — structurally analogous to a Powers
organization (or a parent DAO) that must delegate to, fund, or recognize a large, heterogeneous
set of smaller sub-groups it cannot govern directly. Its central finding is a cautionary one about
how devolution/delegation efforts can fail to actually distribute power even when explicitly
designed to.

---

## Q3 — Mandate Selection

pp. 319–320 (Creative Scotland case): funding relationships with local partners are managed
through informal "'ad-hoc' 'softer relationships'... rather than rely upon formal hierarchies,
procedures, and transactional interactions," and "no formal expectation exists about the
quantity, quality and nature of relationships... left to individual staff discretion." The
documented consequence: "significant importance is placed on identifying the 'right people'...
those areas where relevant actors were particularly proactive in seeking the input of [the
funder] being more likely to receive reciprocal attention" — i.e., a purely discretionary
resource-allocation process systematically rewards already-well-connected, already-organized
applicants over equally deserving but less legible ones. This is a concrete failure mode for
treasury/grant-style mandates: a `BespokeAction_Simple`/`OpenAction` treasury mandate left to a
role-holder's unstructured discretion (no `inputParams` criteria, no objective `target`/`value`
formula) will tend toward the same elite-capture pattern documented here, independent of the
role-holder's good faith — discretion itself, not bad intent, produces the skew. Prefer
`PresetActions`/formula-driven `BespokeAction_Simple` mandates with explicit, auditable allocation
criteria over open-ended discretionary grants whenever a mandate distributes scarce resources
across many potential recipients who cannot all be personally known to the role-holder — this
sharpens Ostrom's "proportional equivalence between benefits and costs" design principle
(`ostrom_2005.md` Q7) with a concrete mechanism for how discretion defeats it even without
malice.

---

## Q6 — Adaptive Capacity and Reform

pp. 325–326 (England case, discussion): Arts Council England's attempt to devolve authority to
"the local" through networked partnerships requires local actors to "adopt specific politically
and economically located identities and develop recognisable organisational structures with which
institutions such as arts councils are able to interact, and fundamentally to trust." The paper's
central argument (p. 326): this recognition requirement is not neutral — "in order to maintain the
integrity of each national network, not all places are able to secure and maintain a position
within it... a culture of competition in cultural policy flourishes... as places jostle
entrepreneurially for the attention of national bodies." This is a genuinely important, transferable
insight for any Powers design that delegates authority to external or federated sub-groups
(`AssignExternalRole`, `RoleByRoles`, the Federated Sub-org Governance pattern in
`institutionalDesign.md` §2): **the bar for being recognized as a legitimate counterparty can
itself function as a hidden centralization mechanism**, even when the explicit goal of the
delegation is to distribute power outward. A sub-org factory or delegate-recognition mandate that
requires prospective delegates to already have formal structure, a track record, or sustained
engagement capacity will systematically favor already-resourced actors — the delegation looks
decentralized on paper (many sub-orgs, many delegates) while functionally re-concentrating
influence among whoever can best perform legibility to the parent organization. When designing a
federated or delegated structure, treat "what does a sub-group need to already have in order to be
recognized" as a design decision with direct distributive consequences, not a mere administrative
formality — consider lowering the legibility bar (simpler `SelfSelect`-style sub-org creation)
where broad access matters more than vetted quality, and only raise it deliberately where
adversarial-resistance or quality-assurance genuinely requires it.

pp. 317–318 (UK devolution context): describes devolution across the UK's nations as
"'asymmetrical' and 'lopsided,'" with the central government "responsible for a residual mix of
UK-wide and England-specific functions" — i.e., authority not explicitly assigned to a devolved
body defaults back to the center by omission, rather than being explicitly retained or
transferred by design. This is a reusable warning for federated/nested Powers structures: an
ambiguous or "residual" default (authority that nobody explicitly decided belongs to the parent
vs. the child) tends, in practice, to function as parent-retained authority, since the parent
already holds it unless a mandate explicitly transfers it away. When scoping a federated sub-org's
authority, enumerate what it *does* control rather than only what it *doesn't* — an implicit
default-to-parent model reproduces exactly the "residual centralization" this case study
documents.

---

## Q7 — Accountability and Monitoring

p. 326 (conclusion): "securing national support for 'local' activity becomes as much (if not
more) about places creating a vehicle by which they can exhibit organisational and administrative
competence as it is about the creative and cultural practices... themselves." When accountability
to a funder is demonstrated primarily through *administrative legibility* (having the right
organizational form, the right reporting structure) rather than through the underlying
activity/outcome itself, the accountability mechanism selects for performing accountability well,
which is a different (and gameable) skill from the activity actually being funded. For Powers
mandate design, this is a caution against conflating "did this role-holder produce good
`StatementOfIntent` documentation" with "did this role-holder do the thing the mandate exists for"
— an accountability chain that only ever observes the former will, over time, select role-holders
and grantees for their documentation/reporting fluency rather than their underlying performance.

---

## What to skip

The extensive descriptive detail on each nation's specific institutional history, funding
formulas, and per-capita expenditure figures (Scotland, England, Northern Ireland sections) is
UK cultural-policy-specific empirical description with no generalisable governance-design content
beyond the two patterns already extracted. The methodology section (interview design, thematic
analysis) is a research-methods account, not a governance finding.

---

## Mandate implications

- Prefer formula-driven or criteria-based allocation mandates (`PresetActions`/structured
  `BespokeAction_Simple`) over open-ended discretionary treasury/grant mandates whenever
  distributing scarce resources across many potential recipients the role-holder cannot
  personally vet — unstructured discretion produces elite capture even without bad intent.
- Treat the "recognition bar" for admitting a delegate, sub-org, or grantee into a federated or
  networked structure as a distributive design decision, not an administrative formality —
  requiring pre-existing formal structure or track record systematically favors already-resourced
  actors and can silently re-centralize a nominally decentralized design.
- When scoping authority for a federated sub-org, enumerate what the sub-org explicitly controls
  rather than leaving unassigned authority as an implicit residual default to the parent — an
  ambiguous residual tends to function as parent-retained authority in practice.
- Distinguish "produced good accountability documentation" from "performed the underlying mandate
  well" when designing accountability chains — selecting only on the former rewards reporting
  fluency over substance.
