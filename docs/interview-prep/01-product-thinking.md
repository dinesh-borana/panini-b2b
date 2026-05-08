# 01 — Product Thinking & Discovery Process

Questions about *how* you approach building products. These come up in senior frontend, full-stack, and tech lead interviews because companies want engineers who think beyond "implement the ticket."

---

## Q: Walk me through how you'd start a new product or feature.

**Why this gets asked:**
Tests whether you jump to code/features (junior) or start with problem and users (senior). It's the most common opener in senior frontend and full-stack interviews.

**Short answer (30 sec):**
> I start with problem discovery — understanding what's broken today and why now. Then user discovery — who they are, what their current alternatives are, and what jobs they're trying to get done. From there I land on a product strategy, define success metrics and risks, and condense it all into a one-page product brief. Only after that do I move to MVP scoping, user flows, and technical design. The mistake juniors make is starting with features; the discipline of seniors is starting with problems.

**Long answer (2–3 min):**
> I follow a structured discovery process before writing any code. There are roughly eight steps:
>
> 1. **Problem discovery** — what's broken today, why does it need fixing now, and what happens if we do nothing?
> 2. **User discovery** — who are the users, what are their current alternatives, what do they love and hate about today's solution?
> 3. **Jobs-to-be-Done analysis** — what job is the user "hiring" the product to do? This sharpens the framing beyond "what feature do they want?"
> 4. **Alternative analysis** — your real competitor isn't always who you think. For my current project, the competitor isn't another B2B portal — it's WhatsApp itself, because that's what buyers use today.
> 5. **Product strategy** — the high-level approach, including what you deliberately won't do.
> 6. **Goals & success metrics** — define quantitatively what winning looks like. I distinguish leading indicators from lagging indicators.
> 7. **Constraints & risk identification** — team, timeline, budget, and the top adoption/technical/market risks.
> 8. **Synthesis into a one-pager** — the product brief that becomes the team's single source of truth.
>
> Only after that do I move into MVP scoping, user flows, system design, and engineering. Most junior engineers skip the first 7 steps and jump to features. The senior discipline is to slow down upfront so you don't waste 3 months building something nobody wants.

**Story to tell from this project:**
> "I'm building a B2B catalog for my jewelry business, Panini Jewels. My first instinct was actually to start with code — I literally drafted a folder structure and ADRs. But when I stepped back, I realized I was solving the wrong problem. So I restarted with discovery. I interviewed myself essentially as the founder, asked who the users are (resellers and retailers on WhatsApp), what they love about WhatsApp today (familiarity, easy photo-forwarding to their own customers), and what hurts about it (volume of repetitive 'rate kya hai' questions, no catalog to send to new retailers). That reframed the entire product from 'B2B e-commerce platform' to 'catalog layer that powers WhatsApp conversations' — a hybrid model where WhatsApp stays as the transaction layer. If I'd skipped discovery, I'd have built a checkout-heavy platform that buyers would have ignored."

**What NOT to say:**
- ❌ "I jump in and start coding to learn the requirements" — signals junior
- ❌ "I just build what the PM tells me" — signals you don't think above your level
- ❌ "I follow Agile / scrum" — Agile is a delivery framework, not a discovery process. Don't confuse them.

**Follow-up questions to expect:**
- "What if the PM doesn't do this work — do you push back, or just build?"
- "How much time do you typically spend in discovery?"
- "Have you ever skipped this and regretted it?"

---

## Q: What's the difference between problem discovery and user research?

**Why this gets asked:**
Tests whether you actually understand the vocabulary or are just memorizing buzzwords.

**Short answer:**
> Problem discovery asks "what's broken and why now?" — it's about the *situation*. User research asks "who is affected, what do they currently do, and what do they need?" — it's about the *people*. You can't do good user research without first knowing what problem you're investigating; you can't deeply understand a problem without talking to the users who experience it. They're sequential but interlocked.

**Story to tell:**
> On Panini B2B, problem discovery told me: there's volume pressure from manual WhatsApp replies and no catalog for onboarding. User research told me: the buyers are Tier-2/3 retailers who *love* WhatsApp's familiarity and would resist abandoning it. Those two insights together pointed at a hybrid model — solve the operational pain without forcing buyers to change behavior. Either insight alone would have led me astray.

---

## Q: What is Jobs-to-be-Done? Have you used it?

