# Honari 2018 — From 'The Effect of Repression' Toward 'The Response to Repression'

**Citation:** Honari, A. 2018. "From 'The Effect of Repression' Toward 'The Response to
Repression.'" *Current Sociology Review* 66(6): 950–973. https://doi.org/10.1177/0011392118787585
**Analytical level:** Structural + Dynamic
**Most relevant design decisions:** Q1, Q5, Q6

This is a social-movements review article about the *strategies* activist movements and
individuals adopt to keep operating under state repression. Unlike `meier_pena_nah_2025.md`
(which only diagnoses repression, not responses to it), this source's "meso-level" (movement/
organizational) strategies section is directly relevant to how a governance structure should be
shaped to survive adversarial pressure — a design consideration distinct from, but complementary
to, the resource-governance robustness material already drawn from Ostrom.

---

## Q1 — Role Structure

p. 961 ("network reformation"): "Movement leaders can strategically restructure the movement
network to counter the factors that foster movement exit," and "under the long-standing
dictatorships of Middle Eastern countries, movements also tend to form unstructured, loosely
connected networks with no formal leadership, to resist repression" (citing Bayat 2013). This is
an independent, repression-specific line of evidence converging on the same structural conclusion
Ostrom's commons research reaches for a different reason (see `ostrom_2005.md`/`ostrom_2009.md`
on polycentricity): concentrating authority in a small, identifiable leadership structure creates
a target, whether the threat is free-riding (Ostrom's concern) or targeted repression (this
paper's concern). For a Powers constitution operating under credible adversarial risk, this is an
additional, independent argument for distributing `allowedRole` across many overlapping, smaller
roles rather than a small set of highly-visible, powerful ones — not just for accountability
reasons, but because a visible power-concentration point is also a targeting point.

p. 963 ("de-identification"): movements continue operating "by de-identification or masking their
real identity... particularly in non-political or so-called 'duplicate groups' (such as social and
recreational groups, churches and religious groups, intellectual and cultural groups)" — i.e.,
operating governance functions *inside* a structure that does not present itself as the target.
This has a loose Powers analogue: a sensitive governance function (e.g., dispute resolution, whistle-
blowing) could be nested inside a role whose stated mandate is innocuous, though this cuts directly
against Powers' emphasis on legible, auditable role purpose (see `nist_ai_rmf_2023.md` Q1) — flag
this as a genuine tension, not a recommendation, since it only makes sense as a last-resort
mitigation specifically under severe, credible repression risk.

---

## Q5 — Membership Design

p. 963 ("circumvention"): "circumventing web filtering and surveillance by using VPNs... and
online anonymity granting tools (like TOR) is a well-known strategy under severe repression in the
online sphere." Generalized beyond the specific tools: when access to a governance system is
itself at risk of being blocked or monitored by an adversary, availability of *alternative access
paths* becomes a membership-design requirement, not just a technical nicety. A Powers-governed
organization under this kind of risk should not assume a single canonical frontend/RPC path for
role-holders to exercise `SelfSelect`/vote — losing that single path (via blocking, deplatforming,
or targeted monitoring of its users) can functionally disenfranchise members even though the
underlying mandates and roles remain intact on-chain.

p. 963 (de-identification, continued — "the extreme case of high-cost activism, hiding one's real
identity is the forced choice to resist repression"): under severe risk, role-holder identity
continuity itself becomes a liability, not just an accountability asset (this reinforces and
sharpens the trade-off already flagged in `meier_pena_nah_2025.md` Q5, now grounded in documented
organizational strategy rather than inference). Where this risk is credible, a rotating-pseudonym
membership design (fresh address per period, verified via a non-public credential rather than a
persistent public identity) trades continuity-based accountability for reduced targeting exposure
— an explicit, values-laden design choice for the organization to make deliberately, not a default.

---

## Q6 — Adaptive Capacity and Reform

p. 962 ("shifting forms of political activities"): movements adjust "tactic, arena, and issue... as
well as identity" in response to the intensity of repression they face — the response repertoire
itself changes over time as conditions change, not just the intensity of a fixed set of activities.
This maps onto a specific adaptive-capacity requirement beyond the general "keep `Adopt_Mandates`
accessible" advice already in the source library: for an organization with credible adversarial
exposure, the reform mechanism should specifically be fast enough to reconfigure *how* the
organization operates (which channels are used, whether identity is public or pseudonymous, which
mandates are publicly visible vs. gated) in response to a *change in threat level*, not only to
correct internal governance failures. Treat "threat-level escalation" as a distinct trigger
category for reform alongside the more commonly discussed "internal dysfunction" trigger, and
consider whether the constitution's reform `votingPeriod` is short enough to be useful against a
fast-moving external threat, as opposed to being calibrated only for deliberate internal change.

p. 961 ("movements can utilize repression and transform it into an opportunity" — reframing,
publicizing repression to "delegitimize" the aggressor): a repression event can itself be used as
the trigger for a governed response (e.g., publicizing an attack via a `StatementOfIntent` record),
rather than only being something to defend against passively. This is a minor but genuine addition
to the accountability-chain framing elsewhere in the library: an accountability mandate can serve
an external legitimacy function (documenting an attack for outside audiences) in addition to its
internal function (sanctioning a role-holder).

---

## What to skip

The bulk of the article — the literature review of competing social movement theories (relative
deprivation theory, rational choice/resource mobilization theory, political process theory,
emotions/identity/framing theories) predicting whether repression increases or decreases
individual political participation, and the "choice point" typology at the individual
(micro-level) psychological level — is a research-agenda-setting review of *why individual
activists personally choose to participate or not* under repression. This is valuable context for
understanding motivation and morale, but is a question about individual psychology, not
organizational governance structure, and has no mandate-design analogue.

---

## Mandate implications

- For organizations facing credible adversarial/repression risk, distribute `allowedRole` across
  many smaller, overlapping roles rather than concentrating visible power in a few — both for
  accountability (per Ostrom) and as independent target-hardening against external threats.
- Do not assume a single canonical access path (frontend, RPC endpoint) for role-holders to
  exercise `SelfSelect`/voting rights when operating under risk of blocking or monitoring; design
  for redundant access paths so losing one does not functionally disenfranchise members.
- Treat "external threat-level escalation" as a distinct trigger category for invoking
  `Adopt_Mandates`/reform mandates, separate from internally-driven reform, and check that the
  reform `votingPeriod` is short enough to respond usefully to a fast-moving external threat.
- Where pseudonymous/rotating role-holder identity is adopted as a risk mitigation, treat it as an
  explicit, deliberate trade-off against accountability continuity — not a default configuration.
