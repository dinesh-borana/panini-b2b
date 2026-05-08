# 02 — Product Brief & One-Pager Questions

Questions specifically about the product brief artifact — both the document itself and the decisions captured inside Panini B2B's brief.

---

## Q: Walk me through a product brief you've written.

**Why this gets asked:**
Tests whether you've actually done this work or just read about it. Interviewers will follow up on inconsistencies.

**Short answer (60 sec):**
> I'm currently building a B2B catalog platform for my jewelry business, Panini Jewels. I wrote the brief myself as the founder. The problem: B2B sales today run on WhatsApp groups with about 1000 buyers, and the team is hitting two walls — repetitive question volume and no standardized catalog for onboarding new retailers. The strategy is hybrid: don't replace WhatsApp, build a catalog layer that makes WhatsApp conversations more efficient. Public pricing, mobile-first, no login to browse. Success is measured by onboarding speed, order capture rate, and quality. The biggest risk is buyer adoption — buyers love WhatsApp's familiarity — so we're baking adoption mechanisms into the MVP itself.

**Long answer (3 min):**
> [Same as above, then add:]
>
> The decisions I'm proudest of in the brief are the *negative* ones — what we deliberately chose NOT to do. Single-tenant instead of multi-tenant SaaS, no MyBillBook integration in v1, no buyer login required to browse, no consumer storefront. Each of those was a real conversation with trade-offs. The single-tenant decision in particular went against my engineering instinct — I initially proposed a "multi-tenant ready" architecture for future SaaS sales — but the founder pointed out that other manufacturers' requirements would diverge enough that we'd refactor anyway. He was right. The brief captures the rationale so future-me doesn't relitigate the same decisions.

**What NOT to say:**
- ❌ "I wrote a PRD" — when asked about a brief, use the right vocabulary
- ❌ Describe only what's IN the brief — senior candidates also describe what's deliberately OUT
- ❌ Skip the metrics — interviewers will probe whether you defined success quantitatively

---

## Q: Why did you choose a hybrid model instead of a pure platform replacement?

**Why this gets asked:**
Tests whether you understand user behavior beyond features. This is the kind of question where senior product-thinking shines.

**Short answer:**
> Buyers in Indian jewelry wholesale are WhatsApp-native and relationship-driven. They use WhatsApp because it's familiar, fast, and lets them forward photos to their own retail customers in the same flow. Forcing them off WhatsApp would destroy the things they love about the current channel and create adoption risk. The hybrid model lets buyers continue using WhatsApp where it works, while the platform solves the *operational* pain on the supplier side — the team replaces "type the price" with "send the link." Adoption becomes opt-in, not forced.

**The principle:**
> When the existing alternative is winning on relationship and habit (not just features), don't try to displace it. Augment it.

**Story to tell:**
> I asked the founder, "what do buyers love about WhatsApp today?" Answer: "they feel familiar with it, and they can forward photos to others." That single answer reshaped the product. If I'd asked "what features do buyers want?" — the standard junior framing — I'd have built a checkout-first portal that buyers would have ignored.

---

## Q: Why public pricing? Isn't that a competitive risk?

**Why this gets asked:**
Tests business judgment. There's no objectively right answer; the interviewer wants to hear how you think about trade-offs.

**Short answer:**
> Public pricing was a deliberate choice with three reasons. First: maximum reach with zero friction — anyone with a link can browse and share, which directly serves the catalog's job of replacing repetitive price replies. Second: simplicity — no login walls means no onboarding friction for casual browsers. Third: adoption — gating prices behind login would make the platform *less* useful than current WhatsApp posts where prices are already visible. The competitive risk is real but smaller than it seems: competitors can already see Panini's prices via the WhatsApp groups today, so we're not exposing anything new.

**What NOT to say:**
- ❌ "Public is just easier to build" — that's the lazy answer; explain the trade-off
- ❌ "We can always add login later" — true but doesn't show you thought about WHY public is right NOW

---

## Q: How did you decide what's in scope vs. out of scope for v1?

