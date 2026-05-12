# Domain Model — Panini B2B

| | |
|---|---|
| **Status** | ✅ v1 — Locked at end of Step 10 |
| **Owner** | [Your Name] |
| **Last Updated** | 2026-05-10 |
| **Related Docs** | [MVP Scope](../product/01-mvp-scope.md), [Buyer Journey](../product/flows/01-buyer-journey-mvp.md) |

---

## What this document is

The complete domain model for Panini B2B — entities, attributes, relationships, lifecycles, and business rules. This sits between the product brief (abstract) and the database schema (concrete) and serves as the shared vocabulary for design decisions and engineering work.

**Audience:** anyone building, reviewing, or extending Panini B2B.

**Generated through Step 10:** 10a (entity identification) → 10b (attributes) → 10c (relationships) → 10d (lifecycles) → 10e (business rules) → 10f (ER diagram) → 10g (synthesis, this doc).

---

## Section 1: Entities

12 entities + 3 controlled-list code constants.

### Catalog entities (5)

#### Product
The core entity. A single jewelry design Panini sells.

| Field | Type | Notes |
|-------|------|-------|
| `id` | UUID | Primary key |
| `designCode` | string (unique) | Human-readable: "PJ-K-128" |
| `name` | string | "Royal Kundan Necklace Set" |
| `description` | text (nullable) | Long-form description |
| `categoryId` | UUID (FK → Category) | Required |
| `platingType` | string (code constant) | gold-tone / silver-tone / rose-gold-tone / oxidized |
| `stoneStyle` | string (nullable, code constant) | Optional; from controlled list |
| `occasionTags` | text[] (Postgres array) | Multiple occasions allowed |
| `price` | decimal(10,2) | INR, flat per design |
| `moq` | integer (default 1) | Minimum order quantity |
| `weightGrams` | decimal(8,2) (nullable) | Optional |
| `dimensions` | string (nullable) | Free-text: "Length: 16 inches" |
| `status` | enum | `draft` / `live` / `hidden` / `archived` |
| `viewCount` | integer (default 0) | Cached counter (no session dedup; some inflation OK) |
| `createdAt`, `updatedAt` | timestamp | |

#### Category
Hierarchical grouping (max 2 levels: parent + one level of children).

| Field | Type | Notes |
|-------|------|-------|
| `id` | UUID | |
| `name` | string | "Necklaces" |
| `slug` | string (unique) | "necklaces" (for URLs) |
| `parentId` | UUID (FK → Category, nullable) | Hierarchical, max 2 levels |
| `displayOrder` | integer | Homepage ordering |
| `isActive` | boolean | |
| `createdAt`, `updatedAt` | timestamp | |

#### ProductImage
One image of a product.

| Field | Type | Notes |
|-------|------|-------|
| `id` | UUID | |
| `productId` | UUID (FK → Product) | |
| `url` | string | CDN URL |
| `altText` | string (nullable) | Accessibility |
| `displayOrder` | integer | Position in gallery |
| `isPrimary` | boolean | Main image shown in cards |
| `createdAt` | timestamp | |

#### ProductSize
Join table for Product ↔ SizeOption (N:M).

| Field | Type | Notes |
|-------|------|-------|
| `id` | UUID | |
| `productId` | UUID (FK → Product) | |
| `sizeOptionId` | UUID (FK → SizeOption) | |

#### SizeOption
Size values per category.

| Field | Type | Notes |
|-------|------|-------|
| `id` | UUID | |
| `categoryId` | UUID (FK → Category) | Sizes are category-specific |
| `value` | string | "14", "2.4 inch", "16 inches" |
| `displayOrder` | integer | |
| `isActive` | boolean | |
| `createdAt`, `updatedAt` | timestamp | |

### Buyer & order entities (3)

#### Buyer
A retailer or reseller. Single flat table (no separate profile entity).

| Field | Type | Notes |
|-------|------|-------|
| `id` | UUID | |
| `phone` | string (unique) | E.164 format ("+919876543210"). Primary identifier. |
| `phoneVerifiedAt` | timestamp (nullable) | Set when OTP succeeds |
| `name` | string | |
| `businessName` | string (nullable) | "Sharma Jewellers" |
| `gstin` | string (nullable) | Optional |
| `email` | string (nullable) | |
| `isActive` | boolean (default true) | Soft-delete via this flag |
| `firstSeenAt` | timestamp | When their phone was first captured |
| `createdAt`, `updatedAt` | timestamp | |

