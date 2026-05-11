# MVP Scope — Panini B2B Catalog

| | |
|---|---|
| **Status** | 🟡 Step 9d complete; 9e–g pending |
| **Owner** | [Your Name] |
| **Last Updated** | 2026-05-09 |
| **Related Docs** | [Product Brief v2](./00-product-brief.md) |

---

## What this document is

The MVP scoping document for Panini B2B. It defines:

1. The riskiest assumptions we're testing in v1 (Step 9a)
2. How we'll know if MVP succeeded (Step 9b)
3. The complete brainstormed feature universe (Step 9c)
4. The MVP filter applied to every feature (Step 9d)
5. Prioritization within MVP (Step 9e — pending)
6. Definition of Done for v1 (Step 9f — pending)
7. Phase 2 backlog (Step 9g — pending)

---

## Step 9a: Riskiest assumptions

### Assumption 1 — Buyer Adoption
> Buyers will actually use the catalog instead of asking on WhatsApp.

### Assumption 2 — Onboarding Speed
> Sharing a catalog link will onboard new retailers faster than the current WhatsApp catalog-forwarding flow.

These two are linked: solving onboarding well (Assumption 2) creates more catalog-aware buyers, which improves adoption (Assumption 1).

---

## Step 9b: Success Criteria (Tiered Targets)

We use **tiered targets** rather than single thresholds:

### Adoption targets (60 days post-launch)

| Metric | Floor | Target | Stretch |
|--------|-------|--------|---------|
| % of active WhatsApp buyers who visit catalog ≥2 times | 15% | 30% | 50% |
| % of WhatsApp design enquiries referencing a catalog item code/link | 10% | 20% | 35% |

### Onboarding targets

| Metric | Floor | Target | Stretch |
|--------|-------|--------|---------|
| Median time: new retailer first contact → first product enquiry | <3 days | <24 hours | Same day |

### Instrumentation note

Hitting these metrics requires we measure them. The MVP must include:
- Page-level analytics (visits, repeat visits per buyer)
- WhatsApp deep-link click-through tracking
- Some method to tag WhatsApp enquiries that reference catalog items (manual tagging by team in v1)

---

## Step 9c: Feature Brainstorm (locked)

The complete brainstormed list of every feature considered. Filtering happens in Step 9d.

> **Note:** This brainstorm preceded the discovery that Panini sells fashion jewelry, not precious-metal goods. The brainstorm itself is unchanged for honesty, but Step 9d verdicts incorporate the fashion-jewelry context.

### Buyer-side
**Catalog browsing:** grid view, pagination, sort (newest/price/popularity), search by SKU/keyword.

**Filters:** Price, Metal, Stone type, Category, Occasion, Stock status, Newest, Size.

**Product detail:** photo gallery, pinch-zoom, video/360°, weight/purity/dimensions/code, making charges, stock status, delivery estimate, available sizes, similar products, AR try-on.

**Sharing:** WhatsApp single, WhatsApp multi-product list, copy link, watermarked download, QR code, SMS/email, branded template.

**Enquiry/Order:** WhatsApp deep-link enquiry, multi-item enquiry, Place Order form, persistent cart, wishlist, quote request, order tracking, order history, reorder, multi-address, custom design request, bulk enquiry.

**Auth:** no-login browse, phone-OTP for orders, WhatsApp OTP, profile, addresses, payment methods, notifications.

**AI features:** Image search, order book scanning.

**Trust:** real-buyer photos, certifications, return policy, About page, contact info, reviews (removed), live chat (removed).

### Admin-side
**Catalog management:** add/edit/archive product, bulk image upload, mark stock, schedule publish, categorize/tag, set making charges, set base price, bulk price update.

**Order/Enquiry management:** view enquiries, view orders, update status, cancel, generate invoice, communicate with buyer, refund, **print packing slip**, **pending order tracking**, **worker assignment**.

**User management:** buyer list, approve retailers, tag VIP/standard/new, view buyer activity, block, send broadcast.

**Analytics:** visit counts, top viewed, top searched, conversion funnel, adoption metrics, WhatsApp CTR.

**Operations:** WhatsApp number config, GST settings, shipping zones, team members/permissions, audit log, data export.

**Marketing:** push notifications, email broadcasts, hero banner, coupons, referral, festival campaigns, A/B tests.

### Cross-cutting/Technical
Mobile-first responsive, image CDN, multi-language, accessibility, SEO, Open Graph, page-load <2s on 3G, offline browsing, PWA, MyBillBook/Tally integration, Razorpay, SMS service, email service, Sentry, PostHog/Mixpanel, dark mode (removed).

