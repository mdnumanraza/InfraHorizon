# Version 0 — Documentation Execution Plan

> **This is NOT a repository document.** It is a planning artifact for the Product Team, kept under `.claude/` (working materials), not under `docs/` (the frozen, version-controlled tree governed by DOC-001).
>
> **Purpose:** define *how* we execute the documentation work that DOC-001 specifies. It is an implementation plan for the documentation itself. After approval, this becomes the working plan Claude follows for the remainder of Version 0.
>
> **Governed by:** DOC-001 (Documentation Architecture Blueprint) — approved & frozen. This plan derives from DOC-001 and does not modify it.
> **Status of this plan:** Draft — awaiting Product Team review.
> **Last Updated:** 2026-07-12

---

## 0. How to Read This Plan

DOC-001 already answers *what* documents exist, *who* owns them, and *in what order* they may be created (its §10). This plan answers the operational question DOC-001 deliberately leaves open: **how do we actually run the work — where do we batch, where do we stop to review, what could go wrong, and how big is each piece?**

Nothing here overrides DOC-001. Where the two touch the same fact (e.g., creation order), this plan restates DOC-001's answer and adds execution detail on top.

One principle threads through everything below, and it comes straight from the project's own values: **reduce review overhead without losing control.** We review at *milestone boundaries*, not after every file — because a solo/small team drowns if every document needs a formal gate, but ships junk if nothing is ever gated.

---

## 1. Recommended Document Creation Order

This is DOC-001 §10's order (the authority), annotated with *why each document comes next*. The rule DOC-001 enforces: **a document may only be written after everything it depends on is approved.**

| # | Document | ID | Why it comes here |
|---|----------|-----|-------------------|
| 1 | `charter.md` | `CHAR-001` | **The root.** Nothing can be scoped or justified until the constitution exists — the Charter Rule ("does this move us toward the mission?") is the test every later document is measured against. Depends on nothing. |
| 2 | `roadmap.md` | `DOC-002` | Derives directly from the Charter. Lays out the version sequence (V0…V6+). Must exist before the PRD so the PRD knows *which* version it's specifying. |
| 3 | `product/prd.md` | `PRD-001` | States what V0 is and its scope in/out. Needs the Charter (mission) and roadmap (which version) above it. Unblocks all requirements. |
| 4 | `functional-requirements.md` | `REQ-F-001…` | Decomposes the PRD's "what it must do" into discrete, identifiable requirements. Blocks architecture. |
| 5 | `non-functional-requirements.md` | `REQ-NF-001…` | Decomposes the PRD's quality attributes. Blocks architecture *and* testing strategy. |
| 6 | `architecture/overview.md` | `ARCH-001` | You design *to* requirements — so both requirement docs must be approved first. Unblocks tech stack, ADRs, testing. |
| 7 | `architecture/tech-stack.md` | `ARCH-002` | Evaluated *against* the architecture's needs. Produced as **multiple proposals with trade-off analysis** (per the Owner's standing instruction), then the choice is locked by an ADR. Unblocks coding standards + testing. |
| 8 | Foundational ADRs | `ADR-001…` | ADR-001 = "we will record decisions"; further ADRs capture the stack choice and any other decisions made during 6–7. ADRs are immutable once accepted. |
| 9 | `coding-standards.md` | `ENG-001` | Language/framework-specific → needs the accepted stack (7/8). Cited later by Definition of Done. |
| 10 | `testing-strategy.md` | `ENG-002` | Depends on architecture + stack + NFRs (what qualities we must verify). Cited by Definition of Done. |
| 11 | `development-workflow.md` | `ENG-003` | Branching, commits, review, release. Largely independent; only needs DOC-001's conventions. Placed here to close out Engineering as a batch. |
| 12 | `planning/v0/goals.md` | `PLAN-001` | Decomposes approved scope into V0 goals. Needs PRD + architecture. |
| 13 | `planning/v0/phases.md` | `PLAN-002` | Decomposes goals into phases. Needs goals. |
| 14 | `planning/v0/definition-of-done.md` | `PLAN-003` | *Cites* coding standards + testing strategy, so those must be approved first. |
| 15 | `planning/v0/risk-register.md` | `PLAN-004` | Risks emerge from concrete plans — needs architecture, stack, and phases to exist before it can name real risks. Comes last. |

