# Meier, Peña & Nah 2025 — From Collusion to Autonomy: Patterns of Hybrid Repression and Human Rights Activism

**Citation:** Meier, L., Peña, A. M., & Nah, A. M. 2025. "From Collusion to Autonomy: Patterns of
Hybrid Repression and Human Rights Activism." *Government and Opposition* 60: 773–798.
https://doi.org/10.1017/gov.2024.32.
**Analytical level:** Dynamic (weakly actionable — see note below)
**Most relevant design decisions:** Q5, Q7

**Note on fit:** this is an empirical political-science paper building a typology of *who
represses activists and how* (state / grey-zone / autonomous perpetrators; channelling /
coercive / attritional tactics), based on 160 interviews across four countries. It does not
discuss how activist organizations structure their own governance to survive repression — that
question is outside its scope. Most of the paper is therefore not actionable for Powers mandate
design in the sense the reading-guide template requires (it provides a threat taxonomy, not a
design pattern). The single transferable point is extracted below; everything else is
background.

---

## Q5 — Membership Design

pp. 776–778 (repression tactic taxonomy — "attrition"): attritional repression targets "the
capacity of activists to remain motivated rather than their physical integrity," including
"protracted surveillance" that causes activists to "develop asocial and untrusting stances,
replacing solidarity with 'security cultures.'" For a Powers constitution governing an
organization operating under genuine adversarial risk (e.g., a human-rights or activism-focused
DAO), this is a reason to reconsider the default assumption that role-holder identity should be
straightforwardly linked to an on-chain address: if role membership is fully transparent and
persistent, the same transparency that normally supports accountability (see Q7) can double as a
targeting list for an adversary using attritional tactics. Where this risk is credible, weigh
`SelfSelect`/`PeerSelect` designs that don't require a persistent, publicly-linkable identity
(e.g., role assignment to a fresh address per member rather than a long-lived doxxable one)
against the accountability cost of weaker identity continuity — this is a genuine trade-off, not
a default best practice, since it works against the design principles favoring rich accountability
elsewhere in this library.

---

## Q7 — Accountability and Monitoring

pp. 775–776 (three perpetrator types: state, grey-zone, autonomous): the paper's central finding
is that threats to activists frequently come from actors *other than* the state authorities that
governance transparency is typically designed to hold accountable to — corporate actors,
communitarian/vigilante groups, and non-state armed actors acting with or without state
sanction. This complicates a simple transparency-equals-accountability assumption: on-chain
governance transparency is effective accountability *toward the organization's own members and
public reputation*, but does nothing to protect members from a hybrid-repression actor using that
same transparency as a surveillance input. When designing accountability chains for an
organization operating in a high-risk political context, treat "who can see this record" as a
separate design question from "who is this record accountable to" — a fully public
`StatementOfIntent` vote trail satisfies the latter but may actively undermine member safety with
respect to the former.

---

## What to skip

The bulk of the article — the three-dimensional typology of hybrid repression (perpetrator ×
tactic × target), the four empirical patterns (state rogue, corporate, communitarian, non-state
armed repression), and the country-comparative findings (Colombia, Egypt, Kenya, Mexico) — is a
descriptive/diagnostic framework for political science and human-rights research, not a set of
organizational design recommendations. It answers "what forms does repression take and why,"
which is valuable context for understanding *why* a design trade-off like the one in Q5 might
matter, but does not itself specify mandate types, parameters, or role structures.

---

## Mandate implications

- For organizations operating under credible adversarial/repression risk, treat full on-chain
  identity transparency for role-holders as a trade-off, not a default: weigh accountability
  benefits against the risk that persistent, public role membership functions as a targeting
  surface for a hostile actor.
- Separate "who is this accountability record for" from "who can see this accountability record"
  as two distinct design questions when configuring `StatementOfIntent` visibility and role
  membership durability for a high-risk organization.
