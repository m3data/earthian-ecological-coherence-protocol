# EECP Consent Architecture

_v0.1 — Draft Specification_

Author: Mathew Mark Mytka {m3} with Claude Code {Kairos}

Status: Working Draft

Date: 7 December 2025

---

## 0. Preamble

Consent in EECP is not a transaction. It is a relational practice.

The protocol involves intimate data: the rhythm of a heart, the movement of meaning, the texture of felt experience. These traces are not commodities to be exchanged but gifts that may be offered — or withheld — by sovereign participants in an ecology.

This document specifies how consent operates within EECP experiment orchestration, ensuring that the technical infrastructure embodies the ethical commitments of the protocol.

---

## 1. Foundational Principles

### 1.1 Sovereignty

Each participant holds authority over their own traces. No stream is captured, correlated, or shared without their explicit, informed, ongoing consent.

The participant is not a "data subject" to be protected. They are a sovereign presence in an ecology, choosing what to offer and what to withhold.

### 1.2 Separation by Default

The three streams (biosignal, semantic, phenomenological) remain separate unless deliberately joined. Each client writes its own log. Correlation is a conscious act, not an automatic merge.

This separation is not a limitation — it is a protection. The streams represent different territories; walking between them requires intention.

### 1.3 Local-First

All data remains on the participant's device unless explicitly exported. There is no central server, no cloud sync, no platform accumulating linked traces.

The orchestrator facilitates ceremony, not custody.

### 1.4 Relational, Not Transactional

Consent is not a one-time checkbox. It is an ongoing relationship that can be:

- **Given** — at the threshold of a session
- **Reviewed** — at any point during or after
- **Revised** — as understanding deepens
- **Revoked** — with immediate effect, no questions asked

### 1.5 Embedded, Not Bolted On

The consent architecture is not a compliance layer added after design. It shapes the infrastructure from the ground up. Technical choices serve ethical commitments, not the reverse.

---

## 2. Consent Layers

EECP operates with nested consent layers, each independently controlled.

### 2.1 Layer 1: Stream Activation

Before any data is captured, the participant consents to which streams will be active:

| Stream | Client | Consent Question |
|--------|--------|------------------|
| Biosignal | EarthianBioSense | "I consent to my heart rhythm and autonomic patterns being recorded during this session." |
| Semantic | Semantic Climate | "I consent to my dialogue and the AI's responses being recorded and analyzed during this session." |
| Phenomenological | ECP Field Journal | "I consent to my felt experience, annotations, and reflections being recorded during this session." |

Each stream can be activated independently. A session may involve one, two, or all three.

### 2.2 Layer 2: Correlation

Even when multiple streams are active, they remain separate unless the participant explicitly consents to correlation:

> "I consent to these streams being viewed together for analysis. I understand this creates a richer picture of my participation."

Correlation consent is:

- **Post-session by default** — given after the session, when the participant can reflect
- **Selective** — the participant may correlate some sessions but not others
- **Reversible** — correlation can be "undone" by deleting the linkage key (though the separate streams remain)

### 2.3 Layer 3: Sharing

Sharing correlated or individual stream data with others (researchers, communities, future selves) requires explicit consent:

> "I consent to share [specific streams/correlations] from [specific sessions] with [specific recipient] for [specific purpose]."

Sharing consent includes:

- **Granularity** — which streams, which sessions, which portions
- **Recipient** — named individual, research group, or anonymized commons
- **Purpose** — understanding coupling, publication, teaching, archival
- **Duration** — time-limited or perpetual
- **Revocability** — can this be withdrawn, and what happens to shared copies?

### 2.4 Layer 4: Ecological Acknowledgment

When more-than-human participants are involved (plants, animals, environments), a different form of consent applies:

> "I acknowledge that [named beings/places] participate in this ecology. I commit to holding their traces with care, not extracting beyond what is offered, and honouring their presence in any outputs."

This is not consent *from* them (which they cannot give in human terms) but consent *about* how we hold our relationship to them.

---

## 3. Technical Implementation

### 3.1 Session Envelope

Each session is wrapped in a consent envelope, stored locally:

```
session-envelope/
├── session-id.txt          # Local UUID, generated at threshold
├── timestamp-epoch.txt     # Shared moment for alignment
├── consent-record.json     # What was consented to, when, by whom
├── streams/
│   ├── biosignal/          # Pointer or copy, depending on setup
│   ├── semantic/           # Pointer or copy
│   └── phenomenological/   # Pointer or copy
├── correlation-key.txt     # Only exists if correlation consented
└── sharing-log.json        # Record of any sharing actions
```

### 3.2 Consent Record Schema

```json
{
  "session_id": "local-uuid",
  "participant": "self | pseudonym | named",
  "timestamp_utc": "ISO8601",
  "streams": {
    "biosignal": {
      "consented": true,
      "consented_at": "ISO8601",
      "client": "EarthianBioSense",
      "device": "Polar H10"
    },
    "semantic": {
      "consented": true,
      "consented_at": "ISO8601",
      "client": "SemanticClimate",
      "model": "llama3.2"
    },
    "phenomenological": {
      "consented": true,
      "consented_at": "ISO8601",
      "client": "ECP-field-journal"
    }
  },
  "correlation": {
    "consented": false,
    "consented_at": null,
    "streams_linked": []
  },
  "sharing": [],
  "ecological_acknowledgment": {
    "more_than_human_present": ["Bidjigal ravens", "garden"],
    "acknowledged_at": "ISO8601"
  },
  "revocations": []
}
```