---

## 2. Milestones

Documents are grouped into **five milestones** by the *question they answer* and by *natural review boundaries*. A milestone is the smallest batch worth stopping to review as a unit.

### Milestone 1 — Project Foundation
**Documents:** `CHAR-001` (Charter), `DOC-002` (Roadmap)
**Answers:** *Why do we exist and where are we going?*
Sets the constitution and the version map. Everything downstream is tested against it.

### Milestone 2 — Product Definition
**Documents:** `PRD-001`, `REQ-F-001…`, `REQ-NF-001…`
**Answers:** *What are we building in V0, and what must it do / how well?*
Turns the mission into concrete, traceable product statements.

### Milestone 3 — Architecture
**Documents:** `ARCH-001` (Overview), `ARCH-002` (Tech Stack proposals), `ADR-001…` (foundational decisions)
**Answers:** *How is it shaped, and on what technology — and why?*
The highest-risk milestone; this is where irreversible-feeling choices get made (and where we deliberately keep the stack as *options with trade-offs* until a decision is ratified).

### Milestone 4 — Engineering Standards
**Documents:** `ENG-001` (Coding Standards), `ENG-002` (Testing Strategy), `ENG-003` (Dev Workflow)
**Answers:** *How do we build it correctly and consistently?*
Depends entirely on the stack being chosen in Milestone 3.

### Milestone 5 — Version 0 Planning
**Documents:** `PLAN-001` (Goals), `PLAN-002` (Phases), `PLAN-003` (Definition of Done), `PLAN-004` (Risk Register)
**Answers:** *What is the concrete plan to execute V0, and when is it done?*
Consumes everything above it. Completing this milestone means V0 planning is finished and implementation can begin.

```
M1 Foundation → M2 Product → M3 Architecture → M4 Engineering → M5 Planning
  (Charter,      (PRD +        (Overview,        (Standards,      (Goals, Phases,
   Roadmap)       Reqs)         Stack, ADRs)      Testing, Flow)   DoD, Risks)
```

---

## 3. Review Gates

**Principle:** review at milestone boundaries, not per document. Within a milestone, documents are drafted and self-reviewed continuously; the formal stop happens only when the milestone is complete. This matches DOC-001 §5's tiered approval (not every doc needs the Owner) and keeps overhead proportional to risk.

The standard gate cycle at each boundary:

```
Milestone Complete → Product Team Review → Approve / Revise → Continue
                                              │
                                              └─ (Revise) → rework → re-review
```

