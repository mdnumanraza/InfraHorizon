# Contributor Reference

> **Purpose:** A snapshot of the project's current state for contributors — what exists, what's in progress, and where to start.
>
> **Update cadence:** updated after every Goal completion. Not updated after individual tasks or phases.
>
> **Last updated:** 2026-07-14 (after: REQ-F-001 approved; M1 complete; M2 in progress)

---

## Current Project State

**Version:** V0 — Foundation
**Active Milestone:** M1 — Project Foundation (Charter + Roadmap)
**Phase:** Pre-Milestone 1 — completing repository foundation before writing first planning documents

infraHorizon is in its documentation and architectural foundation phase. **No implementation code exists yet.** The project is establishing the governance, standards, and architecture that all future versions will build on.

---

## What Has Been Completed

### Milestone 1 — Project Foundation ✅
- ✅ **CHAR-001 — Project Charter** (`docs/charter.md`) — Approved and frozen
- ✅ **DOC-002 — Roadmap** (`docs/roadmap.md`) — Approved and frozen

### Documentation Governance
- ✅ **DOC-001 — Documentation Architecture Blueprint** (`docs/documentation-architecture-blueprint.md`) — Frozen and approved.
- ✅ V0 Documentation Execution Plan — Internal working guide.

### Repository Foundation
- ✅ `README.md`, `KNOWLEDGE_BASE.md`, `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`
- ✅ `docs/README.md`, `docs/decision-log.md`, `docs/contributor-reference.md`

### Milestone 2 — Product Definition (In Progress)
- ✅ **PRD-001** (`docs/product/prd.md`) — Approved and frozen
- ✅ **REQ-F-001** (`docs/product/requirements/functional-requirements.md`) — Approved and frozen; 38 requirements across 5 capability groups
- 🔄 **REQ-NF-001** (`docs/product/requirements/non-functional-requirements.md`) — Next

---

## What Is Currently In Progress

### Milestone 2 — Product Definition (2 of 3 complete)

| Document | ID | Status | Notes |
|----------|----|--------|-------|
| Product Requirements Document | `PRD-001` | ✅ Approved | Frozen |
| Functional Requirements | `REQ-F-001` | ✅ Approved | Frozen; 38 requirements, 5 groups |
| Non-Functional Requirements | `REQ-NF-001` | 🔄 Next | Not yet started |

---

## What Comes Next (Upcoming Milestones)

| Milestone | Documents | Depends On |
|-----------|-----------|------------|
| **M2 — Product** | PRD (`PRD-001`), Functional Reqs, Non-Functional Reqs | M1 approved |
| **M3 — Architecture** | Overview (`ARCH-001`), Tech Stack (`ARCH-002`), ADRs | M2 approved |
| **M4 — Engineering** | Coding Standards, Testing Strategy, Dev Workflow | M3 (stack decided) |
| **M5 — Planning** | V0 Goals, Phases, DoD, Risk Register | M4 approved |

After M5, V0 documentation is complete and implementation can begin.

---

## How to Onboard as a New Contributor

### Reading Path (do this first)

1. **`KNOWLEDGE_BASE.md`** — Project mission, decisions, current state, glossary. The single most important document.
2. **`docs/documentation-architecture-blueprint.md`** (DOC-001) — How all documentation is organized and governed.
3. **`CONTRIBUTING.md`** — How to work on the project (branching, PRs, review, DoR/DoD).
4. **`docs/charter.md`** (CHAR-001) — *once available* — The project constitution.
5. This document — current state and what's claimable.

### Finding Work

1. Browse issues labeled [`good first issue`](https://github.com/infraHorizon/infraHorizon/labels/good%20first%20issue) — self-contained, well-specified, beginner-friendly.
2. Browse issues labeled [`help wanted`](https://github.com/infraHorizon/infraHorizon/labels/help%20wanted) — open to any contributor.
3. Check `status: ready` label — these have passed Definition of Ready and are claimable.

### Before You Start

- Comment on the issue to claim it. Wait for assignment.
- Read the issue's acceptance criteria and Definition of Done.
- If anything is unclear, ask in the issue — do not start work on an under-specified task.
- Remember: **documentation must be approved before implementation.** If there is no document covering your area, write or update one first.

---

## Key People

| Role | Responsibilities |
|------|----------------|
| **Project Owner** | Product vision, final approval, scope decisions |
| **Product Manager** | Planning, governance, acceptance criteria, documentation reviews |
| **Technical Lead** | Architecture, implementation, documentation authoring, ADRs |
| **Senior Advisor** | Architecture guidance, major design reviews |
| **Contributors** | Implementation, documentation, tests — per assigned tasks |

---

## Reference: Document Identifier Map

| Prefix | Applies To | Example |
|--------|-----------|---------|
| `CHAR` | Project Charter | `CHAR-001` |
| `DOC` | Governance / meta docs | `DOC-001`, `DOC-002` |
| `PRD` | Product Requirements Document | `PRD-001` |
| `REQ-F` | Individual functional requirements | `REQ-F-001` |
| `REQ-NF` | Individual non-functional requirements | `REQ-NF-001` |
| `ARCH` | Architecture documents | `ARCH-001` |
| `ADR` | Architecture Decision Records | `ADR-001` |
| `ENG` | Engineering practice documents | `ENG-001` |
| `PLAN` | Planning documents | `PLAN-001` |

---

## V0 Explicit Non-Scope

Never implement or design these in V0:

- Kubernetes visualization
- Plugin runtime or marketplace
- GitHub, Argo CD, Jenkins, Helm integrations
- RCA Engine
- AI features
- Authentication / Authorization
- Multi-cluster support
- Performance optimization
- Fancy animations

If a proposal touches these, apply the Charter Rule and stop.
