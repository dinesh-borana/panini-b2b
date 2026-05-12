# Phase 2 Backlog — Panini B2B Catalog

| | |
|---|---|
| **Status** | ✅ v1 (locked end of Step 9g) |
| **Last Updated** | 2026-05-09 |

## Sequencing rule

**Theme 2 (Admin & Operational Excellence)** starts immediately after MVP — evidence for these gaps already exists from operational history.

**Other themes** wait for triggers based on MVP data.

Themes can run in parallel if multiple triggers fire.

## Theme 1: Full B2B E-commerce

**Trigger:** ≥30% of MVP orders flow through "Place Order Directly" (Path 3) within 60 days post-launch.

**Features:** Persistent cart, wishlist, order history, reorder, multiple addresses, quote request, custom design request, saved payment methods, Razorpay integration, buyer profile, notification preferences.

## Theme 2: Admin & Operational Excellence ⭐ STARTS IMMEDIATELY POST-MVP

**Trigger:** Already justified by existing operational pain.

**Features:** **Pending order management** (priority), worker/artisan assignment, buyer-facing pending visibility, approve retailers, VIP/standard tagging, block/suspend, broadcasts, invoice generation, in-platform messaging, refund workflow, schedule publish dates, bulk price update, drag-drop photo reorder, shipping zones, RBAC team members, audit log, data export.

Data model already includes `lineItemStatus` on OrderItem for Phase 2 readiness.

## Theme 3: AI & Discovery Enhancement

**Trigger:** ≥30% search queries return zero/poor results, OR new-buyer onboarding still slow.

**Features:** Image search (Variant A), order book scanning (OCR), similar products, popularity sort, advanced view/search analytics, visual similarity browse.

## Theme 4: Marketing & Growth

**Trigger:** MVP adoption hits ≥30% target; push toward stretch.

**Features:** Push notifications, email broadcasts, coupons/discount codes, referral program, festival campaigns, A/B testing, QR codes, branded share templates, SMS/email share.

## Theme 5: Reach & Accessibility

**Trigger:** Real research shows specific buyer segments excluded.

**Features:** Multi-language (Hindi), offline browsing, PWA, full WCAG AA, mobile native app.

## Theme 6: Integrations

**Trigger:** Manual data entry pain at order volume.

**Features:** MyBillBook integration, Tally, bulk SMS, advanced email templates, Razorpay (if not from Theme 1), GSTIN verification API.

## Theme 7: Trust & Brand

**Trigger:** Onboarding metrics show buyer hesitation OR requests for more validation.

**Features:** Real shop owner photos, quality assurance content, video/360° spin, AR try-on.

## Phase 3

Doesn't exist yet. Will define after Phase 2 ships with real data.

## Changelog

| Version | Date | Changes |
|---|---|---|
| v1 | 2026-05-09 | Initial backlog locked. 7 themes; Theme 2 starts immediately. |
