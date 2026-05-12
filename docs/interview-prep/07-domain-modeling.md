# 07 — Domain Modeling

Questions about identifying entities, modeling relationships, designing state machines, and the senior patterns that emerge from real domain work.

---

## Q: How do you approach domain modeling for a new product?

**Short answer:**
> I do it as an explicit step between product strategy and system design. Identify entities (the "nouns" the business cares about), define attributes per entity, map relationships with cardinalities, design lifecycles as state machines for entities that change state, capture business rules and constraints, and finally draw an ER diagram for visualization. Doing this independent of tech stack means the data model isn't accidentally shaped by ORM choices or framework idioms.

**Long answer:**
> Before I touch system design, I always do a domain modeling pass. Entities, relationships, lifecycles, constraints — independent of tech stack. Most engineers skip this and go straight from features to schema, which means schema decisions get made accidentally during code, usually badly. Domain modeling lets you reason about the business first, then express it in whatever stack fits. It's also the artifact that onboards new engineers fastest — "read this one doc and you'll understand the system."

**Story:**
> On Panini B2B I produced a domain model with 12 entities, 3 code-constant vocabularies, full state machines for Order and Product, and ~30 business rules — all *before* writing a single line of database schema. When we got to system design, the Postgres schema was essentially already decided. No accidental decisions during coding.

---

## Q: When do you use a database table vs a code constant for a vocabulary?

**Short answer:**
> Rule of thumb: if a value is added or changed monthly or more, it's an entity. If once a year or less, it's a code constant. Confusing the two creates either useless admin pages or rigid hardcoded systems.

**Story:**
> On Panini I had four candidate vocabularies: PlatingType (4 values), StoneStyle (7 values), Occasion (4 values), and SizeOption (sizes per category, edited often). The founder initially wanted all four as DB tables with admin CRUD pages. I surfaced the cost — 3-5 days of extra MVP work for 3 admin screens that would each be touched maybe once a year. He reconsidered and picked the hybrid: PlatingType/StoneStyle/Occasion as TypeScript constants; only SizeOption as DB table. The trade-off framing made the call obvious.

**Principle:**
> Not every concept in a domain needs to be a database entity. Stable, slow-changing vocabularies are often better as code constants — TypeScript autocomplete, zero JOIN cost, no admin UI needed. Configurability has a real engineering tax; only pay it for data that actually changes.

---

## Q: How do you decide whether to snapshot data on a record?

**Short answer:**
> Snapshot anything that represents "what the user saw and agreed to" at a moment in time. Order line items, contract terms, invoice details. These are *historical state*. The catalog is *current state*. They're different concepts and must be modeled differently. Not snapshotting historical data is a one-way door — once orders exist without snapshots, retrofitting requires fabricating values, which corrupts the truth.

**Long answer:**
> This is a classic one-way-door decision in data modeling. If you don't snapshot at creation, you can't truthfully retrofit. So even though snapshotting costs slightly more upfront (extra columns, extra writes), I default to it for any data that represents commitment-at-a-moment. The cost of retrofit is usually 10x the cost of doing it right initially.

**Story:**
> On Panini B2B the founder chose NOT to snapshot product name and design code on OrderItem — only price (for financial integrity). His reasoning: buyers don't typically look at old orders in this trade; current-state lookups are acceptable. I pushed back hard once with full reasoning, got acknowledgment, then locked the decision and moved on. The reasoning is documented in the domain model so if reality shifts later, future-us knows what assumption to revisit.

**The deeper principle (one-way vs two-way doors):**
> Some decisions are one-way doors — once you walk through, you can't easily come back. These deserve careful, slow consideration. Others are two-way — reverse easily. Snapshotting is one-way; lineItemStatus is more reversible. Recognizing which door you're at determines how much scrutiny the decision deserves.

---

## Q: How do you decide between separate booleans and a single status enum?

**Short answer:**
> When I find myself adding a third boolean flag to model an entity's state, I stop and consider an enum instead. Three booleans = 8 possible combinations, most of which are nonsensical or contradictory. An enum forces enumerating valid states explicitly and prevents impossible combinations. The bonus: the enum becomes a state machine specification, which makes business logic easier to reason about.

**Story:**
> On Panini, the Product entity initially had `isPublished`, `isHidden`, and we were about to add `isArchived` — three booleans. I proposed collapsing them into a single `status` enum: `draft`, `live`, `hidden`, `archived`. Cleaner queries (`WHERE status = 'live'`), no impossible state combinations, and the enum doubled as the state machine specification. Founder agreed immediately once he saw the framing.

**Principle:**
> Booleans are fine for genuinely independent flags (e.g., `isActive` + `emailVerified` — orthogonal concerns). They're a smell when they describe the same lifecycle dimension. Watch the count: 2 booleans for the same concept = okay; 3+ = enum it.

