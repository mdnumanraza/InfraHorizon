# infraHorizon — Project Knowledge Base

> **This is the canonical context document for all contributors and AI assistants.**
> Read this first. When in doubt, this document is the starting point.
>
> **Update cadence:** progress-related sections (Current Goal, Completed Goals, Upcoming Goals) are updated after every Goal completion. Mission, Philosophy, and Principles remain stable.

---

## AI Reading Order

Before beginning any work on this project, read the following documents in this exact order:

1. **This document** — `KNOWLEDGE_BASE.md`
2. **Project Charter** — `docs/charter.md` (CHAR-001) *(pending — Milestone 1)*
3. **Documentation Architecture Blueprint** — `docs/documentation-architecture-blueprint.md` (DOC-001)
4. **Roadmap** — `docs/roadmap.md` (DOC-002) *(pending — Milestone 1)*
5. **Current Goal documentation** — see §6 (Current Goal) below
6. **Active ADRs** — `docs/architecture/adr/` *(pending — Milestone 3)*

Do not begin implementation without completing this reading sequence. Architecture and documentation must be approved before implementation begins.

---

## 1. Mission

> Build an event-driven infrastructure visualization platform that transforms live infrastructure behavior into interactive execution graphs for learning, debugging, and operational understanding.

The mission is **permanent**. Every feature, decision, and roadmap item is tested against it.

---

## 2. North Star

A future where engineers and learners can connect to any live infrastructure system and immediately see its behavior as an interactive, explorable execution graph — making distributed systems understandable to anyone, not just those who built them.

---

## 3. What This Project Is — and Is Not

**It is:**
- An event-driven visualization platform
- A learning and debugging tool
- A system that connects to real infrastructure (not simulations)
- An open-source, extensible platform with a plugin architecture (future)

**It is not:**
- A Kubernetes dashboard
- A Kubernetes replacement or simulator
- A monitoring or alerting tool
- An infrastructure management platform

---

## 4. Product Philosophy

- **Real systems only.** We connect to live infrastructure. Simulations and mocks are not the product.
- **Live over polling.** Event-driven wherever possible. Polling is a fallback, not a design choice.
- **Understanding over features.** Every feature must have educational value. If it doesn't help someone understand what's happening, it doesn't belong.
- **Simplicity over completeness.** A lean, correct foundation is worth more than a wide, fragile one.
- **Architecture first.** Every implementation follows approved design. Documentation precedes code.

---

## 5. Core Principles

1. We connect to **real systems**, not simulated ones.
2. Kubernetes is the source of truth (in V1+; V0 is foundation only).
3. Live events are preferred over polling whenever possible.
4. Every feature must have educational value.
5. Every version must be independently usable.
6. Every version must end in a releasable state.
7. Architecture is more important than feature count.
8. Extensibility must be considered but not prematurely implemented.
9. We prefer simplicity over completeness.
10. No feature should be added simply because Kubernetes supports it.

**The Charter Rule:** Every roadmap item, feature, architecture decision, and future plugin must answer: *"Does this move the project toward the mission?"* If the answer is no, it is not included.

---

## 6. Roadmap Overview

| Version | Theme | Status |
|---------|-------|--------|
| **V0** | Foundation — architecture, standards, documentation | **Active** |
| V1 | Kubernetes Workload Visualization | Planned |
| V2 | Networking | Planned |
| V3 | Storage | Planned |
| V4 | Security | Planned |
| V5 | Kubernetes Plugin Extraction | Planned |
| V6+ | External Platform Plugins | Planned |
| Future | RCA Engine | Roadmap |
| Future | Plugin SDK | Roadmap |

Only V0 is being designed and implemented. Future versions are roadmap placeholders only — they are **not** being designed.

---

## 7. Current Version: V0 — Foundation

**Objective:** Build a stable architectural foundation capable of supporting future development.

V0 is primarily a planning and documentation milestone. No Kubernetes visualization, no plugins, no AI, no auth.

**V0 Deliverables:**
- Stable project structure
- Technology stack finalized
- Architecture documented
- Repository structure finalized
- Development workflow finalized
- Documentation structure finalized
- Initial development environment
- Definition of Done established
- Coding standards defined
- Testing strategy documented

---

## 8. V0 Documentation Milestones

V0 documentation executes across five milestones (see `.claude/v0-documentation-execution-plan.md`):

| Milestone | Documents | Status |
|-----------|-----------|--------|
| **M1 — Foundation** | Charter (`CHAR-001`), Roadmap (`DOC-002`) | ✅ Complete |
| **M2 — Product** | PRD (`PRD-001`), Functional Reqs, Non-Functional Reqs | 🔄 In Progress |
| **M3 — Architecture** | Overview (`ARCH-001`), Tech Stack (`ARCH-002`), ADRs | 🔲 Pending |
| **M4 — Engineering** | Coding Standards (`ENG-001`), Testing Strategy (`ENG-002`), Dev Workflow (`ENG-003`) | 🔲 Pending |
| **M5 — Planning** | Goals (`PLAN-001`), Phases (`PLAN-002`), DoD (`PLAN-003`), Risk Register (`PLAN-004`) | 🔲 Pending |

**Completed (pre-milestone):**
- ✅ Documentation Architecture Blueprint (`DOC-001`) — approved and frozen
- ✅ V0 Documentation Execution Plan — internal working guide
- ✅ Repository foundational files (`README.md`, `CONTRIBUTING.md`, `KNOWLEDGE_BASE.md`, etc.)

---

## 9. Current Goal

**Goal:** Complete V0 Milestone 2 — Product Definition

