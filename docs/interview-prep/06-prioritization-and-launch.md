# 06 — MVP Prioritization, Launch Strategy & Roadmaps

Questions about ordering work within an MVP, defining "done," and structuring what comes after.

---

## Q: How do you decide what to build first within an MVP?

**Short answer:**
> I default to **walking-skeleton** delivery. Slice 1 ships the full stack — minimal data, minimal API, minimal UI — for one workflow end-to-end. Each subsequent slice thickens the system. Advantage: never holding half-built features; every slice is demonstrable; integration risk is surfaced day 1 instead of week 8.

**Long answer:**
> The opposite — horizontal layered delivery — is what most teams default to. Build all the data layer, then all the API, then all the UI. Sounds organized but it means you have *nothing demonstrable* until very late, and integration bugs all surface at once. Walking skeleton inverts that. You ship a paper-thin version of everything early, then thicken layer by layer.

**Story:**
> On Panini B2B I split MVP into 6 slices. Slice 1 was deliberately thin — deploy the app, render one product, share to WhatsApp. Just enough to prove the stack works end-to-end. Slice 2 thickened catalog (multiple products, basic filters). Slice 3 added discovery polish (search, multi-select). Slice 4 added platform-native ordering. Slice 5 added measurement and trust pages. Slice 6 was pre-launch hardening with real catalog migration. Every slice was demoable. The team or stakeholders can give feedback after slice 2, not slice 6.

**What NOT to say:**
- ❌ "I build all admin first, then all buyer-facing"
- ❌ "I work on whatever ticket is at the top of the backlog"
- ❌ "We'll figure it out in sprint planning"

---

## Q: How do you estimate timelines for MVP?

**Short answer:**
> I avoid timeline estimates before any code is written. Velocity is empirical — you only know how fast you ship after shipping something. So I rank features and group into slices first, ship Slice 1, then use that velocity to forecast remaining slices. Pre-baseline estimates are theatre, not engineering.

**Story:**
> On Panini B2B, when planning slices, I deliberately didn't commit to "MVP in X weeks." I committed to slice ordering and slice contents, with timelines re-derived after Slice 1 ships. Founder agreed. Most projects fail their stated timeline anyway because the original number was made-up; this approach lets the timeline emerge from data.

---

## Q: What's your Definition of Done for a product launch?

**Short answer:**
> I treat DoD as a *graduated set of milestones*, not a single binary gate. "Ready for friendly users" is a different bar than "ready for unknown users at scale." Pretending they're the same creates pressure to over-build for soft launch or under-build for public launch. Separating them lets each milestone optimize for its own risk profile.

**Story:**
> For Panini B2B I locked two milestones. **Milestone 1 (Soft Launch):** ready to share with 5-10 trusted buyers. Functional + quality + measurement + trust pages + ops readiness criteria. **Milestone 2 (Public Launch):** adds soft-launch outcome criteria ("at least 5 of 10 soft-launch buyers visited"), scale-readiness (load testing, hosting plan), and communication (group-specific launch messages). Public Launch criteria depend on Soft Launch outcomes — proper conditional planning.

**Principle:** DoD is a quality gate. Launch strategy is a rollout question. Different decision-makers, different risk profiles. Conflating them creates pressure to delay DoD or launch before DoD is met.

---

## Q: Definition of Done vs Launch Strategy — what's the difference?

**Short answer:**
> DoD is "is the product ready for users?" — a code/quality gate. Launch strategy is "how fast do we expose it to which users?" — a rollout question. Engineering owns DoD; product/business owns launch strategy. Many teams conflate them and end up trapped — unable to move forward because the calendar says launch but the code isn't ready, or shipping prematurely because launch is committed.

---

## Q: How do you handle a stakeholder pushing for a riskier launch (e.g., simultaneous public vs phased)?

**Short answer:**
> Surface the risk profile of each approach explicitly and let the stakeholder pick with eyes open. I don't push back on the approach; I push back on the implicit assumptions. "Public launch to 1000 buyers simultaneously" assumes everything works the first time and team can handle the volume of incoming WhatsApp enquiries. "Phased soft launch" trades some impact for learning velocity. Both valid; depends on confidence and risk tolerance.

**Story:**
> Founder initially said "public launch, all 4 groups, full announcement." I laid out the risks: blast radius if there's a bug, team responsiveness load, no early-feedback opportunity. Founder reconsidered and chose phased soft launch. Wasn't pushing my preference — was making the trade-offs visible so he could choose informed.

---

## Q: How do you structure a Phase 2 backlog so it doesn't become a graveyard?

**Short answer:**
> Three layers. **Themes** — coherent feature groups that should ship together. **Triggers** — observable signals indicating "now is the right time for this theme." **Within-theme features** — actual feature list. Without themes, Phase 2 is a random list. Without triggers, items get started arbitrarily. With both, Phase 2 becomes a real roadmap that moves at the speed of evidence.

**Story:**
> Panini B2B Phase 2 has 7 themes: Full B2B E-commerce, Admin & Operational Excellence, AI & Discovery, Marketing & Growth, Reach & Accessibility, Integrations, Trust & Brand. Each has a trigger. **Theme 2 (Admin)** starts immediately post-MVP — evidence already exists from operational history. Other themes wait for triggers like "≥30% orders flow through Place Order" (Theme 1) or "≥30% search queries return zero results" (Theme 3).

---

## Q: Why do some Phase 2 themes start immediately and others wait for triggers?

**Short answer:**
> Not all Phase 2 themes have the same evidence threshold. When evidence already exists — from operational history, team interviews, known pain — the theme can start as soon as MVP ships. When evidence is speculative — depending on user behavior we haven't observed — the theme waits for triggers. Treating all Phase 2 work as equally speculative is its own form of fiction.

**Story:**
> Founder pointed out that admin operational improvements (pending order management, worker assignment, broadcast tools) aren't speculative — he's been doing them manually for years and knows exactly what the gap is. So Theme 2 starts immediately. Other themes — like AI features or full e-commerce — depend on what MVP teaches us, and those wait. Sharper thinking than treating "Phase 2" as one big bucket.

---

## Q: How do you avoid roadmap fiction?

**Short answer:**
> Trigger-driven roadmaps over time-driven ones. Calendar-based roadmaps are fiction — they pretend we know in March what we'll need in September. Trigger-based roadmaps tie work to observable signals. "Cart starts when 30% of MVP orders flow through Place Order Directly" is concrete. "Cart in Q3" is a guess. When execs ask for time-based roadmaps, I provide them but anchor each item to a trigger so we know if reality diverges.

---

## Q: How do you handle the "Phase 3" question?

**Short answer:**
> Phase 3 doesn't exist yet. By the time Phase 2 themes are mostly done, we'll have so much new data that any Phase 3 we plan now will be wrong. Better to write Phase 2 with rigor and leave Phase 3 unplanned. Most teams over-plan future phases and refuse to update those plans when reality changes.

---

## Updates log

| Date | Added |
|------|-------|
| 2026-05-09 | Initial set: walking skeleton, timeline humility, two-milestone DoD, DoD vs launch strategy, launch risk framing, Phase 2 structuring, mixed-trigger themes, roadmap fiction, Phase 3 humility |