**Why this gets asked:**
Tests scoping discipline.

**Short answer:**
> I worked backward from the success metrics. Each potential feature got asked: "does this directly serve onboarding speed, order capture, or quality?" If yes, in scope. If no, deferred. Multi-tenancy, MyBillBook integration, mobile native apps, multi-language — all interesting, none directly serve the v1 metrics. They went into a Phase 2 / out-of-scope list with the rationale captured.

**Principle behind it:**
> An MVP should be the *minimum* set of features that lets you validate the riskiest assumption. For Panini B2B, the riskiest assumption is buyer adoption — so the MVP should be just enough to test "will buyers actually use a catalog instead of asking on WhatsApp?"

---

## Q: What's the biggest risk in your project, and what are you doing about it?

**Why this gets asked:**
Senior candidates name a real risk and a specific mitigation. Junior candidates either don't name a risk or hand-wave the mitigation.

**Short answer:**
> Buyer adoption. Buyers love WhatsApp's familiarity and might keep asking on WhatsApp instead of using the link. We're addressing it in four specific ways: every team WhatsApp reply will include the catalog link to passively train buyers; the catalog must be *better* than scrolling old WhatsApp messages, so we're investing in search and category browse; resharing back to WhatsApp has to be one tap, so buyers don't feel they're leaving WhatsApp; and the catalog will include designs that aren't in WhatsApp groups, giving buyers a positive reason to browse.

**Why this answer works:**
- It names the risk specifically (not "general adoption risk")
- It lists *concrete* mitigations, not "we'll do user research"
- It shows the mitigations are baked into the MVP itself, not deferred

---

## Q: Tell me about a product decision you changed your mind on.

**Why this gets asked:**
Tests intellectual honesty. Senior engineers update their views; juniors defend their first idea.

**Short answer:**
> Early in scoping Panini B2B, I proposed a "multi-tenant ready" architecture so we could sell the platform to other jewelry manufacturers later. The founder pushed back — he pointed out that other manufacturers' requirements would diverge enough (different metals, different attributes, different pricing logic) that we'd refactor regardless of upfront tenant-ready architecture. So we'd be paying complexity now for no future savings. He was right. I changed my mind, and we documented "single-tenant" as the explicit architectural choice in the brief, with the reasoning captured so future-me doesn't relitigate it.

**Why this works:**
- It's honest (you were wrong, you said so)
- It's specific (you can describe the exact trade-off)
- It shows the founder pushed back and you listened — humility signal

---

## Q: How do you keep the brief from becoming stale?

**Why this gets asked:**
Tests whether you treat documents as living artifacts or as deliverables to forget.

**Short answer:**
> Two mechanisms. First, the brief has a changelog — every meaningful update gets a dated entry, so anyone reading knows what changed and when. Second, the brief is referenced (not duplicated) by the MVP scope, ADRs, and design docs. When something downstream changes — say, we add a feature that contradicts an "out of scope" item — the change forces an update upstream. The brief becomes the rallying point, not a museum piece.

---

## Q: Could you have done this discovery in less time?

**Why this gets asked:**
Tests whether you understand the cost of process. Discovery for the sake of discovery is anti-pattern; senior thinkers know when to stop.

**Short answer:**
> Probably yes. For Panini specifically, since I'm both the founder and the engineer, a lot of the user research was internal — I didn't need 5 user interviews to know the WhatsApp pain points; I live them. So I could have skipped the formal persona development and gone straight to problem statement and strategy. The full process I followed serves a second purpose for me: rebuilding interview-ready depth on product thinking after a 2-year gap. For a more typical project where I'm not the user, the full discovery is cheap insurance against building the wrong thing.

**Principle:**
> Match the rigor of discovery to the cost of being wrong. For a high-stakes new product, full discovery is essential. For a small feature with a known user base, a 30-minute conversation is enough.

---

## Updates log

| Date | Added |
|------|-------|
| 2026-05-08 | Initial set: 7 questions specific to the product brief and decisions inside it |
