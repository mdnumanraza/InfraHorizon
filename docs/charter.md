# Project Charter

> **ID:** CHAR-001
> **Version:** 1.0
> **Status:** Approved
> **Owner:** Project Owner
> **Approver:** Project Owner
> **Last Updated:** 2026-07-14

---

## 1. Mission

infraHorizon exists to make distributed system behavior understandable.

We do this by connecting to live infrastructure, consuming real events, and transforming them into interactive execution graphs that engineers, learners, and operators can explore and reason about.

---

## 2. North Star

A future where anyone — not just those who built a system — can connect to live infrastructure and immediately see what it is doing, why it is doing it, and what happened when something went wrong.

Understanding should not require expertise in the internals of the system being observed.

---

## 3. Product Philosophy

**Real over simulated.** We connect to live systems. Mock data and simulations are not the product.

**Behavior over state.** We are interested in what a system *does*, not just what it *is*. A snapshot is less valuable than a sequence of events.

**Understanding over features.** Every capability must help someone understand something. A feature that does not teach or illuminate does not belong here.

**Live over polling.** Event-driven observation is preferable to periodic sampling. When a system speaks, we listen in real time.

**Foundation over speed.** A correct, maintainable foundation is worth more than a wide, fragile one. We build slowly and deliberately.

---

## 4. Core Principles

1. We connect to **real systems**, not simulated ones.
2. The infrastructure being observed is always the source of truth.
3. Live events are preferred over polling wherever possible.
4. Every feature must have educational value.
5. Every version must be independently usable.
6. Every version must end in a releasable state.
7. Architecture is more important than feature count.
8. Extensibility must be considered but not prematurely implemented.
9. We prefer simplicity over completeness.
10. No feature should be added simply because a platform supports it.

---

## 5. Project Values

**Clarity.** We write clear code, clear documentation, and clear decisions. If something is hard to understand, that is a problem to solve, not a sign of sophistication.

**Teaching.** Learning is a first-class outcome of this project — not just for users of the platform, but for contributors building it. We explain, mentor, and document with the next person in mind.

**Honesty.** We document decisions that were rejected and why. We acknowledge complexity rather than hiding it. We do not pretend a foundation is more complete than it is.

**Deliberateness.** We plan before we build. We design before we implement. We review before we merge. Thoughtful action produces better systems than fast action.

**Openness.** Contributions, questions, and challenges to our assumptions are welcome at every level of experience. The best ideas come from diverse perspectives.

---

## 6. The Charter Rule

> **Every roadmap item, feature, architecture decision, and future plugin must answer one question:**
>
> *"Does this move the project toward the mission?"*
>
> **If the answer is no, it does not belong in this project.**

This is the primary protection against scope creep. It applies to everyone, at every stage, without exception. When in doubt, reread the Mission.

---

## 7. Explicit Non-Goals

infraHorizon is not, and will never become:

- **A Kubernetes dashboard.** We visualize behavior over time, not current cluster state.
- **A Kubernetes replacement or management tool.** We observe; we do not control.
- **A monitoring or alerting platform.** Alerting and metrics belong to dedicated tools.
- **A simulation or mock environment.** We connect to real systems or we do not run.
- **An all-in-one infrastructure platform.** Scope is defined by the mission, not by what platforms technically support.
- **A product built for a single organization.** We are open-source and built for the community.

These are not deferred goals. They are permanent boundaries.