**Why this gets asked:**
JTBD is a fashionable PM framework. Senior engineers are expected to know it, even if not to apply it daily. Knowing it signals you've worked with thoughtful PMs.

**Short answer:**
> JTBD is a framework popularized by Clayton Christensen. The core idea is people don't buy products; they hire products to do a job. So instead of asking "what features do users want?", you ask "what job is the user trying to get done?" It sharpens the framing dramatically.

**Story to tell:**
> On the Panini project, instead of asking "what B2B features do buyers want?", I asked "what job do they hire WhatsApp to do today?" The answer was: find designs, share them with their own retail customers, and trust the price. So I designed the platform to do those three jobs *better* than WhatsApp — not to replace WhatsApp wholesale. Sharing-back-to-WhatsApp became a first-class feature, not an afterthought.

**What NOT to say:**
- ❌ "JTBD is the same as user stories" — wrong, user stories are tactical, JTBD is strategic
- ❌ "It's just a fancy way of asking what users want" — wrong, it's deliberately about the *outcome* the user wants, not the *feature* they request

---

## Q: How do you identify the right success metrics for a new product?

**Why this gets asked:**
Tests whether you understand business outcomes, not just feature shipping.

**Short answer:**
> I tie metrics back to the original problem statement. If the problem was "onboarding takes too long," success has to include an onboarding-speed metric. I distinguish leading indicators (early signals like catalog visits) from lagging indicators (eventual outcomes like revenue) and aim for a mix. I also explicitly NOT pick metrics that are easy to hit but don't reflect real value — vanity metrics.

**Story to tell:**
> For Panini B2B, I picked three metrics: onboarding speed (new retailer ready to browse in <15 min), order capture rate (≥30% of orders originate on the platform), and quality (near-zero pricing errors). I deliberately did NOT pick "number of products in catalog" or "number of page views" — those are vanity metrics that move easily but don't prove the product is solving the actual problems we identified.

**Follow-up:**
- "What's a North Star metric? Did you pick one?"
- "How do you handle metrics that conflict with each other?"

---

## Q: Why did you decide NOT to integrate MyBillBook in v1?

**Why this gets asked:**
Tests scoping discipline. Senior engineers say no thoughtfully; juniors say yes to everything.

**Short answer:**
> Integrations are time sinks with hidden complexity — auth, data mapping, edge cases, rate limits, and ongoing maintenance burden. For an MVP whose primary risk is buyer adoption, integration would consume time that should go into nailing the catalog experience. Manual reconciliation in v1 is acceptable; the cost is an internal team workflow, not a customer-facing problem. I documented it as out-of-scope in the brief and as a Phase-2 candidate so we don't lose the idea.

**Principle behind this answer:**
> When scoping an MVP, separate "customer-facing risk" from "internal workflow inconvenience." Spend MVP budget on the former, defer the latter.

---

## Q: How do you handle scope creep during discovery?

**Why this gets asked:**
Tests whether you can hold the line on scope without being rigid.

**Short answer:**
> The product brief is my anchor. Any new feature request gets evaluated against the goals and out-of-scope list. If it serves a goal we explicitly haven't committed to, it goes on the Phase 2 list — not into MVP. The discipline isn't refusing ideas; it's deferring them with respect, so we can ship something coherent.

**Story to tell:**
> While drafting Panini's brief, I caught myself adding multi-tenancy because we *might* sell the product to other manufacturers later. The founder pushed back — he pointed out that other manufacturers' requirements would diverge enough that multi-tenancy upfront wouldn't actually save time. He was right. I caught my own scope creep and explicitly added "multi-tenancy" to the out-of-scope list in the brief.

---

## Q: What's the difference between a Product Brief, a PRD, and a One-Pager?

**Why this gets asked:**
Vocabulary check.

**Short answer:**
> All three are alignment documents, but they differ in depth and audience. A **One-Pager** (or Product Brief) is the highest-level — problem, users, strategy, metrics. Read in 5 minutes. A **PRD** (Product Requirements Document) is more detailed — goes into specific user stories, functional requirements, edge cases. Reads in 30 minutes. Amazon famously uses a 6-pager narrative that sits between the two. I generally write a one-pager first to align stakeholders, then a PRD to specify implementation details. Skipping the one-pager and going straight to PRD often means you're specifying a solution before agreeing on the problem.

---

## Updates log

| Date | Added |
|------|-------|
| 2026-05-08 | Initial set: 6 questions covering discovery process, JTBD, metrics, scoping, vocabulary |
