# Phase 2 Backlog — Panini B2B Catalog

| | |
|---|---|
| **Status** | ✅ v1 — Locked at end of MVP scoping (Step 9g) |
| **Owner** | [Your Name] |
| **Last Updated** | 2026-05-09 |

---

## What this document is

The consolidated backlog of every feature deferred from MVP scope, organized into coherent themes with explicit triggers.

**Why this matters:** Without this consolidation, deferred features become the "Phase 2 graveyard" — items that get listed but never built. By grouping into themes and assigning observable triggers, we ensure Phase 2 work begins when evidence justifies it, not arbitrarily.

## Phase 2 sequencing rule

Not all themes wait for triggers:

- **Theme 2 (Admin & Operational Excellence)** starts immediately after MVP launch. The team has already-known operational gaps from existing Panini operations.
- **Other themes** wait for their respective triggers to fire based on MVP data and evidence.
- **Themes can run in parallel** if multiple triggers fire close together.

This distinction matters: trigger-driven roadmaps are right when you don't yet have evidence. But sometimes evidence already exists from operational history, team interviews, or known pain — those items don't need to wait.

---

## Theme 1: Full B2B E-commerce

**Trigger to start:** ≥30% of MVP orders flow through "Place Order Directly" (Path 3) within the first 60 days post-launch. Indicates buyers actually want to transact on platform.

**Hypothesis:** Once buyers prove they're willing to transact on platform, they'll value features that make repeat transactions effortless.

**Features:**
- Persistent cart (across visits, across devices)
- Wishlist / favorites
- Order history (for logged-in buyers)
- Reorder from previous order
- Multiple shipping addresses
- Quote request workflow (RFQ → admin quote → buyer accept)
- Custom design request form
- Saved payment methods
- Razorpay integration for online payments
- Buyer profile management
- Notification preferences

---

## Theme 2: Admin & Operational Excellence ⭐ STARTS IMMEDIATELY POST-MVP

**Trigger to start:** Already justified by existing operational pain. Begins as soon as MVP ships and stabilizes.

**Hypothesis:** The team has known operational gaps from running Panini's B2B for years. These don't need to be re-validated — just built.

**Features:**
- **Pending order management** (per-line-item status workflow) — *priority within theme*
- Worker / artisan assignment for pending items
- Buyer-facing pending order visibility
- Approve new retailers (if access gating becomes desired)
- Tag VIP / standard / new buyer
- Block / suspend buyer
- Send broadcast / announcement
- Generate invoice (consolidate from MyBillBook)
- In-platform messaging with buyers about orders
- Refund order workflow
- Schedule product publish date
- Bulk price update
- Drag-drop photo reordering
- Configure shipping zones / rates
- Team members + permissions (RBAC)
- Audit log of admin actions
- Data export (orders, products, buyers)

**Note on data model readiness:** Per-line-item status field is included in MVP data model from day one, even though only "shipped/cancelled" values are used in MVP. Phase 2 pending-order workflow starts from a foundation, not a refactor.

---

## Theme 3: AI & Discovery Enhancement

**Trigger to start:** MVP analytics show ≥30% of search queries return zero/poor results, OR new-buyer onboarding still feels slow despite the catalog being live. Signals that discovery is the bottleneck.

**Hypothesis:** Once basic catalog is proven, AI-powered discovery features can take buyer experience from useful to memorable.

**Features:**
- **Image search (Variant A)** — buyer uploads external photo, system finds visually similar Panini designs
- **Order book scanning** — OCR of handwritten order books, extracts line items, pre-populates orders
- Similar products section on product detail page
- Sort by popularity (needs view/order data first)
- Visual similarity browse ("more like this")
- Top viewed / top searched (full version vs MVP-lite)

**Why deferred:** Both image search and OCR have high build complexity. Their adoption value is uncertain. Better to validate buyers want the catalog at all before investing in delight features.

---

## Theme 4: Marketing & Growth

**Trigger to start:** MVP adoption hits ≥30% target and we want to push toward stretch (50%+) or expand buyer base.

**Hypothesis:** Premature growth marketing creates noise. Wait until product-market fit is proven, then amplify.

**Features:**
- Push notifications
- Email broadcasts
- Coupon / discount codes
- Referral program
- Festival campaigns (beyond simple hero banner)
- A/B testing infrastructure
- QR code per product
- Branded sharing template (custom-designed share images)
- SMS / Email share options

---

## Theme 5: Reach & Accessibility

**Trigger to start:** Real user research shows specific buyer segments are excluded by current product (e.g., Hindi-only buyers, low-connectivity areas).

**Hypothesis:** Accessibility expansions (language, offline, native apps) should be evidence-driven, not preemptive.

**Features:**
- Multi-language (English + Hindi)
- Offline browsing of viewed products
- PWA installable
- Full WCAG AA accessibility
- Mobile native app (if data shows web is the bottleneck)

---

## Theme 6: Integrations

**Trigger to start:** Manual data entry between Panini B2B and existing tools (MyBillBook, Tally) becomes painful at order volume.

**Hypothesis:** Integrations carry ongoing maintenance burden. Defer until manual reconciliation hurts more than integration upkeep would.

**Features:**
- MyBillBook integration (export/sync orders, products)
- Tally integration (if needed)
- Bulk SMS service for notifications
- More sophisticated email service templates
- Razorpay (if not already triggered by Theme 1)
- Government GSTIN verification API

---

## Theme 7: Trust & Brand

**Trigger to start:** Onboarding metrics show new buyers hesitate to order, OR existing buyers ask for more "validation" content.

**Hypothesis:** Trust-and-presentation enhancements matter when basic trust isn't enough. Don't over-build trust signals before basic ones are proven insufficient.

**Features:**
- Photos of real shop owners using Panini products
- Detailed quality assurance content (materials, finish standards)
- Video / 360° spin on product detail
- AR try-on (jewelry visualization)

---

## On "Phase 3"

Phase 3 doesn't exist yet. It's vapor.

By the time Phase 2 themes are mostly done, we'll have so much new data that any Phase 3 we plan now will be wrong. Better to write Phase 2 with rigor and leave Phase 3 unplanned. We'll define it after Phase 1 ships and we have data.

This is the senior move — most teams over-plan future phases and refuse to update those plans when reality changes.

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| v1 | 2026-05-09 | Initial backlog locked at end of Step 9g. 7 themes. Theme 2 starts immediately post-MVP; others trigger-driven. |
