# 03 — Setting Goals & Metrics Under Uncertainty

Questions about how to set realistic, defensible product goals — especially when you have no historical data to anchor against.

---

## Q: How do you set adoption targets for a new product when you have no baseline data?

**Why this gets asked:**
Tests whether you understand the gap between user need and user behavior. Junior candidates set arbitrary numbers ("we'll aim for 50%"); senior candidates explain how they reason under uncertainty.

**Short answer (45 sec):**
> I use tiered targets — a floor, target, and stretch — instead of a single number. The floor is "something is working," the target is "we're succeeding by reasonable industry benchmarks," and the stretch is "we have a category-defining product." This works better than a single threshold because (1) without baseline data, any single number is arbitrary, and (2) it lets the team tell a richer story even when results are mixed. If we hit floor on adoption but stretch on onboarding speed, we know which assumption was right and which needs rethinking.

**Long answer (2 min):**
> [Same as above, plus the example below]
>
> The single biggest mistake I see in goal-setting is conflating "users need this" with "users will use this." The need is necessary but not sufficient. Even when need is real, you're competing with the habit of the current solution, the trust they have in alternatives, and the awareness gap. A clearly better product with strong product-market fit can still take years to reach 50% adoption — Google Pay is the classic Indian example. So when I set targets, I treat industry benchmarks as the gravity that pulls me toward realistic numbers, even when my gut says we'll outperform.

**Story to tell from this project:**
> On the Panini B2B catalog, my first instinct was to set adoption targets at 50% in 60 days because I was sure buyers would use it — they clearly *need* the information the catalog provides. But I challenged myself: is "they need it" the same as "they'll use it"? It isn't. WhatsApp is a deeply ingrained habit. Even genuinely useful tools have to climb that adoption curve. So I switched to tiered targets — Floor 15%, Target 30%, Stretch 50%. The reasoning got documented in the MVP scoping doc. If we hit 35%, we know we did well. If we hit 15%, we know something works but adoption is harder than expected. Single-threshold targets would have either created a false sense of failure or false sense of success.

**What NOT to say:**
- ❌ "I aim high to motivate the team" — vanity reasoning, not product reasoning
- ❌ "I look at competitors' numbers" — fine, but not enough; competitors had different starting conditions
- ❌ "We'll figure it out after launch" — you need *some* anchor before launch to know what to learn

**Follow-up questions to expect:**
- "What if you hit the floor but not the target — do you keep going or pivot?"
- "How would you measure those metrics technically?"
- "Have you ever set targets you were proud of and then realized were wrong?"

---

## Q: What's the difference between a leading and lagging indicator?

**Why this gets asked:**
Vocabulary check. Common in PM-adjacent senior engineer interviews.

**Short answer:**
> A leading indicator moves before the outcome you care about — it's a *predictor*. A lagging indicator moves after — it's the *outcome itself*. For Panini B2B, repeat catalog visits are leading (they predict adoption); orders captured on the platform are lagging (they confirm adoption already happened). Good metric design uses leading indicators to course-correct before the lagging metric tells you it's too late.

**Story:**
> In our metrics, repeat visits in 60 days is a leading indicator — if visits are climbing, we know order capture will follow. WhatsApp enquiries citing catalog items is *also* leading — it tells us the catalog is becoming a shared vocabulary between buyer and team, even before that buyer places an order. By tracking these together, we'll know if MVP is working long before revenue numbers shift.

---

## Q: How do you avoid vanity metrics?

**Why this gets asked:**
Tests product maturity.

**Short answer:**
> A metric is a vanity metric if it can go up without the underlying product getting better. Total page views, total signups, total products in catalog — all easy to grow without value being created. The fix is to tie every metric to a specific user behavior that maps to value. For Panini, "page views" would be vanity; "% of active WhatsApp buyers who visit twice" is real because it requires actual repeat engagement from a known user base.

---

## Q: How do you decide what to measure when you can only afford to measure a few things?

**Short answer:**
> I work backward from the riskiest assumption. If MVP is a test of an assumption, the metrics should answer "is the assumption true or false?" Anything that doesn't help answer that gets deprioritized in v1 instrumentation. We can always add metrics later; spreading thin too early means we measure everything and learn nothing.

---

## Updates log

| Date | Added |
|------|-------|
| 2026-05-08 | Initial set: 4 questions on goal setting, leading/lagging indicators, vanity metrics, prioritizing measurement |
