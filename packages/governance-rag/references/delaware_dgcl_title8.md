# Delaware General Corporation Law — Title 8, Delaware Code

**Citation:** State of Delaware. *Delaware Code Title 8 — Corporations* (General Corporation Law),
as amended through 85 Del. Laws, c. 275 (2026).
**Analytical level:** Structural + Parametric + Dynamic
**Most relevant design decisions:** Q1, Q2, Q3, Q4, Q6, Q7

Delaware corporate law is the most litigated, judicially refined corporate governance statute in
the US — most large American companies incorporate here specifically because of its depth. It is
the richest single source in this library's legal-regimes collection. This guide covers §§141-147
(directors/officers), §§211-220 (stockholder meetings and voting), and §§361-368 (public benefit
corporations); the remaining ~130 pages (formation mechanics, stock/dividend administration,
mergers, foreign-corporation registration, receivership) are procedural or M&A-specific and are
summarized in "What to skip."

---

## Q1 — Role Structure

§141(c)(2) (non-delegable board powers): a board committee "may exercise all the powers and
authority of the board of directors," **except** it may not approve or recommend to stockholders
any matter that legally requires stockholder approval (other than electing/removing directors),
and may not adopt, amend, or repeal bylaws. This is a precise, enumerated two-tier delegability
model: routine/operational board authority is freely delegable to a smaller committee, but
anything that would otherwise require the *full* membership's approval cannot be re-routed through
a narrower delegate, no matter how the delegation is worded. For Powers mandate design, this
sharpens the non-delegable-core-powers principle already drawn from the Swiss AG source
(`switzerland_limited_company_2023.md` Q1): rather than a vague "core purpose" test, use a
concrete rule — any mandate that constitutionally requires broad membership approval (e.g. via
`Adopt_Mandates` at a defined quorum/`votingPeriod`) should never be re-assignable to a narrower
`allowedRole` through an ordinary reform action; only a constitutional-tier change
(`MandatePackage`) should be able to touch it.

§141(d) (differential director voting power): the certificate of incorporation may give directors
elected by a specific stock class "voting powers greater than or less than those of other
directors," including in committee votes — explicit, deliberate non-uniform voting weight *within
a single governing body*, distinct from Powers' one-account-one-vote principle
(`institutionalDesign.md` §1) which applies at the ongoing-voting level. The weighting here is
fixed by the *selection* mechanism (which class elected this director), not adjusted per-vote —
structurally similar to how Powers already permits token-weighted influence only at the selection
stage (`DelegateTokenSelect`), not in ongoing governance votes. Useful as a real-world precedent
when a designer proposes non-uniform voting weight: it is not inherently illegitimate, but should
be fixed at the point a role-holder is selected/seated, not applied as a live parameter on each
vote.

§216, final sentence (member-set rules outrank board-set rules on the same topic): "A bylaw
amendment adopted by stockholders which specifies the votes... necessary for the election of
directors shall not be further amended or repealed by the board of directors" — even though the
board can normally amend bylaws, a specific rule the *membership* set on this topic is locked
against board override. This is the mirror image of the non-delegable-powers principle above:
some *rules*, once set by the broader body, cannot be unset by a narrower one that would normally
have authority over similar rules. For Powers: consider whether a mandate adopted via full-
membership vote (a high `quorum`/`votingPeriod`) should be protected from being silently reversed
by a lower-threshold reform mandate that could normally modify similar mandates — the protection
should attach to *how the rule was adopted*, not just to a fixed category of "important" rules.

---

## Q2 — Voting Parameters

§214 (cumulative voting): shareholders electing multiple directors at once may "cast all of such
votes for a single director or... distribute them among the number to be voted for" rather than
one vote per seat. This is a minority-protection aggregation rule for *multi-seat* elections,
distinct from every threshold-based aggregation rule already in this library (which addresses
single yes/no decisions): pooling votes onto fewer candidates lets a significant-but-minority
faction guarantee at least one seat, which a simple plurality-per-seat system would deny them. For
a Powers multi-seat `PeerSelect` election, consider whether voters should be able to concentrate
their vote weight on fewer candidates rather than being forced to spread it evenly — cumulative
voting guarantees proportional minority representation mathematically, at the cost of predictable
outcomes.

§215(c)(3) (plurality, not majority, for governing-body elections in nonstock/membership
corporations — the closest real-world analogue to a Powers DAO): "members of the governing body
shall be elected by a **plurality** of the votes... present," while all other matters require a
majority. This distinction matters specifically for multi-candidate races: a majority threshold
can produce no winner at all when votes split across several candidates, while plurality (most
votes wins, however many) cannot deadlock. For a `PeerSelect` election mandate with more
candidates than seats, use a plurality `succeedAt` rule rather than a majority one, reserving
majority/supermajority thresholds for binary yes/no decisions.

