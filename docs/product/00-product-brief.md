# Product Brief v1 — Panini B2B Catalog

| | |
|---|---|
| **Status** | ✅ Approved (v1) |
| **Owner** | [Your Name] |
| **Last Updated** | 2026-05-08 |
| **Next Review** | After MVP scope is locked |

---

## What we're building

A public, shareable B2B catalog platform for Panini Jewels that complements (not replaces) the existing WhatsApp-based sales channel. Buyers — resellers and retailers — can browse Panini's full design library with photos, prices, and key product details. They can share specific products to their own WhatsApp contacts, send their selections back to Panini's team to place orders, or place orders directly on the platform.

## Why we're building it

Panini's B2B operation runs on 4 WhatsApp groups with ~1000 buyers, growing. The team is hitting two scaling walls:

1. **Repetitive question volume** — every "rate kya hai" / "weight kitna" / "stock hai kya" is currently a manual reply. With ~1000 buyers, this is unsustainable and limits how many new retailers we can onboard.
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
3. **Catalog accumulates** — designs don't expire. Stock status is shown as **In Stock** or **Made to Order**.
4. **Mobile-first design** — buyers will mostly browse on phones, often in the middle of WhatsApp conversations.
5. **Catalog completeness over checkout polish** — the platform's job is to surface a great catalog, not push buyers through a checkout funnel.

## Success metrics (6 months post-launch)

| Metric | Type | Target |
|--------|------|--------|
| Onboarding speed | Time | New retailer: first contact → browsing full catalog in <15 minutes |
| Order capture rate | % | ≥30% of B2B orders originate on the platform vs. pure WhatsApp Q&A |
| Quality | Errors | Pricing/stock-status errors drop to near-zero |

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
- ❌ Inventory tracking beyond simple "In Stock / Made to Order" toggle
- ❌ Buyer credit limit management (handled offline as today)
- ❌ Public consumer (B2C) storefront
- ❌ Mobile native apps (mobile web is sufficient)
- ❌ Real-time chat (WhatsApp deep-links are enough)
- ❌ Multi-language (English-first, Hindi if needed later)

## What v1 must do (high level — to be detailed in MVP scope)

- Public catalog browse (no login)
- Categories, search, and filters
- Product detail page with photo gallery, price, weight, purity, design code, stock status
- Easy share to WhatsApp from any product
- "Place order" flow that generates a WhatsApp message to Panini's team OR captures order on platform for prepaid buyers
- Admin panel for Panini's team to manage catalog (add/edit products, prices, stock status)
- Onboarding flow: send a link to a new retailer, optionally collect basic KYC if they want to place orders directly

---

## Discovery summary (how we got here)

This brief is the output of a structured product discovery process across 8 steps:

1. **Problem Discovery** — Confirmed pain is real: volume of repetitive WhatsApp questions + lack of catalog for onboarding
2. **User Discovery** — Identified resellers + retailers, mostly Tier-2/3, WhatsApp-native, relationship-driven
3. **Jobs-to-be-Done** — Buyers "hire" the channel to find designs, share with their customers, and place trusted orders
4. **Alternative Analysis** — Real competitor is WhatsApp itself, not other B2B portals
5. **Product Strategy** — Hybrid model (catalog complements WhatsApp, doesn't replace it). Single-tenant.
6. **Goals & Metrics** — Onboarding speed + order capture % + quality errors
7. **Constraints & Risk** — Adoption is the #1 risk; team/budget/timeline are flexible
8. **Synthesis** — This brief

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| v1 | 2026-05-08 | Initial brief approved |
