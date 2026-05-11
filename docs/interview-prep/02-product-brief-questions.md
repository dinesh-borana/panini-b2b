# 02 — Product Brief & One-Pager Questions

Questions about the product brief artifact — both the document itself and the decisions captured inside Panini B2B's brief.

---

## Q: Walk me through a product brief you've written.

**Short answer (60 sec):**
> I'm currently building a B2B catalog platform for my jewelry business, Panini Jewels. I wrote the brief as the founder. The problem: B2B sales today run on WhatsApp groups with about 1000 buyers, and the team is hitting two walls — repetitive question volume and no standardized catalog for onboarding new retailers. The strategy is hybrid: don't replace WhatsApp, build a catalog layer that makes WhatsApp conversations more efficient. Public pricing, mobile-first, no login to browse. Success measured by onboarding speed, order capture rate, and quality. The biggest risk is buyer adoption — buyers love WhatsApp's familiarity — so we're baking adoption mechanisms into the MVP itself.

**Long answer:**
> [Same as above, then add:]
>
> The decisions I'm proudest of in the brief are the *negative* ones — what we deliberately chose NOT to do. Single-tenant instead of multi-tenant SaaS, no MyBillBook integration in v1, no buyer login required to browse, no consumer storefront. Each was a real conversation with trade-offs. The single-tenant decision in particular went against my engineering instinct — I initially proposed a "multi-tenant ready" architecture for future SaaS sales — but the founder pointed out that other manufacturers' requirements would diverge enough that we'd refactor anyway. He was right. The brief captures the rationale so future-me doesn't relitigate the same decisions.

**What NOT to say:**
- ❌ "I wrote a PRD" — use the right vocabulary
- ❌ Describe only what's IN the brief — senior candidates also describe what's deliberately OUT
- ❌ Skip the metrics — interviewers will probe

---

## Q: Why hybrid model instead of a pure platform replacement?

**Short answer:**
> Buyers in Indian jewelry wholesale are WhatsApp-native and relationship-driven. They use WhatsApp because it's familiar, fast, and lets them forward photos to their own retail customers in the same flow. Forcing them off WhatsApp would destroy what they love and create adoption risk. The hybrid model lets buyers continue using WhatsApp where it works, while the platform solves the *operational* pain on the supplier side.

**Principle:**
> When the existing alternative is winning on relationship and habit (not just features), don't try to displace it. Augment it.

**Story:**
> I asked the founder, "what do buyers love about WhatsApp today?" Answer: "they feel familiar with it, and they can forward photos to others." That single answer reshaped the product. If I'd asked "what features do buyers want?" — the standard junior framing — I'd have built a checkout-first portal that buyers would have ignored.

---

## Q: Why public pricing? Isn't that a competitive risk?

**Short answer:**
> Three reasons. First: maximum reach with zero friction — anyone with a link can browse and share. Second: simplicity — no login walls means no onboarding friction. Third: adoption — gating prices behind login would make the platform *less* useful than current WhatsApp posts where prices are already visible. The competitive risk is smaller than it seems: competitors can already see prices via the WhatsApp groups today.

---

## Q: How did you decide what's in scope vs. out of scope for v1?

**Short answer:**
> I worked backward from the success metrics. Each potential feature got asked: "does this directly serve onboarding speed, order capture, or quality?" If yes, in scope. If no, deferred. Multi-tenancy, MyBillBook integration, mobile native apps, multi-language — all interesting, none directly serve the v1 metrics. They went into Phase 2 with rationale captured.

**Principle:**
> An MVP should be the *minimum* set of features that lets you validate the riskiest assumption.

---

## Q: What's the biggest risk in your project, and what are you doing about it?

**Short answer:**
> Buyer adoption. Buyers love WhatsApp's familiarity and might keep asking on WhatsApp instead of using the link. Four specific mitigations: every team WhatsApp reply will include the catalog link to passively train buyers; the catalog must be *better* than scrolling old WhatsApp messages, so we're investing in search and category browse; resharing back to WhatsApp has to be one tap; and the catalog will include designs that aren't in WhatsApp groups, giving buyers a positive reason to browse.

---

## Q: Tell me about a product decision you changed your mind on.

**Short answer:**
> Early in scoping Panini B2B, I proposed a "multi-tenant ready" architecture so we could sell the platform to other jewelry manufacturers later. The founder pushed back — pointed out that other manufacturers' requirements would diverge enough (different metals, different attributes, different pricing logic) that we'd refactor regardless of upfront tenant-ready architecture. So we'd be paying complexity now for no future savings. He was right. I changed my mind, and we documented "single-tenant" as the explicit architectural choice in the brief.

---

## Q: How do you keep the brief from becoming stale?

**Short answer:**
> Two mechanisms. First, the brief has a changelog — every meaningful update gets a dated entry. Second, the brief is referenced (not duplicated) by the MVP scope, ADRs, and design docs. When something downstream changes that contradicts an "out of scope" item, the change forces an update upstream. The brief becomes the rallying point, not a museum piece.

---

## Q: Could you have done this discovery in less time?

**Short answer:**
> Probably yes. For Panini specifically, since I'm both the founder and the engineer, a lot of the user research was internal — I didn't need 5 user interviews to know the WhatsApp pain points. The full process I followed serves a second purpose: rebuilding interview-ready depth on product thinking after a 2-year gap. For a typical project where I'm not the user, the full discovery is cheap insurance against building the wrong thing.

**Principle:**
> Match the rigor of discovery to the cost of being wrong.

---

## Updates log

| Date | Added |
|------|-------|
| 2026-05-08 | Initial set: 7 questions specific to the product brief and decisions inside it |