### Loose ends added in Batch 10
Sitemap, robots.txt, 404 pages, loading skeletons, empty states, cookie consent, privacy/terms pages, search results page UX, category landing pages, homepage, product visibility flag, live gold rate (removed — not relevant for fashion jewelry).

---

## Step 9d: MVP Filter

Every feature evaluated against:
- **Q1:** Does the MVP test fail without it?
- **Q2:** Is the build cost proportional to its contribution to the test?

Verdicts:
- 🟢 **MVP** — full version
- 🟡 **MVP-lite** — reduced version (limited vocabulary, partial coverage, basic UI)
- 🔴 **Phase 2** — deferred with rationale
- ❌ **Removed** — won't build

### Final filter results — Buyer side

#### Catalog browsing
| Feature | Verdict | Notes |
|---------|---------|-------|
| Grid view | 🟢 MVP | Foundational |
| Pagination | 🟢 MVP | Chosen over infinite scroll for reliability + SEO |
| Sort by newest | 🟢 MVP | |
| Sort by price | 🟡 MVP-lite | Cheap to add |
| Sort by popularity | 🔴 Phase 2 | Needs view/order data first |
| Search by SKU/design code | 🟢 MVP | Critical for "WhatsApp reference to catalog item" success metric |
| Search by keyword | 🟡 MVP-lite | Postgres FTS basic version |

#### Filters (post fashion-jewelry back-fix)
| Filter | Verdict | Vocabulary |
|--------|---------|------------|
| Price range | 🟢 MVP | — |
| **Plating type** *(replaces Metal)* | 🟢 MVP | Gold tone, silver tone, rose gold tone, oxidized |
| **Stone style** *(revised)* | 🟡 MVP-lite | Kundan-style, AD/CZ, polki-style, glass stones, pearl, beads, no stones |
| Category | 🟢 MVP | Rings/necklaces/earrings/bangles/chains/sets/etc. |
| Occasion | 🟡 MVP-lite | Wedding, festival, daily, gifting |
| Newest | 🟢 MVP | Free (sort by created_at) |
| Size | 🟡 MVP-lite | Category-aware: ring sizes, bangle inches, chain length. Build for 2-3 categories first. |
| ~~Stock status~~ | ❌ Removed | Out-of-stock items hidden from catalog instead |

#### Product detail
| Feature | Verdict | Notes |
|---------|---------|-------|
| Photo gallery | 🟢 MVP | Multiple angles. Foundational for jewelry. |
| Pinch-zoom | 🟢 MVP | |
| Design code, name, plating, stone style, dimensions | 🟢 MVP | |
| Weight (in grams of product) | 🟡 MVP-lite | Optional field |
| Price | 🟢 MVP | Flat per design |
| MOQ (minimum order qty) | 🟢 MVP | |
| Available sizes (per product) | 🟢 MVP | Required for Size filter |
| Stock status badge | ❌ Removed | Per back-fix |
| Making charges | ❌ Removed | Not relevant for fashion jewelry |
| Delivery time estimate | 🟡 MVP-lite | Static text |
| Video / 360° spin | 🔴 Phase 2 | |
| Similar products | 🔴 Phase 2 | Needs data |
| AR try-on | 🔴 Phase 2 | |

#### Sharing
| Feature | Verdict | Notes |
|---------|---------|-------|
| Share to WhatsApp (single product) | 🟢 MVP | THE adoption mechanism |
| Copy link button | 🟢 MVP | |
| Open Graph tags (rich previews) | 🟢 MVP | Critical for share quality |
| Watermarked image download | 🟡 MVP-lite | Brand protection |
| Multi-product enquiry list | 🟡 MVP-lite | Selection state across catalog |
| QR code per product | 🔴 Phase 2 | |
| SMS / Email share | 🔴 Phase 2 | |
| Branded sharing template | 🔴 Phase 2 | |

#### Enquiry / Order
| Feature | Verdict | Notes |
|---------|---------|-------|
| Enquire on WhatsApp button | 🟢 MVP | Prefilled deep-link |
| Place Order Directly form | 🟡 MVP-lite | Minimal: items, address, GSTIN, notes |
| Multi-product enquiry list | 🟡 MVP-lite | (same as sharing batch) |
| Bulk enquiry (paste codes) | 🟡 MVP-lite | |
| Persistent cart | 🔴 Phase 2 | Tied to full B2B platform |
| Wishlist / favorites | 🔴 Phase 2 | |
| Quote request flow | 🔴 Phase 2 | |
| Order tracking | 🔴 Phase 2 | |
| Order history | 🔴 Phase 2 | |
| Reorder from previous | 🔴 Phase 2 | |
| Multiple shipping addresses | 🔴 Phase 2 | |
| Custom design request | 🔴 Phase 2 | |

