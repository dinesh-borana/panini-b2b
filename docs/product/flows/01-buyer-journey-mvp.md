# Buyer User Flow — MVP

| | |
|---|---|
| **Status** | ✅ v1 (MVP) |
| **Last Updated** | 2026-05-09 |

> Drawn during MVP scoping (Step 9d, Batch 6) to resolve confusion about auth/order features.

## Three paths, one destination

### Path 0: Discovery (shared)
1. Buyer arrives via WhatsApp link/QR/URL
2. Browse catalog (filters, search, categories)
3. View product detail
4. Decision point

No login required.

### Path 1: Quick enquiry (single product)
1. Tap "Enquire on WhatsApp"
2. WhatsApp opens with prefilled message (design code, name, price, link)
3. Buyer hits send

**Login:** No. Lowest friction, likely dominant flow.

### Path 2: Build a list (multi-product)
1. "Add to Selection" on cards/detail
2. Floating bar shows count: "3 items selected"
3. Selection page → "Share Selection on WhatsApp"
4. WhatsApp opens with all items prefilled

**Login:** No. Killer hybrid feature.

### Path 3: Place order directly
1. Tap "Place Order Directly"
2. Phone-OTP login via SMS
3. Order form (items, name, GSTIN, address, notes)
4. Submit → captured on platform
5. Team confirms via WhatsApp

**Login:** Yes — only place it's required.

## Why this design

**Login gated to commitment:** Browsing zero friction; login is purposeful moment.

**Three commitment levels:** We offer three options and measure which buyers pick.

**Unified team workflow:** All paths converge at "team processes order" — admin workflow doesn't change.

## What distribution tells us

| Distribution | Meaning | Phase 2 implication |
|---|---|---|
| 90/10/0 | Catalog is discovery tool | Don't over-invest in platform transactions |
| 50/40/10 | Selection list gaining; small order interest | Build platform features modestly |
| 30/30/40 | Buyers willing to transact | **Theme 1 trigger fires** — invest in cart/history/reorder |
| 0/0/0 | No adoption | Re-evaluate hybrid model |

## Out of scope (Phase 2)

Cart, wishlist, order tracking/history, reorder, multiple addresses, buyer-facing pending visibility, quote requests, custom design requests.
