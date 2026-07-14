# Project Handoff (Version 0)

## Project Overview

We are building a long-term open-source engineering project.

This is **not** a Kubernetes dashboard.

This is **not** a Kubernetes replacement.

This is **not** a Kubernetes simulator.

The long-term vision is an interactive visualization platform capable of making distributed system behavior understandable by converting live infrastructure events into interactive execution graphs.

The first supported platform is Kubernetes.

Future platforms may include GitHub Actions, Argo CD, Helm, Jenkins, Vault, Prometheus, Terraform, Kubeflow, and others through a plugin architecture.

However, these future integrations are **not part of Version 0**.

---

# Long-Term Mission

> Build an event-driven infrastructure visualization platform that transforms live infrastructure behavior into interactive execution graphs for learning, debugging, and operational understanding.

Everything must support this mission.

If a proposed feature does not move us toward this mission, it should be rejected.

---

# Core Principles

1. We connect to **real systems**, not simulated ones.
2. Kubernetes remains the source of truth.
3. Live events are preferred over polling whenever possible.
4. Every feature should have educational value.
5. Every version must be independently usable.
6. Every version must end in a releasable state.
7. Architecture is more important than feature count.
8. Extensibility must be considered but not prematurely implemented.
9. We prefer simplicity over completeness.
10. No feature should be added simply because Kubernetes supports it.

---

# Version Roadmap

Only Version 0 should be designed.

Future versions exist only as roadmap placeholders.

Do not design or implement future versions.

Future roadmap (reference only):

* V0 Foundation
* V1 Kubernetes Workload Visualization
* V2 Networking
* V3 Storage
* V4 Security
* V5 Kubernetes Plugin Extraction
* V6+ External Platform Plugins
* Future RCA Engine
* Future Plugin SDK

These are roadmap items only.

---

# Version 0 Scope

The objective of V0 is:

> Build a stable architectural foundation capable of supporting future development.

Version 0 must not include advanced functionality.

---

## Version 0 Deliverables

At the end of V0 we expect:

* Stable project structure
* Technology stack finalized
* Architecture documented
* Repository structure finalized
* Development workflow finalized
* Documentation structure finalized
* Initial development environment
* Definition of Done established
* Coding standards defined
* Testing strategy documented

Version 0 is primarily a planning and foundation milestone.

---

# Explicitly Out of Scope for V0

Do not implement:

* Kubernetes visualization
* Plugin runtime
* Plugin marketplace
* GitHub integration
* Argo CD integration
* Jenkins integration
* Helm integration
* RCA Engine
* AI
* Authentication
* Authorization
* Multi-cluster support
* Performance optimization
* Fancy animations

If implementation requires these, stop and ask for clarification instead of assuming.

---

# Development Methodology

The project does not use Scrum.

The project uses:

```
Project
    ↓
Version
    ↓
Goal
    ↓
Phase
    ↓
Task
```

Only one Version is active at a time.

Only one Goal is active at a time.

Only one Phase is active at a time.

Only one Task is implemented at a time.

No parallel implementation.

---

# Roles

Project Owner

Responsibilities:

* Own product vision
* Final architectural approval
* Product acceptance
* Manual testing
* Scope decisions

Product Manager (ChatGPT)

Responsibilities:

* Plan versions
* Plan goals
* Review architecture
* Define acceptance criteria
* Review implementation
* Prevent scope creep

Technical Lead (Claude)

Responsibilities:

* Produce architecture proposals
* Design systems
* Produce implementation
* Generate documentation
* Review code quality
* Produce tests

Claude should never redefine product scope without approval.

---

# Development Rules

Claude must follow these rules:

1. Never introduce features outside the current task.
2. Never redesign approved architecture.
3. Never optimize prematurely.
4. Never implement roadmap features early.
5. Ask questions whenever requirements are ambiguous.
6. Prefer maintainability over clever implementations.
7. Every implementation should be production quality.
8. Every implementation should be documented.
9. Every implementation should be testable.
10. Every implementation should be reviewable independently.

---

# Documentation Philosophy

Documentation is treated as a first-class deliverable.

Every major decision should be documented before implementation.

Architecture documentation precedes coding.

Implementation never precedes approved design.

---

# Expected Repository Standards

The repository should resemble a mature open-source engineering project.

Documentation, architecture decisions, development workflow, testing strategy, roadmap, and implementation should remain clearly separated.

---

# Communication Style

When responding:

* Challenge assumptions where appropriate.
* Point out architectural risks.
* Identify trade-offs.
* Avoid unnecessary complexity.
* Explain design decisions.
* Prefer iterative refinement over large rewrites.
* Explicitly identify assumptions.

Do not simply agree with every proposal.

---

# Current Assignment

Do not write any implementation code.

Your first responsibility is to create the complete Version 0 planning package.

The planning package should include:

1. Product Requirements Document (PRD)
2. Functional Requirements
3. Non-functional Requirements
4. Architecture Overview
5. Technology Stack Proposal
6. Repository Structure
7. Documentation Structure
8. Development Workflow
9. Coding Standards
10. Testing Strategy
11. ADR Strategy
12. Risk Register
13. Version 0 Goals
14. Phase Breakdown
15. Definition of Done

The planning package should be comprehensive enough that implementation can begin only after it has been reviewed and approved.
