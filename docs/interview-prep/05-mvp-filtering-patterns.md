# 05 — MVP Filtering & Senior Patterns

Questions about applying an MVP filter rigorously, recognizing scope creep, handling discovered wrong assumptions, and the senior patterns that emerge from real scoping work.

---

## Q: How do you actually run an MVP filter on a feature list?

**Why this gets asked:**
Tests whether you have a real method or just say "we'd cut features."

**Short answer:**
> I run two questions against every feature: First, would the MVP test fail without this? Second, is the build cost proportional to the value it adds for the test? If both pass, it's MVP. If only the first passes, it's MVP-lite — a reduced version. If neither passes, it's Phase 2. I do this in batches of 6-10 related features at a time, because batching surfaces feature interactions you'd miss going one at a time.

**Long answer:**
> The filter has a third verdict most engineers miss: **MVP-lite**. Senior thinking adds the option to ship a reduced version — say, 5 controlled vocabulary items instead of 30, or basic search instead of typo-tolerant fuzzy search, or browser-print instead of server-side PDF. Lite versions deliver 80% of user value at 30% of build cost. The two-by-two of (in MVP / not in MVP) × (full / lite) gives you four real options instead of two binary ones. Most failed MVPs I've seen tried to ship "full" version of everything in scope.

**Story from this project:**
> On Panini B2B I evaluated about 115 features across 10 batches. Final breakdown: ~50 in MVP full, ~25 in MVP-lite, ~35 in Phase 2, ~5 removed. The lite verdict was applied to filters where we used controlled small vocabularies, to admin tools where we shipped numbered-position inputs instead of drag-drop, and to analytics where we shipped basic counts before cohort dashboards. Each lite decision was a conscious 80/20.

**What NOT to say:**
- ❌ "I cut everything except the most critical features" — too binary, misses the lite option
- ❌ "I let the team decide what's important" — abdicates judgment

---

## Q: How did you handle a moment when a stakeholder wanted to add features back to MVP?

**Why this gets asked:**
Tests whether you push back or roll over. Both junior failures.

**Short answer:**
> I don't just push back on the feature — I surface the strategic conflict. If we're scoping MVP and the founder asks to add cart, history, and persistent login, I'd say: "Adding these means we're now building a full B2B platform, not a catalog-first hybrid. Is the strategy changing, or did Phase 2 just feel scary?" That gets the actual decision on the table instead of a feature debate.

**Story:**
> Mid-Batch-5 of MVP scoping, the founder said "we need a complete B2B Website with cart, login, history." That conflicted with what we'd locked in the brief: catalog-first hybrid, WhatsApp as primary transaction layer. Instead of arguing each feature, I named it: "These features assume a different strategic position. Are we changing the strategy or did the deferred list feel scary?" He reflected and stuck with the original — but parked the full B2B platform as Phase 2. The conversation took 5 minutes; if I'd just argued each feature, it would have taken hours and we'd still be unclear about what we were building.

**Principle:**
> When stakeholders push back on previously-agreed scope, the question isn't "should we add this feature?" It's "are we changing the underlying decision this feature follows from?" Surface the meta-decision, not the surface decision.

---

## Q: Tell me about a time you discovered a foundational assumption was wrong mid-project.

**Why this gets asked:**
Tests intellectual honesty and ability to course-correct without ego.

**Short answer:**
> Mid-MVP scoping on Panini B2B, the founder mentioned almost as an aside: "we don't deal in real gold." I'd been building filters, trust signals, and pricing model around precious-metal trade — gold/silver/diamond filters, hallmarking certifications, gold rate displays, making charges. The actual business is fashion/imitation jewelry. Different filters, different trust signals, different pricing. Two hours of rework saved weeks of subtle product mistakes that would have shipped otherwise.

**The pattern:**
> Most teams patch around discovered wrong assumptions. The senior discipline is to do a "back-fix sweep": identify every locked decision affected by the wrong assumption, revise them as a coherent set, update upstream documents. Patching creates product debt; explicit re-derivation costs a session but keeps the system coherent.

**Specific things I changed:**
> - Metal filter (gold/silver/diamond) → Plating type filter (gold tone, silver tone, rose gold tone, oxidized)
> - Stone type vocabulary changed from "diamond/ruby/emerald" to "kundan-style/AD/glass stones/beads"
> - Stock status filter removed entirely — the founder decided to hide out-of-stock items rather than mark them, simplifying the data model
> - Making charges removed from product detail
> - Bulk price update demoted from MVP-lite to Phase 2 — its justification was "gold rate volatility" which doesn't apply
> - Hallmarking trust signals dropped
> - Live gold rate display removed from consideration entirely
>
> About 15 decisions touched. The brief got a v2 update. The MVP scope doc got a v0.3 update with full changelog. The product stays internally consistent.

---

## Q: Why did you treat analytics, performance, and error monitoring as MVP features instead of "infrastructure"?