#### Authentication
| Feature | Verdict | Notes |
|---------|---------|-------|
| No login required to browse | 🟢 MVP | Locked in brief |
| Phone-OTP login (gated to Place Order) | 🟡 MVP-lite | SMS-based |
| WhatsApp OTP API | 🔴 Phase 2 | |
| Profile management | 🔴 Phase 2 | |
| Saved addresses | 🔴 Phase 2 | |
| Saved payment methods | 🔴 Phase 2 | |
| Notification preferences | 🔴 Phase 2 | |

#### AI / Advanced
| Feature | Verdict | Notes |
|---------|---------|-------|
| Image search (Variant A) | 🔴 Phase 2 | High build cost, uncertain MVP value |
| Order book scanning (OCR) | 🔴 Phase 2 | Brilliant adoption mechanism but not MVP-critical |

#### Trust / Decision-making
| Feature | Verdict | Notes |
|---------|---------|-------|
| About Panini Jewels page | 🟢 MVP | |
| Contact info page | 🟢 MVP | Multiple WhatsApp numbers |
| Return / replacement policy page | 🟡 MVP-lite | Static text |
| Photos of real shop owners | 🔴 Phase 2 | Content collection effort |
| ~~Hallmarking certifications~~ | ❌ N/A | Not relevant for fashion jewelry |
| ~~Reviews / testimonials~~ | ❌ Removed | Trade dynamics |
| ~~Live chat~~ | ❌ Removed | WhatsApp serves this |

### Final filter results — Admin side

#### Catalog management
| Feature | Verdict | Notes |
|---------|---------|-------|
| Add product (single) | 🟢 MVP | |
| Edit / archive product | 🟢 MVP | |
| Bulk image upload | 🟢 MVP | |
| Hide/unhide product (replaces stock toggle) | 🟢 MVP | |
| Categorize / tag products | 🟢 MVP | |
| Set price (per product) | 🟢 MVP | |
| Bulk product upload (CSV) | 🟡 MVP-lite | Migration day tool |
| Reorder photos within product | 🟡 MVP-lite | Numbered positions OK |
| Schedule product publish date | 🔴 Phase 2 | |
| Bulk price update | 🔴 Phase 2 | Demoted from MVP-lite — gold-rate justification doesn't apply for fashion jewelry |
| ~~Set making charges~~ | ❌ Removed | Not relevant |

#### Order / Enquiry management
| Feature | Verdict | Notes |
|---------|---------|-------|
| View incoming enquiries | 🟢 MVP | |
| View placed orders list | 🟢 MVP | |
| Update order status | 🟢 MVP | |
| **Print packing slip (A4, dispatched items)** | 🟢 MVP | Browser print + CSS @media print |
| Cancel order | 🟡 MVP-lite | Status change |
| Generate invoice | 🔴 Phase 2 | MyBillBook handles today |
| Communicate with buyer about order | 🔴 Phase 2 | WhatsApp serves this |
| Refund order | 🔴 Phase 2 | |
| Pending order management | 🔴 Phase 2 | Per-line-item status field added to data model in MVP for Phase 2 readiness |
| Worker / artisan assignment | 🔴 Phase 2 | |
| Buyer-facing pending visibility | 🔴 Phase 2 | |

#### User management
| Feature | Verdict | Notes |
|---------|---------|-------|
| View list of registered buyers | 🟢 MVP | |
| View buyer activity (visits, orders) | 🟡 MVP-lite | Basic table |
| Approve new retailers | 🔴 Phase 2 | No login required to browse |
| Tag VIP / standard / new | 🔴 Phase 2 | |
| Block / suspend buyer | 🔴 Phase 2 | |
| Send broadcast / announcement | 🔴 Phase 2 | WhatsApp groups serve this |

#### Analytics
| Feature | Verdict | Notes |
|---------|---------|-------|
| Daily/weekly/monthly visits | 🟢 MVP | |
| Buyer adoption metrics dashboard | 🟢 MVP | Direct measurement of success criteria |
| WhatsApp deep-link CTR | 🟢 MVP | Sharing measurement |
| Top viewed products | 🟡 MVP-lite | |
| Top searched keywords | 🟡 MVP-lite | |
| Conversion funnel | 🟡 MVP-lite | Basic counts |

