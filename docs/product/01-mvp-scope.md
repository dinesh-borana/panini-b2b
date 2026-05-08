# MVP Scope — Panini B2B Catalog

| | |
|---|---|
| **Status** | 🟡 In Progress (Step 9 of Product Discovery) |
| **Owner** | [Your Name] |
| **Last Updated** | 2026-05-08 |
| **Related Docs** | [Product Brief v1](./00-product-brief.md) |

---

## What this document is

This is the **MVP scoping document** for Panini B2B. It defines:

1. The riskiest assumptions we're testing in v1
2. How we'll know if MVP succeeded
3. The minimum feature set that lets us run that test
4. What's explicitly deferred to later phases

This document is the bridge between the high-level Product Brief and the detailed user flows / system design that follow.

---

## Step 9a: Riskiest assumptions

The MVP exists to test these two assumptions about Panini B2B:

### Assumption 1 — Buyer Adoption
> Buyers will actually use the catalog instead of asking on WhatsApp.

### Assumption 2 — Onboarding Speed
> Sharing a catalog link will onboard new retailers faster than the current WhatsApp catalog-forwarding flow.

These two assumptions are linked: solving onboarding well (Assumption 2) creates more catalog-aware buyers, which improves adoption (Assumption 1).

### Why these and not others?

Other risks were considered and rated lower for MVP:

| Risk | Why deferred |
|------|--------------|
| Team won't keep catalog updated | Operational, can be fixed by process; not a launch-blocker |
| Photos won't convey jewelry well online | Solvable with iteration on photography; not a binary fail |
| Buyers won't trust prices online | Mitigated by public price transparency + consistency with WhatsApp posts |

---

## Step 9b: Success Criteria (Tiered Targets)

We use **tiered targets** rather than a single number, because:

1. We have no baseline data — making single thresholds arbitrary
2. WhatsApp is a habit-driven channel; "need" alone doesn't guarantee adoption
3. Tiered targets distinguish "category-defining win" from "solid product" from "needs work"

### Adoption targets (60 days post-launch)

| Metric | Floor (something works) | Target (success) | Stretch (exceptional) |
|--------|--------------------------|--------------------|------------------------|
| % of active WhatsApp buyers who visit catalog ≥2 times | 15% | 30% | 50% |
| % of WhatsApp design enquiries that reference a catalog item code/link | 10% | 20% | 35% |

### Onboarding targets

| Metric | Floor | Target | Stretch |
|--------|-------|--------|---------|
| Median time: new retailer first contact → first product enquiry | <3 days | <24 hours | Same day |

### Why two adoption metrics?

- **Repeat visits** = is it becoming a habit?
- **WhatsApp references to catalog items** = is the catalog becoming the *source of truth* for buyer-team conversations?

A buyer who visits twice but never mentions catalog items in WhatsApp = curious, not adopted. A buyer whose WhatsApp messages now say "PJ-K-128 ka rate kya hai?" = genuinely adopted.

### Instrumentation note

Hitting these metrics requires we measure them. To be designed in Step 15 (System Design), but the MVP must include:

- Page-level analytics (visits, repeat visits per buyer)
- A way to identify buyers (even loosely — a phone number, a referrer link, anything)
- Some method to tag WhatsApp enquiries that reference catalog items (likely manual tagging by team in v1)

---

## Step 9c: Feature Brainstorm

_To be filled in next session._

---

## Step 9d: MVP Filter

_To be filled in next session._

---

## Step 9e: Prioritization

_To be filled in next session._

---

## Step 9f: Definition of Done for v1

_To be filled in next session._

---

## Step 9g: Deferred Backlog

_To be filled in next session._

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| v0.1 | 2026-05-08 | Steps 9a (assumptions) and 9b (success criteria) locked. Tiered targets adopted after discussion. |
