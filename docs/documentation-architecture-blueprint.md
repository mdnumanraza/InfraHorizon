# Documentation Architecture Blueprint

> **ID:** DOC-001
> **Version:** 1.1
> **Status:** Approved
> **Owner:** Product Manager
> **Approver:** Project Owner
> **Last Updated:** 2026-07-12

---

## 0. Purpose of This Document

This blueprint defines **how documentation works** for infra-observer — the meta-layer that sits above every other document. It is written *once*, reviewed *once*, and thereafter acts as the rulebook for how all other documentation is created, owned, and evolved.

It intentionally does **not** contain product requirements, architecture, or planning content. Those belong in the documents this blueprint governs.

**A note on the driving philosophy.** The guiding question throughout is: *"Does this add real value, or is it unnecessary complexity?"* Where a heavier convention exists (e.g., a formal documentation CMS, a doc-per-decision culture, elaborate cross-referencing schemes), this blueprint deliberately chooses the lean option and says why. This is meant to read like a well-run open-source project, **not** an enterprise process manual.

---

## 1. What Documentation Should Exist?

Documentation exists to answer questions that code and Git history *cannot* answer on their own:

- *Why* does this project exist and what is it deliberately **not**? → Requirements
- *Why* is it built this way? → Architecture + Decision records
- *How* do we work on it? → Workflow, standards, testing
- *Where* is it going? → Roadmap / version planning

Anything that doesn't serve one of those four questions is a candidate for deletion.

We organize documentation into **five categories**. This is the entire universe — if a proposed document doesn't fit one of these, that is a signal to question whether it should exist.

| # | Category | Answers the question | Examples | Volatility |
|---|----------|----------------------|----------|------------|
| 1 | **Governance / Meta** | "How do we run the project and its docs?" | Project Charter, this blueprint, the roadmap, contributing guide | Very low |
| 2 | **Product** | "What are we building and why?" | PRD, functional & non-functional requirements | Low |
| 3 | **Architecture** | "How is it designed and why *this* way?" | Architecture overview, ADRs | Medium |
| 4 | **Engineering Practice** | "How do we build it correctly?" | Coding standards, testing strategy, dev workflow | Medium |
| 5 | **Planning** | "What is the current version's plan?" | V0 goals, phase breakdown, Definition of Done | High (per version) |

### The Project Charter — the constitutional root

Above every other document sits the **Project Charter** (`CHAR-001`). It is the single source of truth for the project's *enduring* truths — the things that should almost never change. It is deliberately short (aim for one screen) and reads like a constitution, not a strategy document.

**Charter sections (and only these):**

- **Mission** — why the project exists, in one or two sentences.
- **North Star** — the single guiding outcome everything aims at.
- **Product Philosophy** — the beliefs that shape *how* we build.
- **Core Principles** — the non-negotiable engineering/product principles.
- **Project Values** — the stable, long-lived values the project holds *(this replaces "Success Metrics" — metrics evolve and belong in the PRD/planning docs, not the constitution)*.
- **Explicit Non-Goals** — what the project deliberately will **not** be.

**The Charter Rule (permanent governance rule).** The Charter carries one binding rule that governs the whole project:

> **Every roadmap item, feature, architecture decision, and future plugin must answer: *"Does this move the project toward the Charter's mission?"* If the answer is no, it is not included in the project.**

This single question is the project's **primary protection against scope creep** — it replaces case-by-case debate with one test that anyone can apply.

> **Why `Success Metrics` was dropped:** success metrics evolve as the product matures, so they violate the "near-frozen" nature of the Charter. They live in the PRD / planning documents instead. The Charter holds only stable concepts.

### The 15 planning-package documents mapped to categories

The assignment names 15 documents. Rather than treating each as an isolated deliverable, we group them so ownership and dependencies become obvious:

- **Product (3):** PRD, Functional Requirements, Non-Functional Requirements *(the two requirements documents are kept separate from the PRD — see below)*
- **Architecture (2):** Architecture Overview, ADR Strategy *(+ the ADRs it spawns)*
- **Engineering Practice (3):** Coding Standards, Testing Strategy, Development Workflow
- **Planning (4):** Version 0 Goals, Phase Breakdown, Definition of Done, Risk Register
- **Deferred (1):** Technology Stack Proposal — produced as *multiple proposals with trade-off analysis*, per the Owner's instruction, and only after requirements + architecture exist.