#### Operations
| Feature | Verdict | Notes |
|---------|---------|-------|
| Configure WhatsApp numbers per category | 🟡 MVP-lite | Settings page |
| Configure GST settings | 🟡 MVP-lite | |
| Configure shipping zones | 🔴 Phase 2 | |
| Team members / permissions (RBAC) | 🔴 Phase 2 | Single admin login is enough |
| Audit log | 🔴 Phase 2 | |
| Data export | 🔴 Phase 2 | |

#### Marketing / Growth
| Feature | Verdict | Notes |
|---------|---------|-------|
| Hero banner management | 🟡 MVP-lite | Single editable banner |
| Push notifications | 🔴 Phase 2 | |
| Email broadcasts | 🔴 Phase 2 | |
| Coupon / discount codes | 🔴 Phase 2 | Pricing is relationship-based |
| Referral program | 🔴 Phase 2 | |
| Festival campaigns | 🔴 Phase 2 | Covered by hero banner |
| A/B testing | 🔴 Phase 2 | |

### Final filter results — Cross-cutting / Technical

| Feature | Verdict | Notes |
|---------|---------|-------|
| Mobile-first responsive | 🟢 MVP | |
| Image optimization / CDN | 🟢 MVP | |
| Page load <2s on 3G | 🟢 MVP | Performance budget |
| Open Graph tags | 🟢 MVP | (already in Sharing) |
| Sentry for errors | 🟢 MVP | Free tier |
| PostHog for analytics | 🟢 MVP | Required for success metric measurement |
| Sitemap (XML) | 🟢 MVP | Free with Next.js |
| Robots.txt | 🟢 MVP | |
| Loading states / skeletons | 🟢 MVP | Critical on 3G |
| Empty states | 🟢 MVP | Usability minimum |
| Search results page UX | 🟢 MVP | |
| Category landing pages | 🟢 MVP | |
| Homepage | 🟢 MVP | Hero banner + featured/newest |
| Product visibility flag (publish/draft + hide) | 🟢 MVP | |
| SEO optimization | 🟡 MVP-lite | Basic meta tags + semantic HTML |
| Email service (transactional) | 🟡 MVP-lite | OTP fallback + order confirmation |
| Accessibility | 🟡 MVP-lite | Semantic HTML + alt text |
| 404 / branded error pages | 🟡 MVP-lite | |
| Cookie consent banner | 🟡 MVP-lite | Required if PostHog used |
| Privacy policy page | 🟡 MVP-lite | Legal hygiene |
| Terms of service page | 🟡 MVP-lite | |
| Multi-language (English + Hindi) | 🔴 Phase 2 | |
| Offline browsing | 🔴 Phase 2 | |
| PWA installable | 🔴 Phase 2 | |
| MyBillBook / Tally integration | 🔴 Phase 2 | |
| Razorpay integration | 🔴 Phase 2 | No platform payments in MVP |
| Bulk SMS service | 🔴 Phase 2 | |
| ~~Dark mode~~ | ❌ Removed | Bright background sells jewelry |
| ~~Live gold rate~~ | ❌ N/A | Not relevant for fashion jewelry |

### Step 9d summary

| Verdict | Count |
|---------|-------|
| 🟢 MVP | ~50 features |
| 🟡 MVP-lite | ~25 features |
| 🔴 Phase 2 | ~35 features |
| ❌ Removed / N/A | ~7 features |

**Total: ~115 features evaluated. ~75 in MVP scope (full or lite).** A substantial MVP — not a thin demo, but deliberately not the "full B2B e-commerce platform" reserved for Phase 2.

---

## Step 9e: Prioritization within MVP

_Next session — rank ~75 MVP features into Sprint 1 / Sprint 2 / Sprint 3 buckets._

---

## Step 9f: Definition of Done for v1

_To be filled in._

---

## Step 9g: Phase 2 Backlog (consolidated)

_To be filled in._

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| v0.1 | 2026-05-08 | Steps 9a (assumptions) and 9b (success criteria) locked. Tiered targets adopted. |
| v0.2 | 2026-05-09 | Step 9c (feature brainstorm) locked. Image search and order book scanning explicitly deferred to Phase 2. Filter set agreed (8 filters, category-aware). |
| v0.3 | 2026-05-09 | Step 9d (MVP filter) complete across 10 batches. Fashion-jewelry back-fix applied: Metal filter → Plating type, Stock status filter removed (out-of-stock items hidden), making charges removed, hallmarking trust signals removed, bulk price update demoted to Phase 2. Print packing slip added to MVP. Pending order management deferred to Phase 2 with data-model readiness commitment. |
