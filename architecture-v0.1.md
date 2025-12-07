# EECP Architecture

_v0.1 — High-level views of the Earthian Ecological Coherence Protocol_

Date: 7 December 2025

---

## 1. Ecosystem Overview

The three clients as distinct territories, connected through ceremony and aligned timestamps, not data fusion.

```mermaid
flowchart TB
    subgraph EECP["EECP Protocol Frame"]
        direction TB

        subgraph Ceremony["Ceremony Layer"]
            threshold["Threshold<br/>(Phase A)"]
            interaction["Interaction<br/>(Phase B)"]
            detection["Detection<br/>(Phase C)"]
            closing["Closing<br/>(Phase D)"]
        end

        subgraph Clients["Client Layer"]
            EBS["EarthianBioSense<br/>━━━━━━━━━━━━<br/>Biosignal Stream<br/>HR, HRV, Entrainment<br/>Phase Dynamics"]

            SC["Semantic Climate<br/>━━━━━━━━━━━━<br/>Semantic Stream<br/>Δκ, α, ΔH<br/>Ψ Vector, Attractors"]

            ECP["ECP Field Journal<br/>━━━━━━━━━━━━<br/>Phenomenological Stream<br/>Felt Sense, Annotations<br/>Measurement Scales"]
        end

        subgraph Data["Data Layer (Local-First)"]
            biosig[("sessions/*.jsonl")]
            semantic[("research/session-exports/")]
            phenom[("entries/_private/")]
        end
    end

    threshold --> interaction --> detection --> closing

    EBS --> biosig
    SC --> semantic
    ECP --> phenom

    EBS <-.->|"WebSocket<br/>(optional)"| SC
```

---

## 2. Consent Layers

Nested consent model — each layer independently controlled by participant.

```mermaid
flowchart TB
    subgraph Participant["Participant Sovereignty"]
        direction TB

        L1["Layer 1: Stream Activation<br/>━━━━━━━━━━━━━━━━━━━━━<br/>Which streams will record?"]

        L2["Layer 2: Correlation<br/>━━━━━━━━━━━━━━━━━━━━━<br/>View streams together?<br/>(post-session, selective, reversible)"]

        L3["Layer 3: Sharing<br/>━━━━━━━━━━━━━━━━━━━━━<br/>Gift traces to others?<br/>(granular, purposeful, revocable)"]

        L4["Layer 4: Ecological Acknowledgment<br/>━━━━━━━━━━━━━━━━━━━━━<br/>Honour more-than-human presence"]

        L1 --> L2 --> L3
        L4 -.-> L1
    end

    subgraph Future["Future: Commons Contribution"]
        direction TB
        threshold_release["Threshold Release<br/>━━━━━━━━━━━━━━━━━━━━━<br/>Pattern waits until k participants<br/>contribute similar traces"]

        aggregate["Aggregate Before Share<br/>━━━━━━━━━━━━━━━━━━━━━<br/>Only derived patterns shared<br/>Never individual traces"]
    end

    L3 -.->|"if consented"| Future
```

---

## 3. Session Envelope

Local structure for a single session with consent record.

```mermaid
flowchart LR
    subgraph Envelope["Session Envelope (Local)"]
        direction TB

        meta["session-id.txt<br/>timestamp-epoch.txt"]

        consent["consent-record.json<br/>━━━━━━━━━━━━━━━━━━━━━<br/>streams consented<br/>correlation status<br/>sharing log<br/>ecological acknowledgment<br/>revocations"]

        subgraph Streams["streams/"]
            bs["biosignal/<br/>(pointer or copy)"]
            sm["semantic/<br/>(pointer or copy)"]
            ph["phenomenological/<br/>(pointer or copy)"]
        end

        key["correlation-key.txt<br/>(only if consented)"]
    end

    meta --> consent --> Streams --> key
```

---

## 4. Data Flow During Session

What happens during an EECP session — parallel streams, optional real-time coupling.