**Documents to produce:**
1. `docs/product/prd.md` (PRD-001) — ✅ Approved and frozen
2. `docs/product/requirements/functional-requirements.md` (REQ-F-001) — ✅ Approved and frozen
3. `docs/product/requirements/non-functional-requirements.md` (REQ-NF-001) — 🔄 Next

**Status:** Two of three M2 documents complete. Writing REQ-NF-001 next.

**Blocked by:** Nothing.

**Next after this goal:** Milestone 3 — Architecture (ARCH-001, ARCH-002, ADRs).

---

## 10. Completed Goals

| Goal | Outcome | Date |
|------|---------|------|
| Establish documentation governance | DOC-001 (Documentation Architecture Blueprint) approved and frozen | 2026-07-12 |
| Create V0 execution plan | `.claude/v0-documentation-execution-plan.md` accepted as working guide | 2026-07-12 |
| Establish repository foundation | README, CONTRIBUTING, KNOWLEDGE_BASE, CODE_OF_CONDUCT, SECURITY, decision log, contributor reference created | 2026-07-14 |
| Complete M1 — Project Foundation | CHAR-001 (Charter) and DOC-002 (Roadmap) approved and frozen | 2026-07-14 |

---

## 11. Accepted Decisions

Key decisions already made. Full log in `docs/decision-log.md`.

| ID | Decision | Rationale |
|----|----------|-----------|
| DOC-001 | Documentation-first, repository-only, Git-as-history | Lean OSS model; no external wiki |
| — | Requirements separate from PRD | Requirements evolve per-version; PRD is stable intent |
| — | `CHAR` identifier namespace reserved for Project Charter | Charter is the constitutional root; deserves its own ID family |
| — | No success metrics in the Charter | Metrics evolve; they live in PRD/planning, not the constitution |
| — | Approval tiered by document reach | Engineering → PM; Architecture → PM+Owner; Vision → Owner |
| — | GitHub Flow (not Git Flow) | Lightweight; no release branches needed at V0 scale |
| — | Single active task per contributor (not globally serial) | Enables collaboration without integration chaos |

---

## 12. Rejected Ideas

Ideas explicitly considered and rejected, with reasons. Recorded to prevent re-debating.

| Idea | Rejected Because |
|------|-----------------|
| Confluence / Notion for docs | Repository-first is the approved standard (DOC-001) |
| Merge Functional + NFR into PRD | Requirements evolve independently; separation improves long-term maintainability |
| Success Metrics in the Charter | Metrics evolve; they violate the Charter's near-frozen nature |
| Git Flow branching model | Heavier than needed for V0; GitHub Flow is sufficient |
| Diagrams folder (binary images) | Diagrams are inline Mermaid in the doc they belong to (DOC-001 §8) |
| Plugin architecture in V0 | Explicitly out of scope; extensibility is considered, not built |
| Per-document changelogs | Git is the history; in-document changelogs are redundant |

---

## 13. Glossary

| Term | Meaning |
|------|---------|
| **Charter Rule** | The scope-creep test: "Does this move the project toward the mission?" If no, it's excluded. |
| **Execution Graph** | A visual, interactive representation of infrastructure behavior derived from live events. |
| **Event-driven** | The platform reacts to live events from infrastructure rather than periodically polling for state. |
| **Plugin** | A future extension that allows infra-observer to connect to platforms beyond Kubernetes. |
| **ADR** | Architecture Decision Record — a short document capturing a design decision and why it was made. |
| **DOC-001** | The Documentation Architecture Blueprint — the frozen governance standard for all docs. |
| **CHAR-001** | The Project Charter — the constitutional root (pending, next to be written). |
| **Charter** | The project's constitution: mission, principles, values, non-goals. Near-frozen. |
| **Milestone** | A logical group of related V0 documents reviewed together as a unit (M1–M5). |
| **Goal** | One unit of work within a Version, containing one or more Phases. |
| **Phase** | A unit of work within a Goal, containing one or more Tasks. |
| **Definition of Ready** | The checklist an issue must pass before a contributor picks it up. |
| **Definition of Done** | The checklist a PR must pass before it can be merged. |
| **Source of Truth** | The single document that owns a fact. All others link to it, never copy it. |

---

## 14. Team

| Role | Responsibilities |
|------|----------------|
| **Project Owner** | Product vision, final architectural approval, scope decisions, product acceptance |
| **Product Manager** | Plan versions/goals, governance, acceptance criteria, documentation reviews, prevent scope creep |
| **Technical Lead** | Architecture proposals, system design, implementation, documentation, tests, ADR creation |
| **Senior Advisor** | Architecture guidance, review of major design decisions |
| **Contributors** | Implementation, documentation, tests — per assigned tasks |

---

## 15. Contributor Onboarding

New to the project? Here is the reading path:

1. Read this document (you are here)
2. Read `docs/documentation-architecture-blueprint.md` (DOC-001) — understand how docs are organized
3. Read `docs/charter.md` (CHAR-001) when available — understand what we're building and why
4. Read `CONTRIBUTING.md` — understand how to work on the project
5. Read `docs/contributor-reference.md` — understand the current state and where to begin
6. Browse `good first issue` labels in GitHub Issues
7. Introduce yourself in a GitHub Discussion or issue comment

**One rule above all others:** never implement before the design is approved. If something isn't documented and approved, ask before building.

---

## 16. Out of Scope (V0)

These will never be part of V0. Don't implement them, don't design them:

- Kubernetes visualization
- Plugin runtime or marketplace
- GitHub, Argo CD, Jenkins, Helm integrations
- RCA Engine
- AI features
- Authentication / Authorization
- Multi-cluster support
- Performance optimization
- Fancy animations

If a proposal touches these areas, apply the Charter Rule and stop.