**Which authority signs off at each gate** (from DOC-001 §5's approval tiers):

| Gate | After Milestone | Approver required | Why this tier |
|------|-----------------|-------------------|---------------|
| **Gate 1** | M1 Foundation | **Project Owner** | Charter + roadmap are product-vision/scope → Owner tier. This is the most important gate: a wrong Charter poisons everything. |
| **Gate 2** | M2 Product | **Project Owner** | PRD/requirements define scope → Owner tier. Locks *what* we build before *how*. |
| **Gate 3** | M3 Architecture | **PM + Project Owner** | Technical architecture → dual approval (DOC-001 §5). Highest technical-risk gate. |
| **Gate 4** | M4 Engineering | **Product Manager** | Engineering docs → PM tier. Owner need not be a bottleneck here. |
| **Gate 5** | M5 Planning | **Project Owner (where scope-affecting)** | Planning docs are PM-owned, Owner-approved where scope is touched (DOC-001 §6). |

**Two lightweight in-milestone checkpoints** (optional, not formal gates — they prevent large rework):
- After **`ARCH-002` tech-stack proposals** are drafted but *before* the ADR locks the choice, do a quick Owner+PM sync. Choosing the stack is the single most expensive decision to reverse; a 10-minute alignment here beats redrafting Milestone 4.
- After **`REQ-F`/`REQ-NF`** are drafted but before architecture starts, a quick PM scan for completeness — because architecture built on incomplete requirements is the classic source of rework.

---

## 4. Risks per Milestone

For each milestone: the risks, the common mistakes, the scope-creep vector, and the avoidance tactic.

### Milestone 1 — Foundation
- **Risk:** The Charter becomes a bloated strategy document instead of a one-page constitution.
- **Common mistake:** Putting *success metrics*, feature lists, or version specifics into the Charter (DOC-001 explicitly moved metrics out to the PRD).
- **Scope creep:** "While we're here, let's also define V1…" — the roadmap starts specifying *how* future versions work.
- **Avoid:** Enforce the six-section Charter limit and the one-screen target. Roadmap lists version *names + one-line intent* only; no version is designed here (the project rules forbid designing future versions).

### Milestone 2 — Product Definition
- **Risk:** Requirements drift beyond V0 scope; the PRD tries to describe the whole product vision.
- **Common mistake:** Writing requirements that presuppose a technology ("must use WebSockets") before architecture exists — that's an architecture decision leaking upward.
- **Scope creep:** Kubernetes visualization, plugins, RCA, auth — all explicitly out of V0 — sneaking into requirements "for completeness."
- **Avoid:** Every requirement must trace to the Charter mission (apply the Charter Rule literally). Keep requirements *solution-agnostic*. Re-read DOC-001/context "Out of Scope" list before drafting.

### Milestone 3 — Architecture
- **Risk:** Over-engineering the foundation for future plugins/platforms that are out of scope; analysis paralysis on the stack.
- **Common mistake:** Committing to one stack without documented alternatives; designing plugin architecture (forbidden in V0).
- **Scope creep:** "Let's make the architecture handle GitHub Actions too, since it's on the roadmap." Extensibility should be *considered, not implemented* (project principle 8).
- **Avoid:** Tech stack is delivered as **multiple proposals + trade-offs**, then locked by one ADR — this forces a decision without premature commitment. Architecture describes only what V0 needs; extension points are noted, not built.

### Milestone 4 — Engineering Standards
- **Risk:** Standards written for a stack that isn't finalized, forcing a rewrite.
- **Common mistake:** Copy-pasting a generic enterprise style guide that doesn't fit a lean OSS project; over-specifying trivial rules (the exact thing DOC-001 says docs should *not* cover).
- **Scope creep:** Testing strategy prescribing heavy CI/CD or coverage gates inappropriate for V0's foundation stage.
- **Avoid:** Sequence Milestone 4 strictly after the stack ADR is accepted. Keep standards to what materially affects quality; testing strategy sized to V0 (a foundation milestone), not a mature product.

### Milestone 5 — Planning
- **Risk:** Goals/phases invent work beyond the approved PRD; the risk register becomes a generic checklist.
- **Common mistake:** Definition of Done that restates the testing strategy instead of *referencing* it (violates DOC-001's no-duplication rule §3).
- **Scope creep:** Phases that quietly include implementation of out-of-scope features.
- **Avoid:** Goals decompose *only* approved PRD scope. DoD links to `ENG-001/002` rather than copying. Risk register names *concrete* risks from the actual architecture/phases, not boilerplate.

**Cross-cutting scope-creep control:** at every gate, ask the Charter Rule out loud for each new document — *"does this move the project toward the mission?"* If a section can't answer yes, cut it.

---

## 5. Estimated Effort (Relative Sizing)

Relative only — **no hours**. Size reflects drafting + expected review iteration, not calendar time.

| Document | Size | Note |
|----------|------|------|
| `CHAR-001` Charter | **Small** | Deliberately one screen; hard to write *well*, but short. |
| `DOC-002` Roadmap | **Small** | Version names + one-line intents; no designing. |
| `PRD-001` | **Medium** | The scoping anchor; needs care on in/out boundaries. |
| `REQ-F` Functional Requirements | **Medium** | Many small entries; volume, not depth. |
| `REQ-NF` Non-Functional Requirements | **Small–Medium** | Fewer items than functional for a V0 foundation. |
| `ARCH-001` Overview | **Large** | Highest-thought document; shapes everything technical. |
| `ARCH-002` Tech Stack (multi-proposal) | **Large** | Multiple options × trade-off analysis is inherently heavy. |
| `ADR-001…` Foundational ADRs | **Small** each | ADRs are intentionally short and focused. |
| `ENG-001` Coding Standards | **Medium** | Stack-specific; keep lean. |
| `ENG-002` Testing Strategy | **Medium** | Must map to NFRs. |
| `ENG-003` Dev Workflow | **Small–Medium** | Mostly conventions. |
| `PLAN-001` Goals | **Small–Medium** | Decomposition of known scope. |
| `PLAN-002` Phases | **Medium** | Where execution detail lives. |
| `PLAN-003` Definition of Done | **Small** | Mostly references other docs. |
| `PLAN-004` Risk Register | **Small–Medium** | Depends how much concrete risk surfaces. |

**Milestone totals (rough):** M1 Small · M2 Medium · M3 **Large** (the heavy one) · M4 Medium · M5 Medium.

---

## 6. Dependencies (What Blocks What)

Derived from DOC-001 §4. Read "A → B" as "A must be approved before B can start."

```
CHAR-001 (Charter)
   │
   ├──► DOC-002 (Roadmap)
   │        │
   │        └──► PRD-001
   │                │
   │                ├──► REQ-F ──┐
   │                └──► REQ-NF ─┤
   │                             ▼
   │                        ARCH-001 (Overview)
   │                             │
   │                             ├──► ARCH-002 (Tech Stack) ──► ADR-001… (stack decision)
   │                             │                                   │
   │                             │        ┌──────────────────────────┘
   │                             ▼        ▼
   │                        ENG-001 (Coding Std) ◄─ needs accepted stack
   │                        ENG-002 (Testing)    ◄─ needs ARCH + stack + REQ-NF
   │                        ENG-003 (Dev Flow)   ◄─ needs DOC-001 only (scheduled here)
   │                             │
   │        ┌────────────────────┘
   │        ▼
   └──► PLAN-001 (Goals) ◄─ needs PRD + ARCH-001
            │
            └──► PLAN-002 (Phases)
                     │
                     ├──► PLAN-003 (DoD) ◄─ also needs ENG-001 + ENG-002
                     └──► PLAN-004 (Risk) ◄─ also needs ARCH + stack + phases
```

**Critical path (longest blocking chain):**
`CHAR-001 → Roadmap → PRD → Requirements → ARCH-001 → ARCH-002/ADR → ENG-002 → PLAN-003`.
Anything that slips on this chain slips the whole plan. The two heaviest nodes on it (`ARCH-001`, `ARCH-002`) are also the largest-effort docs — so **Milestone 3 is the schedule risk to watch**.

---

## 7. Acceptance Criteria per Milestone

Practical and checkable — a milestone is "complete" only when all its boxes are true.

**Milestone 1 — Foundation**
- [ ] Charter contains exactly the six approved sections; fits ~one screen.
- [ ] Charter Rule is stated verbatim and usable as a scope test.
- [ ] Roadmap lists all planned versions with one-line intent; designs none of them.
- [ ] Both approved by the **Project Owner**.

**Milestone 2 — Product Definition**
- [ ] PRD states V0 scope with explicit in/out lists; every in-scope item passes the Charter Rule.
- [ ] Every functional requirement has a `REQ-F-NNN` ID; every NFR has `REQ-NF-NNN`.
- [ ] No requirement names a specific technology (solution-agnostic).
- [ ] No out-of-scope feature (K8s viz, plugins, RCA, auth, etc.) appears.
- [ ] Approved by the **Project Owner**.

**Milestone 3 — Architecture**
- [ ] Overview satisfies the approved requirements and references them by ID.
- [ ] Tech stack presented as **≥2 proposals with trade-offs**, then one chosen.
- [ ] The stack choice is captured in an accepted ADR; ADR-001 ("record decisions") exists.
- [ ] No plugin/extension architecture is *implemented* (only noted as future consideration).
- [ ] Approved by **PM + Project Owner**.

**Milestone 4 — Engineering Standards**
- [ ] Coding standards are specific to the chosen stack.
- [ ] Testing strategy maps to the NFRs it must verify.
- [ ] Dev workflow defines branch/commit/review/release using Git (per DOC-001).
- [ ] Nothing duplicates content owned elsewhere (links instead).
- [ ] Approved by the **Product Manager**.

**Milestone 5 — Planning**
- [ ] Goals trace to approved PRD scope only.
- [ ] Phases decompose goals with no out-of-scope implementation.
- [ ] Definition of Done *references* `ENG-001`/`ENG-002` rather than restating them.
- [ ] Risk register names concrete risks tied to the real architecture/phases.
- [ ] Approved by the **Project Owner** where scope-affecting.

**Overall V0 documentation complete when:** all five milestones are approved, all 15 documents carry a valid header (ID, Version, Status=Approved, Owner, Approver, Last Updated) per DOC-001 §9.1, and every document lives in its DOC-001 §8 location.

---

## 8. Recommendations (Execution-Process Only — DOC-001 unchanged)

Potential issues that could slow V0, with process fixes. **None of these change DOC-001** — they are ways to run *within* it more smoothly.

1. **Milestone 3 is the bottleneck — de-risk it early.** The Overview + multi-proposal Tech Stack are the two largest documents *and* sit on the critical path. **Recommendation:** hold the optional in-milestone Owner/PM sync (see §3) *before* writing the stack ADR, so the expensive choice is aligned before Milestone 4 depends on it. This is the single highest-leverage move to avoid rework.

2. **Requirements completeness gate before architecture.** Architecture built on half-finished requirements is the classic rework trap. **Recommendation:** a quick PM completeness scan of `REQ-F`/`REQ-NF` at the M2→M3 boundary — cheap insurance on the critical path.

3. **Batch the tiny ADRs, don't gate them individually.** ADRs are Small and numerous. **Recommendation:** treat all Milestone-3 ADRs as part of the single Gate 3 review rather than reviewing each ADR separately — consistent with "review at milestone boundaries."

4. **Watch the Definition-of-Done duplication trap.** DoD naturally tends to restate testing/standards. **Recommendation:** when drafting `PLAN-003`, explicitly link to `ENG-001`/`ENG-002` by ID; if a sentence describes *what* to test rather than *that tests pass*, it belongs in `ENG-002`, not the DoD.

5. **Keep a running "out-of-scope parking lot" (working note, not a repo doc).** Good ideas that violate V0 scope *will* surface. **Recommendation:** capture them in a scratch list under `.claude/` so they aren't lost *and* don't leak into V0 documents. This protects scope without discarding future value — and keeps the repo clean.

6. **Don't gate the Roadmap separately from the Charter.** They're both Small and both Owner-approved. **Recommendation:** review them together as Milestone 1 (already reflected in §2/§3) rather than two separate stops.

7. **Fix `DOC-002` for the roadmap ID now, in this plan.** DOC-001 assigns the roadmap to the `DOC` family but doesn't pin its number. **Recommendation (process-level, not a DOC-001 edit):** reserve `DOC-002` for `roadmap.md` so numbering is unambiguous when Milestone 1 starts. Flagging rather than assuming — confirm at Gate 1.

---

## 9. Summary — The Working Plan

After approval, this is the loop Claude follows for the rest of V0:

```
For each milestone M1 → M5:
    1. Draft its documents in the §1 order, applying the Charter Rule to every section.
    2. Self-check against that milestone's §7 acceptance criteria.
    3. Stop at the milestone's review gate (§3); route to the correct approver.
    4. Revise if requested; otherwise mark documents Approved and continue.
Do not start a milestone until the previous gate is passed.
```

**Definition of success for this plan:** the Product Team can complete V0 documentation predictably, incrementally, and review-driven — five gates instead of fifteen, with the heaviest scrutiny on the Foundation and Architecture milestones where mistakes are most expensive.

*No repository documents were created. `CHAR-001`, the PRD, requirements, and architecture remain unwritten, per the constraints. Awaiting Product Team approval of this execution plan.*