**Why this gets asked:**
Most engineers split "features" from "non-functional" and defer non-functional. Senior thinking treats observability as part of MVP.

**Short answer:**
> Without analytics, the MVP is unfalsifiable. We set tiered success targets for adoption — Floor 15%, Target 30%, Stretch 50%. If we ship MVP and can't measure those numbers, we have no idea if it worked. We could build the perfect product and not know. So three analytics features are non-negotiable MVP: visit tracking, an adoption metrics dashboard, and WhatsApp deep-link CTR tracking. Same logic for performance and error monitoring — without them you ship blind. The technical baseline is part of MVP scope, not infrastructure-after-MVP.

**The principle:**
> A B2B catalog with slow images, no error tracking, and no analytics is technically shippable but practically broken — it'll fail in ways you can't even diagnose. Performance budgets, observability, and analytics are MVP features, not "nice to haves."

---

## Q: How do you decide whether to defer a feature's UI but build for it in the data model?

**Why this gets asked:**
Tests architectural foresight and the ability to think across phases.

**Short answer:**
> When a Phase 2 feature has a clear data implication, I separate UI deferral from data deferral. Build the data model with Phase 2 in mind; ship the UI for current MVP only. The cost is 5-10% more upfront work; the savings are weeks of refactoring later.

**Story:**
> On Panini, the founder confirmed pending order management is a Phase 2 priority. The data implication is per-line-item status (an order isn't an atomic blob — each item has its own state: shipped, cancelled, or eventually pending). For MVP we only use shipped/cancelled, but the schema supports pending from day one. When Phase 2 builds the pending-order workflow, we don't refactor the orders table — we just expose new states.

**Principle:**
> Shape the data for the future product, ship the UI for the current one.

---

## Q: How do you decide between infinite scroll and pagination in a catalog product?

**Why this gets asked:**
Looks like a UI question, but actually tests trade-off thinking.

**Short answer:**
> Pagination usually wins for B2B catalogs despite feeling less modern. Reasons: returning to a specific position is easy with pagination (URL has the page number), memory and performance on slow phones are better, SEO is stronger, deep-linking is reliable. Infinite scroll wins for discovery-mode browsing where users don't need to return — Instagram, Pinterest. For Panini's case, where buyers might browse, click into a product, then need to return to the same scroll position, pagination is more reliable. There's also a hybrid called "Load More" that gives 80% of infinite scroll's feel with 80% of pagination's reliability.

**Story:**
> I initially proposed pagination. The founder said infinite scroll. I laid out the trade-off matrix — eight criteria across the two patterns. After seeing the matrix, the founder switched back to pagination. The lesson: framing trade-offs explicitly lets stakeholders pick correctly. Without the matrix, the disagreement was preference vs preference; with it, the better answer became obvious.

---

## Q: What's an example of a small technical detail with disproportionate product impact?

**Short answer:**
> Open Graph tags on a sharing-driven product. When a user pastes a link into WhatsApp without OG tags configured, the message looks like a bare URL — bland, low click-through. With OG tags, it shows a rich preview: photo, name, price. For Panini B2B, where WhatsApp sharing is the #1 adoption mechanism, properly configured OG tags transform every shared link from a bare URL into a rich preview. Build cost: a few hours of metadata work. Impact: measurable lift in click-through rates from shared messages. The lesson: in a sharing-driven product, every step from "share happens" to "click happens" is worth optimizing.

---

## Q: How do you avoid the "Phase 2 graveyard" — where deferred features never actually ship?

**Why this gets asked:**
Cynical question about whether you actually ship deferred items or just say "Phase 2" to dodge.

**Short answer:**
> I treat Phase 2 as a commitment, not a deferral. Every Phase 2 item gets documented with: (1) the trigger that should bring it back, (2) the data we'd need to evaluate it, (3) any architectural commitments that should land in MVP to enable it. For example, on Panini, Phase 2 includes pending order management — but the data model in MVP includes per-line-item status, so Phase 2 starts from a foundation, not a refactor. Without those commitments, Phase 2 becomes a graveyard. With them, Phase 2 becomes a roadmap.

---

## Q: What's the meta-skill you've learned most from MVP scoping?

**Short answer:**
> Surfacing meta-decisions instead of debating surface decisions. Most arguments about features are actually arguments about strategy, sequencing, or risk tolerance — but they get expressed at the feature level. The senior skill is hearing "let's add cart and history to MVP" and recognizing the underlying question is "are we still committed to a catalog-first hybrid or are we now building a full B2B platform?" Surface the right question, and the feature debate often resolves itself.

---

## Updates log

| Date | Added |
|------|-------|
| 2026-05-09 | Initial set: 9 questions on MVP filtering, scope creep recognition, back-fix on wrong assumptions, analytics-as-MVP, data-model-for-Phase-2, infinite scroll vs pagination, OG tags, Phase 2 graveyards, surfacing meta-decisions |
