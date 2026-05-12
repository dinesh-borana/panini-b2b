# 04 — Feature Scoping & Brainstorming

## Q: How do you brainstorm features without filtering yourself?

Separate divergence from convergence — two distinct phases. Brainstorm = no judgment, no filtering. Only after list feels complete do you switch modes and cut. Filtering and creating use different parts of the brain; doing both simultaneously produces mediocre results.

**Story:** Scoping Panini B2B I deliberately produced ~75 features in brainstorm, including impractical ones like AR try-on. Point wasn't to build them — having them on the list forced conscious rejection with reasons documented. When interviewer asks "did you consider AR?" — yes, here's why we deferred. Stronger than "we didn't think of it."

## Q: How did you decide to defer Image Search and Order Book Scanning?

Both are exciting with strong domain value. But neither is *required* to test the riskiest assumption. We can validate adoption with a basic catalog. If we'd spent MVP time on AI features, we'd be testing whether AI drives adoption — different and more expensive bet.

**Story:** Order book scanning was tempting because it's an *adoption hack* — retailers don't have to change habits, the platform just digitizes their workflow. Brilliant product thinking. But "tempting" isn't the bar; "necessary for the MVP test" is. We can validate the core hypothesis with simpler ingestion paths.

**Principle:** Choose essential over exciting — be explicit about WHY each exciting feature is deferred so you don't lose it.

## Q: How do you handle ambiguous requirements?

Try multiple framings — but stay alert when framings create complexity that doesn't exist. Sometimes the user's plain description IS the spec. The skill isn't generating frameworks; it's knowing when to stop.

**Story:** Scoping a size filter, I built up an elaborate framework — three interpretations with different costs. Founder cut through with a one-paragraph plain description: "Standard filter on category page. Pick a size, see designs available." My framework had been adding complexity that didn't exist.

## Q: What's the cost of adding a filter?

Looks like UI, but actually a *data contract*. Every filter commits team to capturing that field per product, maintaining controlled vocabulary, updating availability. Adding a filter is a long-term operational commitment. Rather ship 5 filters that work perfectly than 10 that work for half the catalog.

## Q: How do you choose between essential and exciting features?

Ask: "would the MVP succeed without this?" If yes, exciting but not essential. Essential features are ones that, missing, make MVP test impossible. Exciting features get clear Phase 2 label with documented reason.
