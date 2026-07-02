# UK Companies House 2013 — Model Articles for Private Companies Limited by Shares

**Citation:** Companies House. *Model Articles for Private Companies Limited by Shares*, Schedule
1 to the Companies (Model Articles) Regulations 2008, as amended (post-28 April 2013 version).
**Analytical level:** Structural + Parametric
**Most relevant design decisions:** Q1, Q2, Q4, Q7

This is the base statutory template that the UK CIC model articles already covered extensively in
this library (`cic_model_articles_shares_sch2_small.md` etc.) are built on top of — those guides
cover the CIC-specific additions (asset lock, dual-track removal). This guide extracts granular
procedural mechanics in the base template that are not specific to the CIC layer and are not
already covered there.

---

## Q1 — Role Structure

Art. 5 (directors may delegate): delegation of directors' powers may be to "such person or
committee... by such means... to such an extent... in relation to such matters or territories...
on such terms and conditions as they think fit," and critically, "the directors may revoke any
delegation in whole or part, or alter its terms and conditions" — delegation is never a permanent
transfer of authority; the grantor retains override power over the delegate for as long as the
delegation exists. The articles also explicitly allow sub-delegation ("any such delegation may
authorise further delegation of the directors' powers by any person to whom they are delegated"),
forming a delegation chain. For Powers: this is a template for a general delegation pattern
(`AssignExternalRole` or a bespoke delegate-role structure) where authority can be sub-delegated
multiple levels deep, but the *original* grantor's ability to revoke at any point in the chain
should be preserved by design — a Powers delegation pattern that permanently alienates authority
from its original source (no revocation path back up the chain) is a stricter, less recoverable
commitment than this statutory default and should be a deliberate choice, not an accident of
mandate wiring.

Art. 7 (directors to take decisions collectively — sole-director carve-out): the entire
collective-decision-making apparatus (meetings, quorum, unanimous-decision procedure) is
disapplied by its own terms when "the company only has one director, and no provision of the
articles requires it to have more than one director" — the sole director "may take decisions
without regard to any of the provisions of the articles relating to directors' decision-making."
This is a "degenerate case" design pattern: rather than forcing a single role-holder to go through
machinery built for multiple holders (which would be either meaningless or literally impossible
to satisfy, e.g. a quorum of 2 with 1 holder), the rules explicitly recognise and simplify for the
single-holder case. When designing a Powers role that could plausibly shrink to one holder
(intentionally or via attrition), check whether its voting/quorum-gated mandates degrade sensibly
in that case, or whether they silently become impossible to satisfy — see Q2 below for the
related recovery mechanism when a role falls *below* its functional minimum.

---

## Q2 — Voting Parameters

Art. 11 (quorum for directors' meetings — collapse recovery): the quorum for directors' meetings
"must never be less than two." Critically, if the actual number of directors falls below the
quorum, "the directors must not take any decision **other than** a decision (a) to appoint
further directors, or (b) to call a general meeting so as to enable the shareholders to appoint
further directors." This is a concrete, minimal residual-mandate pattern for a role that has
collapsed below its own functional quorum: rather than either freezing entirely (no path back) or
allowing full normal operation despite the collapse (defeating the point of the quorum), the
articles carve out a narrow, specific self-repair mandate (replenish membership, or escalate to a
higher authority that can). This is directly transferable and not otherwise covered in this
library's existing sources: when a Powers role's holder count can fall below the number required
for its own `quorum`, ensure at least one narrowly-scoped mandate remains reachable even in that
state — typically a `SelfSelect`/`PeerSelect` replenishment mandate with a lower or zero quorum
requirement, or an escalation mandate to a parent/backup role — so the collapsed role is not
permanently deadlocked with no path to recovery.

Art. 47 (amendments to resolutions — amendment vs. new proposal boundary): a pending ordinary
resolution may be amended by further ordinary resolution at the same meeting, provided the
amendment is notified 48 hours in advance and "does not... materially alter the scope of the
resolution"; a pending special resolution can only be amended to fix a "grammatical or other
non-substantive error." This draws an explicit line between a minor in-flight correction (which
doesn't restart the process) and a substantive change (which must be a new proposal). Map this
onto `StatementOfIntent`/proposal-mandate design: define, even informally, what counts as a
non-substantive correction to a pending proposal (typo fixes, clarifying ambiguous wording) versus
a change requiring a fresh `votingPeriod` — without this line, a designer must choose between
never allowing in-flight corrections (rigid) or allowing arbitrary scope creep on a pending vote
(exploitable).

---

## Q4 — Dependency Chains

Art. 4 (shareholders' reserve power — non-retroactivity): shareholders may, by special resolution,
"direct the directors to take, or refrain from taking, specified action," but "no such special
resolution invalidates anything which the directors have done before the passing of the
resolution." An override/redirection mechanism is forward-looking only — it cannot be used to undo
already-completed actions. This is a directly applicable rule for any Powers override or veto
mandate reached via `Revoke_Mandates` or a member-triggered `Adopt_Mandates` redirect: the override
should gate *future* invocations of the redirected mandate, not retroactively unwind actions
already executed under it. Absent this rule being made explicit, a designer or auditor might
assume an override mandate implicitly reverses past harm — it does not, and the accountability
chain (see Q7) must supply that separately if reversal is actually needed.

---

## Q7 — Accountability and Monitoring

Art. 14 (conflicts of interest — scoped recusal with named exceptions): a director with an
interest in a proposed transaction is excluded from voting and from counting toward quorum *for
that specific decision* by default — but the articles name specific "permitted causes" where the
interested director is **not** excluded: guarantees given by/to a director for a company
obligation, ordinary share subscriptions, and standard employee-benefit arrangements that don't
single out directors for special treatment. This gives concrete texture to what should and
shouldn't trigger automatic recusal: routine, non-discretionary, generally-available arrangements
are carved out, while anything bespoke or discretionary is not. For a Powers accountability
mandate implementing conflict-of-interest recusal (excluding an interested role-holder from a
specific `StatementOfIntent` vote's quorum/tally), use this distinction to scope the recusal
mandate precisely: exclude the interested party from *that specific action's* count, not from the
role generally, and consider narrow, named exceptions for genuinely routine/non-discretionary
matters rather than either blanket recusal or no recusal rule at all.

---

## What to skip

The share-mechanics provisions (certificates, replacement certificates, transfers, transmission on
death/bankruptcy, dividend payment mechanics, capitalisation of profits) are UK share-law
administrative detail with no governance-mandate analogue in a token-less or non-share-based
Powers constitution. The directors'-indemnity-and-insurance provisions (Art. 52-53) and the
means-of-communication/company-seal provisions (Art. 48-49) are administrative/legal-formality
content. The defined-terms section (Art. 1) is interpretive scaffolding specific to this
document.

---

## Mandate implications

- When designing a delegation pattern (`AssignExternalRole` or a bespoke delegate structure),
  preserve the original grantor's ability to revoke at any point in a sub-delegation chain, unless
  permanently alienating authority is a deliberate design choice.
- Check that a role's voting/quorum-gated mandates degrade sensibly if the role shrinks to a
  single holder, rather than becoming silently unsatisfiable.
- Ensure a role that can fall below its own functional `quorum` retains at least one narrowly-
  scoped, lower-quorum self-repair mandate (replenish membership or escalate to a parent role) —
  don't let quorum collapse mean permanent deadlock with no recovery path.
- Define, even informally, the line between a non-substantive in-flight correction to a pending
  proposal and a substantive change requiring a fresh `votingPeriod`.
- Design override/veto mandates as forward-looking by default (gating future invocations) —
  don't assume they retroactively unwind already-completed actions unless that's built in
  separately.
- Scope conflict-of-interest recusal to the specific action an interested role-holder is
  conflicted on, not the role generally, and consider named exceptions for routine,
  non-discretionary matters.