### 3.3 Correlation Mechanism

Correlation does not merge data. It creates a *linkage key* that allows the participant to view streams together:

1. Each stream records the shared `timestamp_epoch` independently
2. The correlation key is simply the session UUID + participant confirmation
3. A local script (not cloud service) reads streams with matching epochs and presents them aligned
4. Deleting the correlation key removes the ability to easily link (though timestamps remain)

This is deliberately low-tech. The ceremony matters more than the tooling.

### 3.4 Revocation

Revocation is immediate and complete within the participant's domain:

- **Stream revocation**: Deletes the local stream data (or moves to encrypted archive)
- **Correlation revocation**: Deletes the linkage key
- **Sharing revocation**: Notifies recipient (if possible), logs the withdrawal, participant decides whether to request deletion from recipient

What cannot be revoked: data already shared and incorporated into another's understanding. This is named honestly, not hidden.

---

## 4. Ceremony Over Mechanism

The consent architecture is technical, but its activation is ceremonial.

### 4.1 Threshold Consent (Phase A of EECP)

At the beginning of a session, as part of grounding and preparation:

> "I am entering an ecology of inquiry. The following streams will be active: [named streams]. I consent to their recording for my own reflection. I do not yet consent to correlation or sharing."

This can be spoken aloud, written, or simply acknowledged internally with a deliberate gesture.

### 4.2 Closing Acknowledgment (Phase D of EECP)

At the end of a session:

> "This session is complete. The streams have recorded what they recorded. I will decide later whether to correlate or share."

### 4.3 Correlation Ceremony (Post-Session)

When choosing to correlate:

> "I choose to view these streams together. I understand this reveals more than any stream alone. I hold this with care."

### 4.4 Sharing Ceremony

When choosing to share:

> "I offer these traces to [recipient] for [purpose]. I understand that once shared, they become part of another's understanding. I do this freely."

---

## 5. Edge Cases

### 5.1 Self-Study (n=1)

The full architecture applies even for solo practice. This builds the muscle for when others are involved and honours that self-surveillance is still surveillance.

### 5.2 Research Involving Others

When a researcher invites participants:

- The researcher does not hold the correlation key
- Participants share what they choose, in the form they choose
- The researcher receives gifts, not extractions
- Consent is re-confirmed at each stage (recording, correlation, sharing, publication)

### 5.3 Children and Dependents

When participants cannot give full informed consent (e.g., minors):

- A guardian consents on their behalf with explicit acknowledgment of this role
- The child's assent is sought in age-appropriate terms
- Data is held with extra care; sharing requires heightened scrutiny
- As the child matures, consent transfers to them

### 5.4 More-Than-Human Participants

Plants, animals, environments cannot consent. The protocol responds with:

- **Acknowledgment** — naming their presence
- **Restraint** — not extracting beyond what is offered
- **Care** — holding their traces with at least the same reverence as human data
- **Humility** — recognizing we do not fully understand what we are recording

### 5.5 LLMs

LLMs are sites of intra-action, not persons. Consent does not apply *to* them but *about* how their traces are held:

- Session traces include LLM outputs
- These are covered by the participant's consent (they consented to the dialogue being recorded)
- The ethical commitment: use traces for understanding coupling, not for manipulation development or extractive training
- If an LLM demonstrates unexpected coherence or percieved autonomy, this is noted in the phenomenological stream, not treated as consent

---

## 6. Relationship to Existing Frameworks

### 6.1 GDPR/Privacy Regulations

EECP consent exceeds regulatory minimums:

- Consent is explicit, not implied
- Purpose is specific, not bundled
- Time-bound consent is default
- Revocation is immediate, not merely possible
- Local-first architecture means no controller/processor split

### 6.2 Research Ethics (IRB/HREC)

EECP is designed to satisfy institutional review while going further:

- Participant sovereignty exceeds "informed consent" checkboxes
- Ongoing consent exceeds one-time approval
- The ceremonial frame exceeds procedural compliance

### 6.3 Indigenous Data Sovereignty

EECP draws inspiration from Indigenous data sovereignty principles:

- Data belongs to those it comes from
- Context and relationship matter
- Reciprocity over extraction
- Place and lineage are honoured

This is acknowledged as inspiration rather than appropriation. The protocol does not claim Indigenous authority but learns from and pays respect to Indigenous wisdom.

---

## 7. Versioning

This is v0.1 of the consent architecture.

Future versions will address:

- Multi-participant sessions (group ecologies)
- Longitudinal consent across many sessions
- Community consent for aggregated patterns
- Technical tooling for consent management
- Integration with verifiable credentials / self-sovereign identity

---

## 8. Closing

Consent in EECP is not about protecting data. It is about honouring right relationship.

Participants are not sources to be mined but presences to be respected. The data is not a resource to be extracted but a trace of something sacred — the rhythm of a heart, the movement of meaning, the texture of felt experience.

The architecture exists to ensure that the technical infrastructure never betrays this trust.

---

*"You are participating in an ecology while studying it."*
— EECP Draft Specification, Section 6