#### Order
A purchase request.

| Field | Type | Notes |
|-------|------|-------|
| `id` | UUID | |
| `orderNumber` | string (unique) | Human-readable: "PB-2026-00001" |
| `buyerId` | UUID (FK → Buyer) | Required |
| `status` | enum | `placed` / `confirmed` / `packed` / `shipped` / `delivered` / `cancelled` |
| `shipRecipientName` | string | Denormalized shipping address |
| `shipPhone` | string | |
| `shipAddressLine1` | string | |
| `shipAddressLine2` | string (nullable) | |
| `shipCity` | string | |
| `shipState` | string | |
| `shipPincode` | string | Indian 6-digit PIN |
| `shipCountry` | string (default "India") | |
| `notes` | text (nullable) | Buyer-provided |
| `totalAmount` | decimal(12,2) | Cached at creation |
| `placedAt` | timestamp | |
| `confirmedAt` | timestamp (nullable) | |
| `shippedAt` | timestamp (nullable) | |
| `deliveredAt` | timestamp (nullable) | |
| `cancelledAt` | timestamp (nullable) | |
| `cancellationReason` | text (nullable) | Required when status is `cancelled` |
| `createdAt`, `updatedAt` | timestamp | |

#### OrderItem
A line item — one product, with quantity and locked-in price.

| Field | Type | Notes |
|-------|------|-------|
| `id` | UUID | |
| `orderId` | UUID (FK → Order) | |
| `productId` | UUID (FK → Product) | Live reference (no name/code snapshot) |
| `unitPrice` | decimal(10,2) | Locked at creation (the only snapshotted field; required for financial integrity) |
| `quantity` | integer | |
| `lineTotal` | decimal(12,2) | `quantity × unitPrice` |
| `lineItemStatus` | enum (default 'active') | `active` / `cancelled` in MVP. Phase 2 expands. |
| `notes` | text (nullable) | Per-item notes |
| `createdAt` | timestamp | |

> **Snapshotting decision (recorded for posterity):** Product name and design code are NOT snapshotted on OrderItem. Reasoning: buyers don't typically look at old orders; current-state lookups are acceptable. This is a one-way door — if the assumption ever becomes false (buyers DO ask about old orders, OR product data churns frequently), retrofit will require a data migration.

### Operational entities (4)

#### AdminUser
Team members who log into the admin panel.

| Field | Type | Notes |
|-------|------|-------|
| `id` | UUID | |
| `email` | string (unique) | Login identifier |
| `passwordHash` | string | bcrypt or argon2 |
| `name` | string | |
| `role` | enum (default 'admin') | MVP: only 'admin'. Phase 2 expands. |
| `isActive` | boolean (default true) | Soft-delete |
| `lastLoginAt` | timestamp (nullable) | |
| `createdAt`, `updatedAt` | timestamp | |

#### Enquiry
A "Enquire on WhatsApp" click event. Stored as queryable data, not just analytics.

| Field | Type | Notes |
|-------|------|-------|
| `id` | UUID | |
| `productId` | UUID (FK → Product) | Required |
| `buyerId` | UUID (FK → Buyer, nullable) | Anonymous OK |
| `phone` | string (nullable) | Captured if known |
| `sessionId` | string (nullable) | Correlate anonymous visitor actions |
| `enquiryGroupId` | UUID (nullable) | Shared across rows from same multi-product enquiry |
| `createdAt` | timestamp | |

> Multi-product enquiries are stored as multiple single-product rows sharing an `enquiryGroupId`.

#### HeroBanner
The editable homepage banner.

| Field | Type | Notes |
|-------|------|-------|
| `id` | UUID | |
| `imageUrl` | string | CDN URL |
| `altText` | string | Accessibility |
| `linkUrl` | string (nullable) | Where the banner clicks to |
| `isActive` | boolean (default false) | Only one active at a time |
| `displayOrder` | integer | For Phase 2 rotation |
| `createdAt`, `updatedAt` | timestamp | |