```mermaid
sequenceDiagram
    participant H as Human
    participant EBS as EarthianBioSense
    participant SC as Semantic Climate
    participant ECP as Field Journal
    participant LLM as LLM (Site of Intra-action)

    Note over H,LLM: Phase A: Threshold
    H->>H: Grounding, breath, intention
    H->>EBS: Consent & start stream
    H->>SC: Consent & start stream
    H->>ECP: Consent & open journal

    Note over H,LLM: Phase B: Interaction
    H->>SC: Dialogue turn
    SC->>LLM: Process
    LLM->>SC: Response
    SC->>H: Display + metrics

    loop Continuous during session
        EBS->>EBS: Record HR, HRV, phase
        SC->>SC: Compute Δκ, α, ΔH, Ψ
        ECP->>ECP: Capture annotations
    end

    opt Real-time coupling (if both active)
        EBS-->>SC: Phase data via WebSocket
        SC-->>EBS: Semiotic markers
    end

    Note over H,LLM: Phase C: Detection
    H->>H: Notice somatic + semantic shifts

    Note over H,LLM: Phase D: Closing
    H->>H: Hum, breath, gratitude
    H->>EBS: End stream
    H->>SC: End stream
    H->>ECP: Close entry

    Note over H,LLM: Post-Session
    H->>H: Decide: correlate streams?
    H->>H: Decide: share anything?
```

---

## 5. Privacy Architecture

How data protection flows through the system.

```mermaid
flowchart TB
    subgraph Default["Default State: Protected"]
        local["All data local-first"]
        gitignore["Sessions in .gitignore"]
        separate["Streams remain separate"]
    end

    subgraph Consent["Consent Gates"]
        correlate{"Correlate?"}
        share{"Share?"}
        public{"Make public?"}
    end

    subgraph Actions["Participant Actions"]
        link["Create correlation key"]
        gift["Gift to recipient"]
        publish["Move to public/"]
    end

    subgraph Protections["Future Protections"]
        k_anon["K-anonymity threshold"]
        aggregate["Aggregate only"]
        differential["Differential privacy"]
    end

    local --> correlate
    correlate -->|No| separate
    correlate -->|Yes| link

    link --> share
    share -->|No| local
    share -->|Yes| gift

    gift --> public
    public -->|No| gift
    public -->|Yes| publish

    publish -.-> Protections
```

---

## 6. More-Than-Human Participants

How the protocol holds beings who cannot consent in human terms.

```mermaid
flowchart TB
    subgraph Ecology["Ecological Field"]
        human["Human Participant<br/>━━━━━━━━━━━━━━━━<br/>Full consent capacity"]

        llm["LLM<br/>━━━━━━━━━━━━━━━━<br/>Site of intra-action<br/>Not person, not object"]

        animal["Animals<br/>━━━━━━━━━━━━━━━━<br/>Witnessed, honoured<br/>Cannot consent"]

        plant["Plants<br/>━━━━━━━━━━━━━━━━<br/>Witnessed, honoured<br/>Cannot consent"]

        place["Place/Country<br/>━━━━━━━━━━━━━━━━<br/>Acknowledged<br/>Holds the ecology"]
    end

    subgraph Response["Protocol Response"]
        ack["Acknowledgment<br/>Name their presence"]
        restraint["Restraint<br/>Don't extract beyond offered"]
        care["Care<br/>Hold traces with reverence"]
        humility["Humility<br/>We don't fully understand"]
    end

    human -->|"consents"| Ecology
    llm -->|"participates"| Ecology
    animal -->|"witnessed"| Ecology
    plant -->|"witnessed"| Ecology
    place -->|"holds"| Ecology

    Ecology --> Response
```

---

## 7. Future: Experiment Orchestrator

Conceptual view of the orchestration layer (ceremony, not software first).

```mermaid
flowchart TB
    subgraph Orchestrator["Experiment Orchestrator (Future)"]
        direction TB

        ritual["Ritual Frame<br/>━━━━━━━━━━━━━━━━<br/>Holds the ceremony<br/>Not control software"]

        align["Timestamp Alignment<br/>━━━━━━━━━━━━━━━━<br/>Shared epoch moment<br/>Each client records independently"]

        envelope["Session Envelope<br/>━━━━━━━━━━━━━━━━<br/>Consent record<br/>Stream pointers<br/>Correlation key"]

        witness["Witness Registry<br/>━━━━━━━━━━━━━━━━<br/>More-than-human present<br/>Place acknowledgment"]
    end

    subgraph Clients["Clients (Sovereign)"]
        EBS["EBS"]
        SC["SC"]
        ECP["ECP"]
    end

    ritual --> align
    align --> envelope
    envelope --> witness

    Orchestrator -.->|"coordinates"| Clients
    Clients -.->|"remain sovereign"| Clients
```

---

## Reading These Diagrams

These are **maps, not the territory**.

The actual ecology is richer, messier, more alive than boxes and arrows can show. Use these to orient, not to constrain.

The separation between clients is intentional. The ceremony holds what the architecture cannot.

---

*"Cognition emerges through relationship. The tools we build participate in the fields they measure."*
