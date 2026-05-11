# Buyer User Flow — MVP

| | |
|---|---|
| **Status** | ✅ v1 (MVP) |
| **Owner** | [Your Name] |
| **Last Updated** | 2026-05-09 |

> This flow was drawn during MVP scoping (Step 9d, Batch 6) to resolve confusion about how the auth/order features fit together. It's the foundational buyer journey for v1.

---

## Three paths, one destination

The MVP supports three buyer paths that all converge at the same fulfillment workflow on the team's side.

### Path 0: Discovery (shared by all paths)

1. Buyer arrives via a WhatsApp link, QR code, or direct URL
2. **Browse catalog** — using filters, search, categories
3. **View product detail** — photos, price, design code, plating, stone style, dimensions
4. **Decision point:** how does the buyer want to act?

No login required for any of this.

### Path 1: Quick enquiry (single product)

For: "I want this one design, ask Panini's team about it on WhatsApp."

1. From product detail, tap **"Enquire on WhatsApp"**
2. WhatsApp opens with a prefilled message containing design code, name, price, and link back to the product page
3. Buyer hits send — conversation continues on WhatsApp as it does today

**Login required:** No.
**Why this path matters:** Lowest-friction option. Probably the dominant flow in early adoption. Preserves the WhatsApp relationship layer.

### Path 2: Build a list (multi-product enquiry)

For: "I want 3-5 designs, send the whole list to Panini's team."

1. From product cards or detail pages, tap **"Add to Selection"**
2. A floating bar shows count: "3 items selected — View Selection"
3. Buyer reviews their selection page
4. Tap **"Share Selection on WhatsApp"** — WhatsApp opens with all items in the prefilled message
5. Buyer hits send

**Login required:** No.
**Why this path matters:** Killer hybrid feature. Preserves WhatsApp transaction while making bulk enquiry dramatically easier. Buyer doesn't have to type design codes manually.

### Path 3: Place order directly (platform transaction)

For: "I'm committing to ordering these items now."

1. From selection page or product detail, tap **"Place Order Directly"**
2. **Login prompt** — phone-OTP via SMS
3. Order form appears: items (pre-populated if from selection), buyer name, GSTIN, shipping address, notes
4. Buyer reviews and submits
5. Order is captured on the platform; team sees it in admin panel
6. Team confirms via WhatsApp (or admin panel updates status)

**Login required:** Yes, phone-OTP. This is the only place login is required in MVP.

**Why this path matters:** Platform-native order capture. Validates the "do buyers want to transact on platform?" hypothesis. If 30%+ of MVP orders use this path, Phase 2 should heavily invest in cart, history, reorder.

---

## Why the flow is designed this way

### Login is gated to commitment, not entry

Most platforms force login at the door. We require it only at "Place Order." This means:
- Browsing buyers get zero friction (good for adoption)
- We avoid the worst pattern in B2B: signup-walls before showing prices
- The login moment is *purposeful* — buyer is committing to a transaction, so OTP makes sense

### The three paths deliberately overlap in capability

Path 1 and Path 2 are both "WhatsApp enquiry" — single vs multiple. Path 3 is the only one that captures structured order data on platform. This is intentional: we offer three levels of commitment, and we measure which level buyers actually pick.

### Team workflow is unchanged across paths

Whether the order arrived via Path 1, 2, or 3, the team's job downstream is the same: confirm, ship, invoice. The platform doesn't force operational change just because a feature exists.

---

## What this flow tells us about MVP test outcomes

Different distributions across the three paths tell different stories:

| Distribution | What it means | Phase 2 implication |
|--------------|---------------|---------------------|
| 90% Path 1, 10% Path 2, 0% Path 3 | Buyers prefer single-shot WhatsApp; catalog is mainly a discovery tool | Don't over-invest in platform transactions in Phase 2 |
| 50/40/10 | Selection list is gaining traction; small platform-order interest | Build out platform features modestly |
| 30/30/40 | Buyers are willing to transact on platform | Phase 2 should heavily invest in cart, history, reorder |
| 0% all paths | No adoption | Re-evaluate the entire hybrid model |

This gives the MVP test concrete diagnostic value — not just "did adoption happen" but "what kind of adoption happened, and what does Phase 2 need to look like?"

---

## Out of scope for this flow (Phase 2)

- Cart that persists across visits
- Wishlist / favorites
- Order tracking
- Order history (registered buyers)
- Reorder from previous order
- Multiple shipping addresses
- Buyer-facing pending order visibility
- Quote request flow (distinct from enquiry)
- Custom design request
