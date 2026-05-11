# Product Brief v2 — Panini B2B Catalog

| | |
|---|---|
| **Status** | ✅ Approved (v2) |
| **Owner** | [Your Name] |
| **Last Updated** | 2026-05-09 |
| **Next Review** | After MVP scope is fully locked (Step 9g) |

> **v2 changelog:** Updated product context to reflect that Panini Jewels deals in fashion/imitation jewelry, not precious-metal trade. This propagates to filters, trust signals, and pricing model in MVP scope.

---

## What we're building

A public, shareable B2B catalog platform for Panini Jewels that complements (not replaces) the existing WhatsApp-based sales channel. Buyers — resellers and retailers — can browse Panini's full design library with photos, prices, and key product details. They can share specific products to their own WhatsApp contacts, send their selections back to Panini's team to place orders, or place orders directly on the platform.

## What Panini Jewels actually sells

**Fashion / imitation / artificial jewelry**, sold wholesale to resellers and retailers. Designs are crafted with materials like alloys, brass, plated metals, German silver, kundan-style stones, AD/CZ stones, glass stones, beads, etc. Pricing is per-design (flat), not based on metal weight × purity × daily rate.

This positions Panini in the fashion-jewelry trade, not the precious-metal trade — which has implications for the product:
- Pricing is stable per design (no daily rate volatility)
- Filters are about plating type and stone style, not metal purity
- Trust signals are about design originality and finish quality, not hallmarking certifications
- Inventory is regular product inventory (restockable), not bullion-anchored

## Why we're building it

Panini's B2B operation runs on 4 WhatsApp groups with ~1000 buyers, growing. The team is hitting two scaling walls:

1. **Repetitive question volume** — every "rate kya hai" / "kya available hai" is currently a manual reply. With ~1000 buyers, this is unsustainable and limits how many new retailers we can onboard.
2. **No standardized catalog** — when a new retailer asks for designs, there's no link to send. The team forwards photos manually, which is slow, inconsistent, and a major friction point in onboarding.

## Who it's for

### Primary users

- **Resellers** — buy from Panini, resell into their own retail network
- **Retailers** — buy from Panini, sell directly to consumers in their stores

Both are WhatsApp-native, relationship-driven, and value the personal connection with Panini's team. Most are in Tier-2/3 cities; mobile-first browsing.

### Secondary users

- **Panini's internal team** — manage the catalog, respond to buyers, process orders
- **Panini's leadership** — visibility into onboarding, orders, and catalog health

## Product strategy: Hybrid (catalog-first)

WhatsApp remains the primary transaction layer. The platform is the **discovery layer**:

- Buyers browse, select, and share — on the platform
- Buyers ask questions, negotiate, place orders — on WhatsApp (or via the platform if they prefer)
- Panini's team replaces "type the price" with "send the link"
- New retailer onboarding becomes "send them this link" instead of multi-day catalog-forwarding

## Core principles

1. **No login required to browse** — public catalog, public prices. Maximum reach, zero friction.
2. **WhatsApp-first sharing** — every product page has prominent "Share to WhatsApp" actions.
3. **Show only what's available** — out-of-stock items are hidden from the catalog. Buyers see actionable products only; restock conversations happen via WhatsApp.
4. **Mobile-first design** — buyers will mostly browse on phones, often in the middle of WhatsApp conversations.
5. **Catalog completeness over checkout polish** — the platform's job is to surface a great catalog, not push buyers through a checkout funnel.

## Success metrics (6 months post-launch)

| Metric | Floor | Target | Stretch |
|--------|-------|--------|---------|
| % of active WhatsApp buyers who visit catalog ≥2 times in 60d | 15% | 30% | 50% |
| % of WhatsApp design enquiries referencing a catalog item code/link | 10% | 20% | 35% |
| Median: new retailer first contact → first product enquiry | <3 days | <24 hours | Same day |

## Biggest risk: Buyer adoption

Buyers love WhatsApp's familiarity. They might keep asking on WhatsApp instead of using the link.

**Mitigations baked into MVP and GTM:**

- Every team WhatsApp reply includes the catalog link
- Catalog must be *better* than scrolling old WhatsApp messages — search, category browse, filtered views
- Make resharing back to WhatsApp seamless (so buyers can forward designs to their own customers easily)
- Catalog has designs that *aren't* in WhatsApp groups (incentive to browse)

## Constraints

- **Team:** Founder + 1 team member building this
- **Budget/timeline:** No hard constraints; build it right
- **Existing systems:** MyBillBook is used for billing today — **no integration in MVP**, manual reconciliation acceptable. Plan for a Phase-2 export/sync.
- **Architecture:** Single-tenant for Panini. Other manufacturers' needs likely diverge enough that multi-tenancy isn't worth premature investment.

## Out of scope for v1 (explicit)

- ❌ Multi-tenancy / SaaS for other manufacturers
- ❌ MyBillBook or any third-party integration
- ❌ Full B2B e-commerce (cart, wishlist, order history, reorder, persistent login) — explicitly deferred to **Phase 2** as a strategic decision
- ❌ Pending order management with worker assignment — deferred to Phase 2 (data model accommodates it from day one)
- ❌ Image search and order book scanning (AI features) — deferred to Phase 2
- ❌ Public consumer (B2C) storefront
- ❌ Mobile native apps (mobile web is sufficient)
- ❌ Real-time chat (WhatsApp deep-links are enough)
- ❌ Multi-language (English-first, Hindi later if needed)
- ❌ Live gold rate display (not relevant for fashion jewelry)

## What v1 includes (high level — see [MVP Scope](./01-mvp-scope.md) for detail)

- Public catalog browse (no login)
- 7 buyer-facing filters (category, plating type, stone style, occasion, size, price, newest)
- Product detail with photo gallery, pinch-zoom, design code, dimensions, plating, stone style, price
- Single-product and multi-product WhatsApp sharing
- Phone-OTP login gated to "Place Order Directly"
- Admin panel for catalog CRUD, order capture, packing slip print
- Analytics for measuring success metrics
- Performance baseline (<2s on 3G, image CDN, error monitoring)

---

## Discovery summary (how we got here)

This brief is the output of a structured product discovery process:

1. **Problem Discovery** — Volume of repetitive WhatsApp questions + lack of catalog for onboarding
2. **User Discovery** — Resellers + retailers, mostly Tier-2/3, WhatsApp-native, relationship-driven
3. **Jobs-to-be-Done** — Buyers "hire" the channel to find designs, share with their customers, and place trusted orders
4. **Alternative Analysis** — Real competitor is WhatsApp itself, not other B2B portals
5. **Product Strategy** — Hybrid model (catalog complements WhatsApp, doesn't replace it). Single-tenant.
6. **Goals & Metrics** — Tiered targets across adoption, onboarding, quality
7. **Constraints & Risk** — Adoption is the #1 risk; team/budget/timeline are flexible
8. **Synthesis** — This brief

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| v1 | 2026-05-08 | Initial brief approved |
| v2 | 2026-05-09 | Updated for fashion jewelry context (replaces precious-metal-trade assumptions). Added explicit deferrals from MVP scoping decisions. Updated success metrics to tiered targets format. |
