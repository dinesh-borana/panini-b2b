# 01 — Product Thinking & Discovery Process

Questions about *how* you approach building products. These come up in senior frontend, full-stack, and tech lead interviews because companies want engineers who think beyond "implement the ticket."

---

## Q: Walk me through how you'd start a new product or feature.

**Why this gets asked:**
Tests whether you jump to code/features (junior) or start with problem and users (senior).

**Short answer (30 sec):**
> I start with problem discovery — understanding what's broken today and why now. Then user discovery — who they are, what their current alternatives are, what jobs they're trying to get done. From there I land on a product strategy, define success metrics and risks, and condense it all into a one-page product brief. Only after that do I move to MVP scoping, user flows, and technical design. The mistake juniors make is starting with features; the discipline of seniors is starting with problems.

**Long answer:**
> I follow a structured discovery process before writing any code. Roughly eight steps:
>
> 1. **Problem discovery** — what's broken today, why now, what happens if we do nothing?
> 2. **User discovery** — who are the users, what are their alternatives, what do they love and hate today?
> 3. **Jobs-to-be-Done analysis** — what job is the user "hiring" the product to do?
> 4. **Alternative analysis** — your real competitor isn't always who you think.
> 5. **Product strategy** — including what you deliberately won't do
> 6. **Goals & success metrics** — leading vs. lagging indicators
> 7. **Constraints & risk identification**
> 8. **Synthesis into a one-pager**

**Story from this project:**
> I'm building a B2B catalog for my fashion-jewelry business, Panini Jewels. My first instinct was to start with code — I literally drafted a folder structure. But when I stepped back, I realized I was solving the wrong problem. So I restarted with discovery. Asked who the users are (resellers and retailers on WhatsApp), what they love about WhatsApp today (familiarity, easy photo-forwarding to their own customers), what hurts (volume of repetitive 'rate kya hai' questions, no catalog to send to new retailers). That reframed the entire product from 'B2B e-commerce platform' to 'catalog layer that powers WhatsApp conversations' — a hybrid model where WhatsApp stays the transaction layer.

**What NOT to say:**
- ❌ "I jump in and start coding to learn the requirements"
- ❌ "I just build what the PM tells me"
- ❌ "I follow Agile" — Agile is a delivery framework, not a discovery process

---

## Q: What's the difference between problem discovery and user research?

**Short answer:**
> Problem discovery asks "what's broken and why now?" — it's about the *situation*. User research asks "who is affected, what do they currently do, and what do they need?" — it's about the *people*. They're sequential but interlocked.

**Story:**
> On Panini B2B, problem discovery told me there's volume pressure from manual WhatsApp replies and no catalog for onboarding. User research told me the buyers are Tier-2/3 retailers who *love* WhatsApp's familiarity and would resist abandoning it. Those two insights together pointed at a hybrid model — solve the operational pain without forcing buyers to change behavior.

---

## Q: What is Jobs-to-be-Done?

**Short answer:**
> A framework popularized by Clayton Christensen. People don't buy products; they hire products to do a job. Instead of asking "what features do users want?", ask "what job is the user trying to get done?" Sharper framing.

**Story:**
> Instead of asking "what B2B features do buyers want?", I asked "what job do they hire WhatsApp to do today?" The answer: find designs, share them with their own retail customers, and trust the price. So I designed the platform to do those three jobs *better* than WhatsApp — not to replace WhatsApp wholesale. Sharing-back-to-WhatsApp became a first-class feature, not an afterthought.

---

## Q: How do you identify the right success metrics?

**Short answer:**
> Tie metrics to the original problem statement. If the problem was "onboarding takes too long," success has to include onboarding speed. Distinguish leading indicators (early signals) from lagging indicators (eventual outcomes). Avoid vanity metrics — total page views, total signups — that can grow without value.

**Story:**
> For Panini, I picked onboarding speed (new retailer ready to browse in <15 min), order capture rate (≥30% of orders originate on the platform), and quality (near-zero pricing errors). I deliberately did NOT pick "number of products in catalog" or "page views" — vanity metrics that move easily but don't prove the product is solving the actual problems.

---

## Q: How do you handle scope creep during discovery?

**Short answer:**
> The product brief is my anchor. Any new feature gets evaluated against the goals and out-of-scope list. If it serves a goal we explicitly haven't committed to, it goes on Phase 2 — not into MVP. The discipline isn't refusing ideas; it's deferring them with respect.

**Story:**
> Drafting Panini's brief, I caught myself adding multi-tenancy because we *might* sell the product to other manufacturers later. The founder pushed back — pointed out that other manufacturers' requirements would diverge enough that multi-tenancy upfront wouldn't actually save time. He was right. I caught my own scope creep and explicitly added "multi-tenancy" to the out-of-scope list.

---

## Q: What's the difference between a Product Brief, a PRD, and a One-Pager?

**Short answer:**
> All three are alignment documents differing in depth. **One-Pager** (Product Brief) is highest-level — problem, users, strategy, metrics. Read in 5 minutes. **PRD** is more detailed — user stories, functional requirements, edge cases. Reads in 30 minutes. Amazon uses a 6-pager narrative between the two. Skipping the one-pager and going straight to PRD often means specifying a solution before agreeing on the problem.

---

## Updates log

| Date | Added |
|------|-------|
| 2026-05-08 | Initial set: 6 questions covering discovery process, JTBD, metrics, scoping, vocabulary |
