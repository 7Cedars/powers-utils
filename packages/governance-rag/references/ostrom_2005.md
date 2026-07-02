# Ostrom 2005 — Understanding Institutional Diversity

**Citation:** Ostrom, Elinor. 2005. *Understanding Institutional Diversity.* Princeton, NJ:
Princeton University Press.
**Analytical level:** Structural + Parametric + Dynamic
**Most relevant design decisions:** Q1, Q2, Q4, Q5, Q6, Q7

---

## Q1 — Role Structure

Ch. 5, pp. 139–142 (the ADICO grammar, with S. Crawford): every institutional statement
decomposes into [ATTRIBUTES] [DEONTIC] [AIM] [CONDITIONS] [OR ELSE]. Rules contain all five
components; norms drop OR ELSE; shared strategies drop DEONTIC and OR ELSE. In Powers, a mandate
is always a full rule (ADICO complete) because on-chain execution enforces the OR ELSE
automatically — there is no such thing as an unenforced Powers "norm." Map the components
directly onto mandate design: ATTRIBUTES → `allowedRole`; DEONTIC → the mandate type chosen
(`PresetActions`/`BespokeAction_*` for obliged/forbidden-by-omission actions, `OpenAction` for
broadly permitted ones); AIM → the target function/state change; CONDITIONS → `votingPeriod`,
`timelock`, `needFulfilled`; OR ELSE → the accountability mandate that fires on non-conformance
(`RevokeAccountsRoleId`, `PauseMandates`). Use this decomposition as a drafting checklist: a
mandate missing an explicit OR ELSE path is a norm dressed up as a rule, and will not actually
be enforced against a determined violator.

p. 142 (DEONTIC operators are interdefinable — P, O, F): permitted, obliged, and forbidden can
always be rewritten in terms of one another. In Powers this means the same governance intent
can often be encoded either as a broad `allowedRole` with no explicit prohibition, or as a
narrow `allowedRole` with an explicit fallback mandate covering the forbidden case. Prefer
the encoding that keeps the "forbidden" case impossible to reach (narrow `allowedRole`, no
mandate exists for the excluded actor) over one that relies on a permitted-but-punished pattern
(broad `allowedRole` + an accountability chain to catch misuse after the fact) whenever the
excluded action would be costly to reverse.

pp. 193–194 (position rules, Ch. 7): every position may carry a defined lower bound, upper
bound, both, or neither on the number of participants who can hold it. A quorum rule is a
position rule with a defined lower bound and no upper bound; a capped executive committee is a
position rule with a defined upper bound and no lower bound. In Powers: `PeerSelect`'s
`numberToSelect` is an upper-bound position rule; `quorum` in `Conditions` is a lower-bound
position rule on the *voting* population, not the position itself. Design both bounds
deliberately — an upper bound with no lower bound (a role that can shrink to zero holders) can
silently disable every mandate gated on that `allowedRole`.

---

## Q2 — Voting Parameters

pp. 202–206 (aggregation rules, Ch. 7): aggregation rules fall into three families.
**Nonsymmetric** rules (a single "expert"/dictator position, an oligarchy subgroup, a weighted
vote, a committee-then-full-body two-step) treat positions unequally. **Symmetric** rules
(unanimity, simple majority, supermajority) treat all voting participants alike — Powers' flat
one-account-one-vote model (per `institutionalDesign.md` §1) is a symmetric aggregation rule by
construction; any nonsymmetric weighting must be introduced at the *selection* stage
(`DelegateTokenSelect`) rather than the voting stage. **No-agreement rules** specify what
happens if the vote fails to reach threshold: revert to status quo, zero out the outcome, assign
randomly, or defer to an external decision-maker. Powers' implicit no-agreement rule is "the
action simply does not execute" (status quo) — this is a design choice, not a neutral default,
and should be stated explicitly when specifying `votingPeriod`/`quorum`/`succeedAt`, especially
for mandates where "nothing happens" is itself costly (e.g., an expiring emergency response).

