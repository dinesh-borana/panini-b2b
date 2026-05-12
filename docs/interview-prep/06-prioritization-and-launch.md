# 06 — MVP Prioritization, Launch Strategy & Roadmaps

## Q: How do you decide what to build first within an MVP?

Default to **walking-skeleton** delivery. Slice 1 ships the full stack — minimal data, API, UI — for one workflow end-to-end. Each slice thickens the system. Never holding half-built features; every slice demonstrable; integration risk surfaced day 1, not week 8.

**Story:** Panini B2B split into 6 slices. Slice 1 deliberately thin — deploy app, render one product, share to WhatsApp. Slice 2 thickened catalog. Slice 3 added discovery polish. Slice 4 added orders. Slice 5 added measurement and trust pages. Slice 6 was pre-launch hardening. Every slice demoable.

**Don't say:** "Build all admin first, then buyer." "Whatever's at top of backlog."

## Q: How do you estimate timelines for MVP?

Avoid timeline estimates before any code. Velocity is empirical — you only know how fast you ship after shipping something. Rank features into slices, ship Slice 1, use that velocity to forecast remaining. Pre-baseline estimates are theatre.

## Q: Definition of Done?

Graduated milestones, not a single binary gate. "Ready for friendly users" ≠ "ready for unknown users at scale."

**Story:** For Panini I locked two milestones. **Soft Launch:** ready for 5-10 trusted buyers. Functional + quality + measurement + trust pages + ops readiness. **Public Launch:** adds soft-launch outcomes ("at least 5 of 10 visited"), scale-readiness, communication. Public criteria depend on Soft outcomes — conditional planning.

**Principle:** DoD is a quality gate. Launch strategy is a rollout question. Different decision-makers, different risk profiles.

## Q: Handling stakeholder pushing for riskier launch?

Surface the risk profile of each approach explicitly. Don't push back on the approach; push back on the implicit assumptions.

**Story:** Founder initially said "public launch, all 4 groups, full announcement." I laid out risks: blast radius if bug, team responsiveness load, no early-feedback. Founder reconsidered, chose phased soft launch. Not pushing my preference — making trade-offs visible.

## Q: Structuring Phase 2 to avoid graveyard?

Three layers. **Themes** = coherent feature groups shipping together. **Triggers** = observable signals indicating "now is the right time." **Within-theme features** = the actual list.

**Story:** Panini Phase 2 has 7 themes. Theme 2 (Admin) starts immediately post-MVP — evidence already exists from operational history. Others wait for triggers like "≥30% orders flow through Place Order" (Theme 1).

## Q: Why do some themes start immediately and others wait?

Not all Phase 2 work has equal evidence threshold. When evidence already exists — from operational history, team interviews, known pain — theme can start as soon as MVP ships. When speculative — depending on user behavior we haven't observed — theme waits for triggers. Treating all Phase 2 as equally speculative is its own form of fiction.

## Q: How do you avoid roadmap fiction?

Trigger-driven roadmaps over time-driven. Calendar-based roadmaps are fiction — they pretend we know in March what we'll need in September. Trigger-based tie work to observable signals. "Cart starts when 30% of orders flow through Place Order" is concrete. "Cart in Q3" is a guess.

## Q: Phase 3?

Doesn't exist yet. By the time Phase 2 is mostly done, so much new data exists that any Phase 3 we plan now will be wrong. Write Phase 2 with rigor; leave Phase 3 unplanned.