§216 (quorum floor, stock corporations): quorum "shall [not] consist of less than ⅓ of the shares
entitled to vote," a *proportional* floor rather than the absolute-number floors already seen from
CIC ("minimum quorum floor of 2") and Switzerland ("never less than two"). Both floor styles solve
the same problem (prevent an unrepresentatively small group from acting in the whole body's name)
but suit different scales: an absolute floor is more protective for very small/fixed-size roles, a
proportional floor scales automatically as membership grows. Choose based on whether a role's
membership size is expected to stay roughly fixed or to grow substantially over the constitution's
life.

§141(f) (unanimity for asynchronous board action): action without a meeting requires written
consent from *all* directors, not just a quorum-plus-majority — a stricter bar for asynchronous
decisions than for a live meeting vote. The implicit rationale: a meeting's live deliberation
(persuasion, real-time objection) is itself part of what makes a majority vote legitimate: remove
the meeting, and the threshold compensates by requiring everyone's assent instead. For a Powers
`PresetActions`/off-cycle decision path that bypasses the normal `votingPeriod` deliberation
window, consider whether it should require a higher `succeedAt`/quorum than the equivalent
synchronous vote, rather than reusing the same threshold — asynchronous approval without a
deliberation window is a different kind of legitimacy claim than a normal vote.

---

## Q3 — Mandate Selection

§§361-365 (public benefit corporations — mission encoding as a balancing duty, not a hard lock): a
Delaware PBC must be "managed in a manner that balances the stockholders' pecuniary interests, the
best interests of those materially affected by the corporation's conduct, and the public benefit
... identified in its certificate of incorporation." This is a structurally different mechanism
from the CIC asset lock already extensively covered in this library (a bright-line financial
constraint: cap on distributions, locked assets): the PBC model encodes mission-protection as an
*ongoing standard of conduct* directors must satisfy through judgment, not a hard numeric
constraint any mandate can mechanically check. Two design patterns for encoding mission alongside
operational flexibility, to choose between deliberately: (1) **hard-lock style** (CIC/asset-lock):
a `needFulfilled`/`value`-bounded constraint that mechanically blocks out-of-mission actions,
cheap to enforce but rigid and unable to handle judgment calls; (2) **balancing-duty style** (PBC):
a role is charged with weighing multiple named interests, reviewed under a deferential standard
(see Q7) rather than blocked mechanically — flexible and able to handle genuine trade-offs, but
harder to encode as an on-chain check and requires a working accountability review process to have
teeth at all. A Powers constitution with a genuinely multi-objective mission (not reducible to a
single financial cap) should consider the balancing-duty pattern deliberately, paired with the
disclosure-based accountability mechanism in Q7 — not default to a hard lock just because it's
easier to encode mechanically.

---

## Q4 — Dependency Chains

§211(c) (stall-recovery escalation for lapsed periodic governance cycles): if a mandatory annual
election lapses, the failure "shall not... work a forfeiture or dissolution," but after a defined
grace period (30 days past the due date, or 13 months from the last election with no date set),
"the Court of Chancery may summarily order a meeting to be held upon the application of any
stockholder or director," and critically, "the shares... represented at such meeting... shall
constitute a quorum for the purpose of such meeting, notwithstanding any provision... to the
contrary." This generalizes, at the whole-organization level, the board-quorum-collapse recovery
pattern already drawn from the UK model articles (`uk_model_articles_private_shares_2013.md` Q2):
when a routine governance cycle stalls, the recovery mechanism must be reachable *even if normal
quorum requirements are themselves part of what's broken* — hence the relaxed, forced-meeting
quorum. For a Powers constitution with a mandatory periodic re-election mandate (see
`uk_model_articles_public_2013.md` Q6), pair it with an escalation mandate reachable after a
defined grace period, with its own relaxed `quorum` (potentially even `allowedRole = PUBLIC` for
anyone to trigger), rather than assuming the normal election mandate will always eventually
succeed on its own.

§212(b), (e) (delegated voting authority defaults to revocable and time-bounded): a proxy expires
automatically after 3 years unless stated otherwise, and can only be made irrevocable if it is
"coupled with an interest sufficient in law to support an irrevocable power" — irrevocability
requires the delegate to have independent skin in the game, not just the delegation itself. This
sharpens the delegation-stays-revocable principle already drawn from the UK model articles
(`uk_model_articles_private_shares_2013.md` Q1): default any Powers vote-delegation pattern to
revocable and time-bounded, and treat a permanent, irrevocable delegation as requiring independent
justification (the delegate holding a genuine stake beyond the delegation itself), not as an
acceptable default configuration.

---

## Q6 — Adaptive Capacity and Reform

The mission-balance duty (§365, see Q3) is itself an adaptive-capacity feature: because it's a
standard of judgment rather than a fixed rule, it does not need amending every time circumstances
change the *specific* trade-off between profit and mission — the balancing standard stays
constant while its application adapts. This is a genuine advantage over a hard-coded constraint
for missions that are expected to require different trade-offs over time (compare to the rigid,
frequently-revisited nature of a fixed distribution cap). Weigh this against the accountability
cost noted in Q7 (a judgment standard is harder to enforce than a bright line) when choosing
between the two mission-encoding patterns from Q3.

The stall-recovery escalation pattern (§211(c), see Q4) is also fundamentally a Q6 pattern:
without it, a constitution's own reform/renewal machinery could become permanently unusable
exactly when it's needed most (a collapsed board or lapsed membership cycle). Treat "what happens
if this periodic mandate simply never gets invoked" as a first-class design question for every
recurring governance cycle, not an edge case.

---

## Q7 — Accountability and Monitoring

§144 (three independent safe harbors for conflicted transactions): a transaction involving an
interested director or officer is protected from challenge if **any one** of three independent
paths is satisfied: (1) disclosure to, and good-faith approval by, disinterested directors —
notably, this can be a smaller-than-normal-quorum group of disinterested directors specifically
for this purpose, since requiring a full normal quorum could make some related-party approvals
structurally impossible on a small board; (2) disclosure to and approval by disinterested
stockholders; or (3) the transaction is intrinsically fair to the corporation regardless of
process. This is a more flexible model than a single rigid recusal rule (compare
`uk_model_articles_private_shares_2013.md` Q7's scoped-recusal-with-named-exceptions): offering
multiple independent validation paths, any one of which suffices, accommodates organizations of
different sizes and structures (a small board where a strict quorum requirement would make
self-dealing review impossible vs. a large one where stockholder approval is practical) without
weakening the underlying requirement that *some* genuine, disinterested check occur. For a Powers
conflict-of-interest mandate, consider offering more than one validation path (e.g., a smaller
disinterested-role quorum OR full-membership ratification OR an objective fairness/value-bound
check) rather than a single fixed process.

§365(b)-(c) (deferential review standard for balancing-duty judgment calls): a director satisfies
the balancing duty if their decision is "informed and disinterested and not such that no person of
ordinary, sound judgment would approve" — a low bar, deliberately, and a director's *ordinary*
expected interest in the organization's general success ("ownership of... the stock") does not
itself create a disqualifying conflict for balancing decisions. This is the necessary complement
to choosing the balancing-duty mission-encoding pattern (Q3): a genuine multi-interest balancing
mandate is only workable if the accountability mechanism reviewing it applies a deferential,
good-faith-and-informed standard rather than requiring the role-holder to prove they reached an
objectively "correct" balance — otherwise every decision becomes second-guessable by any
dissatisfied party. If a Powers role is charged with balancing multiple named interests, its
accountability mandate should check for informed, good-faith process (was relevant information
considered? was there an actual, undisclosed personal conflict beyond the role's ordinary
interest?), not for a specific balance outcome.

§366 (periodic disclosure as the primary accountability mechanism for a judgment-based duty): a
PBC must, at least biennially, publish a structured statement covering (1) the objectives the
board set for the public benefit, (2) the standards adopted to measure progress, (3) objective
factual data against those standards, and (4) a self-assessment — with the certificate of
incorporation optionally requiring more frequent reporting, public availability, or third-party
certification. This is a fully specified template for accountability-through-disclosure (extending
the comply-or-explain pattern already drawn from the Swiss AG source,
`switzerland_limited_company_2023.md` Q1, from an exception-triggered disclosure into a mandatory,
structured, periodic one): for a Powers mission-balancing role, implement accountability primarily
via a mandatory, structured `StatementOfIntent`-style reporting mandate on a fixed cadence (define
objectives → define measurement standard → report data → self-assess), rather than relying solely
on ad hoc `RevokeAccountsRoleId` triggers, since the underlying duty is a judgment standard that
resists any single mechanical pass/fail check.

§367 (minimum-stake standing threshold for enforcement suits): any action to enforce the
balancing duty requires plaintiffs to hold, collectively, at least 2% of outstanding shares (or a
lesser percentage capped at $2M market value for listed companies) — a deliberate filter that
allows genuinely significant stakeholders to challenge a judgment call while blocking single-share
nuisance suits over subjective disagreements. This gives a concrete, numeric anchor to the
signal-flooding concern already raised in `ellefsen_jamte_2023.md` (Q7): for a Powers accountability
mandate challenging a *discretionary* judgment call (as opposed to a bright-line rule violation),
gate standing to initiate a formal challenge behind a minimum stake/role-weight threshold, reserving
unrestricted challenge rights for bright-line violations where frivolous-challenge risk is lower.

§145(a)-(b) (indemnification is weaker for harms to the organization itself): a role-holder acting
in good faith on the organization's behalf can be broadly indemnified for third-party claims, but
indemnification for a suit "by or in the right of the corporation" (i.e., harm to the organization
itself) is narrower — no indemnification for a matter on which the person was "adjudged to be
liable to the corporation" unless a court separately determines fairness. This distinction — good-
faith-acting-for-the-org protected broadly; actually-harming-the-org protected narrowly, even in
good faith — is a useful design principle for any Powers indemnification/legal-defense-funding
mandate: default coverage should be broader for harms to third parties than for harms to the
organization's own treasury or membership, since the org's own governance process (not an
indemnification rule) is the appropriate check on the latter.

§219-220 (burden of proof on the party withholding information): a stockholder is entitled to
inspect records "for any purpose germane to the meeting," and if the corporation refuses, "the
burden of proof shall be on the corporation to establish that the examination... is for a purpose
not germane" — disclosure is the default, and the party wanting to withhold information bears the
burden of justifying it, not the requester bearing the burden of justifying their need. Powers'
on-chain-by-default architecture already satisfies this in spirit; the explicit burden-allocation
rule is worth citing when a designer proposes an information-withholding mandate (e.g., gating
access to certain records behind a role) — the design should make the withholding role justify the
restriction, not require requesters to justify access.

---

## What to skip

Formation mechanics (§§101-139: certificate of incorporation contents, registered-agent
requirements, corporate seal/name rules), the entirety of stock/dividend administration and stock
transfer mechanics (§§151-232, largely overlapping in kind with the UK share-mechanics content
already flagged as out-of-scope in `uk_model_articles_private_shares_2013.md`), the amendment/
capital-change procedures (§§241-249), the enormous merger/consolidation/conversion subchapter
(§§251-267, M&A-specific transactional mechanics), asset-sale/dissolution/winding-up procedure
(§§271-284, mostly administrative beyond what's already covered from CIC dissolution content),
insolvency/receivership (§§291-298), certificate renewal/revival (§§311-318), close-corporation
special provisions (§§341-356, largely a smaller-scale variant of the general director/stockholder
rules already covered), foreign-corporation registration (§§371-390), and the domestication/
transfer and franchise-tax chapters are Delaware-specific administrative, transactional, or tax
procedure with no generalisable governance-mandate content beyond what's extracted above.

---

## Mandate implications

- Reserve any mandate that constitutionally requires broad membership approval from being
  reassignable to a narrower `allowedRole` through ordinary `Adopt_Mandates` reform — require a
  constitutional-tier change (`MandatePackage`) instead.
- Protect rules adopted via a high-threshold, full-membership vote from being reversed by a
  lower-threshold reform mandate that would normally have authority over similar rules — the
  protection should attach to how a rule was adopted, not to a fixed category.
- For multi-seat `PeerSelect` elections, consider cumulative voting (concentrate weight on fewer
  candidates) for minority-representation guarantees, and use plurality rather than majority
  `succeedAt` thresholds to avoid vote-splitting deadlock among more than two candidates.
- Choose a proportional (`X%` of role-holders) vs. absolute-number quorum floor based on whether a
  role's membership size is expected to grow substantially over the constitution's life.
- Require a higher approval threshold for asynchronous/off-cycle decision mandates than for
  equivalent synchronous `votingPeriod` votes, to compensate for the absence of live deliberation.
- Deliberately choose between a hard-lock (bright-line `needFulfilled`/value-bound) and a
  balancing-duty (judgment-based, deferentially-reviewed, disclosure-accountable) pattern for
  mission-protection mandates, rather than defaulting to whichever is easier to encode mechanically.
- Pair any mandatory periodic governance-cycle mandate (elections, renewals) with a
  grace-period-triggered escalation mandate that has its own relaxed quorum, so a stalled cycle
  cannot become permanently unrecoverable.
- Default vote-delegation mandates to revocable and time-bounded; require independent
  justification (the delegate holding a genuine stake beyond the delegation) before allowing
  irrevocable delegation.
- Offer multiple independent validation paths for conflict-of-interest mandates (a smaller
  disinterested-role quorum, full-membership ratification, or an objective fairness check), rather
  than a single fixed recusal process.
- For roles charged with balancing multiple named interests, review their accountability against
  an informed-and-good-faith process standard, not a specific outcome — and implement primary
  accountability via mandatory structured periodic disclosure rather than relying solely on
  triggered revocation.
- Gate standing to formally challenge a discretionary judgment call behind a minimum stake/
  role-weight threshold, reserving unrestricted challenge rights for bright-line rule violations.
- Default indemnification/legal-defense-funding mandates to broader coverage for good-faith harms
  to third parties than for harms to the organization's own treasury or membership.
- Place the burden of justification on any mandate that withholds information from role-holders,
  rather than requiring requesters to justify their need for access.
