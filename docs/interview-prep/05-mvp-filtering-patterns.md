# 05 — MVP Filtering & Senior Patterns

## Q: How do you actually run an MVP filter?

Two questions per feature: (1) Would the MVP test fail without this? (2) Is build cost proportional to test value? Both pass → MVP. Only first → MVP-lite (reduced version). Neither → Phase 2. Work in batches of 6-10 related features.

The filter has a third verdict most engineers miss: **MVP-lite**. Senior thinking adds shipping a reduced version — 5 controlled vocabulary items instead of 30, basic search instead of fuzzy, browser-print instead of server-side PDF. Lite delivers 80% of value at 30% of build cost.

**Story:** On Panini I evaluated ~115 features across 10 batches. Final: ~50 MVP full, ~25 MVP-lite, ~35 Phase 2, ~5 removed.

## Q: How did you handle a stakeholder wanting to add features back?

Don't push back on the feature — surface the strategic conflict. If founder asks to add cart, history, login to MVP: "Adding these means we're now building a full B2B platform, not catalog-first hybrid. Are we changing strategy, or did Phase 2 feel scary?" Gets the actual decision on the table.

**Story:** Mid-Batch 5, founder said "we need complete B2B Website with cart, login, history." Conflicted with locked brief. Instead of arguing each feature, I named it. He reflected, stuck with original — parked full B2B as Phase 2. 5-minute conversation; arguing each feature would have taken hours and still been unclear.

**Principle:** When stakeholders push back on agreed scope, the question isn't "should we add this feature?" It's "are we changing the underlying decision this feature follows from?"

## Q: Discovered a foundational assumption was wrong mid-project?

Mid-MVP scoping on Panini, founder mentioned almost as an aside: "we don't deal in real gold." I'd been building filters, trust signals, and pricing around precious-metal trade — gold/silver filters, hallmarking, gold rate, making charges. Actual business is fashion/imitation jewelry. Different filters, trust signals, pricing. Two hours of rework saved weeks of subtle mistakes.

**Pattern:** Most teams patch around discovered wrong assumptions. Senior discipline is a "back-fix sweep": identify every locked decision affected, revise as a coherent set, update upstream docs.

## Q: Why analytics, performance, error monitoring as MVP features?

Without analytics, MVP is unfalsifiable. We set tiered targets — Floor 15%, Target 30%, Stretch 50%. Without measurement, we'd ship the perfect product and not know. Same for performance and error monitoring. Technical baseline is part of MVP scope, not infrastructure-after.

## Q: Why defer UI but build for it in data model?

When a Phase 2 feature has clear data implication, separate UI deferral from data deferral. Build data model with Phase 2 in mind; ship UI for MVP. Cost: 5-10% upfront. Savings: weeks of refactoring later.

**Story:** Panini's pending order management is Phase 2. Data implication: per-line-item status. For MVP we use only `active`/`cancelled`, but schema accommodates `pending`, `dispatched`, etc. Phase 2 starts from foundation, not refactor.

**Principle:** Shape the data for the future product; ship the UI for the current one.

## Q: Infinite scroll vs pagination?

Pagination usually wins for B2B catalogs despite feeling less modern. Returning to position is easy (URL has page number); memory/performance better on slow phones; SEO stronger. Infinite scroll wins for discovery-mode browsing where users don't return. "Load More" hybrid gives 80% of infinite scroll's feel with 80% of pagination's reliability.

**Story:** Initially proposed pagination. Founder said infinite scroll. I laid out the trade-off matrix. After seeing it, founder switched to pagination. Framing trade-offs explicitly lets stakeholders pick correctly.

## Q: Small technical detail with disproportionate impact?

Open Graph tags on a sharing-driven product. Without them, pasted links look like bare URLs in WhatsApp — bland, low CTR. With them, rich preview: photo, name, price. Build cost: hours. Impact: measurable lift in CTR from shared messages.

## Q: How do you avoid the "Phase 2 graveyard"?

Treat Phase 2 as commitment, not deferral. Every Phase 2 item gets: (1) trigger to bring it back, (2) data needed to evaluate, (3) architectural commitments that should land in MVP. Without these, Phase 2 = graveyard. With them, Phase 2 = roadmap.

## Q: Meta-skill from MVP scoping?

Surfacing meta-decisions instead of debating surface decisions. Most arguments about features are actually about strategy, sequencing, or risk tolerance — but expressed at feature level. Senior skill: hearing "let's add cart" and recognizing the underlying question is "are we still committed to catalog-first hybrid?" Surface the right question; feature debate resolves itself.