p. 205: empirically, the specific no-agreement rule used has a *larger* effect on outcomes than
the aggregation threshold itself (citing Grether, Isaac & Plott's landing-slot experiments).
Use this when a `votingPeriod` design keeps failing to reach quorum: the fix may be to change
what happens on failure (e.g., an automatic quorum-waiver re-vote, as in the CIC model articles)
rather than to lower the threshold.

---

## Q4 — Dependency Chains

pp. 149–151 (OR ELSE, Ch. 5): a valid OR ELSE must (1) result from a collective decision, (2) be
backed by a further rule that shifts the DEONTIC of some action for at least one actor under the
non-conformance condition, and (3) affect the constraints facing whoever is responsible for
monitoring. In Powers: an accountability mandate (`RevokeAccountsRoleId`, `PauseMandates`) is not
optional decoration on an execution mandate — without it, the execution mandate's OR ELSE
component is empty and the "rule" functions only as a norm with no enforcement path. Every
mandate with real consequences needs a designed OR ELSE chain, not an assumed one.

pp. 200–210 (choice rules vs. scope rules, Ch. 7): choice rules constrain *actions* (who may do
what); scope rules constrain *outcomes* (what states of the world may result, regardless of the
action taken to get there). This is a design axis distinct from `allowedRole`: a treasury mandate
can be constrained either by restricting *who* can call it (choice/`allowedRole`) or by
restricting *what value/target* the call can produce (scope/`target` and `value` bounds in the
mandate config), independent of caller. The CIC asset lock is a pure scope rule — it constrains
the outcome (funds leaving to non-asset-locked recipients) regardless of which role initiates the
transfer. Use scope rules when the AIM to prevent is the outcome itself, not who causes it; use
choice rules when the risk is specifically about who is trusted to act.

p. 192 (rule configuration interdependence): a rule's CONDITION or OR ELSE
component can affect a different part of the action situation than its AIM most directly targets
— rules are never fully independent. Cross-check `needFulfilled`/`needNotFulfilled` chains for
this: a mandate whose AIM is role assignment (a boundary/electoral rule) but whose OR ELSE
imposes a payoff consequence (e.g., forfeiting a bond) is simultaneously a boundary rule and a
payoff rule, and both effects must be reviewed when the mandate changes.

---

## Q5 — Membership Design

pp. 194–200 (boundary rules, Ch. 7 — the most detailed treatment in the source library): entry
rules are **open** (any eligible participant may join at will — `SelfSelect`), **invitational**
(existing holders select from eligibles — `PeerSelect` following `Nominate`), **competitive**
(participants compete in a separate action situation, e.g. an election — `PeerSelect` with
multiple nominees, or `DelegateTokenSelect`), or **compulsory** (no participant control over
entry — has no clean Powers equivalent; flag as a gap if a design calls for mandatory role
assignment). Exit rules are independently: **voluntary** (`RenounceRole`), **involuntary/for
cause** (`RevokeAccountsRoleId`), or **term-based/automatic** (fixed terms with no eligibility to
succeed oneself, or automatic lapse — `RevokeInactiveAccounts`, or a `PresetActions` mandate that
un-assigns a role after a block-height condition). Entry and exit rules are independent design
choices — a role can be open-entry with for-cause-only exit (sticky membership) or
invitational-entry with automatic term-limited exit (rotating gatekept membership). Always specify
both explicitly; a design that only specifies entry silently defaults to "no exit mechanism,"
which p. 121 (via the 2011 paper) already flags as a completeness gap.

pp. 197–198 ("succession rules"): civil-service (tenure + qualification), seniority
(longest-serving is promoted), and patronage (a "patron" position decides) are three distinct
succession patterns for moving between positions. In Powers, `RoleByRoles` implements a
qualification-based succession pattern (holding role X qualifies for role Y); a seniority pattern
has no direct mandate equivalent and would need an off-chain-computed eligibility list fed through
`Adopt_Mandates`; a patronage pattern is simply a `PeerSelect`/`AssignExternalRole` gated to a
single-holder role.

pp. 198–200 (exit rules and control): the degree of control a position-holder has over their own
exit (full self-control, as in most resignations, vs. no control, as in a fixed term with no
early exit) is itself a fundamental limit on how much power others can exert over that
position-holder. A role with `RenounceRole` available is structurally less coercible than one
without it, independent of any other design feature — use presence/absence of a voluntary exit
mandate as a quick check on whether a role is being used to trap participants rather than govern
them.

---

## Q6 — Adaptive Capacity and Reform

pp. 272–281 (five threats to the sustainability of self-governed institutions): (1) **rapid
exogenous change** outpacing the org's ability to adjust — argues for keeping `Adopt_Mandates`
broadly accessible rather than admin-gated, so reform speed can match environmental change speed;
(2) **transmission failure** — successor members follow rules by rote without understanding the
underlying rationale, and begin finding self-favoring "loopholes" that erode the rule's intent
over time (p. 274, the irrigation-labor example) — a purely on-chain constitution is vulnerable
to this exact failure mode unless paired with off-chain documentation of *why* each mandate
exists, not just what it does; (3) **blueprint thinking** — copying a governance template
wholesale without adapting it to the specific resource, community, and stakes involved — a direct
warning against deploying a stock Powers constitution unmodified; (4) **corruption/rent-seeking**,
concentrated where administratively-created scarcity or subsidy lets a gatekeeping role extract
value — flag any mandate that gives a role discretionary control over an artificially scarce
resource (e.g., a treasury with below-market internal pricing) as a design location to add extra
accountability; (5) **lack of large-scale supportive institutions** — a self-governing
organization still needs external, higher-level sources of reliable information and low-cost
dispute resolution that it cannot produce for itself — in Powers, this maps to `ExternalAction_*`
and `CheckExternalActionState` dependencies on trusted external contracts/oracles, and is a
reminder that full self-containment is not always achievable or even desirable.

p. 273 (transmission failure, mechanism detail): erosion starts small — one participant makes a
self-favoring interpretation of an ambiguous rule, others observe and copy it, and the cumulative
effect unravels the original bargain, without any single violation being an obvious breach. In
Powers, ambiguous `inputParams` or wide `target`/`value` ranges on a `BespokeAction_*` mandate
create the on-chain equivalent of this ambiguity; tightening scope rules (see Q4) closes the gap
that individual "reasonable" interpretations would otherwise exploit one at a time.

---

## Q7 — Accountability and Monitoring

pp. 258–270 (the eight Design Principles — canonical, most complete statement in the source
library): (1) clearly defined boundaries (resource and membership); (2) proportional equivalence
between benefits and costs; (3) collective-choice arrangements (those affected by a rule can help
change it); (4) monitoring, by monitors accountable to or drawn from the user group itself; (5)
graduated sanctions; (6) low-cost, rapid conflict-resolution mechanisms; (7) minimal external
recognition of the group's right to self-organize; (8) nested enterprises for larger systems. Use
this as the master completeness checklist for any constitution — for each principle, name the
specific mandate or parameter that implements it, and treat an unaddressed principle as a named
gap rather than an implicit assumption.

p. 267 (graduated sanctions, mechanism detail): the *first* sanction in a well-functioning
graduated chain is calibrated to carry no real cost — it functions as *information* ("you were
noticed"), not punishment, and preserves the violator's trust that the community is still
extending good faith. Sanctions escalate only on repeated violation. In Powers: the first step of
an accountability chain (e.g., `StatementOfIntent` recording a formal notice, or a `PauseMandates`
that only throttles rather than revokes) should be deliberately low-stakes and reversible; jumping
straight to `RevokeAccountsRoleId` on a first infraction skips the signalling function that
graduated sanctions rely on to preserve long-run cooperation.

p. 261 (boundary defense, extending Design Principle 1): Morrow & Hull's field-tested
reformulation is that boundaries must not just be *defined* but *defensible* — a resource/role
boundary that appropriators (or role-holders) cannot actually enforce against outsiders is
formally compliant but substantively unprotected. Check that a `target`/`allowedRole` restriction
is paired with an actual enforcement mandate (accountability chain), not just a documented
intent.

---

## What to skip

Parts I–IV (chs. 1–4: the general IAD framework overview, laboratory trust/commons-dilemma
experiments, and the evolutionary game theory of norm emergence) are foundational and largely
duplicated, at the level needed for mandate design, by the material already extracted in
`ostrom_2009.md` and `ostrom_2011.md`. The delta-parameter formalism for modeling DEONTIC effects
on game payoffs (pp. 146–148) is a technical modeling tool for game-theoretic analysis, not a
design rule. The extensive field-study citations throughout (Nepal irrigation, Ugandan forests,
Ecuadorian comunas, etc.) are evidentiary support for the principles above rather than
independently actionable claims. The closing polycentricity discussion (pp. 281–287) restates
material already covered in more directly actionable form in `ostrom_2009.md`.

---

## Mandate implications

- Treat every mandate as requiring a complete ADICO structure: an `allowedRole` (ATTRIBUTES), a
  clear obligation/permission logic in the mandate type chosen (DEONTIC), a specific target state
  change (AIM), explicit `votingPeriod`/`timelock`/`needFulfilled` (CONDITIONS), and a paired
  accountability mandate (OR ELSE). A mandate with no OR ELSE path is unenforced by construction.
- Specify the no-agreement outcome for every voting mandate explicitly (status quo / null / retry)
  rather than relying on the implicit "action does not execute" default — and prefer an automatic
  retry/quorum-waiver pattern over a hard failure for mandates where inaction is itself costly.
- When restricting a treasury or sensitive-outcome mandate, decide explicitly whether the risk is
  about *who* acts (use `allowedRole`) or *what outcome* results (use `target`/`value` scope
  bounds) — asset-lock-style protections should be encoded as scope rules, not caller
  restrictions, so they survive role/membership turnover.
- Specify entry and exit mechanisms for every role independently — a role's coercibility is
  determined largely by whether it has a `RenounceRole` exit path, independent of every other
  design feature.
- Use the eight Design Principles as a named checklist against every constitution: for each
  principle, cite the specific mandate that implements it, and treat gaps as explicit, documented
  trade-offs rather than oversights.
- Calibrate the first step of any accountability/graduated-sanction chain to be low-cost and
  reversible (notice, not punishment) — reserve `RevokeAccountsRoleId` for repeated or severe
  violations, consistent with cross-cutting rule 7 already in `reading_guide.md`.
