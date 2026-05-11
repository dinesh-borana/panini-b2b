# 04 — Feature Scoping & Brainstorming

Questions about how to generate, evaluate, and ruthlessly cut feature ideas.

---

## Q: How do you brainstorm features without immediately filtering yourself?

**Short answer:**
> I separate divergence from convergence — two distinct phases. In the brainstorm, the rule is no judgment, no filtering, no "but is this realistic?" Only after the list feels complete do I switch modes and start cutting. If you filter while brainstorming, you anchor too low and miss good ideas. Filtering and creating use different parts of the brain; doing them simultaneously produces mediocre results.

**Story:**
> When I scoped Panini B2B, I deliberately produced a list of about 75 features — including things I knew were impractical, like AR try-on or buyer reviews. The point wasn't to build them; the point was that having them on the list forced me to *consciously reject* each one with reasons documented. When an interviewer asks "did you consider AR?" — yes, here's why we deferred it. That's a stronger answer than "we didn't think of it."

---

## Q: How did you decide to defer Image Search and Order Book Scanning to Phase 2?

**Short answer:**
> Both are exciting features with strong domain-specific value. But neither is *required* to test the riskiest assumption — buyer adoption. We can validate adoption with a basic, well-built catalog. If we'd spent MVP time building image search and OCR, we'd be testing whether AI features drive adoption — a different and more expensive bet. Defer the exciting features until the foundation is proven.

**Story:**
> Order book scanning was tempting because it's an *adoption hack* — retailers don't have to change their habit, the platform just digitizes their existing workflow. That's brilliant product thinking. But "tempting" isn't the bar; "necessary for the MVP test" is. We can validate the core hypothesis with simpler ingestion paths and add scanning in Phase 2 once we know buyers want the platform at all.

**Principle:**
> Exciting features tempt teams. The senior discipline is choosing essential over exciting — being explicit about WHY each exciting feature is being deferred so you don't lose the idea.

---

## Q: How do you handle requirements that feel ambiguous?

**Short answer:**
> I'll often try multiple framings to find the right one — but I stay alert for when my framings are creating complexity that doesn't actually exist in the requirement. Sometimes the user's plain description IS the spec, and my job is to listen, not to taxonomize. The skill isn't generating frameworks; it's knowing when to stop generating them.

**Story:**
> While scoping a size filter for Panini's catalog, I built up an elaborate framework — three interpretations of what "filter by size" could mean, with different implementation costs. The founder cut through it with a one-paragraph plain description: "Standard filter on a category page. Pick a size, see designs available in that size." That was exactly what he wanted. My framework had been adding complexity that didn't exist.

---

## Q: What's the cost of adding a filter to a product?

**Short answer:**
> A filter looks like a UI feature, but it's actually a *data contract*. Every filter you add commits the team to capturing that field for every product, maintaining a controlled vocabulary, and updating availability over time. So adding a filter isn't a UI decision — it's a long-term operational commitment. I'd rather ship 5 filters that work perfectly than 10 that work for half the catalog.

**Story:**
> When picking filters for Panini's catalog, the founder selected 8 — including occasion and stone style, which are subjective fields requiring human judgment. We discussed the trade-off explicitly: each new filter adds data-entry burden on the team. He accepted the trade-off knowingly, which is the right kind of decision-making — not "I want these filters" but "I want these filters AND I'm signing up for the operational cost."

---

## Q: How do you choose between essential and exciting features?

**Short answer:**
> I ask: "would the MVP succeed without this feature?" If yes, it's exciting but not essential. Essential features are the ones that, if missing, make the MVP test impossible. Exciting features get a clear "Phase 2" label and a documented reason for deferral.

---

## Updates log

| Date | Added |
|------|-------|
| 2026-05-09 | Initial set: 5 questions on brainstorming, deferring exciting features, ambiguity, filter trade-offs, essential vs exciting |
