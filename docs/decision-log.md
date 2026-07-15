# Decision Log

> **Purpose:** A concise, chronological record of important architectural and product decisions made during the project.
>
> This log captures the *what* and *why* of decisions. Full reasoning and alternatives live in ADRs (`docs/architecture/adr/`) and the relevant documents. This log is the quick-reference view.
>
> **Update cadence:** add an entry whenever a significant architectural, product, or governance decision is made or reversed. Trivial decisions (e.g., file naming, minor style choices) do not warrant entries.

---

## Log

| Date | ID | Decision | Reason | Status |
|------|-----|----------|--------|--------|
| 2026-07-14 | — | Requirements are never renumbered or deleted; marked Superseded / Deprecated / Obsolete instead | Preserves historical traceability across versions; prevents broken cross-references in architecture and test documents | ✅ Active |
| 2026-07-14 | — | Each requirement carries Type, Satisfied By, and Verified By fields; latter two populated by ARCH-001 and ENG-002 | Enables forward traceability from requirement to implementation and verification without requiring a separate traceability matrix | ✅ Active |
| 2026-07-14 | — | Review reports recommended for future major specification documents (not implemented in V0) | Captures accepted changes, rejected changes, and design rationale in one place; reduces re-debating | ✅ Active (recommendation) |
| 2026-07-12 | DOC-001 | Adopt repository-first, Git-based documentation governance | Lean OSS model; avoids external tool dependency; Git is the history | ✅ Active |
| 2026-07-12 | — | Keep Functional and Non-Functional Requirements as separate documents from the PRD | Requirements evolve per-version; PRD states stable product intent; separation reduces churn | ✅ Active |
| 2026-07-12 | — | Introduce a five-tier document status lifecycle: Draft → In Review → Approved → Superseded → Archived | Makes document maturity legible without external tooling | ✅ Active |
| 2026-07-12 | — | Introduce document identifier convention (`CHAR`, `PRD`, `REQ-F`, `REQ-NF`, `ARCH`, `ADR`, `PLAN`, `ENG`, `DOC`) | Enables traceability between documents without a formal tracker | ✅ Active |
| 2026-07-12 | — | Tier approval by document reach: Engineering → PM; Architecture → PM + Owner; Vision/Roadmap/Scope → Owner | Prevents bottlenecks while preserving governance at high-impact decisions | ✅ Active |
| 2026-07-12 | CHAR-001 | Introduce a dedicated Project Charter above the Documentation Blueprint in the hierarchy | Separates permanent constitutional truths (mission, principles) from versioned plans | ✅ Active |
| 2026-07-12 | — | Reserve `CHAR` as a dedicated identifier namespace for the Project Charter | Charter is the constitutional root; deserves an unmistakable ID family | ✅ Active |
| 2026-07-12 | — | Replace "Success Metrics" in the Charter with "Project Values" | Success metrics evolve; they violate the Charter's near-frozen nature and belong in the PRD/planning docs | ✅ Active |
| 2026-07-12 | — | Establish the Charter Rule as a permanent governance rule: "Does this move toward the mission?" | Single, universally applicable scope-creep test for every feature, ADR, and plugin decision | ✅ Active |
| 2026-07-12 | — | Adopt GitHub Flow (not Git Flow) as the branching strategy | GitHub Flow is sufficient for V0 scale; Git Flow adds complexity that doesn't pay off until regular versioned releases | ✅ Active |
| 2026-07-12 | — | Reinterpret "one active task at a time" as per-contributor serial, not globally serial | Enables multiple contributors to work in parallel on independent tasks without integration chaos | ✅ Active |
| 2026-07-14 | — | Add Project Knowledge Base (`KNOWLEDGE_BASE.md`) as canonical context for contributors and AI assistants | Gives all contributors (human and AI) a stable, single starting point; reduces context loss between sessions | ✅ Active |

---

## Rejected Decisions

Decisions explicitly considered and rejected. Kept here to prevent re-debating.

| Date | Decision Considered | Rejected Because |
|------|---------------------|-----------------|
| 2026-07-12 | Use Confluence / Notion for documentation | Repository-first is the project standard; external tools create sync problems |
| 2026-07-12 | Merge Functional + NFR into PRD | Requirements evolve independently across versions; separation improves maintainability |
| 2026-07-12 | Include Success Metrics in the Charter | Metrics evolve; they violate the near-frozen nature of a constitution |
| 2026-07-12 | Use Git Flow branching model | Heavier than needed for V0; introduces release branch complexity without benefit |
| 2026-07-12 | Store diagrams in a `diagrams/` folder | Diagrams are inline Mermaid in their owning document; a folder creates drift risk |
| 2026-07-12 | Per-document changelogs | Git history is the changelog; in-document histories duplicate information |
| 2026-07-12 | Design plugin architecture in V0 | Explicitly out of scope; extensibility is considered but not built in V0 |
