# UK Companies House — Model Articles of Association for Limited Companies (Overview)

**Citation:** Companies House. "Model Articles of Association for Limited Companies."
GOV.UK guidance, published 21 November 2014, last updated 10 October 2017.
**Analytical level:** Structural (thin — see note below)
**Most relevant design decisions:** Q6

**Note on fit:** this is an index/navigation page listing which version of the UK's default
"model articles" template applies depending on a company's incorporation date, with links to
historical "Table A" versions back to 1856. It has no internal governance content of its own (see
`uk_model_articles_private_shares_2013.md`, `uk_model_articles_private_guarantee_2013.md`, and
`uk_model_articles_public_2013.md` for the actual governance provisions). One structural pattern
is worth extracting.

---

## Q6 — Adaptive Capacity and Reform

"The latest model articles apply by default to all private and public limited companies
incorporated on or after 28 April 2013. The older model articles continue to apply by default to
all companies incorporated between 1 October 2009 and 27 April 2013" — when the default
constitutional template is revised, **already-incorporated companies are not retroactively
migrated** to the new version; they remain governed by whichever template version was in force at
their incorporation date unless they take affirmative action to amend their own articles. This is
real-world corroboration, from an independent source, of the template-freezing design already
specified in `institutionalDesign.md` §2 (Federated Sub-org Governance): "The sub-org constitution
template is frozen at factory-deploy time. Changing the template for future sub-orgs requires
deploying a new factory... All sub-orgs from the same factory share the same [instance]." Use this
as supporting precedent when a designer questions why updating a `PowersFactory` template
shouldn't retroactively affect already-spawned sub-orgs: the UK's own default-company-constitution
regime uses exactly this non-retroactive, version-pinned pattern.

---

## What to skip

The list of historical "Table A" versions (1856-2007) and the specific 2013 amendment removing a
mental-health-based director-termination provision are UK company-law history with no
generalisable governance-design content beyond the versioning pattern above.

---

## Mandate implications

- When updating a `PowersFactory` template or any default constitution template, do not
  retroactively migrate already-deployed instances — they should remain pinned to the template
  version in effect at their creation, moving to a newer version only via their own explicit
  governance action.
