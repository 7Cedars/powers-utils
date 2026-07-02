# UK Companies House — Guidance for Limited Companies, Partnerships and Other Company Types

**Citation:** Companies House. "Guidance for Limited Companies, Partnerships and Other Company
Types." GOV.UK collection, published 13 November 2014, last updated 28 May 2026.
**Analytical level:** Structural + Dynamic
**Most relevant design decisions:** Q1, Q5, Q7

**Note on fit:** this is a hub/index page linking to dozens of Companies House guidance topics
(filing, annual accounts, strike-off, mortgage charges, liquidation, overseas companies, etc.). Most
linked topics are administrative filing procedure with no governance-design content. Two 2025/2026
regulatory reforms described inline on the hub page itself — mandatory identity verification and
Authorised Corporate Service Providers — are genuinely relevant and are extracted below.

---

## Q1 — Role Structure

"Identity verification": "Companies House is introducing a new identity verification process to
help deter those wishing to use companies for illegal purposes. Anyone setting up, running,
owning or controlling a company in the UK will need to verify their identity to prove they are who
they claim to be." This is a live, real-world instance of a Sybil-resistance requirement being
retrofitted onto an *existing*, previously identity-optional legal-entity regime, applying to
every category of controller (director, PSC, company founder) rather than only new entrants. It
independently corroborates the identity-verification design already discussed from a different
angle in `erc_8004_2025.md` (Q5, agent registration Sybil risk) and `nist_ai_600-1_2024.md`
(automation/agent identity), but applied here to human controllers of a legal entity rather than
AI agents — the underlying design problem (anyone can currently claim to control something without
proving who they are) and the underlying fix (mandatory identity verification, gated on the
`allowedRole` in question) is the same pattern recurring in a third, independent domain. For a
Powers constitution granting a powerful role, consider whether `ZKPassport_Check` or an equivalent
identity-verification mandate should gate entry, especially when retrofitting an existing
open-entry role that has accumulated real governance power over time.

---

## Q5 — Membership Design

"Authorised Corporate Service Providers (ACSPs)": "Registering as an Authorised Corporate Service
Provider... is a new requirement that will help us to know who's filing information on the public
register... An authorised agent can be a business... or a person who files on behalf of others."
Rather than the registrar (Companies House) verifying every individual controller directly, it
authorizes intermediaries to perform verification on its behalf — but those intermediaries must
themselves meet a defined verification standard and are individually accountable ("How to meet
Companies House identity verification standard," "Tell Companies House you have verified
someone's identity"). This is a two-tier delegated-trust pattern: a central authority delegates a
gatekeeping function to accountable intermediaries rather than either doing it all centrally or
not gating it at all. For Powers, this maps to `AssignExternalRole`-style delegation of a
verification/onboarding function to a trusted intermediary role, which itself needs its own
`allowedRole` scoping and accountability chain (a verifier of verifiers) — useful when a
constitution wants to scale identity/eligibility verification without requiring every check to
route through a single bottleneck role.

---

## Q7 — Accountability and Monitoring

"Enforcement": Companies House states it will exercise enforcement powers "predictably,
consistently, judiciously, in line with our strategic objectives" when guidance and support are
insufficient to secure compliance. This is a general commitment to non-arbitrary, principle-bound
enforcement rather than ad hoc discretion — a light, independent corroboration of the
graduated-sanctions and hard-coded-constraints themes already established as cross-cutting rules
7 and 10 in this library, from a regulator's self-imposed policy rather than a companies-law
statute.

---

## What to skip

The overwhelming majority of the linked topics — online filing services, annual accounts and
confirmation statements, mortgage-charge registration, strike-off/dissolution/restoration
procedure, PSC-register mechanics, late filing penalties, liquidation and insolvency types, and
guidance for LLPs/LPs/overseas companies — are UK administrative filing procedure with no
governance-design content.

---

## Mandate implications

- When retrofitting an identity-verification requirement onto an existing open-entry role that
  has accumulated real governance power, consider `ZKPassport_Check` or an equivalent gate, rather
  than assuming identity-optional entry is acceptable indefinitely just because it was the
  original design.
- When delegating identity/eligibility verification to an intermediary role rather than a central
  bottleneck, scope the intermediary's `allowedRole` explicitly and give it its own accountability
  chain — delegated verification authority is still authority that needs governing.
