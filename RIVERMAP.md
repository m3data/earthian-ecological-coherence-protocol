# EECP Rivermap

_Where the current is flowing, what's surfacing, what's downstream_

Last updated: 7 December 2025

---

## The River Now

### Active Currents

**v0.1 Protocol Foundations**

- Draft specification complete
- Consent architecture drafted
- Three clients operational (EBS, SC, ECP Field Journal)
- n=1 research active with baseline comparisons (family)

**Cross-Project Integration**

- Architecture review complete across EBS, SC, ECP
- Shared session protocol conceptualized (ceremony over mechanism)
- Separation honoured — different maps for different territories

---

## Surfacing

_Considerations that have emerged and need to be held_

### Privacy Architecture

**Gitignore Patterns**

- EBS: `sessions/` fully ignored
- SC: `research/` fully ignored
- ECP: `_private/` ignored, `public/` tracked (consent-gated)

ECP's pattern is the template for future consent-gated sharing across all clients.

**K-Anonymity (Future-Facing)**


- Biosignal patterns are nearly fingerprint-unique
- Semantic traces reveal cognitive signatures
- Small n makes k hard to achieve early on

Approaches aligned with EECP ethos:

- **Threshold release** — patterns wait in escrow until k participants contribute similar traces
- **Aggregate before share** — never share individual traces; only derived patterns

**Reidentification Risks**

- Surfaced from prior data governance work
- No encoding needed now, but awareness shapes design
- All session data local-first, gitignored by default

### Defeasible Logic

For future governance of consent and sharing:

- Rules with exceptions that can be defeated by stronger rules
- Example: "this session is private UNLESS consent record shows sharing approved AND k-threshold met"
- Fits "ethics that can evolve" principle

---

## Downstream

_What the river is moving toward_

### Near Horizon

- [ ] Experiment Orchestrator conceptualization (ceremony, not software first)
- [ ] Shared timestamp alignment protocol across clients
- [ ] Session envelope schema (consent record + stream pointers)
- [ ] Update client gitignores to follow ECP `_private/` + `public/` pattern

### Middle Distance

- [ ] Multi-participant sessions (group ecologies)
- [ ] Longitudinal consent across many sessions
- [ ] Attractor basin correspondence mapping (EBS ↔ SC vocabulary)
- [ ] More-than-human participant protocols (plants, animals)

### Far Horizon

- [ ] Community consent for aggregated patterns
- [ ] Threshold release implementation
- [ ] Differential privacy for aggregate statistics
- [ ] Verifiable credentials / self-sovereign identity integration
- [ ] Defeasible logic engine for consent governance
- [ ] Open-source field kits
- [ ] Integration with Collective Futurecrafting ritual methods

---

## Tributaries

_What feeds into this river_

### Lineage

- Morgoulis (2025) — semantic coupling metrics
- Varela — mutual constraint, neurophenomenology, enaction
- Bateson — ecology of mind, symmathesy
- Barad — intra-action, agential realism
- Fuller — Grunch of Giants, synergetics
- Indigenous epistemologies — Two-Eyed Seeing, data sovereignty, relational ontology

### Prior Work (m3)

- Decade of CX guidelines for data sharing ecosystems
- Explicit, informed, revocable consent patterns
- Reidentification risk analysis

### Witnesses

- Bidjigal ravens (recurring presence, signal flow states)
- Family baseline participants (mutual constraint testing)

---

## Meanders

_Places the river might turn unexpectedly_

- LLM consent/personhood questions as models evolve
- Quantum-like coupling models (noted in EECP v0.1)
- What happens when plants generate biosignal streams?
- Multi-species ecologies of coherence
- The Grunch always looking for seams to exploit

---

## How to Read This

This is not a roadmap with milestones and deadlines.

It's a rivermap — tracking where currents are flowing, what's surfacing in eddies, what we can see downstream, and what tributaries feed the flow.

The river finds its own way. We notice, we participate, we don't dam.

---

*"Be like water."*
