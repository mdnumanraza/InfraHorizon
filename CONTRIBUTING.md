# Contributing to infraHorizon

Thank you for contributing. This project exists to make distributed systems understandable — and every contribution, from a small doc fix to a major feature, moves us closer to that goal.

Before you start, read `KNOWLEDGE_BASE.md`. It is the canonical context document for the project. If you read only one thing, read that.

---

## Table of Contents

- [Philosophy](#philosophy)
- [How the Project Works](#how-the-project-works)
- [Getting Started](#getting-started)
- [Branch Strategy](#branch-strategy)
- [Pull Request Workflow](#pull-request-workflow)
- [Code Review](#code-review)
- [Documentation-First Development](#documentation-first-development)
- [Issue Labels and Sizing](#issue-labels-and-sizing)
- [Good First Issues](#good-first-issues)
- [Definition of Ready](#definition-of-ready)
- [Definition of Done](#definition-of-done)
- [Testing Responsibilities](#testing-responsibilities)

---

## Philosophy

- **Learning is a first-class outcome.** Reviews should teach, not gatekeep. Ask questions, share context, explain reasoning.
- **Simplicity over cleverness.** The right solution is usually the simplest one that fully solves the problem.
- **Documentation is not optional.** Architecture and documentation are approved before implementation begins. Always.
- **The Charter Rule applies to everything.** Before building anything, ask: *"Does this move the project toward the mission?"* If not, don't build it.

---

## How the Project Works

infraHorizon uses a structured development methodology — not Scrum, not Jira:

```
Project
  └── Version  (e.g., V0 — Foundation)
        └── Goal  (e.g., M1 — Project Foundation)
              └── Phase  (e.g., Write Charter sections)
                    └── Task  (e.g., Draft Mission statement)
```

**What this means for contributors:**
- Only one Version is active at a time.
- One active Goal at a time per version.
- Work is organized into Phases inside a Goal.
- Individual Tasks are the unit of work you pick up and complete.
- **No parallel work on the same task.** Two contributors may work on different tasks simultaneously; no two contributors work on the same task.

The current Goal and its tasks are always documented in `docs/contributor-reference.md`.

---

## Getting Started

1. **Read** `KNOWLEDGE_BASE.md` — understand the project's mission, decisions, and current state.
2. **Read** `docs/documentation-architecture-blueprint.md` (DOC-001) — understand how documentation is governed.
3. **Read** `docs/contributor-reference.md` — see what's actively in progress and what's available to pick up.
4. **Browse** issues labeled [`good first issue`](https://github.com/infraHorizon/infraHorizon/labels/good%20first%20issue) or [`help wanted`](https://github.com/infraHorizon/infraHorizon/labels/help%20wanted).
5. **Comment** on an issue to claim it. A maintainer will assign it to you within 24 hours.
6. **Fork** the repo, create a branch, and begin work.

---

## Branch Strategy

We use **GitHub Flow** — one long-lived branch (`main`) and short-lived feature branches.

```
main   ←   the only permanent branch; always releasable
  ↑
feature/short-description
fix/short-description
docs/short-description
chore/short-description
```

**Rules:**
- Every change goes through a branch + Pull Request. No direct pushes to `main`.
- Branch names: `type/short-description`, lowercase, hyphen-separated.
- Branches are short-lived — days, not weeks. A branch open for more than a week signals the task was too large.
- Delete your branch after it is merged.

---

## Pull Request Workflow

**Keep PRs small and focused.** One PR should do one thing.

### PR Template

When you open a PR, fill out:

```markdown
## What
One sentence: what does this change?

## Why
One sentence: why is this needed? Link to the issue.

## How
Optional: only if the approach is non-obvious.

## Checklist
- [ ] Tests pass (or N/A — explain why)
- [ ] Documentation updated if needed
- [ ] No out-of-scope changes introduced
- [ ] Charter Rule passes — this moves toward the mission
```

### PR Lifecycle

```
Branch created
    ↓
Open as Draft PR (optional but encouraged — gets early feedback)
    ↓
Work complete → Mark Ready for Review
    ↓
Reviewer assigned
    ↓
Review (aim for ≤ 2 rounds)
    ↓
Approval + merge
    ↓
Branch deleted
```

**Draft PRs are encouraged.** Open one early to signal that work is in progress and to catch design issues before they become code problems.

---

## Code Review

Reviews should be educational and constructive. The goal is a better codebase and a smarter contributor — not to protect the repo from people.

### Review Language

Use prefixes to signal intent:

| Prefix | Meaning |
|--------|---------|
| `nit:` | Trivial preference; safe to ignore |
| `suggestion:` | Genuinely better approach; not blocking |
| `question:` | I don't understand this; please explain |
| `blocker:` | Must be resolved before merge |

### Approval Requirements

| Change type | Approvals required |
|-------------|-------------------|
| Documentation (minor) | 1 contributor |
| Documentation (architecture-level) | Technical Lead + Project Owner |
| Feature / fix | 1 approval (Technical Lead if no one available) |
| Architecture-touching change | Technical Lead + Senior Advisor |

**Target response time:** reviewers aim to respond within 48 hours of a PR being marked Ready for Review.

---

## Documentation-First Development

This is a core rule, not a suggestion:

> **Architecture and documentation must be approved before implementation begins.**

This means:
- If you're implementing a feature, the design must exist in an approved document.
- If no document covers your change, write or update the relevant document and get it approved first.
- If you're unsure what document governs your area, check `docs/documentation-architecture-blueprint.md` (DOC-001).

**Why:** a wrong architectural decision caught in a document review takes 10 minutes to fix. The same mistake caught after implementation takes days.

---

## Issue Labels and Sizing

### Type Labels

| Label | Meaning |
|-------|---------|
| `type: feature` | New capability |
| `type: fix` | Something broken |
| `type: docs` | Documentation only |
| `type: chore` | Maintenance, tooling, cleanup |
| `type: question` | Discussion or clarification needed |

### Size Labels

| Label | Meaning | Scope |
|-------|---------|-------|
| `size: small` | Single-purpose; reviewable in < 10 min | Single file, small function, one ADR |
| `size: medium` | One self-contained feature or document | One PR, 15–20 min review |
| `size: large` | Spans multiple areas | Should be split before work starts |

**Large issues should be decomposed into smaller issues before work begins.** Ask in the issue if you're unsure how to split.

### Special Labels

| Label | Meaning |
|-------|---------|
| `good first issue` | Self-contained, well-specified, beginner-friendly |
| `help wanted` | Open for anyone to claim |
| `status: ready` | Definition of Ready passed; claimable |
| `status: blocked` | Waiting on something external |
| `charter-rule-fail` | Proposal violates the Charter Rule; out of scope |

---

## Good First Issues

Issues labeled `good first issue` are specifically designed for contributors new to the project. They are:
- Self-contained (no deep context required)
- Well-specified (clear definition of done)
- Small in scope
- Assigned a mentor (named in the issue)

**Claim process:** comment on the issue expressing interest. A maintainer will assign it within 24 hours. If there is no PR within one week, the issue returns to open — no hard feelings.

---

## Definition of Ready

An issue must meet all of these before it can be claimed:

- [ ] Clear problem statement
- [ ] Specific, checkable acceptance criteria
- [ ] Scope is explicit (in-scope and out-of-scope)
- [ ] Size label applied
- [ ] No hidden blockers or unresolved dependencies
- [ ] No architectural ambiguity (design questions resolved before work starts)
- [ ] `status: ready` label applied

Issues that don't meet this bar have `status: needs-triage`. Comment if you think an issue is ready but hasn't been labelled.

---

## Definition of Done

A PR is done when all of the following are true:

**Implementation:**
- [ ] Feature or fix works as described in the issue's acceptance criteria
- [ ] No regressions (existing tests pass)
- [ ] New tests written for new behavior
- [ ] No unrelated changes in the PR

**Documentation:**
- [ ] Inline comments added where the *why* is non-obvious
- [ ] Affected documentation updated
- [ ] PR description filled out

**Review:**
- [ ] At least one approval from an authorized reviewer
- [ ] All `blocker:` comments resolved
- [ ] Non-blocking comments acknowledged

**Charter:**
- [ ] The Charter Rule passes — the change moves toward the mission
- [ ] No out-of-scope features introduced

**Merge:**
- [ ] Branch is up to date with `main`
- [ ] CI passes (once CI is established)
- [ ] Branch deleted after merge

---

## Testing Responsibilities

- **You write tests for your own code.** Tests are part of the task, not a separate step.
- **Run existing tests before opening a PR.** Don't submit a PR that breaks existing tests.
- **Update tests when your change alters expected behavior.**
- If a test genuinely cannot be written without infrastructure that doesn't yet exist, acknowledge it with a comment and link a follow-up issue. This is an exception, not a pattern.

Full testing strategy is documented in `docs/engineering/testing-strategy.md` (ENG-002) once available.

---

## Questions?

Open a GitHub Discussion or comment on a relevant issue. No question is too small — this project values learning as a first-class outcome.
