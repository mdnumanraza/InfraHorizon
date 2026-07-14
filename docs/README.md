# infraHorizon — Documentation

> The long-term vision is an interactive visualization platform that transforms live infrastructure behavior into interactive execution graphs for learning, debugging, and operational understanding.

---

## What Is infraHorizon?

```mermaid
graph TB
    subgraph LIVE["Live Infrastructure (Source of Truth)"]
        K8S[Kubernetes Cluster]
        GH[GitHub Actions<br/><i>future</i>]
        ARGO[Argo CD<br/><i>future</i>]
        OTHER[Other Platforms<br/><i>future via plugins</i>]
    end

    subgraph CORE["infra-observer Platform"]
        direction TB
        EV[Event Collector<br/><i>live events, not polling</i>]
        EG[Execution Graph Engine<br/><i>converts events → graphs</i>]
        VIZ[Interactive Visualization Layer<br/><i>explore, debug, understand</i>]
    end

    subgraph USERS["Who Uses It"]
        DEV[Engineers<br/><i>debugging behavior</i>]
        LEARN[Learners<br/><i>understanding distributed systems</i>]
        OPS[Operators<br/><i>operational awareness</i>]
    end

    K8S -->|"Watch API<br/>(live events)"| EV
    GH -.->|"future"| EV
    ARGO -.->|"future"| EV
    OTHER -.->|"plugin SDK<br/>(future)"| EV

    EV --> EG
    EG --> VIZ

    VIZ --> DEV
    VIZ --> LEARN
    VIZ --> OPS

    style LIVE fill:#1e293b,stroke:#475569,color:#e2e8f0
    style CORE fill:#0f172a,stroke:#3b82f6,color:#e2e8f0
    style USERS fill:#1e293b,stroke:#475569,color:#e2e8f0
    style K8S fill:#326ce5,stroke:#326ce5,color:#fff
    style EV fill:#1d4ed8,stroke:#3b82f6,color:#fff
    style EG fill:#1d4ed8,stroke:#3b82f6,color:#fff
    style VIZ fill:#1d4ed8,stroke:#3b82f6,color:#fff
    style GH fill:#374151,stroke:#6b7280,color:#9ca3af
    style ARGO fill:#374151,stroke:#6b7280,color:#9ca3af
    style OTHER fill:#374151,stroke:#6b7280,color:#9ca3af
```

**Solid lines** = V0 scope (Kubernetes, live events via Watch API).
**Dashed lines** = future roadmap items via plugin architecture.

This is **not** a Kubernetes dashboard, replacement, or simulator. It is a platform for making distributed system behavior *understandable*.

---

## Documentation Map

| Document | ID | Description |
|----------|----|-------------|
| [Documentation Architecture Blueprint](documentation-architecture-blueprint.md) | `DOC-001` | How all documentation is governed — the meta-layer. Start here to understand how this repo is organized. |
| `charter.md` *(pending)* | `CHAR-001` | Project constitution — mission, principles, values, non-goals. |
| `roadmap.md` *(pending)* | `DOC-002` | Version roadmap — where the project is going. |
| `product/prd.md` *(pending)* | `PRD-001` | Product Requirements Document — what V0 builds and why. |
| `product/requirements/` *(pending)* | `REQ-F/NF` | Functional and non-functional requirements. |
| `architecture/overview.md` *(pending)* | `ARCH-001` | High-level system architecture. |
| `architecture/tech-stack.md` *(pending)* | `ARCH-002` | Technology stack proposals and decision. |
| `architecture/adr/` *(pending)* | `ADR-NNN` | Architecture Decision Records. |
| `engineering/` *(pending)* | `ENG-001…` | Coding standards, testing strategy, development workflow. |
| `planning/v0/` *(pending)* | `PLAN-001…` | V0 goals, phases, Definition of Done, risk register. |

Documents marked *(pending)* are planned per the [execution plan](../.claude/v0-documentation-execution-plan.md) and will be added as Version 0 progresses.

---

## Where to Start

- **Understand the project rules →** [Documentation Architecture Blueprint](documentation-architecture-blueprint.md)
- **Understand what we're building →** `charter.md` *(coming next)*
- **Understand V0 scope →** `product/prd.md` *(coming after charter)*