> **Approved structure (revision 1):** Functional and Non-Functional Requirements are kept as **separate documents** under a `requirements/` folder, distinct from the PRD. Rationale: as the project grows across multiple versions, requirements evolve independently from the PRD — the PRD states the enduring *product intent* (what & why), while requirements accumulate and change version over version. Keeping them separate improves long-term maintainability without adding meaningful complexity. The PRD *links to* the requirements documents rather than restating them.

---

## 2. Document Hierarchy

Documents form a hierarchy where **higher documents constrain lower ones**. A lower document may never contradict a higher one; if it needs to, the higher document must change first (through the review workflow in §5).

```
                    Project Charter            (CHAR-001)
        the constitution: mission, north star, philosophy,
        principles, values, non-goals + the Charter Rule
                            │
                            ▼
        ┌── Documentation Architecture Blueprint ──┐
        │   governs HOW documentation is managed    │   (sits beside the
        │   (does not sit "above" product content;  │    main chain — it is
        │    it defines the rules the chain follows) │    the rulebook)
        └────────────────────────┬──────────────────┘
                            │
                            ▼
                        Roadmap            (derives from the Charter)
                 version sequence; each version must pass the Charter Rule
                            │
                            ▼
                          PRD              (what & why, scope in/out)
                            │
                            ▼
                      Requirements         (functional + non-functional)
                            │
                            ▼
                      Architecture         (overview + ADRs)
                            │
                            ▼
                   Engineering Documents   (coding standards, testing,
                            │               dev workflow)
                            ▼
                     Implementation        (governed by everything above)
```

**Two distinct roles.** The **Charter** sits at the top of the *content* chain — every document below it must serve its mission (the Charter Rule). The **Blueprint** is not "more important" than the PRD or architecture; it sits to the side as the *rulebook* that defines how all these documents are created, owned, and reviewed. Charter = *what the project stands for*; Blueprint = *how we document the project*.

**Reading rule:** to understand a decision, read top-down from the Charter. To make a change, propose it at the lowest layer that fully contains the change, and only escalate upward if the change contradicts a higher layer.

---

## 3. Source of Truth (One Owner Per Concern)

The core anti-goal is **duplicated information that drifts out of sync**. We enforce this rule:

> Every fact has **exactly one** source-of-truth document. Everywhere else, that fact is *linked to*, never copied.

| Concern | Single Source of Truth |
|---------|------------------------|
| Mission, north star, philosophy, principles, values, non-goals | `charter.md` |
| Version sequence / roadmap | `roadmap.md` (derives from the Charter) |
| How documentation itself works | This blueprint |
| Product scope & intent — what we're building and why, what's in/out | `product/prd.md` |
| Functional requirements (what the system must *do*) | `product/requirements/functional-requirements.md` |
| Non-functional requirements (qualities: performance, reliability, etc.) | `product/requirements/non-functional-requirements.md` |
| High-level system design | `architecture/overview.md` |
| A specific, dated design decision | The individual ADR in `architecture/adr/` |
| Technology choices & their justification | The accepted ADR(s) + `architecture/tech-stack.md` |
| How to write code | `engineering/coding-standards.md` |
| How we test | `engineering/testing-strategy.md` |
| How we branch, commit, review, release | `engineering/development-workflow.md` |
| Current version's goals & acceptance | `planning/v0/` |
| What "done" means | `planning/v0/definition-of-done.md` |
| Known risks | `planning/v0/risk-register.md` |

**Example of the rule in action:** the Definition of Done will *reference* the Testing Strategy ("all tests defined by the testing strategy pass") rather than restating what tests exist. If the testing approach changes, only one document changes.

---

## 4. Dependencies Between Documents

A document may only be *written* (approved) after the documents it depends on are approved. This is what makes the review order in §10 non-arbitrary.