---

## Q: How do you handle deletion in a domain model?

**Short answer:**
> By default, I soft-delete anything that's referenced by historical records — Products (referenced by orders), Buyers (referenced by orders), AdminUsers (referenced by audit logs). Hard-delete only standalone entities like HeroBanner or event-log entries like Enquiries where audit value is low. The soft-delete approach preserves referential integrity and audit trails at the cost of one extra flag per entity.

**Story:**
> On Panini, Product uses `status='archived'` as soft-delete. This means old orders still resolve their products correctly. The same product can be restored if needed. Buyers use `isActive=false` — preserves order history and is DPDP-friendly (can anonymize PII fields later without hard-delete). For Orders and OrderItems, we never delete at all — status changes only (`cancelled`, `lineItemStatus='cancelled'`).

**Trade-off:**
> Every query has to filter out archived/inactive records. Solved with a "default scope" pattern at the ORM layer so it's not a constant manual concern. Soft-delete tax is real but small; the alternative (broken references in historical data) is much worse.

---

## Q: When do you draw an explicit state machine?

**Short answer:**
> Whenever an entity has more than 2 states. Below that, a boolean is fine. Above it, you need an explicit transition diagram because the question "can we go from state X to state Y?" has different answers in different people's heads until the diagram forces a decision.

**Story:**
> On Panini, I drew state machines for two entities: Order (`placed → confirmed → packed → shipped → delivered`, plus `cancelled` from multiple states) and Product (`draft → live → hidden → archived`, with restore). Founder initially didn't think about whether you could cancel a shipped order. Drawing the diagram surfaced the question, and we made the decision explicitly: yes, in-transit cancellation is allowed; post-delivery returns are out of scope for MVP.

**Principle:**
> State machines are partly for the engineer and partly for the business. They surface transitions that look ambiguous in prose but become unambiguous when drawn.

---

## Q: How do you model many-to-many relationships?

**Short answer:**
> Two options. Join table (explicit row per relationship) — most portable, supports per-relationship metadata. Array column on the parent — Postgres-native, simpler, no JOIN needed. Use the join table when you have metadata about the relationship itself (e.g., "buyer's role in this group"). Use the array column when the relationship is just membership and you're on Postgres.

**Story:**
> On Panini, Product has multiple occasion tags (wedding, festival, etc.). I considered both options. Since we're on Postgres + Drizzle and the relationship has no metadata (just membership), I used a `text[]` array column. For Product ↔ SizeOption I used a join table because SizeOption is a real entity with its own attributes.

**Principle:**
> The join table is the textbook answer; the array column is the pragmatic one when conditions allow. Don't blindly default to either — choose based on relationship semantics and tech stack capabilities.

---

## Q: How do you decide whether to capture something as a domain entity vs an analytics event?

**Short answer:**
> Ask: do I want to *act on* this data inside the application, or just *measure* it? If acting (route sales follow-up to buyers who clicked X times, show pending order summary, etc.), it's a domain entity. If measuring (conversion rates, funnel analysis, A/B testing), an analytics event suffices. The cost difference: entities live in your DB with relationships; events live in PostHog/similar with no relationships.

**Story:**
> On Panini, WhatsApp deep-link clicks ("Enquire on WhatsApp" button) needed to be queryable inside the app — we want to identify "buyers most likely to need a sales follow-up." So Enquiry became a real entity. If we'd only wanted to measure CTR, PostHog would have been enough.

---

## Q: How did you handle a stakeholder you disagreed with on a one-way-door decision?

**Short answer:**
> Make the case once with full reasoning, ask the decision-maker to acknowledge the trade-off, then commit fully to whatever they decide. The mistake juniors make is either silent dissent (festers) or re-litigating the same point repeatedly (corrodes trust). Senior engineers disagree clearly, get acknowledgment, and commit.

**Story:**
> On Panini's order snapshotting question, I disagreed with the founder's choice not to snapshot product names/codes. I laid out the scenario (product renamed 6 months later, old order shows wrong name), the cost (3 extra columns, ~30 bytes per row), the alternative (no easy retrofit). Founder acknowledged the trade-off and held his position with new reasoning ("buyers don't look at old orders"). I locked it, documented the reasoning in the doc, and moved on. The documentation matters — future us reviewing this decision in 6 months will understand what assumption was made.

**Principle:**
> Disagree clearly once. Get acknowledgment. Commit. Document. Move on.

---

## Updates log

| Date | Added |
|---|---|
| 2026-05-10 | Initial set: 9 questions on domain modeling approach, vocabulary placement, snapshotting/one-way doors, enum vs booleans, deletion semantics, state machines, N:M modeling, entity vs event, disagreeing with stakeholders |