#### WhatsAppNumberConfig
Maps categories to WhatsApp numbers.

| Field | Type | Notes |
|-------|------|-------|
| `id` | UUID | |
| `categoryId` | UUID (FK → Category, nullable) | Nullable means "default for all" |
| `whatsappNumber` | string | E.164 format |
| `displayLabel` | string | "Necklaces enquiry" |
| `isActive` | boolean | |
| `createdAt`, `updatedAt` | timestamp | |

### Code constants (3 vocabularies, NOT entities)

These live in TypeScript, not in the database:

```typescript
export const PlatingTypes = ['gold-tone', 'silver-tone', 'rose-gold-tone', 'oxidized'] as const;
export type PlatingType = typeof PlatingTypes[number];

export const StoneStyles = ['kundan-style', 'ad-cz', 'polki-style', 'glass-stones', 'pearl', 'beads', 'no-stones'] as const;
export type StoneStyle = typeof StoneStyles[number];

export const Occasions = ['wedding', 'festival', 'daily-wear', 'gifting'] as const;
export type Occasion = typeof Occasions[number];
```

Stored on Product as plain string columns (with TypeScript-enforced values; optional DB check constraints).

> **Rationale (recorded):** These vocabularies are stable and slow-changing. Hardcoding gives TypeScript autocomplete, zero JOIN cost, and removes the need for admin UI to manage them. If change frequency increases, we can promote to DB tables later (a Phase 2 migration if it ever becomes necessary).

---

## Section 2: Relationships

### Cardinality reference

| Relationship | Cardinality | Implementation |
|--------------|-------------|----------------|
| Category → Category (parent/child) | 1:N self-ref | `parentId` FK on Category |
| Category → Product | 1:N | `categoryId` FK on Product |
| Product → ProductImage | 1:N | `productId` FK on ProductImage |
| Product ↔ SizeOption | N:M | `ProductSize` join table |
| Category → SizeOption | 1:N | `categoryId` FK on SizeOption |
| Product → Occasion tags | N:M | Array column on Product (Postgres-native) |
| Buyer → Order | 1:N | `buyerId` FK on Order |
| Order → OrderItem | 1:N | `orderId` FK on OrderItem |
| Product → OrderItem | 1:N | `productId` FK on OrderItem |
| Buyer → Enquiry | 1:N (nullable) | `buyerId` FK on Enquiry, nullable |
| Product → Enquiry | 1:N | `productId` FK on Enquiry |
| Category → WhatsAppNumberConfig | 1:N (nullable) | `categoryId` FK on config, nullable |

### Deletion behavior