| Document | Depends on (must exist & be approved first) | Why |
|----------|---------------------------------------------|-----|
| Project Charter | — | Constitutional root; states mission, principles, non-goals |
| This Blueprint | Project Charter | Documentation rules serve the Charter's project |
| Roadmap | Project Charter, Blueprint | Every version must pass the Charter Rule; follows doc conventions |
| PRD | Roadmap, Charter | Scope traces to the roadmap and the Charter's mission |
| Functional Requirements | PRD | Requirements decompose the product intent |
| Non-Functional Requirements | PRD | Quality attributes derive from the product intent |
| Architecture Overview | PRD, Functional & Non-Functional Requirements | You design *to* requirements |
| Tech Stack Proposal(s) | Architecture Overview | Options are evaluated *against* the architecture's needs |
| ADRs | Architecture Overview | Each ADR refines a part of the architecture |
| Coding Standards | Tech Stack (accepted) | Standards are language/framework-specific |
| Testing Strategy | Architecture Overview, Tech Stack | Test approach depends on what's being built & the stack |
| Development Workflow | Blueprint | Mostly independent; needs doc/review conventions |
| V0 Goals | PRD, Architecture Overview | Goals decompose the approved scope |
| Phase Breakdown | V0 Goals | Phases decompose goals |
| Definition of Done | Testing Strategy, Coding Standards | "Done" cites these |
| Risk Register | Architecture, Tech Stack, Phase Breakdown | Risks emerge from concrete plans |

---

## 5. Review Workflow & Approval Hierarchy

Kept deliberately lightweight — this is an open-source project, not a compliance shop.

**The mechanism is Git.** Every document change is a branch → Pull Request → review → merge. No separate review tooling. The PR *is* the review record; Git history *is* the audit trail.

```
Author drafts on a branch          (status: Draft)
        │
        ▼
Opens Pull Request                 (status: In Review; labeled docs + category)
        │
        ▼
Review + approval per the hierarchy below
        │
        ▼
        Merge                      (status: Draft/In Review → Approved)
```

### Approval hierarchy

Approval scales with how far-reaching the document is. This prevents bottlenecks on routine engineering docs while preserving governance over vision and architecture.

| Document type | Reviewers / approvers required |
|---------------|-------------------------------|
| **Engineering documentation** (coding standards, testing strategy, dev workflow) | **Product Manager** |
| **Technical architecture** (architecture overview, tech stack, ADRs) | **Product Manager + Project Owner** |
| **Product vision / roadmap / scope** (Project Charter, roadmap, PRD, requirements, this blueprint) | **Project Owner** |

**Rules:**
- **No document is "active" (Approved) until its PR is merged.** Draft and In Review work lives openly in the repo — we label status (§8B), we don't hide work-in-progress.
- Planning documents (goals, phases, DoD, risk register) are **PM-owned, TL-drafted, and Owner-approved where applicable** (see §6). In practice they follow the *product/scope* lane above when they touch scope, and the *engineering* lane when they're purely execution detail.
- The **Product Manager reviews everything** — even documents the Owner ultimately approves — to guard against scope creep and to validate acceptance criteria. The hierarchy above lists the *approver*; PM review is assumed throughout.

---

## 6. Ownership

Ownership means "responsible for authoring and keeping it correct," not "only person allowed to edit." The model below matches the approved role responsibilities.

### Role responsibilities

**Project Owner**
- Product vision
- Final product decisions
- Final approval for roadmap and architecture

**Product Manager**
- Planning
- Governance
- Reviews
- Acceptance criteria
- Documentation reviews

**Technical Lead**
- Draft technical documentation
- Architecture proposals
- Implementation
- Testing
- ADR creation

### Ownership per category

| Category | Author (drafts) | Owner (correctness) | Approver |
|----------|-----------------|---------------------|----------|
| **Project Charter** (`CHAR-001`) | Technical Lead | Project Owner | Project Owner |
| Governance / Meta (blueprint, roadmap) | Technical Lead | Product Manager | Project Owner |
| Product (PRD, requirements) | Technical Lead | Product Manager | Project Owner |
| Architecture / ADRs | Technical Lead | Technical Lead | Product Manager + Project Owner |
| Engineering Practice | Technical Lead | Technical Lead | Product Manager |
| Planning (goals, phases, DoD, risk) | Technical Lead | Product Manager | Project Owner (where applicable) |

**Planning documents specifically are: PM-owned, TL-drafted, Owner-approved where applicable.** The Technical Lead writes the breakdown; the Product Manager owns that it correctly reflects planned scope and acceptance criteria; the Project Owner approves where scope or product direction is affected.

---

## 7. How Documentation Evolves Across the Lifecycle

Different categories change at different rates, and we treat them accordingly:

- **Governance & Product** — change *rarely*, and only through deliberate PRs. A change here ripples downward, so it's high-ceremony.
- **Architecture** — the **Overview evolves in place** (it always describes the *current* system). **ADRs are immutable once accepted** — you never edit a decision; you supersede it with a new ADR that references the old one. This gives us a decision *history*, which is the whole point of ADRs.
- **Engineering Practice** — evolves in place as the team learns. Low ceremony.
- **Planning** — **versioned by folder**. V0's plan lives in `planning/v0/` and is essentially *frozen* once V0 completes; V1 gets `planning/v1/`. We never rewrite V0's history to match V1 — completed plans become a record of what was actually decided.

