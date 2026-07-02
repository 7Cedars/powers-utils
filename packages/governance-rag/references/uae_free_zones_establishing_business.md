# UAE Ministry of Economy & Tourism — Establishing Business in Free Zones

**Citation:** UAE Ministry of Economy & Tourism. "Establishing Business in Free Zones."
moet.gov.ae, Regulation of Business / Companies Registrars section.
**Analytical level:** Structural (weak fit — see note below)
**Most relevant design decisions:** Q3

**Note on fit:** this is a government registration-procedure webpage (steps to obtain a free-zone
business licence: identify activity type, choose a legal form, reserve a trade name, obtain
approvals, register). It describes *how to register* one of three free-zone legal forms (Free
Zone LLC, Free Zone Company, Free Zone Establishment) but does not describe how any of them
allocate governance authority internally (no mention of general meetings, boards, voting, or
member rights) — unlike the Swiss SME Portal sources, which document the actual internal
governance provisions of each legal form. The content here is almost entirely administrative
licensing procedure.

---

## Q3 — Mandate Selection

The document notes that "these legal forms are not registered by all free zones" and that
available legal structures vary by which specific free zone is chosen, with the advice to "refer
to the concerned body in the management of every free zone individually." This is a thin but real
point: a menu of governance-template options is not necessarily portable across deployment
contexts — the same nominal legal form (e.g., "limited liability company") may not be available,
or may carry different default rules, depending on which jurisdiction/zone an organisation
registers in. For a Powers analogue: a `MandatePackage`/constitution template designed for one
deployment context (a specific chain, a specific set of available integrations) should not be
assumed portable to another without checking what's actually available there — template reuse
requires verifying the target environment supports the same primitives, not just copying the
template.

---

## What to skip

The licensing-procedure checklist (identifying activity type, trade name registration, office
selection, document submission for "initial approval," fee payment) is UAE administrative
process with no governance-design content. The list of free-zone support services (telecom,
office space, visa processing) is marketing/informational content for prospective registrants.

---

## Mandate implications

- When reusing a governance template across deployment contexts, verify the target environment
  actually supports the same primitives/legal forms rather than assuming portability.