| Entity | Behavior | Rationale |
|--------|----------|-----------|
| Product | Soft-delete via `status='archived'` | Preserves order history |
| Buyer | Soft-delete via `isActive=false` | Preserves order history; DPDP-friendly |
| Order | Never delete; status changes only | Audit trail |
| OrderItem | Never delete; status changes only | Audit trail |
| Category | RESTRICT if has products; soft-delete pattern | Prevents orphaned products |
| ProductImage | Cascade on Product hard-delete (we don't do anyway) | Tied to parent |
| Enquiry | Hard-delete OK (or retention policy Phase 2) | Event log; no audit value |
| HeroBanner | Hard-delete OK | Replaceable content |
| AdminUser | Soft-delete via `isActive=false` | Preserve attribution history |

---

## Section 3: Lifecycles & State Machines

### Order state machine

States:
- `placed` — buyer submitted (initial)
- `confirmed` — admin accepted
- `packed` — ready to ship
- `shipped` — in transit
- `delivered` — terminal success
- `cancelled` — terminal failure (allowed from `placed`, `confirmed`, `packed`, AND `shipped` for in-transit cancellation)

Allowed transitions:

| From | To | Trigger | Side effects |
|------|-----|---------|--------------|
| (none) | placed | Buyer submits | Creates Order + OrderItems; email confirmation |
| placed | confirmed | Admin "Confirm" | Sets `confirmedAt` |
| confirmed | packed | Admin "Mark packed" | UI state only |
| packed | shipped | Admin "Mark shipped" | Sets `shippedAt`; courier notification |
| shipped | delivered | Admin "Mark delivered" | Sets `deliveredAt`; closes order |
| shipped | cancelled | Admin "Cancel (in transit)" | Sets `cancelledAt` + reason; courier RTS |
| placed/confirmed/packed | cancelled | Admin "Cancel" | Sets `cancelledAt` + reason |

Terminal states: `delivered`, `cancelled` — no transitions out.

### Product state machine

States: `draft`, `live`, `hidden`, `archived`

Allowed transitions:
- `draft → live` (admin publishes) — requires image + category + plating set
- `live → hidden` (out of stock)
- `hidden → live` (restocked)
- any → `archived` (soft delete)
- `archived → live` (admin restores)

### OrderItem lifecycle

- `active → cancelled` allowed
- No reverse transition

### Buyer lifecycle

- Binary `isActive` flag
- `phoneVerifiedAt` timestamp — set once on OTP success, never edited

---

## Section 4: Business Rules

### Product
1. `designCode` must be unique (case-insensitive recommended)
2. `price > 0`
3. `moq >= 1`
4. `status` must be a valid enum value
5. State transitions follow the Product state machine
6. **A `live` product must have:** at least one ProductImage, a category, and a `platingType` set. Enforced at status-change-to-`live` time.
7. `occasionTags` array values must be from the `Occasions` constant
8. `stoneStyle` if set must be from the `StoneStyles` constant
9. `viewCount` increments on every product detail view (no session dedup); cannot be decremented manually

### Category
1. `slug` must be unique
2. No circular parent references
3. **Maximum depth: 2 levels** (parent + one level of children)
4. RESTRICT deletion if category has non-archived products

### Buyer
1. `phone` must be unique, validated against E.164 Indian pattern: `^\+91[6-9]\d{9}$`
2. Deduplicate on `phone` before insert
3. `gstin` if present must match: `^[0-9]{2}[A-Z]{5}[0-9]{4}[A-Z]{1}[1-9A-Z]{1}Z[0-9A-Z]{1}$`
4. `phoneVerifiedAt` set only after OTP success, never manually edited
5. `isActive = false` blocks new order creation

### Order
1. `orderNumber` unique, format `PB-YYYY-NNNNN` (auto-generated)
2. `buyerId` must reference an active buyer at creation
3. At least one OrderItem required
4. `totalAmount` must equal sum of non-cancelled `OrderItem.lineTotal`
5. State transitions follow Order state machine
6. `cancellationReason` required when status is `cancelled`
7. Timestamp fields (`placedAt`, `confirmedAt`, etc.) are append-only

### OrderItem
1. `quantity > 0`
2. `lineTotal = quantity × unitPrice` (enforced at write)
3. `unitPrice` set once at creation, never edited
4. `productId` must reference a non-archived product at creation; archive later is OK
5. `lineItemStatus`: `active → cancelled` allowed, no reverse

### Enquiry
1. `productId` must reference a non-archived product
2. At least one of `buyerId`, `phone`, or `sessionId` must be set
3. `enquiryGroupId` links multi-product enquiries; null = standalone

### Platform-wide
1. Only one `HeroBanner` with `isActive = true` at any time (partial unique index)
2. `AdminUser.email` unique and valid format
3. At least one `WhatsAppNumberConfig` with `categoryId = null` (fallback for uncategorized)
4. All timestamps stored in UTC; converted to IST for display
5. Money fields use exactly 2 decimal places (paise); never floats

---

## Section 5: Open Questions / Deferred Decisions

These were deferred during Step 10 and need resolution in later steps:

1. **Anonymous visitor tracking** — should we track pre-login browsing as a domain entity? Deferred until authentication design (Step 11).
2. **Automatic cleanup of unverified Buyers** — when phone is captured but OTP never succeeds, the Buyer row exists with `phoneVerifiedAt = null`. Phase 2 may want a job to clean these up after N days.
3. **Order returns** — only in-transit cancellation is supported in MVP. Post-delivery returns handled via WhatsApp informally. Phase 2 Theme 2 (Admin & Operational Excellence) may add a formal return workflow.

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| v1 | 2026-05-10 | Initial domain model locked. 12 entities, 3 code-constant vocabularies, full state machines for Order and Product, complete business rules. |