**Every document carries a status header** following the lifecycle defined in §8B (`Draft → In Review → Approved → Superseded | Archived`). This one convention makes a document's lifecycle legible at a glance without any external tracking system.

---

## 8. Repository Folder Structure

Optimized for **flat-where-possible, nested-only-where-it-earns-its-keep.** All docs live under a single top-level `docs/` tree so the root stays clean and contributors have one obvious place to look.

```
infra-observer/
├── README.md                      # Front door: what this is, links into docs/
├── CONTRIBUTING.md                # How to contribute (points at dev workflow)
├── LICENSE                        # (deferred decision — placeholder until chosen)
│
└── docs/
    ├── README.md                  # Documentation index / map — the "you are here"
    ├── charter.md                 # CHAR-001 — the constitution (mission, principles, non-goals)
    ├── documentation-architecture-blueprint.md   # THIS document — how docs are managed
    ├── roadmap.md                 # Version sequence (derives from the Charter)
    │
    ├── product/
    │   ├── prd.md                 # Product intent: what & why, scope in/out
    │   └── requirements/
    │       ├── functional-requirements.md      # REQ-F-NNN entries
    │       └── non-functional-requirements.md  # REQ-NF-NNN entries
    │
    ├── architecture/
    │   ├── overview.md            # High-level system architecture (living doc)
    │   ├── tech-stack.md          # Chosen stack + rationale (points to ADRs)
    │   └── adr/
    │       ├── README.md          # ADR index + the ADR template
    │       └── 0001-record-architecture-decisions.md
    │
    ├── engineering/
    │   ├── coding-standards.md
    │   ├── testing-strategy.md
    │   └── development-workflow.md
    │
    ├── planning/
    │   └── v0/
    │       ├── goals.md
    │       ├── phases.md
    │       ├── definition-of-done.md
    │       └── risk-register.md
    │
    └── templates/
        ├── adr-template.md
        ├── document-header-template.md
        └── planning-doc-template.md
```

**Why this shape:**
- **One `docs/` root** — contributors never wonder where documentation lives.
- **Category folders, not deep trees** — max two levels deep in the common case (`docs/architecture/adr/`). Avoids the "click through six folders to find one file" problem.
- **`planning/v<N>/`** — the *only* place we version by folder, because plans are inherently per-version. Everything else is a living document.
- **ADRs get their own folder** because they're numerous and numbered; everything else stays flat.
- **`templates/`** is the source of truth for structure, keeping consistency without a rigid CMS.

**What we deliberately did *not* create** (complexity without value):
- No `docs/decisions/` separate from ADRs (ADRs *are* the decision log).
- No per-document changelog files (Git history is the changelog).
- No `diagrams/` folder yet — diagrams live inline (as text/Mermaid) in the doc they belong to, so they can't drift from their context. We add a folder only if binary image assets appear later.

---

## 8A. Document Identifier Convention

Every major document carries a **stable identifier** in its header. Identifiers give us traceability — later, a phase can cite the requirement it satisfies (`PLAN-003 implements REQ-F-012`), and an ADR can cite the requirement that forced it. The identifier is stable even if the document is renamed or reorganized.

**Format:** `<PREFIX>-<NNN>` — a category prefix, a hyphen, and a zero-padded three-digit sequence number.

| Prefix | Applies to | Example |
|--------|-----------|---------|
| `CHAR` | Project Charter — the constitutional root (its own dedicated namespace) | `CHAR-001` |
| `PRD` | Product Requirements Document | `PRD-001` |
| `REQ-F` | Functional requirement (individual, within the functional-requirements doc) | `REQ-F-001` |
| `REQ-NF` | Non-functional requirement (individual, within the non-functional-requirements doc) | `REQ-NF-001` |
| `ARCH` | Architecture document / major architectural concern | `ARCH-001` |
| `ADR` | Architecture Decision Record | `ADR-001` |
| `PLAN` | Planning document (goal, phase, DoD, risk) | `PLAN-001` |
| `ENG` | Engineering-practice document (standards, testing, workflow) | `ENG-001` |
| `DOC` | Other governance / meta document (this blueprint, roadmap, contributing guide) | `DOC-001` |

