# MVP Scope — Panini B2B Catalog

| | |
|---|---|
| **Status** | ✅ Step 9 COMPLETE |
| **Last Updated** | 2026-05-09 |

## Step 9a: Riskiest assumptions

**Assumption 1 — Buyer Adoption:** Buyers will use the catalog instead of asking on WhatsApp.
**Assumption 2 — Onboarding Speed:** Sharing a catalog link will onboard new retailers faster than current WhatsApp catalog-forwarding flow.

## Step 9b: Success Criteria (Tiered Targets)

### Adoption (60 days post-launch)
| Metric | Floor | Target | Stretch |
|---|---|---|---|
| % WhatsApp buyers visit catalog ≥2 times | 15% | 30% | 50% |
| % WhatsApp enquiries referencing catalog item | 10% | 20% | 35% |

### Onboarding
| Metric | Floor | Target | Stretch |
|---|---|---|---|
| Median: first contact → first product enquiry | <3 days | <24 hours | Same day |

## Step 9c: Feature Brainstorm

~115 features brainstormed across buyer-side, admin-side, cross-cutting. Full list preserved in earlier doc versions.

## Step 9d: MVP Filter

| Verdict | Count |
|---|---|
| 🟢 MVP (full) | ~50 |
| 🟡 MVP-lite | ~25 |
| 🔴 Phase 2 | ~35 |
| ❌ Removed/N/A | ~7 |

### Buyer-side MVP features

**Catalog browsing:** Grid + pagination, sort by newest/price (lite), search by SKU/keyword (lite)

**Filters (post fashion-jewelry back-fix):**
- 🟢 Price range, Category, Plating type (gold-tone/silver-tone/rose-gold-tone/oxidized), Newest
- 🟡 Stone style (kundan-style/AD-CZ/polki-style/glass-stones/pearl/beads/no-stones), Occasion (wedding/festival/daily/gifting), Size (rings/bangles/chains only)
- ❌ Stock status filter (out-of-stock hidden instead)

**Product detail:** Photo gallery + pinch-zoom, design code/name/plating/stone/dimensions/MOQ/sizes/price, weight (lite, optional), delivery estimate (lite, static)

**Sharing:** WhatsApp single (full), copy link, Open Graph tags, watermarked download (lite), multi-product enquiry list (lite)

**Enquiry/Order:** Enquire on WhatsApp button (full), Place Order Directly form (lite), bulk enquiry (lite)

**Auth:** No login to browse (full), phone-OTP gated to Place Order (lite)

**Trust:** About, Contact pages (full); Return/Privacy/Terms (lite)

### Admin-side MVP features

**Catalog mgmt:** Add/edit/archive product, bulk image upload, hide/unhide, categorize, set price; bulk CSV upload (lite), photo reorder (lite)

**Orders:** View enquiries, view orders, update status, **print packing slip (A4)**; cancel order (lite)

**User mgmt:** View buyer list; buyer activity (lite)

**Analytics:** Visits, adoption dashboard, WhatsApp CTR; top viewed/searched/funnel (lite)

**Ops (lite):** WhatsApp number config, GST settings, hero banner

### Cross-cutting MVP

- 🟢 Mobile-first, image CDN, <2s on 3G, OG tags, Sentry, PostHog, sitemap/robots, loading states, empty states, search/category/homepage pages, product visibility flag
- 🟡 SEO basics, email service (OTP/order confirm), accessibility basics, 404 page, cookie consent, privacy/terms pages

### Removed
Stock status filter, making charges, hallmarking, gold rate display, reviews/testimonials, live chat, dark mode

## Step 9e: 6 Vertical Slices (Walking Skeleton)

1. **Walking Skeleton** — Deploy app, render one product, share to WhatsApp end-to-end
2. **Catalog Foundation** — Categories, multiple products, basic filters (Plating/Category/Newest/Price), mobile responsive, 30-50 products
3. **Discovery Polish** — Search, remaining filters lite, sort options, multi-product selection + share, empty/loading states
4. **Order Capture** — Phone-OTP auth, Place Order form, admin orders list, status workflow, print packing slip, email service
5. **Measurement & Trust** — PostHog, performance, trust pages, SEO, error handling, email templates
6. **Pre-Launch Hardening** — 100+ products migrated, configuration, MVP-lite admin polish, cross-browser QA, launch prep

## Step 9f: Two-Milestone Definition of Done

**Milestone 1 — Soft Launch:** Ready to share with 5-10 trusted buyers. All 6 slices complete, no critical bugs, <2s on 3G, 100+ products, analytics + Sentry running, all trust pages live, team trained.

**Milestone 2 — Public Launch:** Ready for all 4 WhatsApp groups. Soft launch outcomes met (5+ buyers visited, 2+ orders/real enquiries, bugs fixed), scale readiness, launch communication prepared.

## Step 9g: Phase 2 Backlog

See [Phase 2 Backlog](./02-phase2-backlog.md)

## Changelog

| Version | Date | Changes |
|---|---|---|
| v0.4 | 2026-05-09 | Full Step 9 complete (a–g) |