The Charter gets its **own identifier family (`CHAR`)** rather than sharing the generic `DOC` namespace, because it is the single highest-level governance document and deserves to be unmistakable at a glance.

**Rules (kept intentionally minimal):**
- Numbers are assigned in creation order **within a prefix** and are **never reused**, even if a document is archived.
- `REQ-F` and `REQ-NF` identify *individual requirements inside* their document, so a single functional-requirements file contains many `REQ-F-NNN` entries. All other prefixes identify a *whole document*.
- The identifier lives in the document header (§9.1) and, for requirements, at the start of each requirement line.
- Sequence numbers are **not** version-scoped — `PLAN-001` is unique across the whole project, not reset per version. This keeps cross-version traceability unambiguous.

We deliberately avoid encoding the version or category-depth into the identifier (e.g., `V0-PLAN-PHASE-001`) — that couples the ID to organizational details that change, defeating the purpose of a *stable* identifier.

---

## 8B. Document Status Lifecycle

Every major document declares a single status in its header. This is the one convention that makes a document's maturity legible at a glance, with no external tracking tool.

```
Draft ──► In Review ──► Approved ──► Superseded
                                └──► Archived
```

| Status | Meaning | Who sets it |
|--------|---------|-------------|
| **Draft** | Being written; not yet ready for review. | Author |
| **In Review** | Open as a PR; under review by the approvers in §5. | Author (on opening PR) |
| **Approved** | Merged and active — the current source of truth for its concern. | Set on merge by the approver |
| **Superseded** | Replaced by a newer document that took over its concern; kept for history, links forward to its replacement. | Approver of the replacement |
| **Archived** | No longer relevant (e.g., a completed version's planning doc, or an abandoned proposal); kept read-only for the record. | Approver |

**Rules:**
- A document is only a source of truth when **Approved**. Draft and In Review work happens openly in the repo — we label status, we don't hide work.
- **Superseded** always points to what replaced it. **Archived** is terminal and needs no forward link.
- ADRs use a slightly narrower set (`Proposed → Accepted → Superseded`) because an accepted decision is never "in review" again — a *new* ADR supersedes it. This is noted in the ADR template (§9.2).

---

## 9. Document Templates

We keep templates to the **minimum set that guarantees consistency**. Three templates cover everything:

### 9.1 Standard Document Header (every doc starts with this)

This is the **standard header for all major project documents**. Exactly six metadata fields — lightweight, and enough to answer "what is this, how mature is it, and who owns it" at a glance.

```markdown
# <Title>

> **ID:** <PREFIX>-NNN                                              (see §8A)
> **Version:** <document version, e.g. 0.1 / 1.0>
> **Status:** Draft | In Review | Approved | Superseded | Archived  (see §8B)
> **Owner:** <role>
> **Approver:** <role>
> **Last Updated:** YYYY-MM-DD

## Purpose
One paragraph: what question this document answers and for whom.

## Contents
<the body>
```

**On the `Version` field:** this is the *document's* version (its editorial revision, e.g. `0.1` while drafting, `1.0` once approved), not the product version. It is bumped by the author on each substantive change. It does **not** replace Git — see the note below.

> **No changelogs, no in-document revision histories.** The header's `Version` + `Last Updated` fields plus Git history are the complete record of how a document changed. We do **not** maintain per-document changelog sections or revision-history tables — Git remains the single source of history.

> **Note on `Category`:** the earlier draft header also carried a `Category` field. The approved six-field header above omits it, since a document's category is already implied by its folder (§8). If you'd prefer `Category` retained as a seventh field for at-a-glance scanning, that's a one-line addition — flagging rather than deciding silently.

### 9.2 ADR Template (the classic lightweight ADR)

```markdown
# ADR-NNNN: <Short Title of Decision>

> **ID:** ADR-NNN
> **Status:** Proposed | Accepted | Superseded by ADR-XXX
> **Date:** YYYY-MM-DD

## Context
The forces at play. What problem are we deciding on? What constraints exist?

## Decision
The choice we made, stated in one or two sentences.

## Consequences
What becomes easier, what becomes harder, what we're now committed to.

## Alternatives Considered
Options we rejected, and briefly why. (This is where trade-off analysis lives.)
```

### 9.3 Planning Document Template

```markdown
# <Version> — <Goal | Phase | DoD>

> **Status:** ...  (standard header)

## Objective
What this planning artifact achieves.

## Scope (In / Out)
Explicit in-scope and out-of-scope lists — the primary anti-scope-creep tool.

## Breakdown
Goals → Phases → Tasks, as applicable to this doc's level.

## Acceptance Criteria
How we know this is complete.
```

**Why only three:** a header template enforces consistency everywhere; the ADR template is a well-established open-source standard; the planning template encodes the Project→Version→Goal→Phase→Task methodology. A PRD or architecture doc doesn't need a rigid template — it needs the header plus good writing. More templates than this would be process for its own sake.

---

## 10. Creation Order for the Version 0 Planning Documents

This order is **derived from the dependency graph in §4** — each document is created only after everything it depends on is approved. This is the concrete sequence to follow *after this blueprint is approved*.

| Order | Document | Category | Unblocks |
|-------|----------|----------|----------|
| 0 | *(This blueprint — already approved)* | Governance | Everything |
| 1 | `charter.md` (`CHAR-001`) | Governance | Roadmap, and the Charter Rule for all scope |
| 2 | `roadmap.md` | Governance | PRD framing |
| 3 | `product/prd.md` (product intent, scope in/out) | Product | Requirements, Goals |
| 4 | `product/requirements/functional-requirements.md` | Product | Architecture, Goals |
| 5 | `product/requirements/non-functional-requirements.md` | Product | Architecture, Testing |
| 6 | `architecture/overview.md` | Architecture | Tech stack, ADRs, testing |
| 7 | `architecture/tech-stack.md` (multiple proposals + trade-offs) | Architecture | Coding standards, testing |
| 8 | Foundational ADRs (e.g., ADR-001 "record decisions", + stack decision) | Architecture | — |
| 9 | `engineering/coding-standards.md` | Engineering | DoD |
| 10 | `engineering/testing-strategy.md` | Engineering | DoD |
| 11 | `engineering/development-workflow.md` | Engineering | — |
| 12 | `planning/v0/goals.md` | Planning | Phases |
| 13 | `planning/v0/phases.md` | Planning | Risk register |
| 14 | `planning/v0/definition-of-done.md` | Planning | — |
| 15 | `planning/v0/risk-register.md` | Planning | — |

**Rationale for the sequencing choices:**
- **Charter first** — nothing can be scoped until the constitution and the Charter Rule exist to test it against.
- **Requirements before architecture, architecture before stack** — directly honors the Owner's instruction to defer stack/deployment/licensing until requirements and architecture are documented.
- **Tech stack as *proposals* (step 7) then locked by an *ADR* (step 8)** — the trade-off analysis lives in the proposal doc and the ADR; the final `tech-stack.md` records the outcome.
- **Standards & testing before Definition of Done** — because DoD cites them.
- **Planning docs last** — they consume everything above.

---

## 11. Definition of Success (Self-Check)

This blueprint is successful if it is:

- ✅ **Simple** — five categories, three templates, one `docs/` root, Git-based review, one ID convention, one status lifecycle.
- ✅ **Scalable** — new versions add a `planning/vN/` folder; new decisions add a numbered ADR; identifiers extend without renumbering; nothing else restructures.
- ✅ **Maintainable** — living docs evolve in place; only ADRs and completed plans are frozen; requirements live separately so they evolve without churning the PRD.
- ✅ **Low duplication** — one source of truth per concern (§3); everything else links.
- ✅ **Traceable** — stable identifiers (§8A) let planning docs and ADRs cite the requirements they satisfy.
- ✅ **Clear ownership** (§6), **clear review order** (§5, §10), and a **clear status lifecycle** (§8B).
- ✅ **Approachable** — a new contributor reads `docs/README.md` and understands the whole system.
- ✅ **Ready to execute** — the moment this is approved, we start at step 1 in §10 (the Project Charter).

---

## 12. Status of This Blueprint

This blueprint is the **permanent documentation governance standard for the entire project**. Every convention it defines — the five categories plus the Charter root (§1), source-of-truth rule (§3), review & approval hierarchy (§5), ownership model (§6), folder structure (§8), identifier convention incl. the `CHAR` family (§8A), status lifecycle (§8B), and templates (§9) — is active and self-applied by this document.

Consistent with §9.1, this section intentionally carries **no revision history or changelog**. How the blueprint reached its current form is recorded in Git, not restated here.

Once approved, the next step is the foundational-document decision below, then the Version 0 planning documents beginning at step 1 in §10.

